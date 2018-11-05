# 钩

> `DragDropContext > Hooks`

挂钩是顶级应用程序事件,您可以使用它们来执行自己的状态更新,样式更新以及制作屏幕阅读器公告.

> 有关控制屏幕阅读器的更多信息,请参阅我们的[屏幕阅读器指南](docs/guides/screen-reader.md)

## 什么钩子可用?

### 主

-   `onDragStart`:拖动已经开始了
-   `onDragUpdate`:在拖动过程中发生了一些变化
-   `onDragEnd` **(需要)**:拖累已结束.此挂钩的责任是同步应用由拖动导致的更改

### 次要

> 通常你不需要使用`onBeforeDragStart`,它与其他钩子的功能签名略有不同

-   `onBeforeDragStart`\\:就在之前打电话`onDragStart`并且可以用于进行尺寸锁定[表重新排序](docs/patterns/tables.md).

## 挂钩的第二个参数:`provided: HookProvided`

```js
type HookProvided = {|
  announce: Announce,
|};

type Announce = (message: string) => void;
```

所有挂钩(除了`onBeforeDragStart`)提供了第二个参数:`HookProvided`.该对象有一个属性:`announce`.此功能用于同步向屏幕阅读器发布消息.如果您不使用此功能,我们将宣布默认的英语消息.我们创造了一个[屏幕阅读器使用指南](docs/guides/screen-reader.md)如果您有兴趣为自己控制屏幕阅读器消息并支持国际化,我们建议使用.如果你正在使用`announce`它必须同步调用.

## `onDragStart`(可选的)

```js
type OnDragStartHook = (start: DragStart, provided: HookProvided) => mixed;
```

`onDragStart`拖动开始时会收到通知.这个钩子是*可选的*因此不需要提供.它是**强烈推荐**您使用此功能来阻止对所有人的更新`Draggable`和`Droppable`拖动过程中的组件.(看到**拖动期间阻止更新**下面)

您将获得以下详细信息:

### `start: DragStart`

```js
type DragStart = {|
  draggableId: DraggableId,
  type: TypeId,
  source: DraggableLocation,
|};
```

-   `start.draggableId`:的id`Draggable`现在正在拖延
-   `start.type`:`type`的`Draggable`现在正在拖延
-   `start.source`: 那个地点 (`droppableId`和`index`)拖动项目在a内开始的位置`Droppable`.

### `onDragStart`类型信息

**注意:**而返回类型是`mixed`,不使用返回值.

```js
type OnDragStartHook = (start: DragStart, provided: HookProvided) => mixed;

// supporting types
type DragStart = {|
  draggableId: DraggableId,
  type: TypeId,
  source: DraggableLocation,
|};

type DraggableLocation = {|
  droppableId: DroppableId,
  // the position of the draggable within a droppable
  index: number,
|};
type Id = string;
type DraggableId = Id;
type DroppableId = Id;
type TypeId = Id;
```

## `onDragUpdate`(可选的)

```js
type OnDragUpdateHook = (update: DragUpdate, provided: HookProvided) => mixed;
```

只要在拖动过程中发生变化,就会调用此挂钩.可能的变化是:

-   的立场`Draggable`已经改变
-   该`Draggable`现在变得与众不同了`Droppable`
-   该`Draggable`现在已经过去了`Droppable`

重要的是你不要因为这个功能而做太多的工作,因为它会减慢阻力.而返回类型是`mixed`,不使用返回值.

### `update: DragUpdate`

```js
type DragUpdate = {|
  ...DragStart,
  // may not have any destination (drag to nowhere)
  destination: ?DraggableLocation,
|};
```

-   `update.draggableId`:的id`Draggable`现在正在拖延
-   `update.type`:`type`的`Draggable`现在正在拖延
-   `update.source`: 那个地点 (`droppableId`和`index`)拖动项目在a内开始的位置`Droppable`.
-   `update.destination`: 那个地点 (`droppableId`和`index`)现在拖动项目的位置.如果用户当前没有拖动任何内容,则此值可以为null`Droppable`.

## `onDragEnd`(需要)

这个功能是*非常*重要且在应用程序生命周期中发挥关键作用.**这个功能必须导致*同步*重新排序列表`Draggables`**

它提供了有关拖动的所有信息:

### `result: DropResult`

```js
type DropResult = {|
  ...DragUpdate,
  reason: DropReason,
|};

type DropReason = 'DROP' | 'CANCEL';
```

-   `result.draggableId`:的id`Draggable`那是拖延.
-   `result.type`:`type`的`Draggable`那是拖延.
-   `result.source`:所在的位置`Draggable`开始.
-   `result.destination`:所在的位置`Draggable`完了.该`destination`将会`null`如果用户在没有超过a的情况下掉线`Droppable`.
-   `result.reason`:发生跌落的原因.这些信息可以帮助您制作更有用的消息`HookProvided`>`announce`功能.

