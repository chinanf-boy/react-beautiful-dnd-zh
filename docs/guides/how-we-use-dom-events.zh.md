# 我们如何使用DOM事件

> 这个页面详细介绍了我们如何使用DOM输入事件,我们对它们做了什么，以及如何在我们的使用之上构建工作。**通常,您不需要知道此信息**但是,如果您还将自己的事件处理程序绑定到 window 或 一个*拖动控制*，这些信息会有用。

> ⚠️注意:由于[webkit中的一个错误](https://bugs.webkit.org/show_bug.cgi?id=184250),特别是当`event.preventDefault()`被调用，诸如类`mousemove`事件将无法正确设`event.defaultPrevented`为`true`。您可以关注此问题的进展在[这里](https://github.com/atlassian/react-beautiful-dnd/issues/413).

## 知识预备

本页假定您具有DOM事件的工作知识。有关DOM事件的详细介绍,请参阅:

-   [浏览器事件简介](https://javascript.info/introduction-browser-events)
-   [捕获事件和冒泡的工作原理](https://javascript.info/bubbling-and-capturing)

## 安全事件绑定

无需深入了解下面的所有细节,这里是`react-beautiful-dnd`最上层的最高安全的事件处理程序:

> 这些都可以添加到*拖动控制*，'树'上任何其他地方或直接在window.

-   `onClick`:如果作为拖动交互部分发生了，`event.defaultPrevented`属性将设置为`true`。即使拖动未完成诸如`mouseup`或`touchend`之类的预先单击操作。看[马虎点击和点击预防](https://github.com/atlassian/react-beautiful-dnd#sloppy-clicks-and-click-prevention-).
-   `onKeyDown`:如果它被用作拖拽的一部分，`event.defaultPrevented`属性将设置为`true`。如果你想添加`onKeyDown`到*拖动控制*，你将需要猴子补丁 下[`DragHandleProps`](https://github.com/atlassian/react-beautiful-dnd#draghandleprops-type-information) `onKeyDown`事件处理程序

您可能需要使用来自[`onDragStart`](https://github.com/atlassian/react-beautiful-dnd#ondragstart-optional)和[`onDragEnd`](https://github.com/atlassian/react-beautiful-dnd#ondragend-required)的信息来提高事件处理程序的逻辑了解，明确知道在这些事件发生时，是否’交火‘了.

欢迎您添加其他事件处理程序,但您可能更需要`onDragStart`和`onDragEnd`的信息.

## 通用规则

### 事件预防

当我们使用输入事件作为拖放交互的一部分时,我们通常会调用`event.preventDefault()`函数，此函数会退出标准浏览器的事件行为。当调用`event.preventDefault()`，也**不会停止**我们事件的传播，所有即使我们使用一个`mousemove`拖动事件，**我们也不会阻止**该事件发布(传播)，最后被您的事件处理程序接收.

-   我们用:`event.preventDefault()`
-   我们不使用:`event.stopPropagation()`

我们添加了一些事件处理程序到*拖动控制*本身(见[`DragHandleProps`](https://github.com/atlassian/react-beautiful-dnd#draghandleprops-type-information))和我们又添加了其他的到`window`在里面[捕获阶段](https://javascript.info/bubbling-and-capturing#capturing)。这意味着只要您在[冒泡阶段](https://javascript.info/bubbling-and-capturing#bubbling)中使用事件处理程序(这是事件处理程序的默认设置)，然后事件的行为将如此页面所述.

为了知道我们是否已经把事件用在了拖放功能，您需要检查[`event.defaultPrevented`](https://developer.mozilla.org/en-US/docs/Web/API/Event/defaultPrevented)属性.

所以假设你要添加一个window的`click`处理程序。你可以这样做:

```js
window.addEventListener('click', (event: MouseEvent) => {
  // 事件 已用于 drag 和 drop
  if (event.defaultPrevented) {
    return;
  }

  doMyCoolThing();
});
```

### 直接和间接的行动

某些用户事件会对拖动有直接影响:例如当鼠标拖动时的一个`mousemove`或用键盘**向上箭头** <kbd>↑</kbd>拖动时的`keydown`事件。这些直接事件都会有`event.preventDefault()`的调用，以此来阻止他们的默认浏览器行为。有些事件则会间接影响了，如当取消拖动时的`resize`事件之类。对于间接影响拖动的事件,并不会调用`event.preventDefault()`。影响拖拽的间接事件通常以取消拖动为主，例如`reize`或`orientationchange`事件.

## 鼠标拖动🐭

### 初始`mousedown`

-   `preventDefault()`会 **被调用**😞

> 这是我们规则集合中的唯一已知的例外。不幸的是,这只是第一个!

当用户第一次在*拖动控制*上触及`mousedown`时，我们不确定他们是否打算点击或拖动。理想情况下,我们不会调用`preventDefault()`，因为我们不确定它是否是拖动的一部分.但是,我们需要调用`preventDefault()`，这样是为了避免项目获得焦点,因为它有一个`tabIndex`.

### 我们还不确定是否会开始拖动

-   `preventDefault()`没有被调用

在我们将运动视为拖动之前,用户需要移动一个小阈值。在这段时间我们不会在`任何`mousemove`事件调用`preventDefault(),因为我们不确定他们是拖动还是，只是[马虎点击](https://github.com/atlassian/react-beautiful-dnd#sloppy-clicks-and-click-prevention-)

### 用户表示他们不是鼠标拖动

-   `preventDefault()`没有调用，因有让拖动结束的事件(例如`mouseup`和`keydown`)。在有挂起拖动时，任何`keydown`事件被激活将被视为间接取消拖动
-   `preventDefault()`并不调用在随后的`click`事件,如果有的话

### 鼠标拖动已经开始,用户现在正在拖动

-   `preventDefault()`在`mousemove`事件中被调用
-   `preventDefault()`在少数`keydown`事件中被调用，阻止其标准浏览器行为的事件
-   `preventDefault()`在`keyup`事件中没有被调用，即使`keydown`被阻止了

### 拖动正在结束

-   `preventDefault()`在一个`mouseup`中被调用，如果它结束了拖动
-   `preventDefault()`在**退出** <kbd>esc</kbd> `keydown`中被调用，如果因为它直接结束拖动
-   `preventDefault()`在下一个`click`事件时被调用，不管拖动是如何结束,都会发生事件.看[马虎点击和点击预防](https://github.com/atlassian/react-beautiful-dnd#sloppy-clicks-and-click-prevention-)
-   `preventDefault()`不会在其他事件上调用，如`resize`间接结束了拖动
-   `preventDefault()`在`keyup`事件不会被调用,即使它们导致拖动结束

## 触摸拖动📱

> 触摸拖动的逻辑与鼠标拖动的工作方式类似

### 初始`touchstart`

-   `preventDefault()`在`touchstart`没有被调用.

当用户在`Draggable`上按下他们的手指(或其他输入)时，我们不确定他们是否打算去*单点*,*重压*,*滚屏*要么*拖动*。因为我们不知道用户想要做什么, 反正我们不调用`preventDefault()`在这个事件上.

### 用户表示他们没有触摸拖动

-   `preventDefault()`不会在任何事件上被调用

用户可以通过将手指👇在元素组件上保持一小段时间🕑(长按)来开始拖动.如果用户在这段时间内，移动了，触发`touchmove`事件，那我们在这个事件上不调用`preventDefault()`.

可通过如一个`orientationchange`或者一个`touchcancel`之类的时间取消触摸拖动。在这些事件上我们都不会调用`preventDefault`.

### 触摸拖动已开始,用户现在正在拖动

-   `preventDefault()`在`touchmove`事件上被调用

✌️

### 触摸拖动正在结束

-   `preventDefault()`在`touchend`事件上被调用
-   `preventDefault()`在`touchcancel`事件上被调用
-   `preventDefault()`在作为直接取消的**退出** <kbd>esc</kbd> `keydown`上调用。`preventDefault()`在任何其他`keydown`事件不调用，因为哪些事件是间接取消.
-   `preventDefault()`不会在其他如`orientationchange`事件上调用，因其可取消拖动

### 大力按压

> 看[大力按压支持](https://github.com/atlassian/react-beautiful-dnd#force-press-support)

-   如果拖动尚未开始，`preventDefault()`没有被调用`touchforcechange`
-   如果拖动已经开始但尚未发生移动，`preventDefault()`没有被调用`touchforcechange`。重压会取消拖动且是间接取消.
-   在拖动的`touchforcechange`已经开始和`touchmove`已经结束了之后，`preventDefault()`调用。这是为了防范`touchmove`之后`touchforcechange`不应该发生.

## 键盘拖动🎹

> 我们只用`keydown`事件应对用于键盘拖动，所以`keyup`事件中从来没有调用过`preventDefault()`

### 拖动开始

> `preventDefault()`在`keydown`被调用

与鼠标拖动不同,键盘拖动会在用户按下**空格键** <kbd>空间</kbd>时，立即开始。这个初始的键盘交互就会有`event.preventDefault()`调用.

### 拖着

-   如果事件被用作拖动的一部分(例如**向上箭头** <kbd>↑</kbd>)，`preventDefault()`在`keydown`被调用
-   当我们想要阻止标准浏览器行为(例如`enter`键入)，`preventDefault()`在`keydown`事件被调用
-   若我们不用于拖动的事件，`preventDefault()`在`keydown`上没有被调用，

### 拖动结束

-   如果是**空格键** <kbd>space</kbd>键的话，`preventDefault()`在`keydown`被调用，因为它正在放下
-   如果是**退出** <kbd>esc</kbd>键的话，`preventDefault()`在`keydown`被调用,因为它明确取消拖动
-   `preventDefault()`不会在间接取消拖动的事件上调用,例如`resize`要么`mousedown`.
