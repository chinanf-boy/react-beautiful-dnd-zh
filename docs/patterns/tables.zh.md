# 表格

| 使用`<table>`的好处              | 提供商                  |
| -------------------------------- | ----------------------- |
| 清晰显示表格数据的方式           | 浏览器                  |
| 很棒的浏览器支持                 | 浏览器                  |
| 可以将表格复制粘贴到其他应用程序中 | 浏览器                  |
| 可以重新排序表格格，中的项目!          | `react-beautiful-dnd`😎 |

`react-beautiful-dnd`不需要额外的包装元素，就可以创建`Draggable`和`Droppable`组件。因此你可能有一个效的 HTML的`<table>`，而它具有支持拖放的功能.

> 我们还没有找到在这个阶段实现，表格列的语义重新排序的方法。这是因为没有一个元素能表示整个表格列 - 现实是一列，仅为重复行中单元格放置的结果。正如不能包裹一个`Draggable`在"列"周围,以使其可拖动。如果您找到这种工作方法,欢迎PR指南!

## 策略

重新排序表格时，可以使用两种策略.

1.  固定-Fixed 布局(更快更简单)
2.  尺寸锁定(更慢但更稳健)

### 策略 1:固定布局

为了使用此策略,需要修复列的宽度 - 也就是说,它们不会根据单元格中放置的内容而更改.这可以用一个 `table-layout: fixed`或者`table-layout: auto`来实现，您要手动设置单元格的宽度(例如`50%`).

你唯一需要做的就是，在拖动时在`Draggable`上设定`display: table`.

[请参阅此处的示例代码](https://react-beautiful-dnd.netlify.com/?selectedKind=Tables&selectedStory=with%20fixed%20width%20columns&full=0&addons=1&stories=1&panelRight=0&addonPanel=storybook%2Factions%2Factions-panel)

### 策略 2:尺寸锁定

此策略适用于具有基于内容的自动对称的列。它也适用于固定布局.**这是一个比第一个更强大的策略,但它的性能也较差.**

当我们应用`position: fixed`到拖动项目，将其从表格使用的自动列宽计算中删除。所以在拖动开始之前，我们通过使用内联样式*锁好*所有单元格宽度,以防止在拖动开始时，更改列尺寸。你可以用[`onBeforeDragStart`钩子](hooks.zh.md)实现这个目标.

这需要耗费大量的性能功能,因为它需要:

1.  在每一行都调用`render()`
2.  每一行都读 DOM(`window.getComputedStyles`)

对于少于 50 行的表格,这应该没问题!

[请参阅此处的示例代码](https://react-beautiful-dnd.netlify.com/?selectedKind=Tables&selectedStory=with%20dimension%20locking&full=0&addons=1&stories=1&panelRight=0&addonPanel=storybook%2Factions%2Factions-panel)

## 高级:使用[`React.Portal`](https://reactjs.org/docs/portals.html)

如果你想使用`React.Portal`与表格行重新排序相结合,您需要经过几个额外的步骤.

首先,请阅读我们的[使用 portal 模式](using-a-portal.zh.md)内容熟悉这种方法.

了解 React 中 mount / unmount 操作的 时机 非常重要。我们创造了一个[codesandbox.io 示例](https://codesandbox.io/s/nkl52y1wn0)显示进出`React.Portal`时， 到mount时刻又应如何工作.

移动现有`<tr>`变成一个`React.Portal`时，重要的是要知道现有的`<tr>`是unmount 的 和 新的`<tr>`会被安装到 portal。以下是这些操作的顺序:

1.  旧`<tr>`被`componentWillUnmount`调用
2.  新`<tr>`被`componentWillMount`调用

为了保留我们正在移动到`React.Portal`的行中的单元格的尺寸，我们需要使用内联样式锁定其尺寸(请参阅策略#2)。遗憾的是,新组件在移动到 portal 之前，不能直接访问树中组件的信息。所以为了做到知晓尺寸这一点,当`<tr>` unmount我们需要获得它的单元尺寸，并当新的`<tr>`在`componentDidMount`安装时，要重新应用到.

在`componentDidMount`阶段，没有什么好办法做到上面那点，因为我们不确定组件是否在不再需要就卸载`tr`, 或者因为它即将进入 portal，它正在卸载。

似乎让事情发挥作用的唯一方法是:

1.  `tr`的`componentWillUnmount`阶段从 DOM 中读取单元格的当前宽度。然后,将此值存储在组件外部,以便可以让正在装入的新组件读取该值.
2.  如果组件正在安装，并且`DraggableStateSnapshot > isDragging`为true，那么你可以看到是否有先前记录的宽度。如果有,则可以应用该宽度.

这有点复杂 - 所以我们[创造另一个例子](https://react-beautiful-dnd.netlify.com/?selectedKind=Tables&selectedStory=with%20portal&full=0&addons=1&stories=1&panelRight=0&addonPanel=storybook%2Factions%2Factions-panel)为您展示这项技术的工作原理! 别客气!
