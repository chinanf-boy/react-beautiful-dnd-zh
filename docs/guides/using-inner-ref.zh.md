# 运用`innerRef`

> 如果你还没有用过`ref`以前,请看看[`React`:参考和 DOM 指南](https://reactjs.org/docs/refs-and-the-dom.html)在他们的文档网站上.

我们的`Draggable`和`Droppable`组件都需要一个[`HTMLElement`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement)提供给他们.这是使用`innerRef`物业`DraggableProvided`和`DroppableProvided`对象.

```diff
<Draggable draggableId="draggable-1" index={0}>
  {(provided, snapshot) => (
    <div
+      ref={provided.innerRef}
      {...provided.draggableProps}
      {...provided.dragHandleProps}
    >
      <h4>My draggable</h4>
    </div>
  )}
</Draggable>;
```

```diff
<Droppable droppableId="droppable-1">
  {(provided, snapshot) => (
    <div
+     ref={provided.innerRef}
      {...provided.droppableProps}
    >
      <h2>I am a droppable!</h2>
      {provided.placeholder}
    </div>
  )}
</Droppable>;
```

## 不是全部`ref`s 创造平等

混乱可能因为如何产生而产生`ref`回调适用于`React`.

在一个*零件*如`<Person />`该`ref`回调将返回*例*的`Person`零件.

在一个*ReactElement*如`<div />`该`ref`回调将返回*HTML 元素*那个*ReactElement*与...有关.

[见`codesandbox.io`](https://codesandbox.io/s/xok96ovo8p)

```js
class Person extends React.Component {
  state = {
    sayHello: false
  };
  sayHello() {
    this.setState({
      sayHello: true
    });
  }
  render() {
    if (this.state.sayHello) {
      return <div {...this.props}>Hello</div>;
    }

    return <div {...this.props}>'I am a person, I think..'</div>;
  }
}

class App extends React.Component {
  setPersonRef = ref => {
    this.personRef = ref;

    // When the ref changes it will firstly be set to null
    if (this.personRef) {
      // personRef is an instance of the Person class
      this.personRef.sayHello();
    }
  };
  setDivRef = ref => {
    this.divRef = ref;

    if (this.divRef) {
      // div ref is a HTMLElement
      this.divRef.style.backgroundColor = 'lightgreen';
    }
  };
  render() {
    return (
      <React.Fragment>
        <Person ref={this.setPersonRef} />
        <div ref={this.setDivRef}>hi there</div>
      </React.Fragment>
    );
  }
}
```

## 一个常见的错误 🐞

看看这个例子:

```js
<Draggable draggableId="draggable-1" index={0}>
  {(provided, snapshot) => (
    <Person
      ref={provided.innerRef}
      {...provided.draggableProps}
      {...provided.dragHandleProps}
    />
  )}
</Draggable>
```

虽然它看起来是正确的,但它**会导致你的应用程序爆炸 💥!**

这是因为`react-beautiful-dnd`期待`provided.innerRef`的功能`Draggable`和 a`Droppable`要使用组件的 DOM 节点调用,而不是*例*班上的.在这个例子中我们正在打电话`provided.innerRef`与*例*的`Person`而不是底层的 DOM 节点.

## 从组件中公开 DOM ref

一种简单的公开方式*HTML 元素*你的组件是**创造你自己的`innerRef`支柱**:

```js
class Person extends React.Component {
  render() {
    return (
      <div {...this.props} ref={this.props.innerRef}>
        I am a person, I think..
      </div>
    );
  }
}
```

> 注意,名称`innerRef`只是一个惯例.您可以为组件调用它.就像是`domRef`很好.

然后,您可以正确地将 DOM 节点提供给 a`Draggable`要么`Droppable`

```diff
<Draggable draggableId="draggable-1" index={0}>
  {(provided, snapshot) => (
    <Person
-      ref={provided.innerRef}
+      innerRef={provided.innerRef}
      {...provided.draggableProps}
      {...provided.dragHandleProps}
    >
      <h4>My draggable</h4>
    </div>
  )}
</Draggable>
```

⚠️ 这种方法会导致 a`React`警告,因为我们正在将组件的所有道具传播到 DOM 节点上.`{...this.props}`这包括`innerRef`道具哪个`React`不喜欢你添加到元素.所以你可以像这样设置:

```diff
class Person extends React.Component {
  render() {
-    return (
-      <div {...this.props} ref={this.props.innerRef}>
-        I am a person, I think..
-      </div>
-    );
  }
}
class Person extends React.Component {
  render() {
+    const { provided, innerRef } = this.props;
+    return (
+      <div
+        {...provided.draggableProps}
+        {...provided.dragHandleProps}
+        ref={innerRef}
+      >
+        I am a person, I think..
+      </div>
+    );
  }
}

<Draggable draggableId="draggable-1" index={0}>
  {(provided, snapshot) => (
    <Person
      innerRef={provided.innerRef}
-      {...provided.draggableProps}
-      {...provided.dragHandleProps}
+      provided={provided}
    />
  )}
</Draggable>
```

如果你还需要使用*HTML 元素*在你的*零件*你可以有一个更强大的 ref 设置方法:

```js
class Person extends React.Component {
  setRef = ref => {
    // keep a reference to the dom ref as an instance property
    this.ref = ref;
    // give the dom ref to react-beautiful-dnd
    this.props.innerRef(ref);
  };
  render() {
    const {provided, innerRef} = this.props;
    return (
      <div
        {...provided.draggableProps}
        {...provided.dragHandleProps}
        ref={this.setRef}
      >
        I am a person, I think..
      </div>
    );
  }
}
```

## 把它们放在一起

以下示例展示了本指南中提供的知识:<https://codesandbox.io/s/v3p0q71qn5>

## 关于 SVG 的说明

`react-beautiful-dnd`不支持拖动`<svg>`元素.包裹你的`<svg>`在一个`HTMLElement`如`<span>`要么`<div>`提供良好的无障碍和跨浏览器支持.见我们的[使用 SVGs 指南](https://github.com/atlassian/react-beautiful-dnd/tree/master/docs/guides/using-svgs.md)欲获得更多信息.
