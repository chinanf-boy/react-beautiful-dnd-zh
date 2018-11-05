# 运用`innerRef`

> 如果以前你还没有用过`ref`,请看看官方文档[`React`: Refs 和 DOM 指南](https://reactjs.org/docs/refs-and-the-dom.html)

我们的`Draggable`和`Droppable`组件，都要求拥有一个[`HTMLElement`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement)。通过使用`DraggableProvided`的`innerRef`属性和`DroppableProvided`对象.

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

## 不是全部的`ref`，都生而一样

混乱可能来自，`React`中`ref`回调工作的方式.

在一个*Component*，如`<Person />`的`ref`回调，将返回`Person`Component的*实例-instance*.

在一个*ReactElement*，如`<div />`的`ref`回调，将返回与*ReactElement*有关的*HTML 元素*.

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

    // 当 ref一改变， 它被设为 null
    if (this.personRef) {
      // personRef 是 Person 类的一个实例
      this.personRef.sayHello();
    }
  };
  setDivRef = ref => {
    this.divRef = ref;

    if (this.divRef) {
      // div ref 是 HTMLElement
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

这是因为`react-beautiful-dnd`期待提供给`Draggable`的`provided.innerRef`函数，和`Droppable`的调用要使用组件的 DOM 节点,而不是类的*实例*。在这个例子中我们正在调用`provided.innerRef`与`Person`*实例*，而不是底层的 DOM 节点.

## 从组件中公开 DOM ref

一种简单的公开你组件的*HTML 元素*，就是**创造你自己的`innerRef` porps**:

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

> 注意,名称`innerRef`只是一个惯例。您可以为组件调用它。就像是`domRef`一样样的.

然后,您可以正确地将 DOM 节点提供给 一个`Draggable`要么`Droppable`

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

⚠️ 这种方法会导致 一个`React`警告,因为我们正在将组件的`{...this.props}`所有**props-道具**传播到 DOM 节点上。这包括`innerRef`，而`React`不喜欢你添加到元素。所以你可以像这样设置:

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

如果你还需要在你的*Component*使用*HTML 元素*，那你需要有一个更强大的 ref 设置方法:

```js
class Person extends React.Component {
  setRef = ref => {
    // 保持 reference 到 dom ref 作为 实例的属性
    this.ref = ref;
    // 将 dom ref 给予 react-beautiful-dnd
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

以下示例展示了，本指南中提供的知识:<https://codesandbox.io/s/v3p0q71qn5>

## 关于 SVG 的说明

`react-beautiful-dnd`不支持拖动`<svg>`元素.包裹你的`<svg>`到一个`HTMLElement`，如`<span>`要么`<div>`，此方式提供良好的无障碍和跨浏览器支持。见我们的[使用 SVGs 指南](https://github.com/atlassian/react-beautiful-dnd/tree/master/docs/guides/dragging-svgs.zh.md)获得更多信息.
