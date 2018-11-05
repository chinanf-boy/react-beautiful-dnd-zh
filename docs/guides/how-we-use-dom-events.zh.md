# 我们如何使用DOM事件

> 这个页面详细介绍了我们如何使用DOM输入事件,我们如何使用它们,以及如何在我们的使用之上构建事物.**通常,您不需要知道此信息**但是,如果您还将自己的事件处理程序绑定到窗口或a*拖动手柄*.⚠️注意:由于a[webkit中的错误](https://bugs.webkit.org/show_bug.cgi?id=184250),特别是诸如此类事件`mousemove`将无法正确设置`event.defaultPrevented`至`true`什么时候`event.preventDefault()`叫做.您可以关注此问题的进展[这里](https://github.com/atlassian/react-beautiful-dnd/issues/413).

## 先验知识

本页假定您具有DOM事件的工作知识.有关DOM事件的详细介绍,请参阅:

-   [浏览器事件简介](https://javascript.info/introduction-browser-events)
-   [事件捕获和冒泡的工作原理](https://javascript.info/bubbling-and-capturing)

## 安全事件绑定

无需深入了解下面的所有细节,这里是最安全的事件处理程序`react-beautiful-dnd`:

> 这些可以添加到*拖动手柄*,树上任何其他地方或直接窗口.

-   `onClick`:`event.defaultPrevented`属性将设置为`true`如果作为拖动交互的一部分发生.即使拖动未通过诸如之类的预先单击操作完成,也是如此`mouseup`要么`touchend`.看到[邋click点击和点击预防](https://github.com/atlassian/react-beautiful-dnd#sloppy-clicks-and-click-prevention-).
-   `onKeyDown`:`event.defaultPrevented`属性将设置为`true`如果它被用作拖拽的一部分.如果你添加`onKeyDown`到了*拖动手柄*你将需要猴子补丁[`DragHandleProps`](https://github.com/atlassian/react-beautiful-dnd#draghandleprops-type-information) `onKeyDown`事件处理程序

您可能需要使用来自的信息来提高事件处理程序的逻辑[`onDragStart`](https://github.com/atlassian/react-beautiful-dnd#ondragstart-optional)和[`onDragEnd`](https://github.com/atlassian/react-beautiful-dnd#ondragend-required)了解在这些事件发生时是否发生阻力.

欢迎您添加其他事件处理程序,但您可能更依赖`onDragStart`和`onDragEnd`信息.

## 通用规则

### 事件预防

当我们使用输入事件作为拖放交互的一部分时,我们通常会调用`event.preventDefault()`在事件上选择退出事件的标准浏览器行为.我们**不要停**我们称之为事件的传播`event.preventDefault()`即使我们可以使用一个`mousemove`拖动事件**我们不会阻止**该事件发布(传播)并由您的事件处理程序接收.

-   我们用:`event.preventDefault()`
-   我们不使用:`event.stopPropagation()`

我们添加了一些事件处理程序*拖动手柄*本身(见[`DragHandleProps`](https://github.com/atlassian/react-beautiful-dnd#draghandleprops-type-information))和我们添加的其他人`window`在里面[捕获阶段](https://javascript.info/bubbling-and-capturing#capturing).这意味着只要您在中使用事件处理程序[冒泡阶段](https://javascript.info/bubbling-and-capturing#bubbling)(这是事件处理程序的默认设置)然后事件的行为将如此页面所述.

为了知道我们是否已经将事件用于拖放的目的,您需要检查[`event.defaultPrevented`](https://developer.mozilla.org/en-US/docs/Web/API/Event/defaultPrevented)属性.

所以假设你要添加一个窗口`click`处理程序.你可以这样做:

```js
window.addEventListener('click', (event: MouseEvent) => {
  // event has already been used for drag and drop
  if (event.defaultPrevented) {
    return;
  }

  doMyCoolThing();
});
```

### 直接和间接的行动

某些用户事件会对拖动产生直接影响:例如a`mousemove`用鼠标拖动时**向上箭头** <kbd>↑</kbd> `keydown`用键盘拖动时的事件.这些直接事件将有`event.preventDefault()`呼吁他们阻止他们的默认浏览器行为.有些事件间接影响了诸如a之类的拖拽`resize`取消阻力的事件.对于间接影响拖动的事件,我们不会调用`event.preventDefault()`在他们.通常影响拖拽的间接事件是取消阻力的事件,例如`reize`要么`orientationchange`事件.

## 鼠标拖动🐭

### 初始`mousedown`

-   `preventDefault()` **被召唤`mousedown`**😞

> 这是我们规则集中唯一已知的例外.不幸的是,这是第一个出现在本指南中的!

当用户第一次执行时`mousedown`在...上*拖动手柄*我们不确定他们是否打算点击或拖动.理想情况下,我们不会打电话`preventDefault()`因为我们不确定它是否是拖累的一部分.但是,我们需要打电话`preventDefault()`为了避免项目获得焦点,因为它有一个`tabIndex`.

### 我们还不确定是否会开始拖累

-   `preventDefault()`没有被召唤`mousemove`

在我们将运动视为阻力之前,用户需要移动一个小阈值.在这段时间我们不打电话`preventDefault()`任何`mousemove`事件,因为我们不确定他们是拖动还是只是执行[马虎点击](https://github.com/atlassian/react-beautiful-dnd#sloppy-clicks-and-click-prevention-)

### 用户表示他们不是鼠标拖动

-   `preventDefault()`没有调用导致挂起拖动结束的事件(例如`mouseup`和`keydown`).任何`keydown`在有挂起拖动时被激活的事件将被视为间接取消
-   `preventDefault()`随后没有调用`click`事件,如果有的话

### 鼠标拖动已经开始,用户现在正在拖动

-   `preventDefault()`被召唤`mousemove`事件
-   `preventDefault()`被召集的几个人`keydown`阻止其标准浏览器行为的事件
-   `preventDefault()`没有被召唤`keyup`事件即使是`keydown`被阻止了

### 阻力正在结束

-   `preventDefault()`被召唤`mouseup`如果它结束了阻力
-   `preventDefault()`被召唤**逃逸** <kbd>退出</kbd> `keydown`如果它结束拖动,因为它直接结束拖动
-   `preventDefault()`被称为下一个`click`无论阻力如何结束,都会发生事件.看到[邋click点击和点击预防](https://github.com/atlassian/react-beautiful-dnd#sloppy-clicks-and-click-prevention-)
-   `preventDefault()`不会在其他事件上调用`resize`间接结束了拖累
-   `preventDefault()`没有被召唤`keyup`事件,即使他们导致阻力结束

## 触摸拖动📱

> 触摸拖动的逻辑与鼠标拖动的工作方式类似

### 初始`touchstart`

-   `preventDefault()`没有被召唤`touchstart`.

当用户按下他们的手指(或其他输入)时`Draggable`我们不确定他们是否打算这样做*龙头*,*迫使压力*,*滚动容器*要么*拖动*.因为我们不知道用户想要做什么,但我们不打电话`preventDefault()`在这个事件上.

### 用户表示他们没有触摸拖动

-   `preventDefault()`不会在任何事件上被调用

用户可以通过将手指👇在元件上保持一小段时间来开始拖动🕑(长按).如果用户在此期间移动`touchmove`然后我们不打电话`preventDefault()`在这个事件上.

可以通过诸如之类的过度事件来取消触摸拖动`orientationchange`或者a`touchcancel`.我们不打电话`preventDefault`在这些事件上.

### 触摸拖动已开始,用户现在正在拖动

-   `preventDefault()`被召唤`touchmove`事件

✌️

### 触摸拖动正在结束

-   `preventDefault()`被召唤`touchend`
-   `preventDefault()`被召唤`touchcancel`
-   `preventDefault()`被召唤**逃逸** <kbd>退出</kbd> `keydown`作为直接取消.`preventDefault()`不是任何其他人的电话`keydown`因为它是间接取消.
-   `preventDefault()`不会在其他事件上调用`orientationchange`这可以取消阻力

### 强行压力

> 看到[强迫支持](https://github.com/atlassian/react-beautiful-dnd#force-press-support)

-   `preventDefault()`没有被召唤`touchforcechange`如果拖动尚未开始
-   `preventDefault()`没有被召唤`touchforcechange`已经开始但尚未发生移动的拖拽.强制按下取消拖动并且是间接取消.
-   `preventDefault()`在打完之后打电话`touchforcechange`阻力已经开始了`touchmove`已经解雇了.作为一种力量压力,这是防御性的`touchforcechange`之后不应该发生`touchmove`.

## 键盘拖动🎹

> 我们只用`keydown`用于键盘拖动的事件`keyup`事件从来没有`preventDefault()`呼唤他们

### 拖动开始

> `preventDefault()`被召唤`keydown`

与鼠标拖动不同,键盘拖动会在用户按下时立即开始**空格键** <kbd>空间</kbd>.这个初始的键盘交互有`event.preventDefault()`呼吁它.

### 拖着

-   `preventDefault()`被召唤`keydown`如果事件被用作拖动的一部分(例如**向上箭头** <kbd>↑</kbd>)
-   `preventDefault()`被召唤`keydown`事件是我们想要阻止标准浏览器行为(例如`enter`提交)
-   `preventDefault()`没有被召唤`keydown`我们不用于拖动的事件

### 拖动结束

-   `preventDefault()`被召唤`keydown`如果是的话**空格键** <kbd>空间</kbd>键,因为它正在丢弃该项目
-   `preventDefault()`被召唤`keydown`如果是的话**逃逸** <kbd>退出</kbd>键,因为它明确取消拖动
-   `preventDefault()`不会在间接取消拖动的事件上调用,例如`resize`要么`mousedown`.