## 二级:`onBeforeDragStart`

> 这个钩子的用例是超级有限的

一旦我们获得了开始拖动所需的所有信息,我们就称之为`onBeforeDragStart`功能.这是在我们更新之前调用的`snapshot`的价值观`Draggable`和`Droppable`组件.此时应用程序不处于拖动状态,因此更改道具等`isDropDisabled`将失败.该`onBeforeDragStart`hook是进行任何维度锁定的好机会[表重新排序](docs/patterns/tables.md).

-   ✅可以对现有组件进行修改以锁定其大小
-   ❌无法删除或添加任何内容`Draggable`要么`Droppable`
-   ❌无法修改任何尺寸`Draggable`要么`Droppable`
-   ❌还没有屏幕阅读器公告

### `OnBeforeDragStartHook`类型信息

**注意:**而返回类型是`mixed`,不使用返回值.

```js
// No second 'provided' argument
type OnBeforeDragStartHook = (start: DragStart) => mixed;

// Otherwise the same type information as OnDragStartHook
```

## 挂钩什么时候叫?

### 阶段1:准备(异步步骤)

-   用户启动拖动
-   我们准备并收集拖动所需的信息(异步).如果拖拽在此阶段完成之前结束,则不会触发任何挂钩.

### 阶段2:发布(同步步骤)

-   `onBeforeDragStart`叫做
-   `Draggable`和`Droppable`组件使用initial更新`snapshot`值
-   `onDragStart`叫做

### 阶段3:更新

-   用户移动拖动项目
-   `Draggable`和`Droppable`组件使用最新更新`snapshot`值
-   `onDragUpdate`叫做

### 阶段4:下降

-   用户删除拖动项目
-   一旦下降动画完成了`Draggable`和`Droppable`组件通过休息更新`snapshot`值
-   `onDragEnd`叫做

## 同步重新排序

因为这个库不能控制你的状态,所以由你来决定*同步*根据您的列表重新排序您的列表`result: DropResult`.

### 这是你需要做的

-   如果`destination`是`null`: 全部完成!
-   如果`source.droppableId`等于`destination.droppableId`您需要从列表中删除该项目并将其插入正确的位置.
-   如果`source.droppableId`不等于`destination.droppableId`,那么你需要删除`Draggable`来自`source.droppableId`列出并将其添加到正确的位置`destination.droppableId`名单.

### 坚持重新订购

如果需要将重新排序持久保存到远程数据存储 - 在客户端上同步更新列表,并在后台触发请求以保留更改.如果远程保存失败,则由您决定如何将该信息传达给用户并更新或不更新列表.

## 拖动期间阻止更新

它是**高度**建议在用户拖动时阻止任何可能影响数量的状态更新`Draggable`s和`Droppable`s,或它们的尺寸.请听`onDragStart`并阻止更新`Draggable`s和`Droppable`直到你收到`onDragEnd`.

当用户开始拖动时,我们会拍摄适用的所有尺寸的快照`Draggable`和`Droppable`节点.如果这些在拖动期间发生变化,我们将无法了解它.

### 你如何阻止更新?

根据您管理数据的方式,更新阻止会有所不同.最好通过例子来解释:

假设您正在使用React组件状态来管理应用程序的状态.您的应用程序状态与每30秒轮询一次数据更新的REST端点相关联.在拖动过程中,您不应该应用任何可能影响可见内容的服务器更新.

这可能意味着:

-   拖动期间停止服务器轮询
-   在拖动过程中忽略服务器调用的任何结果(不要调用`this.setState`在包含新数据的组件中)

### 没有更新阻止可能导致糟糕的时间

如果您更改了某些内容,可能会出现一些糟糕的用户体验*在拖拽期间*:

-   如果增加节点数量,那么库将不会知道它们,并且当用户期望它们时它们不会被移动.
-   如果减少节点数量,则列表中可能存在间隙和意外移动.
-   如果更改任何节点的尺寸,则可能导致更改的节点以及其他节点在不正确的时间移动.
-   如果删除用户正在拖动的节点,则拖动将立即结束
-   如果更改拖动节点的尺寸,则其他内容将不会在正确的时间移开.

## `onDragStart`和`onDragEnd`配对

我们非常努力地确保每一个`onDragStart`事件与单个配对`onDragEnd`事件.然而,可能存在一种流氓情况,而事实并非如此.如果发生这种情况 - 这是一个错误.目前没有机制告诉库从外部取消当前拖动.
