# 多拖

> 此页面旨在指导您在`react-beautiful-dnd`列表，添加自己的多拖动体验.

一次拖动多个`Draggable`(多拖)，目前是一种需要在其`react-beautiful-dnd`上构建的模式。我们没有将这种功能纳入库本身。这样做是因为多拖动体验会引入了许多概念,决策和意见。我们已经做了很多工作来确保有一个标准的基础，其建立在[dom事件管理](how-we-use-dom-events.zh.md).

我们创造了一个[参考应用](react-beautiful-dnd.netlify.com/iframe.html?selectedKind=Multi%20drag&selectedStory=pattern&full=0&down=1&left=1&panelRight=0&downPanel=storybook%2Factions%2Factions-panel)([源码](/stories/9-multi-drag-story.js))实现这种多拖模式。该应用程序是相当基本的,并不能很好地处理大型列表中的性能.因此,如果您想支持大于50的列表，这有[些我们使用的性能建议](#performance), 也添加到了我们的参考应用程序中.

![multi drag demo](https://user-images.githubusercontent.com/2182637/37322724-7843a218-26d3-11e8-9ebb-8d5853387bb3.gif)

## 经验

我们已经决定开始使用简单，但非常灵活且可扩展的多拖动模式.它不像我们标准的拖动交互那样*美丽* - 但它是一个很好的基础构建，并跨过许多问题领域.

## 用户体验

我们可以分三个阶段打破用户体验.

1.  [**选择**](#selection):用户选择一个或多个物品.
2.  [**拖拽**](#dragging):用户拖动一个物品，作为整个组的表示.
3.  [**放下**](#dropping):用户将物品放入新位置。我们将所有选定的物品移动到新位置

## 通告

请记住内部`react-beautiful-dnd`不知道多拖动模式的。因此建议您使用为多拖动，通告通告`HookProvided > Announce`有意义的屏幕阅读器消息。见我们的[屏幕阅读器指南](../guides/screen-reader.zh.md),有关如何控制屏幕阅读器消息传递的详细信息

## 选择

在拖动开始之前,我们需要允许用户*可选*选择一些`Draggable`拖动。我们选择了一个物品,您应该将样式更新应用到`Draggable`，例如背景颜色更改以指示物品已被选中.

### 选择互动建议

> 这些交互基于Mac OSX[*Finder*](https://support.apple.com/en-au/HT201732)(文件浏览器)应用程序.

### 行动:切换部分

如果用户单击某个物品,则应切换该物品的选定状态。此外,当用户**enter** <kbd>⏎</kbd>键按下时,应更新物品的选定状态。该**enter** <kbd>⏎</kbd>是相当不错的,因为我们不使用它来拿起或放下 - 我们是用**空格键** <kbd>space</kbd>来做.

![toggle-selection](https://user-images.githubusercontent.com/2182637/37323080-6d67f04a-26d5-11e8-8bc1-8ff5178018bc.gif)

#### `onClick`事件处理程序

-   附加一个`onClick`到你的*拖动控制*或`Draggable`
-   仅在用户使用[`primaryButton`](https://developer.mozilla.org/en-US/docs/Web/API/MouseEvent/button)时，切换选择(`event.button === 0`)
-   防止`click`的默认操作，因为你正在使用它进行选择(唯一对你有用是调用`event.preventDefault()`避免移除*选择*)

#### 键盘事件处理程序

-   当用户按下**enter** <kbd>⏎</kbd>时，切换物品的选择
-   **选项1**:附上一个`onKeyDown`，处理你的*拖动控制*或`Draggable`。你将需要猴子补丁下`DragHandleProvided > onKeyDown`键盘处理程序
-   **选项2**:附上一个`onKeyUp`，处理你的*拖动控制*。那你就不需要猴子补丁了`onKeyDown`处理程序。然而,`keyup`事件不会阻止其默认操作,因此您将无法检查`event.defaultPrevented`，也就是查看按键是否用于拖动。如果你只是在你事件控制时，使用**enter** <kbd>⏎</kbd>，那你应该没事,因为它不用作拖动的一部分.
- 如果要在选择时切换选择，则阻止对`keydown` /`keyup`事件的默认操作，因为您要退出标准浏览器行为，并提供已使用此事件的线索。

#### 切换选择行为

-   如果之前未选择该物品,请将其设为唯一选定的物品
-   如果该物品先前已被选中，**但不是选择组的一部分**:取消选择该物品
-   如果该物品先前已被选中，**且是选择组的一部分**:使其成为唯一选定的物品

### 操作:切换组中的选择

这为用户提供了向选择组添加或放下物品的能力.

![toggle-selection-in-a-group](https://user-images.githubusercontent.com/2182637/37323084-73c31eec-26d5-11e8-8c5c-7a1fc82f098b.gif)

#### 事件处理程序

如果用户`click`或按下**enter** <kbd>⏎</kbd>键,我们将执行此操作，除了按住适当的修饰键，以切换物品选择(根据操作系统).

> 注意:在Macintosh  系统上,这是`⌘ Command`键.在Windows系统上,这是`⎈ Ctrl`键.

#### 切换组行为中的选择

-   如果未选择该物品,则将该物品添加到所选物品
-   如果先前已选择该物品,则将其从所选物品中放下.

### 动作:多选

能够在列表中，进一步单击物品，并选择其中的所有内容.

#### 事件处理程序

如果用户执行`click`或按下**enter** <kbd>⏎</kbd>,我们将执行此操作，是除了按住[shift 键](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/shiftKey).

### 多选:行为

通过此操作,用户可以使用单个命令就选择多个物品。这种行为是最复杂的.它稍微偏离了`MacOSX`简单行为理念.

![multi-select](https://user-images.githubusercontent.com/2182637/37323230-7a108d60-26d6-11e8-84b1-1a608bab3686.gif)

#### 没有选择任何东西

如果用户触发此操作时，未选择任何内容:只需将所选物品设置为唯一选定的物品.

#### 选择其他列表

如果用户正在选择与，上一个选定物品位于不同列表中的物品: 清除所有选定物品，并选择新列表中所选物品的索引之前的所有内容

#### 选择在同一列表中

-   选择新选择的物品，和最后选择的物品之间的所有内容.

> MacOSX比这复杂一点,但就我们的目的而言,这似乎是一个很好的默认值

-   如果在我们开始时，使用相同的索引 - 我们不需要做任何事情

### 事件逻辑图

以下是在组件中，组成上述事件处理逻辑的示例

```js
class Task extends Component<Props> {
  onKeyDown = (
    event: KeyboardEvent,
    // 我们会在这里打上 猴子补丁
    provided: DraggableProvided,
    snapshot: DraggableStateSnapshot,
  ) => {
    if (provided.dragHandleProps) {
      provided.dragHandleProps.onKeyDown(event);
    }

    if (event.defaultPrevented) {
      return;
    }

    if (snapshot.isDragging) {
      return;
    }

    if (event.keyCode !== keyCodes.enter) {
      return;
    }

    // 为了选择，我们使用此事件 we are using the event for selection
    event.preventDefault();

    this.performAction(event);
  };

  // 使用 onClick ，若时个拖动行为，将有效阻止
  onClick = (event: MouseEvent) => {
    if (event.defaultPrevented) {
      return;
    }

    if (event.button !== primaryButton) {
      return;
    }

    // 标记此事件被使用了
    event.preventDefault();

    this.performAction(event);
  };

  // 确定是否使用了组密钥中，特定于平台的切换选择
  wasToggleInSelectionGroupKeyUsed = (event: MouseEvent | KeyboardEvent) => {
    const isUsingWindows = navigator.platform.indexOf('Win') >= 0;
    return isUsingWindows ? event.ctrlKey : event.metaKey;
  };

  // 确定是否使用了multiSelect键
  wasMultiSelectKeyUsed = (event: MouseEvent | KeyboardEvent) => event.shiftKey;

  performAction = (event: MouseEvent | KeyboardEvent) => {
    const {
      task,
      toggleSelection,
      toggleSelectionInGroup,
      multiSelectTo,
    } = this.props;

    if (this.wasToggleInSelectionGroupKeyUsed(event)) {
      toggleSelectionInGroup(task.id);
      return;
    }

    if (this.wasMultiSelectKeyUsed(event)) {
      multiSelectTo(task.id);
      return;
    }

    toggleSelection(task.id);
  };

  render() {
    return (
      <Draggable draggableId={task.id} index={this.props.index}>
        {(provided: DraggableProvided, snapshot: DraggableStateSnapshot) => (
          <Container
            innerRef={provided.innerRef}
            {...provided.draggableProps}
            {...provided.dragHandleProps}
            onClick={this.onClick}
            onKeyDown={(event: KeyboardEvent) =>
              this.onKeyDown(event, provided, snapshot)
            }
          >
            {task.content}
          </Container>
        )}
      </Draggable>
    );
  }
}
```

### 行动: 清除选择

#### `window` `click`处理器

我们添加一个`click`处理程序到`window`，用来检测不在`Draggable`的点击。我们将调用`preventDefault`在我们的选择的`onClick`中，因此`click`事件会将`event.defaultPrevented`属性设置为`true`。此外,如果拖动发生默认`click`行动[将被阻止](https://github.com/chinanf-boy/react-beautiful-dnd-zh#马虎点击并点击预防)。所以,如果我们在window上收到一个`click`,而其上`event.defaultPrevented`没有设为false，我们就清除当前选择。

#### `window` `keydown`处理器

此事件处理程序的运行方式与上面类似。如果一个`keydown`事件没有阻止, 且是**esc**按键，那我们清除当前的选择。如果是用于取消拖动，该**esc** `keydown`事件会被阻止.

### 移动选择

当用户使用触摸输入，按下物品时,不应执行"切换选择"动作,而应执行"组中的切换选择"。在触摸设备上,无法添加额外的输入,如一个`metaKey`或`shiftKey`.

你可以使用`onTouchEnd`操作，触发元素上的事件。与其他处理程序一样 - 只有在触发选择时，为`false`的`event.defaultPrevented`属性才会更改。当动作触发，一定调用`event.preventDefault()`事件，且会标记为已使用.

您还可能需要添加一个`window` `touchend`处理程序,其工作方式与`click`和`keydown` `window`处理一样。当用户执行`touchend`时,此处理程序将取消选择所有内容，这里的`touchend`不是拖动或选择的一部分.

我们用`touchend`，因为这是拖放生命周期的一部分。我们在`touchstart`上不调用`preventDefault()`，因为我们当时不知道该事件是否是一个拖动的一部分.[更多信息](../guides/how-we-use-dom-events.zh.md).

### 行动: 走箭头

> 这在我们的参考应用中，没有实现

欢迎您构建选择步行键盘交互模式。你可以使用箭头键(<kbd>↑</kbd> <kbd>↓</kbd> <kbd>→</kbd> <kbd>←</kbd>)移动选择。理想情况下,这些移动也会改变浏览器的焦点,以便用户可以按下**空格键** <kbd>space</kbd>立即举起

### 动作:鼠标选择框

> 这在我们的参考应用中，没有实现

您可以构建自己的抽象(或使用一些其他)来添加选择框的想法。您可以使用此选项允许用户，在要选择的物品围成框，拖动.[例子](http://threedubmedia.com/code/event/drop/demo/selection)

## 拖拽

我们需要检测下`onDragStart`。如果用户开始拖动未选择的内容,则需要清除选择.

随着拖动的开始,我们需要添加一些视觉效果:

1.  向拖动项添加计数，以指示此拖动代表的物品数。如果只拖动一个物品,则不显示计数.
2.  将未拖动的所选物品的外观更改为灰色/禁用状态。这会是一个scale[性能](#performance)问题.

我们不会从列表中，放下所选物品。如果我们完全放下物品,可以更改列表的尺寸,这可能导致列表折叠和滚动跳转。如果我们将它们留在列表中，并使它们不可见,那么列表中的大空白部分没有任何意义,并且可能会混淆交互。因此,我们建议将物品留在列表中，并进行直观更改.

## 放下

我们希望尽可能保留用户在拖动开始之前，所选择的物品。这样他们可以在拖拽后，继续移动相同的物品.

### 没变

取消拖动,无处放置或放入相同位置时，会发生这种情况。不需要重新排序,您可以保留以前的选择

### 放入不同的列表

将物品移动到新列表时,应将它们插入到放下拖动物品的索引处的新列表中.我们建议按以下顺序放置移动的物品:

1.  将所选物品移动到第一个位置

这样做是为了确保用户拖动的物品不会在放下时，突然消失.

2.  无论列表如何,按物品自然索引排序。例如,如果'item alpha'在索引2的第1列中开始,而'item beta'在索引2的第2列中开始,那么'item beta'应该放在'item alpha'之前

这优先考虑原始索引。但是,您可能希望优先考虑列表。因此,在先前列表中选择的物品，将在后续列表中选择的物品之前.

3.  如果出现平局,则按选择物品的顺序排序.

此策略确实会在语义上更改物品的顺序: 特别是 步骤1 ，始终将所选物品移动到顶部。如果您不想这样做,则不必这样做 - 但是它在视觉上更好,并且有助于使用户明确.

### 放在同一个列表中

目的是将所选物品移动到新位置。我们想要在放下拖动物品的索引处，插入所有物品。与上面的策略一样,我们建议放下物品的顺序如下:

1.  将所选物品移动到第一个位置
2.  按其自然指数排序其余部分

## 性能

以高效的方式进行多拖动交互可能具有挑战性。你想要做的核心是避免在不需要更新的组件上调用`render()`。目前最好的做法是使用[`redux`](https://github.com/reactjs/redux)与[`react-redux`](https://github.com/reactjs/react-redux)结合,[`reselect`](https://github.com/reactjs/reselect)和[`memoize-one`](https://github.com/alexreardon/memoize-one)。我们建议您查看以下资源:

-   [React性能介绍](https://medium.com/@alexandereardon/performance-optimisations-for-react-applications-b453c597b191)
-   [`redux`怎么样可以帮助您编写快速应用程序](https://medium.com/@alexandereardon/performance-optimisations-for-react-applications-round-2-2042e5c9af97)
-   [高级优化](https://medium.com/@alexandereardon/dragging-react-performance-forward-688b30d40a33)

### 选择物品的状态改变

响应您的选择，尽可能砍掉关于`Draggable`和`Droppable`组件的调用`render`成本。在我们的示例应用程序中,只要选择更改,我们就会重新渲染整个树。这种方法不推荐(not scale)。因此,我们建议使用上面列出的优化.

如果出现"取消全选"操作,您可能需要一次渲染大量组件,以清除其选定的样式.对于大多数用途,这还好。如果你想更进一步,你需要避免选择样式的变化，而调用`render`.

-   你可以考虑使用[动态共享样式模式](https://medium.com/@alexandereardon/dragging-react-performance-forward-688b30d40a33).
-   你可以记上一个**唯一**数据属性给每个物品,然后让*被选物*样式应用在父组件中的，动态选择器的样式.

此外,当拖动开始时,我们需要立刻更新很多`Draggables`的外观。因此,您也需要解决此问题,就像'取消所有选择'操作一样.

### 拖动计数

拖动时,您需要显示拖动物品的计数。在我们的示例中,我们通过重新呈现树来提供此信息。与选择更改一样,仅渲染需要更改的物品会还好。您可以使用`redux`和`redux-select`发布此信息。对于这个特殊的问题,你会想跑到[`unstated`](https://github.com/jamiebuilds/unstated)或新的[React 16.3`Context`api](https://github.com/reactjs/rfcs/blob/master/text/0002-new-version-of-context.zh.md)那里去看看.
