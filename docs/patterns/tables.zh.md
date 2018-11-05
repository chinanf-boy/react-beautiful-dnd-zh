# 表

| 使用的好处`<table>`              | 提供商                  |
| -------------------------------- | ----------------------- |
| 清晰显示表格数据的方式           | 浏览器                  |
| 很棒的浏览器支持                 | 浏览器                  |
| 可以将表复制粘贴到其他应用程序中 | 浏览器                  |
| 可以重新排序表中的项目!          | `react-beautiful-dnd`😎 |

`react-beautiful-dnd`不需要创建额外的包装元素`Draggable`和`Droppable`组件.因此有可能有一个`<table>`它具有有效的 HTML 以及支持拖放功能.

> 我们还没有找到在这个阶段实现表列的语义重新排序的方法.这是因为没有一个元素表示表列 - 而是一列是重复行中单元格放置的结果.如不能包裹一个`Draggable`在"列"周围,以使其可拖动.如果您找到工作方法,欢迎本指南的 PR!

## 策略

重新排序表时可以使用两种策略.

1.  固定布局(更快更简单)
2.  尺寸锁定(更慢但更稳健)

### 策略 1:固定布局

为了使用此策略,需要修复列的宽度 - 也就是说,它们不会根据单元格中放置的内容而更改.这可以用 a 来实现`table-layout: fixed`要么`table-layout: auto`只要您手动设置单元格的宽度(例如`50%`).

你唯一需要做的就是设定`display: table`在...上`Draggable`在拖动时排.

[请参阅此处的示例代码](https://react-beautiful-dnd.netlify.com/?selectedKind=Tables&selectedStory=with%20fixed%20width%20columns&full=0&addons=1&stories=1&panelRight=0&addonPanel=storybook%2Factions%2Factions-panel)

### 策略 2:维度锁定

此策略适用于具有基于内容的自动列宽的列.它也适用于固定布局.**这是一个比第一个更强大的策略,但它的性能也较差.**

当我们申请`position: fixed`拖动项目将其从表格使用的自动列宽计算中删除.所以在拖动开始之前我们*锁*所有单元格宽度都使用内联样式,以防止在拖动开始时更改列尺寸.你可以实现这个目标[`onBeforeDragStart`钩](docs/guides/hooks.md).

这需要大规模的性能特征,因为它需要:

1.  调用`render()`在每一行
2.  读 DOM(`window.getComputedStyles`)每一行

对于少于 50 行的表,这应该没问题!

[请参阅此处的示例代码](https://react-beautiful-dnd.netlify.com/?selectedKind=Tables&selectedStory=with%20dimension%20locking&full=0&addons=1&stories=1&panelRight=0&addonPanel=storybook%2Factions%2Factions-panel)

## 高级:使用[`React.Portal`](https://reactjs.org/docs/portals.html)

如果你想使用`React.Portal`与表行重新排序相结合,您需要经过几个额外的步骤.

首先,请阅读我们的内容[使用门户模式](docs/patterns/using-a-portal.md)熟悉这种方法.

了解 React 中挂载/卸载操作的时间非常重要.我们创造了一个[codesandbox.io 示例](https://codesandbox.io/s/nkl52y1wn0)显示进出时间时挂载时间如何工作`React.Portal`.

移动现有时`<tr>`变成一个`React.Portal`重要的是要知道现有的`<tr>`是未安装的和新的`<tr>`安装到 portal.以下是这些操作的顺序:

1.  老人`<tr>`具有`componentWillUnmount`叫
2.  新的`<tr>`具有`componentWillMount`叫

为了保留我们正在移动到的行中的单元格的单元格尺寸`React.Portal`我们需要使用内联样式锁定其维度(请参阅策略#2).遗憾的是,新组件在移动到门户之前不能直接访问树中组件的信息.所以为了做到这一点,我们需要获得细胞的尺寸`<tr>`当它卸载并重新应用到新的`<tr>`当它安装在`componentDidMount`.

没有什么好办法可以做到这一点`componentDidMount`被称为我们不确定组件是否正在卸载`tr`不再需要,或者如果它正在卸载,因为它即将进入 portal.

似乎让事情发挥作用的唯一方法是:

1.  在`componentWillUnmount`的`tr`从 DOM 中读取单元格的当前宽度.然后,将此值存储在组件外部,以便可以通过正在装入的新组件读取该值.
2.  如果组件正在安装并且`DraggableStateSnapshot > isDragging`如果是,那么你可以看到是否有先前记录的宽度.如果有,则可以应用该宽度.

这有点复杂 - 所以我们[创造另一个例子](https://react-beautiful-dnd.netlify.com/?selectedKind=Tables&selectedStory=with%20portal&full=0&addons=1&stories=1&panelRight=0&addonPanel=storybook%2Factions%2Factions-panel)为您展示这项技术的工作原理!别客气!
