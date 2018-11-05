# 多拖

> 此页面旨在指导您添加自己的多拖动体验`react-beautiful-dnd`名单.

拖动多个`Draggable`s立即(多拖)目前是一种需要在其上构建的模式`react-beautiful-dnd`.我们没有将这种互动纳入图书馆本身.这样做是因为多拖动体验引入了许多概念,决策和意见.我们已经做了很多工作来确保有一个标准的基础[dom事件管理](/docs/guides/how-we-use-dom-events.md)建立在.

我们创造了一个[参考申请](react-beautiful-dnd.netlify.com/iframe.html?selectedKind=Multi%20drag&selectedStory=pattern&full=0&down=1&left=1&panelRight=0&downPanel=storybook%2Factions%2Factions-panel)([资源](/stories/9-multi-drag-story.js))实现这种多拖模式.该应用程序是相当基本的,并不能很好地处理大型列表中的性能.因此,有[一些性能建议](#performance)如果您想支持大于50的列表,我们建议您也添加到我们的参考应用程序中.

![multi drag demo](https://user-images.githubusercontent.com/2182637/37322724-7843a218-26d3-11e8-9ebb-8d5853387bb3.gif)

## 经验

我们已经决定开始使用简单但非常灵活且可扩展的多拖动模式.它不是*美丽*作为我们标准的拖动交互 - 但它是一个很好的基础,可以构建并扩展到许多问题空间.

## 用户体验

我们可以分三个阶段打破用户体验.

1.  [**选择**](#selection):用户选择一个或多个项目.
2.  [**拖延**](#dragging):用户拖动一个项目作为整个组的表示.
3.  [**删除**](#dropping):用户将项目放入新位置.我们将所有选定的项目移动到新位置

## 通告

请记住内部`react-beautiful-dnd`不知道多拖.因此建议您使用`HookProvided > Announce`宣布有意义的屏幕阅读器消息以进行多拖动.见我们的[屏幕阅读器指南](docs/guides/screen-reader.md)有关如何控制屏幕阅读器消息传递的详细信息

## 选择

在拖动开始之前,我们需要允许用户*可选*选择一些`Draggable`拖动.我们选择了一个项目,您应该将样式更新应用到`Draggable`例如背景颜色更改以指示项目已被选中.

### 选择互动建议

> 这些交互基于Mac OSX[*发现者*](https://support.apple.com/en-au/HT201732)(文件浏览器)应用程序.

### 行动:切换部分

如果用户单击某个项目,则应切换该项目的选定状态.此外,当用户按下时,应更新项目的选定状态**输入** <kbd>⏎</kbd>键.该**输入** <kbd>⏎</kbd>钥匙是相当不错的,因为我们不使用它来提升或下降 - 我们使用**空格键** <kbd>空间</kbd>对于那些.

![toggle-selection](https://user-images.githubusercontent.com/2182637/37323080-6d67f04a-26d5-11e8-8bc1-8ff5178018bc.gif)

#### `onClick`事件处理程序

-   附上一个`onClick`处理你的*拖动手柄*要么`Draggable`
-   仅在用户使用时切换选择[`primaryButton`](https://developer.mozilla.org/en-US/docs/Web/API/MouseEvent/button)(`event.button === 0`)
-   防止默认操作`click`因为你正在使用它进行选择(它只对你有用`event.preventDefault()`避免*选择清算*)

#### 键盘事件处理程序

-   当用户按下时**输入** <kbd>⏎</kbd>切换项目的选择
-   **选项1**:附上一个`onKeyDown`处理你的*拖动手柄*要么`Draggable`.你将需要猴子补丁`DragHandleProvided > onKeyDown`键盘处理程序
-   **选项2**:附上一个`onKeyUp`处理你的*拖动手柄*.那你就不需要猴子补丁了`onKeyDown`处理程序.然而,`keyup`事件不会阻止其默认操作,因此您将无法检查`event.defaultPrevented`查看按键是否用于拖动.如果你只是使用**输入** <kbd>⏎</kbd>键入你的事件处理程序然后你应该没事,因为它不用作拖动的一部分.
-   防止默认操作`keydown`/`keyup`如果您在选择时切换选择,因为您要选择退出标准浏览器行为并且还提供已使用此事件的线索,则会触发该事件.

#### 切换选择行为

-   如果之前未选择该项目,请将其设为唯一选定的项目
-   如果该项目先前已被选中**并不是其中的一部分**选择组:取消选择该项目
-   如果该项目先前已被选中**并且是一部分**选择组:使其成为唯一选定的项目

### 操作:切换组中的选择

这为用户提供了向选择组添加或删除项目的能力.

![toggle-selection-in-a-group](https://user-images.githubusercontent.com/2182637/37323084-73c31eec-26d5-11e8-8c5c-7a1fc82f098b.gif)

#### 事件处理程序

如果用户执行此操作,我们将执行此操作`click`或按下**输入** <kbd>⏎</kbd>键除了保持适当的修饰键以切换其操作系统的项目选择.

> 注意:在Macintosh系统上,这是`⌘ Command`键.在Windows系统上,这是`⎈ Ctrl`键.

#### 切换组行为中的选择

-   如果未选择该项目,则将该项目添加到所选项目
-   如果先前已选择该项目,则将其从所选项目中删除.

### 动作:多选

能够在列表中进一步单击项目并选择其中的所有内容.

#### 事件处理程序

如果用户执行此操作,我们将执行此操作`click`或按下**输入** <kbd>⏎</kbd>关键是除了持有[换班钥匙](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/shiftKey).

### 多选:行为

通过此操作,用户可以使用单个命令选择多个项目.这种行为是最复杂的.它稍微偏离了`MacOSX`行为简单.

![multi-select](https://user-images.githubusercontent.com/2182637/37323230-7a108d60-26d6-11e8-84b1-1a608bab3686.gif)

#### 没有选择任何东西

如果用户触发此操作时未选择任何内容:只需将所选项目设置为唯一选定的项目.

#### 选择其他列表

如果用户正在选择与上一个选定项目位于不同列表中的项目:清除所有选定项目并选择新列表中所选项目的索引之前的所有内容

#### 选择在同一列表中

-   选择新选择的项目和最后选择的项目之间的所有内容.

> MacOSX比这复杂一点,但就我们的目的而言,这似乎是一个很好的默认值

-   如果在我们开始时使用相同的索引 - 我们不需要做任何事情

### 事件逻辑图

以下是在组件中组成上述事件处理逻辑的示例

```js
class Task extends Component<Props> {
  onKeyDown = (
    event: KeyboardEvent,
    // we will be monkey patching this
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

    // we are using the event for selection
    event.preventDefault();

    this.performAction(event);
  };

  // Using onClick as it will be correctly
  // preventing if there was a drag
  onClick = (event: MouseEvent) => {
    if (event.defaultPrevented) {
      return;
    }

    if (event.button !== primaryButton) {
      return;
    }

    // marking the event as used
    event.preventDefault();

    this.performAction(event);
  };

  // Determines if the platform specific toggle selection in group key was used
  wasToggleInSelectionGroupKeyUsed = (event: MouseEvent | KeyboardEvent) => {
    const isUsingWindows = navigator.platform.indexOf('Win') >= 0;
    return isUsingWindows ? event.ctrlKey : event.metaKey;
  };

  // Determines if the multiSelect key was used
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

### 行动:明确选择

#### `window` `click`处理器

我们添加一个`click`处理程序`window`检测不在的点击`Draggable`.我们称之为`preventDefault`在我们的选择`onClick`处理程序`click`用于选择的事件将具有`event.defaultPrevented`属性设置为`true`.此外,如果拖动发生默认值`click`行动[将被阻止](https://github.com/atlassian/react-beautiful-dnd#sloppy-clicks-and-click-prevention-).所以,如果我们收到一个`click`窗口上没有的事件`event.defaultPrevented`设置为false我们清除当前选择.

#### `window` `keydown`处理器

此事件处理程序的运行方式与此类似*`window` `click`处理器*如上所述.如果一个`keydown`没有阻止的事件,是**逃逸**然后我们清除当前的选择.该**逃逸** `keydown`如果用于取消拖动,将阻止事件.

### 移动选择

当用户使用触摸输入按下项目时,不应执行"切换选择"动作,而应执行"组中的切换选择".在触摸设备上,无法添加额外的输入,例如a`metaKey`要么`shiftKey`.

你可以使用`onTouchEnd`触发此操作的元素上的事件.与其他处理程序一样 - 只有在触发选择时才会更改`event.defaultPrevented`财产是`false`.当发射动作时一定要打电话`event.preventDefault()`将事件标记为已使用.

您还需要添加一个`window` `touchend`处理程序,其工作方式与`click`和`keydown` `window`处理程序.当用户执行时,此处理程序将用于取消选择所有内容`touchend`这不是拖动或选择的一部分.

我们用`touchend`因为这是拖放生命周期的一部分.我们不打电话`preventDefault()`在...上`touchstart`因为我们当时不知道该事件是否是一个阻力的一部分.[更多信息](/docs/guides/how-we-use-dom-events.md).

### 行动:走路

> 这在我们的参考申请中没有实现

欢迎您构建选择步行键盘交互模式.你可以使用箭头键(<kbd>↑</kbd> <kbd>↓</kbd> <kbd>→</kbd> <kbd>←</kbd>)移动选择.理想情况下,这些移动也会改变浏览器的焦点,以便用户可以按下**空格键** <kbd>空间</kbd>立即举起

### 动作:鼠标选择框

> 这在我们的参考申请中没有实现

您可以构建自己的抽象(或使用一些其他)来添加选择框的想法.您可以使用此选项允许用户在要选择的项目周围拖动一个框.[例](http://threedubmedia.com/code/event/drop/demo/selection)

## 拖延

我们需要办理一张登机手续`onDragStart`.如果用户开始拖动未选择的内容,则需要清除选择.

随着阻力的开始,我们需要添加一些视觉效果:

1.  向拖动项添加计数以指示此拖动代表的项目数.如果只拖动一个项目,则不显示计数.
2.  将未拖动的所选项目的外观更改为灰色/禁用状态.这可以是一个[性能](#performance)大规模发行.

我们不会从列表中删除所选项目.如果我们完全删除项目,可以更改列表的尺寸,这可能导致列表折叠和滚动跳转.如果我们将它们留在列表中并使它们不可见,那么列表中的大空白部分没有任何意义,并且可能会混淆与之交互.因此,我们建议将项目留在列表中并进行直观更改.

## 删除

我们希望尽可能保留用户在拖动开始之前所具有的选择.这样他们可以在拖拽后继续移动相同的物品.

### 没变

取消拖动,无处放置或放入相同位置时会发生这种情况.不需要重新排序,您可以保留以前的选择

### 放入不同的列表

将项目移动到新列表时,应将它们插入到删除拖动项目的索引处的新列表中.我们建议按以下顺序放置移动的项目:

1.  将所选项目移动到第一个位置

这样做是为了确保用户拖动的项目不会在下降时突然消失.

2.  无论列表如何,按项目自然索引排序.例如,如果'item alpha'在索引2的第1列中开始,而'item beta'在索引2的第2列中开始,那么'item beta'应该放在'item alpha'之前

这优先考虑原始索引.但是,您可能希望优先考虑列表.因此,在先前列表中选择的项目将在后续列表中选择的项目之前.

3.  如果出现平局,则按选择项目的顺序排序.

此策略确实会在语义上更改项目的顺序:特别是步骤1始终将所选项目移动到顶部.如果您不想这样做,则不必这样做 - 但是它在视觉上更好,并且有助于使用户保持接地.

### 放在同一个列表中

目标是将所选项目移动到新位置.我们想要在删除拖动项目的索引处插入所有项目.与上面的策略一样,我们建议删除项目的顺序如下:

1.  将所选项目移动到第一个位置
2.  按其自然指数排序其余部分

## 性能

以高效的方式进行多拖动交互可能具有挑战性.你想要做的核心是避免打电话`render()`在不需要更新的组件上.目前最好的做法是使用[`redux`](https://github.com/reactjs/redux)与...结合[`react-redux`](https://github.com/reactjs/react-redux),[`reselect`](https://github.com/reactjs/reselect)和[`memoize-one`](https://github.com/alexreardon/memoize-one).我们建议您查看以下资源:

-   [React性能介绍](https://medium.com/@alexandereardon/performance-optimisations-for-react-applications-b453c597b191)
-   [怎么样`redux`可以帮助您编写快速应用程序](https://medium.com/@alexandereardon/performance-optimisations-for-react-applications-round-2-2042e5c9af97)
-   [高级优化](https://medium.com/@alexandereardon/dragging-react-performance-forward-688b30d40a33)

### 选择状态改变

响应您要调用的选择更改`render`关于最低金额`Draggable`和`Droppable`组件尽可能.在我们的示例应用程序中,只要选择更改,我们就会重新渲染整个树.这种方法不会扩展.因此,我们建议使用上面列出的优化.

如果出现"取消全选"操作,您可能需要一次渲染大量组件以清除其选定的样式.对于大多数用途,这将是好的.如果你想更进一步,你需要避免打电话`render`用于选择样式的变化.

-   你可以考虑使用[动态共享样式模式](https://medium.com/@alexandereardon/dragging-react-performance-forward-688b30d40a33).
-   你可以申请一个**独特**数据属性到每个项目,然后应用*选*在父组件中动态使用选择器的样式.

此外,当拖动开始时,我们也可以更新很多的外观`Draggables`立刻.因此,您需要解决此问题,就像'取消选择所有'操作一样.

### 拖动计数

拖动时,您需要显示拖动项目的计数.在我们的示例中,我们通过重新呈现树来提供此信息.与选择更改一样,仅渲染需要更改的项目会很好.您可以使用发布此信息`redux`和`redux-select`.对于这个特殊的问题,你可能会逃脱[`unstated`](https://github.com/jamiebuilds/unstated)或新的[反应16.3`Context`api](https://github.com/reactjs/rfcs/blob/master/text/0002-new-version-of-context.md).
