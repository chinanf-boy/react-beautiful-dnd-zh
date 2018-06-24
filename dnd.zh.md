
![react beautiful dnd](https://raw.githubusercontent.com/alexreardon/files/master/resources/react-beautiful-dnd-logo.png)

# 反应 - 美丽 - 免打扰

美丽,可访问的拖放列表与[`React.js`](https://facebook.github.io/react/)

[![Build Status](https://travis-ci.org/atlassian/react-beautiful-dnd.svg?branch=master)](https://travis-ci.org/atlassian/react-beautiful-dnd) [![npm](https://img.shields.io/npm/v/react-beautiful-dnd.svg)](https://www.npmjs.com/package/react-beautiful-dnd) [![dependencies](https://david-dm.org/atlassian/react-beautiful-dnd.svg)](https://david-dm.org/atlassian/react-beautiful-dnd) [![Greenkeeper badge](https://badges.greenkeeper.io/atlassian/react-beautiful-dnd.svg)](https://greenkeeper.io/) [![SemVer](https://img.shields.io/badge/SemVer-2.0.0-brightgreen.svg)](http://semver.org/spec/v2.0.0.html)

![quote application example](https://raw.githubusercontent.com/alexreardon/files/master/resources/website-board.gif?raw=true)

## 例子🎉

看看它对你自己有多美丽!

### 在桌面上查看

[所有的例子!](https://react-beautiful-dnd.netlify.com)

### 在手机或平板电脑上查看

-   [简单的列表](https://react-beautiful-dnd.netlify.com/iframe.html)
-   [板](https://react-beautiful-dnd.netlify.com/iframe.html?selectedKind=board&selectedStory=simple)- 最好在风景中观看

> 目前,我们为触摸设备提供不同的链接[故事书](https://github.com/storybooks/storybook)没有很好的移动菜单体验[更多信息](https://github.com/storybooks/storybook/issues/124)

## 基本使用示例

我们已经创建了一些基本的例子`codesandbox`为你直接玩: 

-   [简单的垂直列表](https://codesandbox.io/s/k260nyxq9v)
-   [简单的水平列表](https://codesandbox.io/s/mmrp44okvj)
-   [两个列表之间的简单DnD](https://codesandbox.io/s/l7ro2231o7)

> 即将推出: 获取入门指南!

## 升级

我们在发行说明中创建了升级说明,以帮助您升级到最新版本!

-   [从...升级`6.x`至`7.x`](https://github.com/atlassian/react-beautiful-dnd/releases/tag/v7.0.0)
-   [从...升级`5.x`至`6.x`](https://github.com/atlassian/react-beautiful-dnd/releases/tag/v6.0.0)
-   [从...升级`4.x`至`5.x`](https://github.com/atlassian/react-beautiful-dnd/releases/tag/v5.0.0)
-   [从...升级`3.x`至`4.x`](https://github.com/atlassian/react-beautiful-dnd/releases/tag/v4.0.0)

## 核心特点

-   美丽,自然的物品移动
-   清洁且功能强大的api简单易用
-   与标准浏览器交互非常好
-   Unopinionated样式
-   没有创建额外的包装DOM节点 -  flexbox和焦点管理友好!
-   无障碍

## 目前支持的功能集

-   垂直列表↕
-   水平列表↔
-   列表之间的移动 (▤↔▤) 
-   鼠标🐭,键盘🎹和触摸👉📱 (手机,平板电脑等) 支持
-   自动滚动 - 在拖动过程中根据需要自动滚动容器和窗口 (即使使用键盘🔥) 
-   [多拖动支持](/docs/patterns/multi-drag.md)
-   令人难以置信的屏幕阅读器支持 - 我们为开箱即用的英文屏幕阅读器提供了惊人的体验. 我们还为需要它的人提供完整的定制控制和国际化支持
-   条件[拖延](https://github.com/atlassian/react-beautiful-dnd#props-1)和[落下](https://github.com/atlassian/react-beautiful-dnd#conditionally-dropping)
-   在一个页面上有多个独立的列表
-   灵活的项目大小 - 可拖动的项目可以有不同的高度 (垂直列表) 或宽度 (水平列表) 
-   与语义表重新排序兼容 -[表格模式](/docs/patterns/tables.md)
-   与...兼容[`React.Portal`](https://reactjs.org/docs/portals.html)-[门户模式](/docs/patterns/using-a-portal.md)
-   自定义拖动手柄 - 您可以通过拖动整个项目的一部分
-   一个`Droppable`列表可以是滚动容器 (没有可滚动的父项) 或者是滚动容器的子项 (也没有可滚动的父项) 
-   独立的嵌套列表 - 列表可以是另一个列表的子项,但不能将项目从父列表拖到子列表中
-   服务器端渲染兼容
-   和...一起玩[嵌套的交互式元素](https://github.com/atlassian/react-beautiful-dnd#interactive-child-elements-within-a-draggable)默认

### 更多即将推出

您可以查看即将登陆的所有功能[在我们的问题页面上](https://github.com/atlassian/react-beautiful-dnd/issues). 

## 并不适合所有人

有很多库允许React中的拖放交互. 其中最值得注意的是惊人的[`react-dnd`](https://github.com/react-dnd/react-dnd). 它提供了一套非常出色的拖放原语,这些原语在特定情况下非常适用[疯狂地不一致](https://www.quirksmode.org/blog/archives/2009/09/the_html5_drag.html)html5拖放功能. `react-beautiful-dnd` **是为垂直和水平列表专门构建的更高级别的抽象**. 在该功能的子集内`react-beautiful-dnd`提供强大,自然和美丽的拖放体验. 但是,它没有提供react-dnd提供的广泛功能. 所以这个库可能不适合你,这取决于你的用例是什么. 

## 驾驶理念: 物理性

核心设计理念`react-beautiful-dnd`是物质性的: 我们希望用户感觉他们正在移动物体

### 应用1: 没有即时移动

这是一个相当标准的拖放模式,用于响应用户拖动而消失并重新出现的东西. 对于更自然的拖动,我们为物品的移动设置动画,因为它们需要在拖动时偏移以更清晰地显示拖动效果. 我们还制作了一件物品的下落,以便将其移动到新的位置. 在任何时候,物品都不会随时随地移动 - 无论它是否在拖动. 

### 应用2: 知道何时移动

拖放交互基于用户开始拖动的位置很常见. 

在`react-beautiful-dnd`拖动物品的影响是基于其重心 - 无论用户从哪里抓取物品. 拖动项目的影响遵循类似的规则a️. 以下是一些遵循的规则,即使对于灵活高度的物品也可以实现自然的拖拽体验: 

-   列表是*拖过去*当拖动项目的中心位置越过列表的边界之一时
-   当拖动物品的中心位置越过休息物品的边缘时,休息拖动物品将移出拖动物品的路线. 换句话说: 一旦物品 (A) 的中心位置越过另一物品 (B) 的边缘,B就会移开. 

### 应用程序3: 没有阴影

在物品及其目的地四处移动的环境中,阴影很有用. 但是,与`react-beautiful-dnd`根据物品的移动情况,物品的放置位置应该很明显. 这可能会在未来发生变化 - 但实验是要看看我们能够在没有任何这些可供选择的情况下获得多少. 

### 应用4: 最大化交互性

`react-beautiful-dnd`真的很难避免尽可能多的非互动性阶段. 用户应该觉得他们在控制界面,而不是等待动画完成,然后才能继续与界面交互. 然而,为了让每个人的生活更加健康,在正确性和权力之间需要做出平衡. 以下是有些事情不具有互动性的唯一情况: 

1.  从用户取消拖动到拖放动画完成时. 取消时有很多事情要回到他们应该在的地方. 如果您在不是真正的家的位置抓取物品,则以下拖动将不正确. 
2.  开始拖动动画自己放置的项目. 为了简单起见,情况就是这样 - 在家动画的时候实际上很难抢东西. 它可以被编码 - 但它似乎是一个边缘案例,会增加很多复杂性. 

请记住,这些不活动时间可能并不总是存在. 

### 应用5: 无拖动轴锁定

目前,库不支持拖动轴锁定 (又名拖轨) . 这是用户被限制在只沿一个轴拖动的地方. 目前的想法是,这打破了我们正在寻找的物理隐喻,并向用户发送一条消息,即他们正在与一个软件进行交互,而不是移动物理对象. 可以确保用户只能通过使用道具放入单个列表中`type`和`isDropDisabled`. 您也可以对列表进行一些视觉处理`onDragStart`向用户显示这是他们唯一可以与之互动的地方. 

### 应用6: 自然交叉表移动

而不是使用基于索引的方法在列表之间移动键盘,`react-beautiful-dnd`基于. 执行交叉表移动**惯性,重力和碰撞**. 您可以通过阅读博客了解更多关于这是如何工作的["列表之间的自然键盘移动"](https://medium.com/@alexandereardon/friction-gravity-and-collisions-3adac3a94e19). 

![example](https://raw.githubusercontent.com/alexreardon/files/master/resources/collision.gif?raw=true)

## 精心设计的动画

随着事情的发展,用户会很容易被动画分散注意力或阻碍他们前进. 我们调整了各种动画,以确保指导,表演和互动性之间的平衡. 

### 删除

当你拖放一个拖动项目时,它的运动是基于物理的 (谢谢[`react-motion`](https://github.com/chenglou/react-motion)) . 这导致下降感觉更加重和物理. 

### 走出困境

移出拖动项目的项目是通过CSS过渡而非物理过程来实现的. 这是通过允许GPU处理运动来最大化性能. CSS动画曲线的设计是为了避免沟通. 

它是如何组成的: 

1.  一个模拟自然反应时间的热身期
2.  一个小阶段,可以快速移除
3.  长尾巴,以便人们可以阅读动画后半部分正在动画的任何文字

![animation curve](https://raw.githubusercontent.com/alexreardon/files/master/resources/dnd-ease-in-out-small.png?raw=true)

> 动画曲线在移动时使用

## 关心交互细节

### 重点管理

`react-beautiful-dnd`不会创建任何包装元素. 这意味着它不会影响文档的常用选项卡流程. 例如,如果你正在包装一个*锚*标签,则用户将直接标签到锚点,而不是围绕该标签的元素*锚*. 无论你包装什么元素都会得到一个`tab-index`以确保用户可以选择要素以执行键盘拖动. 

### 自动滚动

当用户拖动一个`Draggable`靠近边缘*容器*我们会自动滚动容器,以便为其腾出空间`Draggable`. 

> 一个*容器*是一个`Droppable`这是可滚动的或有一个滚动父 - 或`window`. 

| 鼠标和触摸                                                                                                                     | 键盘                                                                                                                           |
| ------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| ![auto-scroll-mouse](https://user-images.githubusercontent.com/2182637/36520373-c9e2cb7e-17e4-11e8-9e93-4d2389d51fa4.gif) | ![auto-scroll-keyboard](https://user-images.githubusercontent.com/2182637/36520375-cc1aa45c-17e4-11e8-842d-94aed694428a.gif) |

它也适用于所有输入类型的多列表配置

| 鼠标和触摸                                                                                                                           | 键盘                                                                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| ![auto-scroll-board-mouse](https://user-images.githubusercontent.com/2182637/36520670-57752526-17e6-11e8-95b3-b5a3978a5312.gif) | ![auto-scroll-board-keyboard](https://user-images.githubusercontent.com/2182637/36520650-3d3638f8-17e6-11e8-9cba-1fb439070285.gif) |

#### 对于鼠标和触摸输入🐭📱

当一个中心`Draggable`在距离容器边缘很小的距离内,我们开始自动滚动. 随着用户靠近容器的边缘,我们增加了自动滚动的速度. 这种加速度使用缓动功能来指数地增加我们移向边缘越近的加速度. 我们从容器的真实边缘到达最大加速度,使得用户不需要非常精确以获得最大的滚动速度. 该逻辑适用于可滚动的任何边缘. 

自动滚动所需的距离分别基于容器的垂直和水平滚动的高度或宽度的百分比. 通过使用百分比而不是原始像素值,无论容器的大小和形状如何,我们都可以获得丰富的体验. 

##### 鼠标滚轮和触控板

除了自动滚动,我们还允许用户滚动窗口或a`Droppable`手动使用他们的*鼠标滚轮*要么*触控板*👌

##### 关于大的一个笔记`Draggable`小号

如果`Draggable`比您要滚动的轴上的容器大 - 我们将不允许在该轴上滚动. 例如,如果你有一个`Draggable`这比窗口的高度更长,我们不会自动垂直滚动. 不过,我们仍然会允许水平滚动. 

##### iOS自动滚动摇晃📱🤕

当在iOS浏览器 (webkit) 上自动滚动时`Draggable`明显地震动. 这是由于一个[与webkit的错误](https://bugs.webkit.org/show*bug.cgi?id=181954)没有已知的工作. 我们尝试了很长时间来解决这个问题!如果你看到这种改进感兴趣,请与我们联系[webkit问题](https://bugs.webkit.org/show*bug.cgi?id=181954). 

#### 用于键盘拖动🎹

拖动键盘时,我们也会根据需要正确更新滚动位置. 为了移动一个`Draggable`进入正确的位置,我们可以做一个组合`Droppable`滚动,`window`滚动和手动移动以确保`Draggable`响应用户移动指令结束在正确的位置. 这是老板🔥. 

对于有视觉障碍的用户来说,这是惊人的,因为他们可以在大列表中正确移动项目而无需使用鼠标定位. 

### 无障碍

传统上,拖放交互一直是鼠标或触摸交互. 这个库支持拖放交互**只使用键盘**. 这使高级用户可以完全从键盘上获得他们的体验. 以及向以前被排除在外的用户开放这些体验. 

我们提供**对屏幕阅读器的精彩支持**帮助视觉 (或其他) 损伤的用户. 我们随机附带英文短信📦. 但是,欢迎您使用. 覆盖这些消息`announce`它提供给所有的函数`DragDropContext > hook`功能. 

见我们的[屏幕阅读器指南](docs/guides/screen-reader.md)为指导制作有用的屏幕阅读器信息. 

#### 示例屏幕阅读器行为

![screen-reader-text](https://user-images.githubusercontent.com/2182637/36571009-d326d82a-1888-11e8-9a1d-e44f8b969c2f.gif)

## 鼠标拖动

### 马虎点击并点击预防🐱🎁

当用户在元素上按下鼠标时,我们无法确定用户是在点击还是在拖动. 另外,有时当用户点击时,他们可以稍微移动光标 - 一个马虎的点击. 所以我们只有在用户用鼠标向下移动超过一定距离时才会开始拖拽 (拖拽阈值)  - 如果他们只是马上点击,它们会比他们更多. 如果没有超过拖拽阈值,则用户交互就像常规点击一样. 如果超过了拖拽阈值,则该交互将被分类为拖拽并且不会发生标准点击行为. 

这允许消费者包装诸如锚的交互元素,并且以自然的方式使其既是标准锚也是可拖动项. 

 (🐱🎁是一个[薛定谔的猫](https://www.youtube.com/watch?v=IOYyCHGWJq4)玩笑) 

> 要查看更多关于我们如何影响标准浏览器事件的深入信息,请参阅我们的[我们如何使用DOM事件指南](docs/guides/how-we-use-dom-events.md)

### 键盘快捷键: 鼠标拖动

当一个拖动**没有发生** `react-beautiful-dnd`不会影响任何标准键盘交互 (它没有绑定的监听器) . 

当一个拖动**正在发生**与*老鼠*用户可以执行以下键盘快捷键: 

-   **逃逸** <kbd>退出</kbd>- 取消拖动

在鼠标拖动过程中,以下标准键盘事件被阻止,以防止出现不好的体验: 

-   **标签** <kbd>标签↹</kbd>- 防止绊倒
-   **输入** <kbd>⏎</kbd>- 防止提交

除了这些明确禁止键盘事件外,所有标准键盘事件都应按预期工作. 

## 键盘拖动

`react-beautiful-dnd`仅支持使用键盘进行拖动. 我们审核了我们的键盘快捷键如何与标准浏览器键盘交互进行交互. 当用户没有拖动时,他们可以像平常一样使用键盘. 拖动时,我们覆盖并禁用某些浏览器快捷方式 (如`tab`) 以确保用户的流畅体验. 

> 要查看更多关于我们如何影响标准浏览器事件的深入信息,请参阅我们的[我们如何使用DOM事件指南](docs/guides/how-we-use-dom-events.md)

### 键盘快捷键: 键盘拖动

当没有发生拖动时,用户将能够浏览`Draggable`在使用该标准的页面上**标签** <kbd>标签↹</kbd>通过可放置元素前进的关键和 (**转移**+**标签**)  (<kbd>转移</kbd>+) <kbd>标签↹</kbd>) 向后移动. 我们通过添加一个`tab-index`到了`Draggable`. 当一个`Draggable`已经集中了**空格键** <kbd>空间</kbd>将**电梯**一个`Draggable`. 这将开始拖动. 

一旦开始拖动,可以使用以下键盘快捷键: 

-   **空格键** <kbd>空间</kbd>- 放下`Draggable`
-   **逃逸** <kbd>退出</kbd>- 取消拖动

以下命令也可用,但它们依赖于`type`的`Droppable`那个`Draggable`是*目前*在: 

#### 在一个垂直列表中

-   **向上箭头** <kbd>↑</kbd>- 移动一个`Draggable`向上`Droppable`
-   **向下箭头** <kbd>↓</kbd>- 移动一个`Draggable`向下在一个`Droppable`
-   **右箭头** <kbd>→</kbd>- 移动一个`Draggable`到一个`Droppable`到了*对*目前`Droppable` (移至新列表) 
-   **左箭头** <kbd>←</kbd>- 移动一个`Draggable`到一个`Droppable`到了*剩下*目前`Droppable` (移至新列表) 

#### 在一个水平列表中

-   **向上箭头** <kbd>↑</kbd>- 移动一个`Draggable`到一个`Droppable`至*以上*目前`Droppable` (移至新列表) 
-   **向下箭头** <kbd>↓</kbd>- 移动一个`Draggable`到一个`Droppable`至*下面*目前`Droppable` (移至新列表) 
-   **右箭头** <kbd>→</kbd>- 移动一个`Draggable`到了*对*在目前`Droppable`
-   **左箭头** <kbd>←</kbd>- 移动一个`Draggable`到了*剩下*在目前`Droppable`

在拖动过程中,以下标准键盘事件的默认行为被阻止 (通过`event.preventDefault()`) 以避免不好的体验: 

-   **标签** <kbd>标签↹</kbd>- 防止绊倒
-   **输入** <kbd>⏎</kbd>- 防止提交

## 触摸拖动

`react-beautiful-dnd`支持拖动手机和平板电脑等触摸设备. 

![Mobile landscape](https://github.com/alexreardon/files/blob/master/resources/iphone-landscape.gif?raw=true)

> 录制在iPhone 6s上

### 理解意图: 点击,强制按下,滚动并拖动

当用户按下他们的手指 (或其他输入) 时`Draggable`我们不确定他们是否有意*龙头*,*强制按压*,*滚动容器*要么*拖动*. **越多越好`react-beautiful-dnd`旨在确保用户默认的交互体验不受影响**. 

> 要查看更多关于我们如何影响标准浏览器事件的深入信息,请参阅我们的[我们如何使用DOM事件指南](docs/guides/how-we-use-dom-events.md)

### 开始拖动: 长按

用户可以通过在一个元素上长时间握住手指start开始拖动🕑 (长按) 

### 点按支持

如果用户在定时器完成之前提起手指,然后我们将该事件释放给浏览器,以确定是否执行标准的点击/点击操作. 这可以让你有一个`Draggable`这既是可点击的,例如锚点以及可拖动的. 如果该项目被拖动,那么我们会阻止点击操作的发生. 

### 原生滚动支持

如果我们发现一个`touchmove`在长按计时器到期之前,我们取消挂起的拖动并允许用户正常滚动. 这意味着用户需要相当有意和准确地抓住他们. 第一次`touchmove`发生时,我们必须选择是否加入本地滚动. 

-   如果长按定时器**没有**过期: *允许本地滚动并防止拖动*
-   如果长按定时器**具有**过期: *拖动已经开始,我们阻止本地滚动*

### 强制按压支持

> 只有Safari

如果用户在移动元素之前按下元素 (即使拖动已经开始) ,则拖动被取消并且发生标准的力按压操作. 对于一个锚点,这是一个网站预览. 

### 振动

> 这只是一个想法 - 如果你想要这种行为,你可以添加它. 

如果你喜欢,你也可以触发一个[振动事件](https://developer.mozilla.org/en-US/docs/Web/API/Vibration*API)当用户拿起一个`Draggable`. 这可以提供用户正在做的事情的触觉反馈. 目前仅在Android版Chrome中支持. 

```js
class App extends React.Component {
  onDragStart = () => {
    // good times
    if (window.navigator.vibrate) {
      window.navigator.vibrate(100);
    }
  };
  /*...*/
}
```

## 多拖

我们创造了一个[多拖动模式](/docs/patterns/multi-drag.md)你可以建立在顶部`react-beautiful-dnd`为了支持拖动多个`Draggable`项目一次. 

![multi drag demo](https://user-images.githubusercontent.com/2182637/37322724-7843a218-26d3-11e8-9ebb-8d5853387bb3.gif)

## 预设样式

我们应用了许多不可见的样式来促进拖拽体验. 我们使用造型目标和技术的组合来做到这一点. 图书馆的目标是提供无选择的造型. 但是,我们确实应用了一些合理的`cursor`默认情况下在拖动手柄上创建样式. 这是为了使图书馆尽可能简单地工作而设计的. 如果你想使用你自己的游标,你是不是欢迎. 您所需要做的就是通过使用规则来覆盖光标样式规则[特异性更高](https://css-tricks.com/specifics-on-css-specificity/). 

以下是在拖动生命周期中的各个点上应用的样式: 

### 在每个阶段

#### 总是: 拖动手柄

样式适用于: **拖动手柄元素**使用`data-react-beautiful-dnd-drag-handle`属性. 

长按锚点通常会弹出一个内容菜单,其中包含链接选项,例如"在新标签中打开". 由于长按是用来开始拖动,我们需要退出此行为

```css
-webkit-touch-callout: none;
```

基于Webkit的浏览器在锚点处于活动状态时为其添加灰色叠加层. 我们删除了这个龙头叠加层,因为它会让用户感到困惑. [更多信息](https://css-tricks.com/snippets/css/remove-gray-highlight-when-tapping-links-in-mobile-safari/). 

```css
-webkit-tap-highlight-color: rgba(0,0,0,0);
```

避免这种情况*拉动以刷新行动*和*延迟锚定焦点*在Android Chrome上

```css
touch-action: manipulation;
```

#### 始终: 可以丢弃

样式适用于: **droppable元素**使用`data-react-beautiful-dnd-droppable`属性. 

当浏览器功能试图保持滚动位置,当DOM变化超过折叠时,选择退出. 我们已经正确地保持滚动位置. 自动`overflow-anchor`行为导致错误的滚动定位后删除. 

```css
overflow-anchor: none;
```

### 阶段: 休息

####  (阶段: 休息) : 拖动手柄

样式适用于: **拖动手柄元素**使用`data-react-beautiful-dnd-drag-handle`属性. 

添加一个光标样式让用户知道这个元素是可拖动的. 欢迎您覆盖此. 

```css
cursor: grab;
```

### 阶段: 拖动

####  (阶段: 拖动) : 拖动句柄元素

**使用该样式应用的样式`data-react-beautiful-dnd-drag-handle`属性**

避免处理的优化`pointer-events`拖动时. 还用于允许通过带轨迹板或鼠标滚轮的拖动手柄进行滚动. 

```css
pointer-events: none;
```

####  (阶段: 拖动) : 可拖动的元素

**使用该样式应用的样式`data-react-beautiful-dnd-draggable`属性**

这是我们用来控制的`Draggable`这需要摆脱拖拉的方式`Draggable`. 

```css
transition: ${string};
```

**使用内联样式应用的样式**

这由类型描述[`DraggableStyle`](https://github.com/atlassian/react-beautiful-dnd#type-information-1). 

####  (阶段: 拖动) : body元素

我们在拖动时应用光标,以向用户反馈发生拖动的情况. 欢迎您覆盖此. 一个好的方面是做到这一点`onDragStart`事件. 

```css
cursor: grabbing;
```

为防止用户在拖动时选择文本,应用此样式

```css
user-select: none;
```

### 阶段: 下降

####  (阶段: 删除) : 拖动句柄元素

**使用该样式应用的样式`data-react-beautiful-dnd-drag-handle`属性**

我们将抓取光标应用于除拖动手柄之外的所有拖动手柄`Draggable`. 此时用户可以拖动其他`Draggable`如果他们喜欢的话. 

```css
cursor: grab;
```

####  (阶段: 下降) : 可拖动

与拖动阶段相同

### 阶段: 用户取消

> 当用户显式取消拖动时

这与之相同`Phase: dropping`. 但我们不适用`cursor: grab`拖动手柄. 在用户启动取消期间,我们不允许拖放其他项目,直到放下动画完成. 

### 预设样式是供应商的前缀

所有应用的样式都是供应商正确的前缀以符合我们的要求[支持浏览器矩阵](https://confluence.atlassian.com/cloud/supported-browsers-744721663.html). 这是手工完成的,以避免通过包含一个css-in-js库来增加react-beautiful-dnd的大小

## 安装

### 包管理器

```bash
# yarn
yarn add react-beautiful-dnd

# npm
npm install react-beautiful-dnd --save
```

### 分发包

一个[通用模块定义](https://github.com/umdjs/umd)捆绑发布于`npm`在下面`/dist`消耗文件夹. 我们发布以下文件: 

-   `dist/react-beautiful-dnd.js`
-   `dist/react-beautiful-dnd.min.js` (缩小束) 

这些捆绑列表`react`作为需要提供的外部. 这样做是为了减少捆绑包的大小并防止消费者加载`react`多次. 你可以提供`react`通过你的模块系统或简单地通过拥有`react`上`window`. 

您可以使用UMD运行`react-beautiful-dnd`直接在浏览器中. 

```html
<!-- peer dependency -->
<script src="https://unpkg.com/react@16.3.1/umd/react.development.js"></script>
<!-- lib (change x.x.x for the version you would like) -->
<script src="https://unpkg.com/react-beautiful-dnd@x.x.x/dist/react-beautiful-dnd.js"></script>
<!-- needed to mount your react app -->
<script src="https://unpkg.com/react-dom@16.3.1/umd/react-dom.development.js"></script>

<script>
  const React = window.React;
  const ReactDOM = window.ReactDOM;
  const { DragDropContext, Draggable, Droppable } = window.ReactBeautifulDnd;

  class App extends React.Component {
    //...
  }

  // You can use JSX if your environment supports it
  ReactDOM.render(React.createElement(App), document.getElementById('app'));
</script>
```

还有一个[示例codepen](https://codepen.io/alexreardon/project/editor/ZyNMPo)你可以使用这个安装方法来玩. 

## [`ClojureScript`](https://clojurescript.org/)

你可以消耗`react-beautiful-dnd`从内部`ClojureScript`运用[CLJSJS](https://cljsjs.github.io/)!

## API

好吧,进入有趣的东西 - 那么你如何使用图书馆?

## `DragDropContext`

为了使用拖放,你需要拥有你的部分`React`树,你想能够使用拖放在包裹在一个`DragDropContext`. 建议将您的整个应用程序包装在一个`DragDropContext`. 嵌套`DragDropContext`是的*不*支持的. 你将能够使用道具实现你想要的条件拖放`Droppable`和`Draggable`. 你可以想到`DragDropContext`与...有类似的目的[react-redux提供程序组件](https://github.com/reactjs/react-redux/blob/master/docs/api.md#provider-store)

### 道具

```js
type Hooks = {|
  // optional
  onDragStart?: OnDragStartHook,
  onDragUpdate?: OnDragUpdateHook,
  // always required
  onDragEnd: OnDragEndHook,
|}

type OnDragStartHook = (start: DragStart, provided: HookProvided) => void;
type OnDragUpdateHook = (update: DragUpdate, provided: HookProvided) => void;
type OnDragEndHook = (result: DropResult, provided: HookProvided) => void;

type Props = {|
  ...Hooks,
  children: ?Node,
|}
```

### 基本用法

```js
import { DragDropContext } from 'react-beautiful-dnd';

class App extends React.Component {
  onDragStart = () => {
    /*...*/
  };
  onDragUpdate = () => {
    /*...*/
  }
  onDragEnd = () => {
    // the only one that is required
  };

  render() {
    return (
      <DragDropContext
        onDragStart={this.onDragStart}
        onDragUpdate={this.onDragUpdate}
        onDragEnd={this.onDragEnd}
      >
        <div>Hello world</div>
      </DragDropContext>
    );
  }
}
```

### `Hook`小号

这些是顶级应用程序事件,您可以使用它来执行自己的状态更新以及制作屏幕阅读器公告. 有关控制屏幕阅读器的更多信息,请参阅我们的[屏幕阅读器指南](docs/guides/screen-reader.md)

### `provided: HookProvided`

```js
type HookProvided = {|
  announce: Announce,
|}

type Announce = (message: string) => void;
```

所有钩子都提供了第二个参数: `HookProvided`. 该对象有一个属性: `announce`. 此功能用于同步向屏幕阅读器发布消息. 如果你不使用这个功能,我们会宣布一个默认的英文信息. 我们创造了一个[屏幕阅读器使用指南](docs/guides/screen-reader.md)如果您有兴趣为自己控制屏幕阅读器信息并支持国际化,我们建议您使用它. 如果你正在使用`announce`它必须被同步调用. 

### `onDragStart` (可选的) 

```js
type OnDragStartHook = (start: DragStart, provided: HookProvided) => void;
```

`onDragStart`将在拖动开始时收到通知. 这个钩子是*可选的*因此不需要提供. 它是**强烈推荐**您使用此功能来阻止所有更新`Draggable`和`Droppable`在拖动过程中的组件.  (看到[*最佳实践`hooks` *](https://github.com/atlassian/react-beautiful-dnd#best-practices-for-hooks)) 

您将获得以下详细信息: 

#### `start: DragStart`

```js
type DragStart = {|
  draggableId: DraggableId,
  type: TypeId,
  source: DraggableLocation,
|}
```

-   `start.draggableId`: 的ID`Draggable`现在正在拖动
-   `start.type`: `type`的`Draggable`现在正在拖动
-   `start.source`:  那个地点  (`droppableId`和`index`) 拖动项目在a中开始的位置`Droppable`. 

#### `onDragStart`类型信息

```js
type OnDragStartHook = (start: DragStart, provided: HookProvided) => void;

// supporting types
type DragStart = {|
  draggableId: DraggableId,
  type: TypeId,
  source: DraggableLocation,
|}

type DraggableLocation = {|
  droppableId: DroppableId,
  // the position of the draggable within a droppable
  index: number
|};
type Id = string;
type DraggableId = Id;
type DroppableId = Id;
type TypeId = Id;
```

### `onDragUpdate` (可选的) 

```js
type OnDragUpdateHook = (update: DragUpdate, provided: HookProvided) => void;
```

只要拖动过程中发生某些变化,就会调用该钩子. 可能的变化是: 

-   的位置`Draggable`已经改变
-   该`Draggable`现在已经完全不同了`Droppable`
-   该`Draggable`现在没有`Droppable`

由于此功能,您不需要做太多工作,因为它会减慢阻力. 

#### `update: DragUpdate`

```js
type DragUpdate = {|
  ...DragStart,
  // may not have any destination (drag to nowhere)
  destination: ?DraggableLocation,
|}
```

-   `update.draggableId`: 的ID`Draggable`现在正在拖动
-   `update.type`: `type`的`Draggable`现在正在拖动
-   `update.source`:  那个地点  (`droppableId`和`index`) 拖动项目在a中开始的位置`Droppable`. 
-   `update.destination`:  那个地点  (`droppableId`和`index`) 拖动项目现在的位置. 如果用户当前没有拖动任何内容,则该值可以为null`Droppable`. 

### `onDragEnd` (需要) 

这个功能是*非常*在应用程序生命周期中扮演着重要的角色. **这个功能必须导致*同步*重新排序列表`Draggables`**

它提供了有关拖动的所有信息: 

#### `result: DropResult`

```js
type DropResult = {|
  ...DragUpdate,
  reason: DropReason,
|}

type DropReason = 'DROP' | 'CANCEL';
```

-   `result.draggableId`: 的ID`Draggable`那是在拖. 
-   `result.type`: `type`的`Draggable`那是在拖. 
-   `result.source`: 所在的位置`Draggable`开始. 
-   `result.destination`: 所在的位置`Draggable`完了. 该`destination`将会`null`如果用户在不超过a的情况下掉线`Droppable`. 
-   `result.reason`: 发生下降的原因. 这些信息可以帮助我们制作更有用的消息`HookProvided`>`announce`功能. 

### 同步重新排序

因为这个图书馆不能控制你的状态,所以你可以这样做*同步*重新排列你的名单基于`result: DropResult`. 

#### 这是你需要做的

-   如果`destination`是`null`:  全做完了!
-   如果`source.droppableId`等于`destination.droppableId`您需要从列表中删除该项目并将其插入到正确的位置. 
-   如果`source.droppableId`不相等`destination.droppableId`,那么你需要删除`Draggable`来自`source.droppableId`列表并将其添加到正确的位置`destination.droppableId`名单. 

### 坚持重新排序

如果您需要将重新排序保留到远程数据存储区 - 在客户端上同步更新列表,并在后台触发请求以保持更改. 如果远程保存失败,则由您决定如何与用户通信并更新或不更新列表. 

### 最佳实践`hooks`

#### 在拖动过程中阻止更新

它是**高度**建议在用户拖动时阻止可能影响数量的任何状态更新`Draggable`s和`Droppable`s或其尺寸. 请听`onDragStart`并阻止更新`Draggable`s和`Droppable`直到你收到`onDragEnd`. 

当用户开始拖动时,我们会拍摄适用的所有尺寸的快照`Draggable`和`Droppable`节点. 如果在拖动过程中这些变化我们不会知道. 

##### 你如何阻止更新?

取决于您如何管理数据,更新阻止会有所不同. 这可能是最好的例子解释: 

假设您正在使用React组件状态来管理应用程序的状态. 您的应用程序状态与您每隔三十秒轮询一次数据更新的REST端点相关联. 在拖动过程中,您不应该应用任何可能会影响可见效果的服务器更新. 

这可能意味着: 

-   在拖动过程中停止服务器轮询
-   在拖动过程中忽略来自服务器调用的任何结果 (不要调用`this.setState`在您的组件中使用新数据) 

##### 没有更新阻止会导致不好的时间

这里有一些糟糕的用户体验,如果你改变了事情,可能会发生*在拖动期间*: 

-   如果增加节点数量,那么库将不知道它们,并且当用户期望它们时它们将不会移动. 
-   如果您减少节点数量,那么列表中可能会出现空白和意外动作. 
-   如果更改任何节点的维度,则可能导致更改的节点以及其他节点在不正确的时间移动. 
-   如果您删除用户正在拖动的节点,则该拖动将立即结束
-   如果您更改拖动节点的尺寸,那么其他内容在正确的时间将不会移动. 

### `onDragStart`和`onDragEnd`配对

我们非常努力地确保每一个`onDragStart`事件与单一配对`onDragEnd`事件. 但是,在这种情况下可能会出现流氓情况. 如果发生这种情况 - 这是一个错误. 目前没有任何机制可以告诉图书馆从外部取消当前的拖拽. 

## `Droppable`

`Droppable`组件可以**由一个`Draggable`**. 他们也**包含** `Draggable`秒. 一个`Draggable`必须包含在一个`Droppable`. 

```js
import { Droppable } from 'react-beautiful-dnd';

<Droppable droppableId="droppable-1" type="PERSON">
  {(provided, snapshot) => (
    <div
      ref={provided.innerRef}
      style={{ backgroundColor: snapshot.isDraggingOver ? 'blue' : 'grey' }}
      {...provided.droppableProps}
    >
      <h2>I am a droppable!</h2>
      {provided.placeholder}
    </div>
  )}
</Droppable>;
```

### 可投掷道具

-   `droppableId`:  一个*需要* `DroppableId(string)`唯一标识该应用程序的可投入程序. 请不要更改此道具 - 特别是在拖动时. 
-   `type`: 安*可选的* `TypeId(string)`可以用来简单地接受一类`Draggable`. 例如,如果您使用该类型`PERSON`那么它只会允许`Draggable`类型的`PERSON`放弃自己. `Draggable`类型的`TASK`将无法被放在a上`Droppable`与类型`PERSON`. 如果不`type`提供,它将被设置为`'DEFAULT'`. 目前来说`type`的`Draggable`在...之内`Droppable` **一定是**一样. 如果有一个有效的用例,这个限制在将来可能会放松. 
-   `isDropDisabled`: 安*可选的*标志来控制当前是否允许丢弃`Droppable`. 你可以用它来实现你自己的条件丢弃逻辑. 它将默认为`false`. 
-   `direction`: 物品在这个物品中流动的方向. 选项是`vertical` (默认) 和`horizontal`. 
-   `ignoreContainerClipping`:  当一个`Droppable`在一个可滚动的容器内,它的区域受到限制,所以你只能放在容器的一部分`Droppable`你可以看到. 设置这个道具不会出现这种行为,允许你放在任何地方`Droppable`即使它被一个可滚动的父级视觉隐藏. 默认行为适用于大多数情况,所以您不需要使用此道具,但如果您的道具很长,它可能会很有用`Draggable`s在一个短的滚动容器内. 请记住,如果您有多个,它可能会导致一些意外的行为`Droppable`在同一页面上滚动容器. 

### 儿童功能

该`React`一个孩子`Droppable`必须是返回a的函数[`ReactElement`](https://tylermcginnis.com/react-elements-vs-react-components/). 

```js
<Droppable droppableId="droppable-1">
  {(provided, snapshot) => ({
    /*...*/
  })}
</Droppable>;
```

该函数提供了两个参数: 

#### 1.提供:  (DroppableProvided) \*\*: 为了使droppable能够正常工作,

```js
type DroppableProvided = {|
  innerRef: (?HTMLElement) => void,
  droppableProps: DroppableProps,
  placeholder: ?ReactElement,
|}

type DroppableProps = {|
  // used for shared global styles
  'data-react-beautiful-dnd-droppable': string,
|}
```

-   `provided.innerRef`你必须**绑定**到最高可能的DOM节点中`provided.innerRef`. `ReactElement`我们这样做是为了避免需要使用查找您的DOM节点. `ReactDOM`有关使用的更多信息

> 看我们的`innerRef`运用[指南`innerRef`: 这用于在中创建空间](/docs/patterns/using-inner-ref.md)

-   `provided.placeholder`根据需要拖动. `Droppable`当用户拖动不是主列表的列表时,需要此空间. 请确保将占位符放在您为其提供参考的组件中. 我们需要增加大小本身. `Droppable`: 这是一个Object,它包含需要应用于Droppable元素的属性. 
-   `provided.droppableProps (DroppableProps)`它需要应用于您应用的相同元素至. `provided.innerRef`它目前包含一个属性,我们用它来控制一些不可见的CSS. `data`2.快照:  (DroppableStateSnapshot) \*\*

```js
<Droppable droppableId="droppable-1">
  {(provided, snapshot) => (
    <div ref={provided.innerRef} {...provided.droppableProps}>
      Good to go

      {provided.placeholder}
    </div>
  )}
</Droppable>;
```

#### 该功能还提供有与当前拖动状态有关的少量状态. 

```js
type DroppableStateSnapshot = {|
  // Is the Droppable being dragged over?
  isDraggingOver: boolean,
  // What is the id of the draggable that is dragging over the Droppable?
  draggingOverWith: ?DraggableId,
|};
```

这可以选择用于增强组件. `children`一个常见的用例是改变a的外观而它正在被拖动. 有条件地下降`Droppable`s只能通过

```js
<Droppable droppableId="droppable-1">
  {(provided, snapshot) => (
    <div
      ref={provided.innerRef}
      style={{ backgroundColor: snapshot.isDraggingOver ? 'blue' : 'grey' }}
      {...provided.droppableProps}
    >
      I am a droppable!

      {provided.placeholder}
    </div>
  )}
</Droppable>;
```

### 那些共享相同的人

-   `Droppable`. `Draggable`这是允许有条件丢弃的一种简单方法. `type`如果你不提供一个`type`为了`Droppable`,那么它只会接受`Draggable`s也有默认的类型. `Draggable`s和`Droppable`两个人都会有他们的`types`设置`'DEFAULT'`当没有提供. 目前没有办法设置多个`types`或者a`type`通配符,将接受`Draggable`s的多种任何类型. 如果有一个有效的用例,可以添加它. 
-   使用`isDropDisabled`你可以有条件地允许掉落. 这使您可以执行任意复杂的条件转换. 这只会被视为如果`type`的`Droppable`匹配`type`当前正在拖动`Draggable`. 
-   您可以禁用放弃`Droppable`总是由总设定`isDropDisabled`至`true`. 你可以这样做来创建一个永远不能被拖放但包含的列表`Draggable`秒. 
-   技术上你不需要使用`type`并用你的所有条件放置逻辑来完成`isDropDisabled`功能. 该`type`参数是常见用例的便捷捷径. 

### 滚动容器

该库支持在滚动容器 (具有DOM元素) 中拖动`overflow: auto;`要么`overflow: scroll;`) . 该**只要**支持的用例有: 

1.  该`Droppable`本身可以是一个滚动容器**没有可滚动的父母**
2.  该`Droppable`具有**一个可滚动的父项**

哪里一个*可滚动的父级*指的是一个不是窗口本身的滚动容器. 

### 空`Droppable`小号

建议你把一个`min-height`在垂直`Droppable`或者a`min-width`在水平`Droppable`. 否则当`Droppable`是空的可能没有足够的目标`Draggable`被触摸或鼠标输入拖动*过度*该`Droppable`. 

### 推荐Droppable性能优化

当用户拖拉或停止拖动时,a`Droppable`我们重新渲染`Droppable`与更新`DroppableStateSnapshot > isDraggingOver`值. 这对于设计样式非常有用`Droppable`. 但是,默认情况下,这将导致所有的孩子的渲染`Droppable`- 可能是100的`Draggable`小号!这可能导致明显的帧速下降. 为了避免这个问题,我们建议您创建一个组件,它是一个子组件`Droppable`谁的责任是避免渲染儿童,如果不是必需的话. 

以下是你如何做到这一点的例子: 

```js
import React, { Component } from 'react';

class Student extends Component<{ student: Person }> {
  render() {
    // Renders out a draggable student
  }
}

class InnerList extends Component<{ students: Person[] }> {
  // do not re-render if the students list has not changed
  shouldComponentUpdate(nextProps: Props) {
    if(this.props.students === nextProps.students) {
      return false;
    }
    return true;
  }
  // You could also not do your own shouldComponentUpdate check and just
  // extend from React.PureComponent

  render() {
    return this.props.students.map((student: Person) => (
      <Student student={student} />
    ))
  }
}

class Students extends Component {
  render() {
    return (
      <Droppable droppableId="list">
        {(provided: DroppableProvided, snapshot: DroppableStateSnapshot) => (
          <div
            ref={provided.innerRef}
            style={{ backgroundColor: provided.isDragging ? 'green' : 'lightblue' }}
            {...provided.droppableProps}
          >
            <InnerList students={this.props.students} />
            {provided.placeholder}
          </div>
        )}
      </Droppable>
    )
  }
}
```

通过使用该方法,您可以将样式更改为a`Droppable`当它被拖动时,但你避免不必要地重新渲染所有的孩子. 请记住,如果你正在使用`React.PureComponent`你的组件会[对上下文中的变化没有反应](https://github.com/facebook/react/issues/2517). 

不幸的是我们[无法为您应用此优化](https://medium.com/merrickchristensen/function-as-child-components-5f3920a9ace9). 它是使用函数作为子模式的副产品. 

## `Draggable`

`Draggable`组件可以拖动并拖放到其上`Droppable`秒. 一个`Draggable`必须始终包含在一个`Droppable`. 它是**可能**重新排序`Draggable`在其家中`Droppable`或移动到另一个`Droppable`. 它是**可能**因为a`Droppable`可以自由地控制它允许投入的内容. 

一切`Draggable`有一个*拖动手柄*. 一个*拖动手柄*是用户为了拖动而与之交互的元素`Draggable`. 一个*拖动手柄*可以是`Draggable`元素本身,还是孩子的`Draggable`. 

```js
import { Draggable } from 'react-beautiful-dnd';

<Draggable draggableId="draggable-1" index={0}>
  {(provided, snapshot) => (
    <div
      ref={provided.innerRef}
      {...provided.draggableProps}
      {...provided.dragHandleProps}
    >
      <h4>My draggable</h4>
    </div>
  )}
</Draggable>;
```

> 注意: 当库移动到React 16时,这将被清理一些,因为我们可以将占位符作为兄弟返回到您的子函数,而无需创建包装元素

### 可拖动道具

-   `draggableId`:  一个*需要* `DraggableId(string)`唯一标识的`Draggable`为应用程序. 请不要更改此道具 - 特别是在拖动时. 
-   `index`:  一个*需要* `number`它与. 的顺序相匹配`Draggable`在里面`Droppable`. 它只是简单的索引`Draggable`在列表中. 该`index`在一个内部需要是唯一的`Droppable`但不需要是唯一的`Droppables`. 通常情况下`index`价值将是简单的`index`由...提供`Array.prototype.map`功能: 

```js
{this.props.items.map((item, index) => (
  <Draggable draggableId={item.id} index={index}>
    {(provided, snapshot) => (
      <div ref={provided.innerRef} {...provided.draggableProps}>
        {item.content}
      </div>
    )}
  </Draggable>
))}
```

-   `isDragDisabled`: 安*可选的*标志来控制是否`Draggable`被允许拖动. 您可以使用它来实现自己的条件拖动逻辑. 它将默认为`false`. 
-   `disableInteractiveElementBlocking`: 安*可选的*标志选择不阻止交互式元素的拖动. 有关更多信息,请参阅本节*交互式的子元素`Draggable`*

### 儿童功能 (渲染道具) 

该`React`一个孩子`Draggable`必须是返回a的函数`ReactElement`. 

```js
<Draggable draggableId="draggable-1" index={0}>
  {(provided, snapshot) => (
      <div
        ref={provided.innerRef}
        {...provided.draggableProps}
        {...provided.dragHandleProps}
      >
        Drag me!
      </div>
  )}
</Draggable>;
```

该函数提供了两个参数: 

#### 1.提供:  (DraggableProvided) \*\*所有内容

```js
type DraggableProvided = {|
  innerRef: (HTMLElement) => void,
  draggableProps: DraggableProps,
  // will be null if the draggable is disabled
  dragHandleProps: ?DragHandleProps,
|}
```

提供*对象必须被应用于*正常运行. `Draggable`: 为了

-   `provided.innerRef (innerRef: (HTMLElement) => void)`正确运行,`Droppable`你必须**绑定**功能`innerRef`你想被认为是`ReactElement`节点. `Draggable`我们这样做是为了避免需要使用查找您的DOM节点. `ReactDOM`有关使用的更多信息

> 看我们的`innerRef`运用[指南`innerRef`例](/docs/patterns/using-inner-ref.md)

##### `innerRef`: 这是一个包含a的对象

```js
<Draggable draggableId="draggable-1" index={0}>
  {(provided, snapshot) => <div ref={provided.innerRef}>Drag me!</div>}
</Draggable>;
```

-   `provided.draggableProps (DraggableProps)`属性和内联`data`. `style`此对象需要应用于您应用的同一节点至. `provided.innerRef`这将控制可拖动的拖动操作,而不是拖动拖动操作. 欢迎您将自己的样式添加到- 但请不要移除或替换任何属性. `DraggableProps.style`类型信息

##### `draggableProps`例

```js
// Props that can be spread onto the element directly
export type DraggableProps = {|
  // inline style
  style: ?DraggableStyle,
  // used for shared global styles
  'data-react-beautiful-dnd-draggable': string,
|}

type DraggableStyle = DraggingStyle | NotDraggingStyle
type DraggingStyle = {|
  position: 'fixed',
  width: number,
  height: number,
  boxSizing: 'border-box',
  pointerEvents: 'none',
  top: number,
  left: number,
  margin: 0,
  transition: 'none',
  transform: ?string,
  zIndex: ZIndex,
|}
type NotDraggingStyle = {|
  transform: ?string,
  transition: null | 'none',
|}
```

##### `draggableProps`定位所有权

```js
<Draggable draggableId="draggable-1" index={0}>
  {(provided, snapshot) => (
    <div ref={provided.innerRef} {...provided.draggableProps}>
      Drag me!
    </div>
  )}
</Draggable>;
```

##### 它是该库的一个合约,它拥有拖动元素的定位逻辑. 

这包括诸如`top`,`right`,`bottom`,`left`和`transform`. 图书馆可能会改变它如何定位事物以及它使用的是哪些属性,而不会执行主要的版本冲突. 也建议你不要使用你自己的`transition`属性添加到拖动元素. 

##### 警告: `position: fixed`

`react-beautiful-dnd`使用`position: fixed`定位拖动元素. 这是相当强大的,并允许你有`position: relative | absolute | fixed`父母. 然而,不幸的是`position:fixed`是[受到影响`transform`](http://meyerweb.com/eric/thoughts/2011/09/12/un-fixing-fixed-elements-with-css-transforms/) (如`transform: rotate(10deg);`) . 这意味着如果你有一个`transform: *`对某人的父母之一`Draggable`那么拖动时定位逻辑将不正确. 瘸!对于大多数消费者来说,这不会是一个问题. 

为了解决这个问题,你可以使用[`React.Portal`](https://reactjs.org/docs/portals.html). 我们不会默认启用此功能,因为它有性能问题. 我们有一个[使用门户指南](/docs/patterns/using-a-portal.md)更详细地解释性能问题以及如何设置自己的问题`React.Portal`如果你想. 

##### 在列表之间移动时保持焦点

当移动一个`Draggable`从一个列表到另一个列表,默认的浏览器行为是为了*拖动手柄*元素放松焦点. 这是因为旧元素正在被破坏,并且正在创建一个新元素. 当用键盘拖动时,焦点丢失并不好,因为用户无法继续与元素交互. 为了改善这种用户体验,我们自动给出一个*拖动手柄*重点时: 

-   它在拖动结束时被卸载
-   它有重点
-   它在安装时启用
-   在拖动手柄安装之前,没有其他元素获得浏览器焦点

##### 扩展`DraggableProps.style`

如果您使用内联样式,欢迎您将其扩展`DraggableProps.style`目的. 你也欢迎申请`DraggableProps.style`使用内联样式的对象,并为组件本身使用自己的样式解决方案 - 例如[风格组件](https://github.com/styled-components/styled-components). 

如果您重写内联样式,请务必在展开后进行`provided.draggableProps`或者传播会覆盖你的内联风格. 

```js
<Draggable draggable="draggable-1" index={0}>
  {(provided, snapshot) => {
    // extending the DraggableStyle with our own inline styles
    const style = {
      backgroundColor: snapshot.isDragging ? 'blue' : 'white',
      fontSize: 18,
      ...provided.draggableProps.style,
    };
    return (
      <div
        ref={provided.innerRef}
        {...provided.draggableProps}
        style={style}
      >
        Drag me!
      </div>
    );
  }}
</Draggable>;
```

##### 避免边缘折叠`Draggable`小号

[边缘崩溃](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS*Box*Model/Mastering*margin*collapsing)是CSS中非常困难的部分之一. 对于我们的目的,如果你有一个`Draggable`与`margin-bottom: 10px`和下一个`Draggable`有一个`margin-top: 12px`这些利润率将会*坍方*并由此产生的余量将是两者中较大的一个: `12px`. 当我们进行我们的计算时,我们目前没有考虑边缘折叠. 如果你确实想在兄弟姐妹身上留下一个空白,那么把它们都包在一个`div`并将边缘应用于内部`div`所以他们不是直系兄弟姐妹. 

##### `Draggable`s应该是可见的兄弟姐妹

这是一个假设`Draggable`s是*可见的兄弟姐妹*彼此之间. 中间还可以有其他元素,但这些元素不应占用额外的空间. 无论如何,你可能不会这样做,但只要说出来就非常清楚. 

```js
// Direct siblings ✅
<Draggable draggableId="draggable-1" index={0}>
  {() => {}}
</Draggable>
<Draggable draggableId="draggable-2" index={1}>
  {() => {}}
</Draggable>

// Not direct siblings, but are visible siblings ✅
<div>
  <Draggable draggableId="draggable-1" index={0}>
    {() => {}}
  </Draggable>
</div>
<div>
  <Draggable draggableId="draggable-2" index={1}>
    {() => {}}
  </Draggable>
</div>

// Spacer elements ❌
<Draggable draggableId="draggable-1" index={0}>
    {() => {}}
</Draggable>
<p>I will break things!</p>
<Draggable draggableId="draggable-2" index={1}>
    {() => {}}
</Draggable>

// Spacing on non sibling wrappers ❌
<div style={{padding: 10}}>
  <Draggable draggableId="draggable-1" index={0}>
    {() => {}}
  </Draggable>
</div>
<div style={{padding: 10}}>
  <Draggable draggableId="draggable-2" index={1}>
    {() => {}}
  </Draggable>
</div>
```

-   `provided.dragHandleProps (?DragHandleProps)`一切`Draggable`有一个*拖动手柄*. 这是用来拖动整个的`Draggable`. 通常这将是与`Draggable`,但有时它可能是一个孩子的`Draggable`. `DragHandleProps`需要应用到您想要成为拖动句柄的节点. 这是一些需要应用到道具上的道具`Draggable`节点. 最简单的方法是将道具散布到可拖动节点上 (`{...provided.dragHandleProps}`) . 但是,你也欢迎[猴子补丁](https://davidwalsh.name/monkey-patching)这些道具如果你还需要回应他们. DragHandleProps将会`null`什么时候`isDragDisabled`被设定为`true`. 

##### `dragHandleProps`类型信息

```js
type DragHandleProps = {|
  onFocus: () => void,
  onBlur: () => void,
  onMouseDown: (event: MouseEvent) => void,
  onKeyDown: (event: KeyboardEvent) => void,
  onTouchStart: (event: TouchEvent) => void,
  'data-react-beautiful-dnd-drag-handle': string,
  'aria-roledescription': string,
  tabIndex: number,
  draggable: boolean,
  onDragStart: (event: DragEvent) => void,
|}
```

##### `dragHandleProps`例如: 标准

```js
<Draggable draggableId="draggable-1" index={0}>
  {(provided, snapshot) => (
    <div
      ref={provided.innerRef}
      {...provided.draggableProps}
      {...provided.dragHandleProps}
    >
      Drag me!
    </div>
  )}
</Draggable>;
```

##### `dragHandleProps`例如: 自定义拖动手柄

通过它的一部分控制整个可拖动

```js
<Draggable draggableId="draggable-1" index={0}>
  {(provided, snapshot) => (
    <div ref={provided.innerRef} {...provided.draggableProps}>
      <h2>Hello there</h2>
      <div {...provided.dragHandleProps}>Drag handle</div>
    </div>
  )}
</Draggable>;
```

##### `dragHandleProps`猴子补丁

你可以重写一些`dragHandleProps`如果你需要的话,你可以使用自己的行为. 

```js
const myOnMouseDown = event => console.log('mouse down on', event.target);

<Draggable draggableId="draggable-1" index={0}>
  {(provided, snapshot) => {
    const onMouseDown = (() => {
      // dragHandleProps might be null
      if (!provided.dragHandleProps) {
        return onMouseDown;
      }

      // creating a new onMouseDown function that calls myOnMouseDown as well as the drag handle one.
      return (event) => {
        provided.dragHandleProps.onMouseDown(event);
        myOnMouseDown(event);
      };
    })();

    return (
      <div
        ref={provided.innerRef}
        {...provided.draggableProps}
        {...provided.dragHandleProps}
        onMouseDown={onMouseDown}
      >
        Drag me!
      </div>
    );
  }}
</Draggable>;
```

#### 2.快照:  (DraggableStateSnapshot) \*\*该

```js
type DraggableStateSnapshot = {|
  isDragging: boolean,
  // What Droppable (if any) the Draggable is currently over
  draggingOver: ?DroppableId,
|};
```

功能还提供有与当前拖动状态有关的少量状态. `children`这可以选择用于增强组件. 一个常见的用例是改变a的外观而它被拖拽. `Draggable`注意: 如果你想改变光标到类似的东西您需要将样式添加到可拖动. `grab` (看到[扩展`DraggableProps.style`](#extending-draggableprops-style)以上) 

```js
<Draggable draggableId="draggable-1" index={0}>
  {(provided, snapshot) => {
    const style = {
      backgroundColor: snapshot.isDragging ? 'blue' : 'grey',
      ...provided.draggableProps.style,
    };

    return (
      <div
        ref={provided.innerRef}
        {...provided.draggableProps}
        {...provided.dragHandleProps}
        style={style}
      >
        Drag me!
      </div>
    );
  }}
</Draggable>;
```

### `Draggable`占位符

当拖动一个`Draggable`我们留下了一个*占位符* `React.Element`保持空间`Droppable`以防止它崩溃. 占位符模仿样式和布局 (包括`width`,`height`,`margin`,`tagName`和`display`) 以确保列表尺寸在拖动时不受影响. 它将被插入`react-beautiful-dnd`作为一个直接的兄弟姐妹`React.Node`由...返回`Draggable`儿童功能. 

### 添加一个`onClick`处理程序`Draggable`或者a*拖动手柄*

欢迎您添加您自己的`onClick`处理程序`Draggable`或者a*拖动手柄* (这可能是相同的元素) . `onClick`如果发生点击,事件处理程序将始终被调用. 如果我们阻止点击,那么我们就是`event.defaultPrevented`财产将被设置为`true`. 我们阻止用户拖动项目时发生点击事件. 看到[#马虎-点击和点击 -  prevention-] \(马虎点击和点击预防) 了解更多信息. 

### 交互式的子元素`Draggable`

这是可能的你的`Draggable`包含交互元素. 默认情况下,我们阻止拖动这些元素. 通过这样做,我们允许这些元素以通常的方式运行. 以下是默认阻止拖动的交互式元素列表: 

-   `input`
-   `button`
-   `textarea`
-   `select`
-   `option`
-   `optgroup`
-   `video`
-   `audio`
-   [`contenteditable`](https://developer.mozilla.org/en-US/docs/Web/HTML/Global*attributes/contenteditable) (任何元素是`contenteditable`或者在一个`contenteditable`容器) 

您可以通过添加选项退出此行为`disableInteractiveElementBlocking`支持`Draggable`. 但是,您是否应该这样做是值得怀疑的,因为它会使交互式元素无法使用. 如果你需要*有条件的*阻止从可添加的交互式元素拖动`disableInteractiveElementBlocking`支持选择退出默认的阻塞和猴子补丁`dragHandleProps (DragHandleProps)`事件处理程序根据需要禁用拖动. 

## `resetServerContext`

该`resetServerContext`函数应该在服务器端呈现 (SSR) 时使用. 它确保上下文状态不会在服务器上的多个呈现中持续存在,这会在服务器上呈现多个请求后导致客户端/服务器标记不匹配. 

在调用服务器端渲染方法之前使用它: 

```js
import { resetServerContext } from 'react-beautiful-dnd';
import { renderToString } from 'react-dom/server';

...

resetServerContext();
renderToString(...);
```

## 流量使用

`react-beautiful-dnd`是使用键入的[`flowtype`](https://flow.org). 这大大提高了代码库内部的一致性. 我们还公开了许多公共类型,如果您愿意,可以输入您的javascript. 如果你不使用`flowtype`这不会阻止你使用该库. 对于那些想要它的人来说,这只是额外的安全. 

### 公共流量类型

```js
// id's
type Id = string;
type TypeId = Id;
type DroppableId = Id;
type DraggableId = Id;

// hooks
type DragStart = {|
  draggableId: DraggableId,
  type: TypeId,
  source: DraggableLocation,
|}

type DragUpdate = {|
  ...DragStart,
  // may not have any destination (drag to nowhere)
  destination: ?DraggableLocation,
|}

type DropResult = {|
  ...DragUpdate,
  reason: DropReason,
|}

type DropReason = 'DROP' | 'CANCEL'

type DraggableLocation = {|
  droppableId: DroppableId,
  // the position of the droppable within a droppable
  index: number
|};

// Droppable
type DroppableProvided = {|
  innerRef: (?HTMLElement) => void,
  placeholder: ?ReactElement,
|}

type DroppableStateSnapshot = {|
  isDraggingOver: boolean,
  draggingOverWith: ?DraggableId,
|}

// Draggable
type DraggableProvided = {|
  innerRef: (?HTMLElement) => void,
  draggableProps: DraggableProps,
  dragHandleProps: ?DragHandleProps,
|}

type DraggableStateSnapshot = {|
  isDragging: boolean,
  draggingOver: ?DroppableId,
|}

export type DraggableProps = {|
  style: ?DraggableStyle,
  'data-react-beautiful-dnd-draggable': string,
|}
type DraggableStyle = DraggingStyle | NotDraggingStyle
type DraggingStyle = {|
  position: 'fixed',
  width: number,
  height: number,
  boxSizing: 'border-box',
  pointerEvents: 'none',
  top: number,
  left: number,
  margin: 0,
  transition: 'none',
  transform: ?string,
  zIndex: ZIndex,
|}
type NotDraggingStyle = {|
  transition: ?string,
  transition: null | 'none',
|}

type DragHandleProps = {|
  onFocus: () => void,
  onBlur: () => void,
  onMouseDown: (event: MouseEvent) => void,
  onKeyDown: (event: KeyboardEvent) => void,
  onTouchStart: (event: TouchEvent) => void,
  'data-react-beautiful-dnd-drag-handle': string,
  'aria-roledescription': string,
  tabIndex: number,
  draggable: boolean,
  onDragStart: (event: DragEvent) => void,
|}
```

### 使用流量类型

这些类型作为模块的一部分导出,因此使用它们非常简单: 

```js
import type { DroppableProvided } from 'react-beautiful-dnd';
```

## 打字稿

如果你正在使用[打字稿](https://www.typescriptlang.org/)你可以使用社区维护[DefinitelyTyped类型定义](https://www.npmjs.com/package/@types/react-beautiful-dnd). [安装说明](http://definitelytyped.org/). 

### 用流程类型示例应用程序

我们创造了一个[样本申请](https://github.com/alexreardon/react-beautiful-dnd-flow-example)它练习流型. 这是一个超级简单`React`基于[`react-create-app`](https://github.com/facebookincubator/create-react-app). 你可以用它作为参考,看看如何正确设置. 

## 工程健康

### 类型化

这个代码库是用键入的[流动型](https://flow.org)促进更大的内部一致性和更有弹性的代码. 

### 经测试

该代码库使用许多不同的测试策略,包括单元,性能和集成测试. 测试系统的各个方面有助于提高其质量和稳定性. 

代码覆盖率是[不是代码健康的保证](https://stackoverflow.com/a/90021/1374236),这是一个很好的指标. 此代码库目前位于**〜90%的覆盖率**. 

### 性能

这个代码库被设计为**非常高效**- 它是它的DNA的一部分. 它旨在执行尽可能少的更新. 您可以阅读关于完成的性能工作`react-beautiful-dnd`这里: 

-   [反思拖放](https://medium.com/@alexandereardon/rethinking-drag-and-drop-d9f5770b4e6b)
-   [向前拖动React性能](https://medium.com/@alexandereardon/dragging-react-performance-forward-688b30d40a33)

## 尺寸

已经非常谨慎地保持图书馆尽可能轻. 这是目前**〜38kb (gzip) **在尺寸方面. 如果您已经在使用某个基础依赖关系,那么净成本可能会更低. 

## 支持的浏览器

该库支持该标准[Atlassian支持的浏览器](https://confluence.atlassian.com/cloud/supported-browsers-744721663.html)用于桌面: 

| 桌面                                     | 版               |
| -------------------------------------- | --------------- |
| Microsoft Internet Explorer (Windows)  | 版本11            |
| Microsoft Edge                         | 支持最新的稳定版本       |
| Mozilla Firefox (所有平台)                 | 支持最新的稳定版本       |
| Google Chrome (Windows和Mac)            | 支持最新的稳定版本       |
| Safari (Mac)                           | 支持最新OS版本的最新稳定版本 |

| 移动                    | 版                              |
| --------------------- | ------------------------------ |
| Chrome (Android和iOS)  | 支持最新的稳定版本                      |
| 移动Safari (iOS)        | 支持最新的稳定版本                      |
| Android (Android)     | Android 4.0.3上的默认浏览器 (冰淇淋三明治)  |

## 翻译

该库的文档也可用其他语言提供: 

-   ![kr](https://raw.githubusercontent.com/gosquared/flags/master/flags/flags/shiny/24/South-Korea.png) **朝鲜的**: [leehyunggeun /反应 - 美丽 - 免打扰](https://github.com/LeeHyungGeun/react-beautiful-dnd-kr)

这些翻译由社区维护,不会由本库的维护人员审阅或维护. 如果您想更新相关翻译,请提出相关问题. 

## 作者

亚历克斯里尔登 -[@alexandereardon](https://twitter.com/alexandereardon)

## 维护者

杰瑞德克罗 -[@jaredjcrowe](https://twitter.com/jaredjcrowe)

## 合作者

Bogdan Chadkin  -[@IAmTrySound](https://twitter.com/IAmTrySound)  
卢克Batchelor  -[@alukebatchelor](https://twitter.com/alukebatchelor)  
很多别的[@Atlassian](https://twitter.com/Atlassian)的!
