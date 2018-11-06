# 钩子-`Hook`s

## 目录
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
<!-- END doctoc -->

- [什么钩子可用?](#%E4%BB%80%E4%B9%88%E9%92%A9%E5%AD%90%E5%8F%AF%E7%94%A8)
  - [主要](#%E4%B8%BB%E8%A6%81)
  - [次要](#%E6%AC%A1%E8%A6%81)
- [钩子的第二个参数:`provided: HookProvided`](#%E9%92%A9%E5%AD%90%E7%9A%84%E7%AC%AC%E4%BA%8C%E4%B8%AA%E5%8F%82%E6%95%B0provided-hookprovided)
- [`onDragStart`(可选的)](#ondragstart%E5%8F%AF%E9%80%89%E7%9A%84)
  - [`start: DragStart`](#start-dragstart)
  - [`onDragStart`类型信息](#ondragstart%E7%B1%BB%E5%9E%8B%E4%BF%A1%E6%81%AF)
- [`onDragUpdate`(可选的)](#ondragupdate%E5%8F%AF%E9%80%89%E7%9A%84)
  - [`update: DragUpdate`](#update-dragupdate)
- [`onDragEnd`(需要)](#ondragend%E9%9C%80%E8%A6%81)
  - [`result: DropResult`](#result-dropresult)
- [次要:`onBeforeDragStart`](#%E6%AC%A1%E8%A6%81onbeforedragstart)
  - [`OnBeforeDragStartHook`类型信息](#onbeforedragstarthook%E7%B1%BB%E5%9E%8B%E4%BF%A1%E6%81%AF)
- [钩子什么时候调用?](#%E9%92%A9%E5%AD%90%E4%BB%80%E4%B9%88%E6%97%B6%E5%80%99%E8%B0%83%E7%94%A8)
  - [阶段 1:准备(异步)](#%E9%98%B6%E6%AE%B5-1%E5%87%86%E5%A4%87%E5%BC%82%E6%AD%A5)
  - [阶段 2:发布(同步)](#%E9%98%B6%E6%AE%B5-2%E5%8F%91%E5%B8%83%E5%90%8C%E6%AD%A5)
  - [阶段 3:更新](#%E9%98%B6%E6%AE%B5-3%E6%9B%B4%E6%96%B0)
  - [阶段 4:放下](#%E9%98%B6%E6%AE%B5-4%E6%94%BE%E4%B8%8B)
- [同步重新排序](#%E5%90%8C%E6%AD%A5%E9%87%8D%E6%96%B0%E6%8E%92%E5%BA%8F)
  - [这是你需要做的](#%E8%BF%99%E6%98%AF%E4%BD%A0%E9%9C%80%E8%A6%81%E5%81%9A%E7%9A%84)
  - [坚持重新排序](#%E5%9D%9A%E6%8C%81%E9%87%8D%E6%96%B0%E6%8E%92%E5%BA%8F)
- [在拖动过程中阻止更新](#%E5%9C%A8%E6%8B%96%E5%8A%A8%E8%BF%87%E7%A8%8B%E4%B8%AD%E9%98%BB%E6%AD%A2%E6%9B%B4%E6%96%B0)
  - [你如何阻止更新?](#%E4%BD%A0%E5%A6%82%E4%BD%95%E9%98%BB%E6%AD%A2%E6%9B%B4%E6%96%B0)
  - [没有更新阻止会导致不好的时间](#%E6%B2%A1%E6%9C%89%E6%9B%B4%E6%96%B0%E9%98%BB%E6%AD%A2%E4%BC%9A%E5%AF%BC%E8%87%B4%E4%B8%8D%E5%A5%BD%E7%9A%84%E6%97%B6%E9%97%B4)
- [`onDragStart`和`onDragEnd`配对](#ondragstart%E5%92%8Condragend%E9%85%8D%E5%AF%B9)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


> `DragDropContext > Hooks`

钩子是顶级应用程序事件,您可以使用它来执行自己的状态更新 以及 制作屏幕阅读器公告.

> 有关控制屏幕阅读器的更多信息,请参阅我们的[屏幕阅读器指南](screen-reader.zh.md)

## 什么钩子可用?

### 主要

- `onDragStart`:拖动已经开始了
- `onDragUpdate`:在拖动过程中发生了一些变化
- `onDragEnd` **(必要)**:拖拽已结束。此钩子的责任是同步应用由拖动导致的更改

### 次要

> 通常你不需要使用`onBeforeDragStart`,它与其他钩子函数签名略有不同

- `onBeforeDragStart`\\:就在`onDragStart`之前，并且可以用于进行[表格 重新排序](tables.zh.md)的尺寸锁定.

## 钩子的第二个参数:`provided: HookProvided`

```js
type HookProvided = {|
  announce: Announce
|};

type Announce = (message: string) => void;
```

所有钩子(除了`onBeforeDragStart`)提供了第二个参数:`HookProvided`。该对象有一个属性:`announce`。此函数用于同步发布屏幕阅读器的消息.如果您不使用此函数,我们将宣布默认的英语消息。我们创造了一个[屏幕阅读器使用指南](screen-reader.zh.md)，如果您有兴趣自己控制屏幕阅读器消息,并支持国际化,我们建议使用。如果你正在使用`announce`，请必须同步调用.

## `onDragStart`(可选的)

```js
type OnDragStartHook = (start: DragStart, provided: HookProvided) => mixed;
```

`onDragStart`拖动开始时，会收到通知。这个钩子是*可选的*因此不需要提供。但**强烈推荐**您使用此函数来阻止拖动过程中对所有`Draggable`和`Droppable`组件的更新。(可看下面**拖动期间阻止更新**)

您将获得以下详细信息:

### `start: DragStart`

```js
type DragStart = {|
  draggableId: DraggableId,
  type: TypeId,
  source: DraggableLocation
|};
```

- `start.draggableId`: `Draggable`正在拖拽的 ID
- `start.type`:`Draggable`正在拖拽的`type`
- `start.source`: (`droppableId`和`index`) 拖动物在`Droppable`中一个开始的位置. 

### `onDragStart`类型信息

**注意:**返回类型是`mixed`,不使用返回值.

```js
type OnDragStartHook = (start: DragStart, provided: HookProvided) => mixed;

// supporting types
type DragStart = {|
  draggableId: DraggableId,
  type: TypeId,
  source: DraggableLocation
|};

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

## `onDragUpdate`(可选的)

```js
type OnDragUpdateHook = (update: DragUpdate, provided: HookProvided) => mixed;
```

只要拖动过程中发生某些变化,就会调用该钩子. 可能的变化是: 

-   已经改变`Draggable`的位置
-   该`Draggable`现在被不同`Droppable`覆盖
-   该`Draggable`现在被没有`Droppable`覆盖

重要的是，你不要因为这个函数而做太多的工作,因为它会减慢拖动。而返回类型是`mixed`,不使用返回值.

### `update: DragUpdate`

```js
type DragUpdate = {|
  ...DragStart,
  // may not have any destination (drag to nowhere)
  destination: ?DraggableLocation
|};
```

-   `update.draggableId`: 现在正在拖动`Draggable`的ID
-   `update.type`: 现在正在拖动`Draggable`的`type`
-   `update.source`:  (`droppableId`和`index`) 拖动物在`Droppable`中开始的位置. 
-   `update.destination`:  (`droppableId`和`index`) 拖动物在`Droppable`中现在的位置. 如果用户当前没有拖动任何内容,则该值可以为null`Droppable`. 

## `onDragEnd`(需要)

这个函数是在应用程序生命周期中扮演着*非常*重要的角色. **这个功能必然导致*同步*重新排序列表`Draggables`**

它提供了有关拖动的所有信息: 

### `result: DropResult`

```js
type DropResult = {|
  ...DragUpdate,
  reason: DropReason
|};

type DropReason = 'DROP' | 'CANCEL';
```

-   `result.draggableId`: 现在正在拖动`Draggable`的ID
-   `result.type`: 现在正在拖动`Draggable`的`type`
-   `result.source`: `Draggable`开始所在的位置. 
-   `result.destination`: `Draggable`借宿所在的位置. 该`destination`将会`null`,如果用户在不放在`Droppable`. 
-   `result.reason`: 发生放下的原因. 这些信息可以帮助我们制作更有用的消息`HookProvided`>`announce`功能. 

## 次要:`onBeforeDragStart`

> 这个钩子的用例是超级有限的

一旦我们获得了开始拖动所需的所有信息,我们就调用`onBeforeDragStart`函数。这是在我们更新调用之前的`Draggable`和`Droppable`组件的`snapshot-快照`。此时应用程序不处于拖动状态,因此更改props, 类似`isDropDisabled`，都将失。该`onBeforeDragStart`钩子 是对[表格 重新排序](tables.zh.md)的尺寸锁定的好方法.

- ✅ 可以对现有组件进行修改，以锁定其大小
- ❌ 无法删除或添加任何`Draggable`要么`Droppable`
- ❌ 无法修改任何`Draggable`要么`Droppable`尺寸
- ❌ 还没有屏幕阅读器公告

### `OnBeforeDragStartHook`类型信息

**注意:**而返回类型是`mixed`,不使用返回值.

```js
// 没有第二哥 'provided' 参数
type OnBeforeDragStartHook = (start: DragStart) => mixed;

// 其他的 就像 OnDragStartHook
```

## 钩子什么时候调用?

### 阶段 1:准备(异步)

- 用户启动拖动
- 我们准备，并收集拖动所需的信息(异步)。如果拖拽在此阶段完成之前结束,则不会触发任何钩子.

### 阶段 2:发布(同步)

- `onBeforeDragStart`被调用
- `Draggable`和`Droppable`组件使用 初次`snapshot-快照`值 更新
- `onDragStart`被调用

### 阶段 3:更新

- 用户移动拖动项目
- `Draggable`和`Droppable`组件使用最新`snapshot`值更新
- `onDragUpdate`被调用

### 阶段 4:放下

- 用户放下了拖动项目
- 一旦放下动画完成了，`Draggable`和`Droppable`组件通过剩下`snapshot`值更新
- `onDragEnd`被调用

## 同步重新排序

因为这个 库 不能控制你的状态,所以你可以基于`result: DropResult`, *同步*重新排列你的列表. 

### 这是你需要做的

-   如果`destination`是`null`:  全做完了!
-   如果`source.droppableId`等于`destination.droppableId`您需要从列表中删除该项目并将其插入到正确的位置. 
-   如果`source.droppableId`不相等`destination.droppableId`,那么你需要删除来自`source.droppableId`列表的`Draggable`, 并将其添加到正确的位置`destination.droppableId`列表. 

### 坚持重新排序

如果您需要将重新排序保留到远程数据存储区 - 在客户端上同步更新列表,并在后台触发请求以保持更改. 如果远程保存失败,则由您决定如何与用户通信并更新或不更新列表. 

## 在拖动过程中阻止更新

**高度**建议: 用户拖动时阻止可能影响数量的任何状态更新`Draggable`s和`Droppable`或其尺寸. 请监听`onDragStart`并阻止更新`Draggable`s和`Droppable`直到你收到`onDragEnd`. 

当用户开始拖动时,我们会拍摄适用的所有尺寸的快照`Draggable`和`Droppable`节点. 如果在拖动过程中这些变化我们不会知道. 

### 你如何阻止更新?

取决于您如何管理数据,更新阻止会有所不同. 这可能是最好的例子解释: 

假设您正在使用React组件状态来管理应用程序的状态. 您的应用程序状态与 您每隔三十秒轮询一次数据更新 的REST端点相关联. 在拖动过程中,您不应该应用任何可能会影响可见效果的服务器更新. 

这可能意味着: 

-   在拖动过程中停止服务器轮询
-   在拖动过程中忽略来自服务器调用的任何结果 (不要调用`this.setState`在您的组件中使用新数据) 

### 没有更新阻止会导致不好的时间

这里有一些糟糕的用户体验,如果你改变了事情,*在拖动期间*可能会发生: 

-   如果增加节点数量,那么 库 将不知道它们,并且当用户期望它们时, 它们将不会移动. 
-   如果您减少节点数量,那么列表中可能会出现空白和意外动作. 
-   如果更改任何节点的维度,则可能导致更改的节点以及其他节点在不正确的时间移动. 
-   如果您删除用户正在拖动的节点,则该拖动将立即结束
-   如果您更改拖动节点的尺寸,那么其他内容在正确的时间将不会移动. 

## `onDragStart`和`onDragEnd`配对

我们非常努力地确保每一个`onDragStart`事件与单一配对`onDragEnd`事件. 但是,在这种情况下可能会出现流氓情况. 如果发生这种情况 - 这是一个错误. 目前没有任何机制可以告诉 库 从外部取消当前的拖拽. 