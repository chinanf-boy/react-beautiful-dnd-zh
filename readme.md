# react-beautiful-dnd [![explain](http://llever.com/explain.svg)](https://github.com/chinanf-boy/Source-Explain)

「 `React.js` 漂亮,可移植性 列表拖拽库 」{翻译}

[github source](https://github.com/atlassian/react-beautiful-dnd)

---

穷

<a href="https://patreon.com/yobrave">
<img src="https://c5.patreon.com/external/logo/become_a_patron_button@2x.png" height="30">
</a>

---

## 中文翻译

[中文 dnd.zh.md](./dnd.zh.md)

<details>

<summary> 原文-commit readme.md 链接 </summary>

https://github.com/atlassian/react-beautiful-dnd/blob/cea1a62c0011f8560edf7935dc06cdfa71d51110/README.md

</details>

### 校对

- [ ] [React 美丽 免打扰](./dnd.zh.md#%E5%8F%8D%E5%BA%94---%E7%BE%8E%E4%B8%BD---%E5%85%8D%E6%89%93%E6%89%B0)
  - [ ] [例子🎉](./dnd.zh.md#%E4%BE%8B%E5%AD%90)
    - [ ] [在桌面上查看](./dnd.zh.md#%E5%9C%A8%E6%A1%8C%E9%9D%A2%E4%B8%8A%E6%9F%A5%E7%9C%8B)
    - [ ] [在手机或平板电脑上查看](./dnd.zh.md#%E5%9C%A8%E6%89%8B%E6%9C%BA%E6%88%96%E5%B9%B3%E6%9D%BF%E7%94%B5%E8%84%91%E4%B8%8A%E6%9F%A5%E7%9C%8B)
  - [ ] [基本使用示例](./dnd.zh.md#%E5%9F%BA%E6%9C%AC%E4%BD%BF%E7%94%A8%E7%A4%BA%E4%BE%8B)
  - [ ] [升级](./dnd.zh.md#%E5%8D%87%E7%BA%A7)
  - [ ] [核心特点](./dnd.zh.md#%E6%A0%B8%E5%BF%83%E7%89%B9%E7%82%B9)
  - [ ] [目前支持的功能集](./dnd.zh.md#%E7%9B%AE%E5%89%8D%E6%94%AF%E6%8C%81%E7%9A%84%E5%8A%9F%E8%83%BD%E9%9B%86)
    - [ ] [更多即将推出](./dnd.zh.md#%E6%9B%B4%E5%A4%9A%E5%8D%B3%E5%B0%86%E6%8E%A8%E5%87%BA)
  - [ ] [并不适合所有人](./dnd.zh.md#%E5%B9%B6%E4%B8%8D%E9%80%82%E5%90%88%E6%89%80%E6%9C%89%E4%BA%BA)
  - [ ] [驾驶理念: 物理性](./dnd.zh.md#%E9%A9%BE%E9%A9%B6%E7%90%86%E5%BF%B5-%E7%89%A9%E7%90%86%E6%80%A7)
    - [ ] [应用1: 没有即时移动](./dnd.zh.md#%E5%BA%94%E7%94%A81-%E6%B2%A1%E6%9C%89%E5%8D%B3%E6%97%B6%E7%A7%BB%E5%8A%A8)
    - [ ] [应用2: 知道何时移动](./dnd.zh.md#%E5%BA%94%E7%94%A82-%E7%9F%A5%E9%81%93%E4%BD%95%E6%97%B6%E7%A7%BB%E5%8A%A8)
    - [ ] [应用程序3: 没有阴影](./dnd.zh.md#%E5%BA%94%E7%94%A8%E7%A8%8B%E5%BA%8F3-%E6%B2%A1%E6%9C%89%E9%98%B4%E5%BD%B1)
    - [ ] [应用4: 最大化交互性](./dnd.zh.md#%E5%BA%94%E7%94%A84-%E6%9C%80%E5%A4%A7%E5%8C%96%E4%BA%A4%E4%BA%92%E6%80%A7)
    - [ ] [应用5: 无拖动轴锁定](./dnd.zh.md#%E5%BA%94%E7%94%A85-%E6%97%A0%E6%8B%96%E5%8A%A8%E8%BD%B4%E9%94%81%E5%AE%9A)
    - [ ] [应用6: 自然交叉表移动](./dnd.zh.md#%E5%BA%94%E7%94%A86-%E8%87%AA%E7%84%B6%E4%BA%A4%E5%8F%89%E8%A1%A8%E7%A7%BB%E5%8A%A8)
  - [ ] [精心设计的动画](./dnd.zh.md#%E7%B2%BE%E5%BF%83%E8%AE%BE%E8%AE%A1%E7%9A%84%E5%8A%A8%E7%94%BB)
    - [ ] [删除](./dnd.zh.md#%E5%88%A0%E9%99%A4)
    - [ ] [走出困境](./dnd.zh.md#%E8%B5%B0%E5%87%BA%E5%9B%B0%E5%A2%83)
  - [ ] [关心交互细节](./dnd.zh.md#%E5%85%B3%E5%BF%83%E4%BA%A4%E4%BA%92%E7%BB%86%E8%8A%82)
    - [ ] [重点管理](./dnd.zh.md#%E9%87%8D%E7%82%B9%E7%AE%A1%E7%90%86)
    - [ ] [自动滚动](./dnd.zh.md#%E8%87%AA%E5%8A%A8%E6%BB%9A%E5%8A%A8)
      - [ ] [对于鼠标和触摸输入🐭📱](./dnd.zh.md#%E5%AF%B9%E4%BA%8E%E9%BC%A0%E6%A0%87%E5%92%8C%E8%A7%A6%E6%91%B8%E8%BE%93%E5%85%A5)
        - [ ] [鼠标滚轮和触控板](./dnd.zh.md#%E9%BC%A0%E6%A0%87%E6%BB%9A%E8%BD%AE%E5%92%8C%E8%A7%A6%E6%8E%A7%E6%9D%BF)
        - [ ] [关于大的一个笔记`Draggable`小号](./dnd.zh.md#%E5%85%B3%E4%BA%8E%E5%A4%A7%E7%9A%84%E4%B8%80%E4%B8%AA%E7%AC%94%E8%AE%B0draggable%E5%B0%8F%E5%8F%B7)
        - [ ] [iOS自动滚动摇晃📱🤕](./dnd.zh.md#ios%E8%87%AA%E5%8A%A8%E6%BB%9A%E5%8A%A8%E6%91%87%E6%99%83)
      - [ ] [用于键盘拖动🎹](./dnd.zh.md#%E7%94%A8%E4%BA%8E%E9%94%AE%E7%9B%98%E6%8B%96%E5%8A%A8)
    - [ ] [无障碍](./dnd.zh.md#%E6%97%A0%E9%9A%9C%E7%A2%8D)
      - [ ] [示例屏幕阅读器行为](./dnd.zh.md#%E7%A4%BA%E4%BE%8B%E5%B1%8F%E5%B9%95%E9%98%85%E8%AF%BB%E5%99%A8%E8%A1%8C%E4%B8%BA)
  - [ ] [鼠标拖动](./dnd.zh.md#%E9%BC%A0%E6%A0%87%E6%8B%96%E5%8A%A8)
    - [ ] [马虎点击并点击预防🐱🎁](./dnd.zh.md#%E9%A9%AC%E8%99%8E%E7%82%B9%E5%87%BB%E5%B9%B6%E7%82%B9%E5%87%BB%E9%A2%84%E9%98%B2)
    - [ ] [键盘快捷键: 鼠标拖动](./dnd.zh.md#%E9%94%AE%E7%9B%98%E5%BF%AB%E6%8D%B7%E9%94%AE-%E9%BC%A0%E6%A0%87%E6%8B%96%E5%8A%A8)
  - [ ] [键盘拖动](./dnd.zh.md#%E9%94%AE%E7%9B%98%E6%8B%96%E5%8A%A8)
    - [ ] [键盘快捷键: 键盘拖动](./dnd.zh.md#%E9%94%AE%E7%9B%98%E5%BF%AB%E6%8D%B7%E9%94%AE-%E9%94%AE%E7%9B%98%E6%8B%96%E5%8A%A8)
      - [ ] [在一个垂直列表中](./dnd.zh.md#%E5%9C%A8%E4%B8%80%E4%B8%AA%E5%9E%82%E7%9B%B4%E5%88%97%E8%A1%A8%E4%B8%AD)
      - [ ] [在一个水平列表中](./dnd.zh.md#%E5%9C%A8%E4%B8%80%E4%B8%AA%E6%B0%B4%E5%B9%B3%E5%88%97%E8%A1%A8%E4%B8%AD)
  - [ ] [触摸拖动](./dnd.zh.md#%E8%A7%A6%E6%91%B8%E6%8B%96%E5%8A%A8)
    - [ ] [理解意图: 点击,强制按下,滚动并拖动](./dnd.zh.md#%E7%90%86%E8%A7%A3%E6%84%8F%E5%9B%BE-%E7%82%B9%E5%87%BB%E5%BC%BA%E5%88%B6%E6%8C%89%E4%B8%8B%E6%BB%9A%E5%8A%A8%E5%B9%B6%E6%8B%96%E5%8A%A8)
    - [ ] [开始拖动: 长按](./dnd.zh.md#%E5%BC%80%E5%A7%8B%E6%8B%96%E5%8A%A8-%E9%95%BF%E6%8C%89)
    - [ ] [点按支持](./dnd.zh.md#%E7%82%B9%E6%8C%89%E6%94%AF%E6%8C%81)
    - [ ] [原生滚动支持](./dnd.zh.md#%E5%8E%9F%E7%94%9F%E6%BB%9A%E5%8A%A8%E6%94%AF%E6%8C%81)
    - [ ] [强制按压支持](./dnd.zh.md#%E5%BC%BA%E5%88%B6%E6%8C%89%E5%8E%8B%E6%94%AF%E6%8C%81)
    - [ ] [振动](./dnd.zh.md#%E6%8C%AF%E5%8A%A8)
  - [ ] [多拖](./dnd.zh.md#%E5%A4%9A%E6%8B%96)
  - [ ] [预设样式](./dnd.zh.md#%E9%A2%84%E8%AE%BE%E6%A0%B7%E5%BC%8F)
    - [ ] [在每个阶段](./dnd.zh.md#%E5%9C%A8%E6%AF%8F%E4%B8%AA%E9%98%B6%E6%AE%B5)
      - [ ] [总是: 拖动手柄](./dnd.zh.md#%E6%80%BB%E6%98%AF-%E6%8B%96%E5%8A%A8%E6%89%8B%E6%9F%84)
      - [ ] [始终: 可以丢弃](./dnd.zh.md#%E5%A7%8B%E7%BB%88-%E5%8F%AF%E4%BB%A5%E4%B8%A2%E5%BC%83)
    - [ ] [阶段: 休息](./dnd.zh.md#%E9%98%B6%E6%AE%B5-%E4%BC%91%E6%81%AF)
      - [ ] [(阶段: 休息) : 拖动手柄](./dnd.zh.md#%E9%98%B6%E6%AE%B5-%E4%BC%91%E6%81%AF--%E6%8B%96%E5%8A%A8%E6%89%8B%E6%9F%84)
    - [ ] [阶段: 拖动](./dnd.zh.md#%E9%98%B6%E6%AE%B5-%E6%8B%96%E5%8A%A8)
      - [ ] [(阶段: 拖动) : 拖动句柄元素](./dnd.zh.md#%E9%98%B6%E6%AE%B5-%E6%8B%96%E5%8A%A8--%E6%8B%96%E5%8A%A8%E5%8F%A5%E6%9F%84%E5%85%83%E7%B4%A0)
      - [ ] [(阶段: 拖动) : 可拖动的元素](./dnd.zh.md#%E9%98%B6%E6%AE%B5-%E6%8B%96%E5%8A%A8--%E5%8F%AF%E6%8B%96%E5%8A%A8%E7%9A%84%E5%85%83%E7%B4%A0)
      - [ ] [(阶段: 拖动) : body元素](./dnd.zh.md#%E9%98%B6%E6%AE%B5-%E6%8B%96%E5%8A%A8--body%E5%85%83%E7%B4%A0)
    - [ ] [阶段: 下降](./dnd.zh.md#%E9%98%B6%E6%AE%B5-%E4%B8%8B%E9%99%8D)
      - [ ] [(阶段: 删除) : 拖动句柄元素](./dnd.zh.md#%E9%98%B6%E6%AE%B5-%E5%88%A0%E9%99%A4--%E6%8B%96%E5%8A%A8%E5%8F%A5%E6%9F%84%E5%85%83%E7%B4%A0)
      - [ ] [(阶段: 下降) : 可拖动](./dnd.zh.md#%E9%98%B6%E6%AE%B5-%E4%B8%8B%E9%99%8D--%E5%8F%AF%E6%8B%96%E5%8A%A8)
    - [ ] [阶段: 用户取消](./dnd.zh.md#%E9%98%B6%E6%AE%B5-%E7%94%A8%E6%88%B7%E5%8F%96%E6%B6%88)
    - [ ] [预设样式是供应商的前缀](./dnd.zh.md#%E9%A2%84%E8%AE%BE%E6%A0%B7%E5%BC%8F%E6%98%AF%E4%BE%9B%E5%BA%94%E5%95%86%E7%9A%84%E5%89%8D%E7%BC%80)
  - [ ] [安装](./dnd.zh.md#%E5%AE%89%E8%A3%85)
    - [ ] [包管理器](./dnd.zh.md#%E5%8C%85%E7%AE%A1%E7%90%86%E5%99%A8)
    - [ ] [分发包](./dnd.zh.md#%E5%88%86%E5%8F%91%E5%8C%85)
  - [ ] [`ClojureScript`](./dnd.zh.md#clojurescript)
  - [ ] [API](./dnd.zh.md#api)
  - [ ] [`DragDropContext`](./dnd.zh.md#dragdropcontext)
    - [ ] [道具](./dnd.zh.md#%E9%81%93%E5%85%B7)
    - [ ] [基本用法](./dnd.zh.md#%E5%9F%BA%E6%9C%AC%E7%94%A8%E6%B3%95)
    - [ ] [`Hook`小号](./dnd.zh.md#hook%E5%B0%8F%E5%8F%B7)
    - [ ] [`provided: HookProvided`](./dnd.zh.md#provided-hookprovided)
    - [ ] [`onDragStart` (可选的)](./dnd.zh.md#ondragstart-%E5%8F%AF%E9%80%89%E7%9A%84)
      - [ ] [`start: DragStart`](./dnd.zh.md#start-dragstart)
      - [ ] [`onDragStart`类型信息](./dnd.zh.md#ondragstart%E7%B1%BB%E5%9E%8B%E4%BF%A1%E6%81%AF)
    - [ ] [`onDragUpdate` (可选的)](./dnd.zh.md#ondragupdate-%E5%8F%AF%E9%80%89%E7%9A%84)
      - [ ] [`update: DragUpdate`](./dnd.zh.md#update-dragupdate)
    - [ ] [`onDragEnd` (需要)](./dnd.zh.md#ondragend-%E9%9C%80%E8%A6%81)
      - [ ] [`result: DropResult`](./dnd.zh.md#result-dropresult)
    - [ ] [同步重新排序](./dnd.zh.md#%E5%90%8C%E6%AD%A5%E9%87%8D%E6%96%B0%E6%8E%92%E5%BA%8F)
      - [ ] [这是你需要做的](./dnd.zh.md#%E8%BF%99%E6%98%AF%E4%BD%A0%E9%9C%80%E8%A6%81%E5%81%9A%E7%9A%84)
    - [ ] [坚持重新排序](./dnd.zh.md#%E5%9D%9A%E6%8C%81%E9%87%8D%E6%96%B0%E6%8E%92%E5%BA%8F)
    - [ ] [最佳实践`hooks`](./dnd.zh.md#%E6%9C%80%E4%BD%B3%E5%AE%9E%E8%B7%B5hooks)
      - [ ] [在拖动过程中阻止更新](./dnd.zh.md#%E5%9C%A8%E6%8B%96%E5%8A%A8%E8%BF%87%E7%A8%8B%E4%B8%AD%E9%98%BB%E6%AD%A2%E6%9B%B4%E6%96%B0)
        - [ ] [你如何阻止更新?](./dnd.zh.md#%E4%BD%A0%E5%A6%82%E4%BD%95%E9%98%BB%E6%AD%A2%E6%9B%B4%E6%96%B0)
        - [ ] [没有更新阻止会导致不好的时间](./dnd.zh.md#%E6%B2%A1%E6%9C%89%E6%9B%B4%E6%96%B0%E9%98%BB%E6%AD%A2%E4%BC%9A%E5%AF%BC%E8%87%B4%E4%B8%8D%E5%A5%BD%E7%9A%84%E6%97%B6%E9%97%B4)
    - [ ] [`onDragStart`和`onDragEnd`配对](./dnd.zh.md#ondragstart%E5%92%8Condragend%E9%85%8D%E5%AF%B9)
  - [ ] [`Droppable`](./dnd.zh.md#droppable)
    - [ ] [可投掷道具](./dnd.zh.md#%E5%8F%AF%E6%8A%95%E6%8E%B7%E9%81%93%E5%85%B7)
    - [ ] [儿童功能](./dnd.zh.md#%E5%84%BF%E7%AB%A5%E5%8A%9F%E8%83%BD)
      - [ ] [1.提供:  (DroppableProvided) \*\*: 为了使droppable能够正常工作,](./dnd.zh.md#1%E6%8F%90%E4%BE%9B--droppableprovided-%5C%5C-%E4%B8%BA%E4%BA%86%E4%BD%BFdroppable%E8%83%BD%E5%A4%9F%E6%AD%A3%E5%B8%B8%E5%B7%A5%E4%BD%9C)
      - [ ] [该功能还提供有与当前拖动状态有关的少量状态.](./dnd.zh.md#%E8%AF%A5%E5%8A%9F%E8%83%BD%E8%BF%98%E6%8F%90%E4%BE%9B%E6%9C%89%E4%B8%8E%E5%BD%93%E5%89%8D%E6%8B%96%E5%8A%A8%E7%8A%B6%E6%80%81%E6%9C%89%E5%85%B3%E7%9A%84%E5%B0%91%E9%87%8F%E7%8A%B6%E6%80%81)
    - [ ] [那些共享相同的人](./dnd.zh.md#%E9%82%A3%E4%BA%9B%E5%85%B1%E4%BA%AB%E7%9B%B8%E5%90%8C%E7%9A%84%E4%BA%BA)
    - [ ] [滚动容器](./dnd.zh.md#%E6%BB%9A%E5%8A%A8%E5%AE%B9%E5%99%A8)
    - [ ] [空`Droppable`小号](./dnd.zh.md#%E7%A9%BAdroppable%E5%B0%8F%E5%8F%B7)
    - [ ] [推荐Droppable性能优化](./dnd.zh.md#%E6%8E%A8%E8%8D%90droppable%E6%80%A7%E8%83%BD%E4%BC%98%E5%8C%96)
  - [ ] [`Draggable`](./dnd.zh.md#draggable)
    - [ ] [可拖动道具](./dnd.zh.md#%E5%8F%AF%E6%8B%96%E5%8A%A8%E9%81%93%E5%85%B7)
    - [ ] [儿童功能 (渲染道具)](./dnd.zh.md#%E5%84%BF%E7%AB%A5%E5%8A%9F%E8%83%BD-%E6%B8%B2%E6%9F%93%E9%81%93%E5%85%B7)
      - [ ] [1.提供:  (DraggableProvided) \*\*所有内容](./dnd.zh.md#1%E6%8F%90%E4%BE%9B--draggableprovided-%5C%5C%E6%89%80%E6%9C%89%E5%86%85%E5%AE%B9)
        - [ ] [`innerRef`: 这是一个包含a的对象](./dnd.zh.md#innerref-%E8%BF%99%E6%98%AF%E4%B8%80%E4%B8%AA%E5%8C%85%E5%90%ABa%E7%9A%84%E5%AF%B9%E8%B1%A1)
        - [ ] [`draggableProps`例](./dnd.zh.md#draggableprops%E4%BE%8B)
        - [ ] [`draggableProps`定位所有权](./dnd.zh.md#draggableprops%E5%AE%9A%E4%BD%8D%E6%89%80%E6%9C%89%E6%9D%83)
        - [ ] [它是该库的一个合约,它拥有拖动元素的定位逻辑.](./dnd.zh.md#%E5%AE%83%E6%98%AF%E8%AF%A5%E5%BA%93%E7%9A%84%E4%B8%80%E4%B8%AA%E5%90%88%E7%BA%A6%E5%AE%83%E6%8B%A5%E6%9C%89%E6%8B%96%E5%8A%A8%E5%85%83%E7%B4%A0%E7%9A%84%E5%AE%9A%E4%BD%8D%E9%80%BB%E8%BE%91)
        - [ ] [警告: `position: fixed`](./dnd.zh.md#%E8%AD%A6%E5%91%8A-position-fixed)
        - [ ] [在列表之间移动时保持焦点](./dnd.zh.md#%E5%9C%A8%E5%88%97%E8%A1%A8%E4%B9%8B%E9%97%B4%E7%A7%BB%E5%8A%A8%E6%97%B6%E4%BF%9D%E6%8C%81%E7%84%A6%E7%82%B9)
        - [ ] [扩展`DraggableProps.style`](./dnd.zh.md#%E6%89%A9%E5%B1%95draggablepropsstyle)
        - [ ] [避免边缘折叠`Draggable`小号](./dnd.zh.md#%E9%81%BF%E5%85%8D%E8%BE%B9%E7%BC%98%E6%8A%98%E5%8F%A0draggable%E5%B0%8F%E5%8F%B7)
        - [ ] [`Draggable`s应该是可见的兄弟姐妹](./dnd.zh.md#draggables%E5%BA%94%E8%AF%A5%E6%98%AF%E5%8F%AF%E8%A7%81%E7%9A%84%E5%85%84%E5%BC%9F%E5%A7%90%E5%A6%B9)
        - [ ] [`dragHandleProps`类型信息](./dnd.zh.md#draghandleprops%E7%B1%BB%E5%9E%8B%E4%BF%A1%E6%81%AF)
        - [ ] [`dragHandleProps`例如: 标准](./dnd.zh.md#draghandleprops%E4%BE%8B%E5%A6%82-%E6%A0%87%E5%87%86)
        - [ ] [`dragHandleProps`例如: 自定义拖动手柄](./dnd.zh.md#draghandleprops%E4%BE%8B%E5%A6%82-%E8%87%AA%E5%AE%9A%E4%B9%89%E6%8B%96%E5%8A%A8%E6%89%8B%E6%9F%84)
        - [ ] [`dragHandleProps`猴子补丁](./dnd.zh.md#draghandleprops%E7%8C%B4%E5%AD%90%E8%A1%A5%E4%B8%81)
      - [ ] [2.快照:  (DraggableStateSnapshot) \*\*该](./dnd.zh.md#2%E5%BF%AB%E7%85%A7--draggablestatesnapshot-%5C%5C%E8%AF%A5)
    - [ ] [`Draggable`占位符](./dnd.zh.md#draggable%E5%8D%A0%E4%BD%8D%E7%AC%A6)
    - [ ] [添加一个`onClick`处理程序`Draggable`或者a*拖动手柄*](./dnd.zh.md#%E6%B7%BB%E5%8A%A0%E4%B8%80%E4%B8%AAonclick%E5%A4%84%E7%90%86%E7%A8%8B%E5%BA%8Fdraggable%E6%88%96%E8%80%85a%E6%8B%96%E5%8A%A8%E6%89%8B%E6%9F%84)
    - [ ] [交互式的子元素`Draggable`](./dnd.zh.md#%E4%BA%A4%E4%BA%92%E5%BC%8F%E7%9A%84%E5%AD%90%E5%85%83%E7%B4%A0draggable)
  - [ ] [`resetServerContext`](./dnd.zh.md#resetservercontext)
  - [ ] [流量使用](./dnd.zh.md#%E6%B5%81%E9%87%8F%E4%BD%BF%E7%94%A8)
    - [ ] [公共流量类型](./dnd.zh.md#%E5%85%AC%E5%85%B1%E6%B5%81%E9%87%8F%E7%B1%BB%E5%9E%8B)
    - [ ] [使用流量类型](./dnd.zh.md#%E4%BD%BF%E7%94%A8%E6%B5%81%E9%87%8F%E7%B1%BB%E5%9E%8B)
  - [ ] [打字稿](./dnd.zh.md#%E6%89%93%E5%AD%97%E7%A8%BF)
    - [ ] [用流程类型示例应用程序](./dnd.zh.md#%E7%94%A8%E6%B5%81%E7%A8%8B%E7%B1%BB%E5%9E%8B%E7%A4%BA%E4%BE%8B%E5%BA%94%E7%94%A8%E7%A8%8B%E5%BA%8F)
  - [ ] [工程健康](./dnd.zh.md#%E5%B7%A5%E7%A8%8B%E5%81%A5%E5%BA%B7)
    - [ ] [类型化](./dnd.zh.md#%E7%B1%BB%E5%9E%8B%E5%8C%96)
    - [ ] [经测试](./dnd.zh.md#%E7%BB%8F%E6%B5%8B%E8%AF%95)
    - [ ] [性能](./dnd.zh.md#%E6%80%A7%E8%83%BD)
  - [ ] [尺寸](./dnd.zh.md#%E5%B0%BA%E5%AF%B8)
  - [ ] [支持的浏览器](./dnd.zh.md#%E6%94%AF%E6%8C%81%E7%9A%84%E6%B5%8F%E8%A7%88%E5%99%A8)
  - [ ] [翻译](./dnd.zh.md#%E7%BF%BB%E8%AF%91)
  - [ ] [作者](./dnd.zh.md#%E4%BD%9C%E8%80%85)
  - [ ] [维护者](./dnd.zh.md#%E7%BB%B4%E6%8A%A4%E8%80%85)
  - [ ] [合作者](./dnd.zh.md#%E5%90%88%E4%BD%9C%E8%80%85)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


## 翻译

- 使用[translate-mds](https://github.com/chinanf-boy/translate-mds) 完成初稿