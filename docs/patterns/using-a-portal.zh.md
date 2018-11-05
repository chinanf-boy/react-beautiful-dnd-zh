# 使用 portal

> 本指南将介绍，在拖拽时，如何让您的`Draggable`变成一个[`React.Portal`](https://reactjs.org/docs/portals.html).

> ⚠️ 目前，在 一个`touchstart` 之后将物品变成 React Portal无法正常工作 😞.反应问题:[#13113](https://github.com/facebook/react/issues/13113)。我们在这里跟踪它:[#582](https://github.com/atlassian/react-beautiful-dnd/issues/582).由于 React Portal 的这个问题, 若使用 React Portal,拖放将无法在触摸设备上运行

## 背景

我们在拖动时，将元素留在原位。在我们移动它们时，我们应用`position: fixed`到此元素。这非常强大,可以让你拥有`position: relative | absolute | fixed`父母。然而,不幸的是`position:fixed`是可会[受到`transform`影响](http://meyerweb.com/eric/thoughts/2011/09/12/un-fixing-fixed-elements-with-css-transforms/)(如`transform: rotate(10deg);`)。这意味着,如果你在一个`transform: *`上，而其的一个父母是一个`Draggable`。那拖动时定位逻辑将不正确。不过! 对于大多数消费者来说,这不是问题.

要解决此问题,您可以使用`portal`.

## `Portals`

等等,什么是`portal`?一个`portal`是当前组件树之外的另一个 DOM 节点。通过使用 portal,您在拖动时可以移动`Draggable`进入另一个 DOM 节点。这可以让你绕过`position: fixed`局限.

## 默认情况下不使用`React.Portal`

React 为使用`portals`提供了第一类 api:[`React.Portal`](https://reactjs.org/docs/portals.html)。最初我们想要将它用于所有的`Draggable`。不幸的是,它有很大的性能损失 - 特别是在拖动有很多孩子的节点时([反应问题](https://github.com/facebook/react/issues/12247))。原因是因为组件变成`React.Portal`需要mount和重新mount,这是非常昂贵的.因此,我们目前不支持开箱即用.

如果你的`Draggable`没有很多孩子节点,欢迎您在`react-beautiful-dnd`上使用`React.Portal`。如果你只是在一个列表简单拖动卡片，那么你的`React.Portal`*应该*还好。但是,如果您拖动一个满是卡片的列,那么当拖动开始时,您将获得明显的不适.

## 例

<!-- TODO: embed example here on new website -->

我们创造了一个[工作实例](https://react-beautiful-dnd.netlify.com/?selectedKind=Portals&selectedStory=Using%20your%20own%20portal&full=0&addons=1&stories=1&panelRight=0&addonPanel=storybook%2Factions%2Factions-panel)，其指导你`React.Portal`的使用。你可以查看[源码](https://github.com/atlassian/react-beautiful-dnd/blob/master/stories/11-portal-story.js)

## 表格

如果正在对`<table>`的重新排序的进行拖和放，我们也在[表格指南](/docs/patterns/tables.zh.md)里面创建了一个 portal
