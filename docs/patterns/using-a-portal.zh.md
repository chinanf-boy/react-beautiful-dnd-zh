# 使用 portal

> 本指南将介绍如何移动您的`Draggable`变成一个[`React.Portal`](https://reactjs.org/docs/portals.html)拖着.
>
> ⚠️ 在 a 之后将项目移动到 React Portal`touchstart`目前无法正常工作 😞.反应问题:[#13113](https://github.com/facebook/react/issues/13113).我们在这里跟踪它:[#582](https://github.com/atlassian/react-beautiful-dnd/issues/582).由于 React Portal 的这个问题,如果使用 React Portal,拖放将无法在触摸设备上运行

## 背景

我们在拖动时将元素留在原位.我们申请`position: fixed`在我们移动它们时的元素.这非常强大,可以让你拥有`position: relative | absolute | fixed`父母.然而,不幸的是`position:fixed`是[受到影响`transform`](http://meyerweb.com/eric/thoughts/2011/09/12/un-fixing-fixed-elements-with-css-transforms/)(如`transform: rotate(10deg);`).这意味着,如果你有一个`transform: *`在一个父母的`Draggable`然后拖动时定位逻辑将不正确.瘸!对于大多数消费者来说,这不是问题.

要解决此问题,您可以使用`portal`.

## `Portals`

等等,什么是`portal`?一个`portal`是当前组件树之外的另一个 DOM 节点.通过使用 portal,您可以移动`Draggable`拖动时进入另一个 DOM 节点.这可以让你绕过局限`position: fixed`.

## 不使用`React.Portal`默认情况下

React 为使用提供了第一类 api`portals`:[`React.Portal`](https://reactjs.org/docs/portals.html).最初我们想要将它用于所有人`Draggable`拖着时.不幸的是,它有很大的性能损失 - 特别是在拖动有很多孩子的节点时([反应问题](https://github.com/facebook/react/issues/12247)).原因是因为组件移动到了`React.Portal`安装和重新安装,这是非常昂贵的.因此,我们目前不支持开箱即用.

如果你的`Draggable`没有很多孩子节点,欢迎您使用`React.Portal`在之上`react-beautiful-dnd`.如果你只是在列表中拖动卡,那么你*应该*好好用`React.Portal`.但是,如果您拖动一个满是卡片的列,那么当拖动开始时,您将获得显着的凹陷.

## 例

<!-- TODO: embed example here on new website -->

我们创造了一个[工作实例](https://react-beautiful-dnd.netlify.com/?selectedKind=Portals&selectedStory=Using%20your%20own%20portal&full=0&addons=1&stories=1&panelRight=0&addonPanel=storybook%2Factions%2Factions-panel)用的`React.Portal`指导你.你可以查看[来源这里](https://github.com/atlassian/react-beautiful-dnd/blob/master/stories/11-portal-story.js)

## 表

如果正在进行拖放重新排序`<table>`我们在里面创建了一个 portal[表格指南](/docs/patterns/tables)
