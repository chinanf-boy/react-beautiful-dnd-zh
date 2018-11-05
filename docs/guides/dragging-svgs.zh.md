# 拖延`<svg>`小号

> 摘要:`react-beautiful-dnd`不支持使用`<svg>`(`SVGElement`) 为一个`Draggable`或者它*拖动手柄*.您仍然可以使用下面列出的许多不同策略拖动SVG

## 背景:[`HTMLElement`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement)

我们需要一个`Draggable`它的拖动手柄是一个`HTMLElement`.您在浏览器中创建的几乎所有元素都是`HTMLElement`.[查看MDN上的巨大列表](https://developer.mozilla.org/en-US/docs/Web/HTML/Element).一个`HTMLElement`扩展[`Element`](https://developer.mozilla.org/en-US/docs/Web/API/Element)

![HTMLElement](https://user-images.githubusercontent.com/2182637/42302315-9150d4e0-805d-11e8-8345-71bc32135203.png)

## 使用焦点

如果需要,我们在拖动过程中使用并操纵焦点.对于依赖于焦点管理的键盘拖动尤其如此.

一个元素在移动到一个元素时会失去焦点[`React Portal`](https://reactjs.org/docs/portals.html).我们可以检测到什么时候`Draggable`正在进入门户网站,我们在门户网站焦点中提供新元素`.focus()`.此外,我们还会在您搬家时保持专注`Draggable`从一个列表到另一个列表使用`.focus()`如果它在拖动时有焦点.键盘拖动时,元素始终具有焦点.

## 输入[`SVGElement`](https://developer.mozilla.org/en-US/docs/Web/API/SVGElement)🖼

一个`SVGElement`没有实现`HTMLElement`,并直接延伸`Element`.

![SVGElement](https://user-images.githubusercontent.com/2182637/42304424-8360143e-8069-11e8-9693-64f5e9763315.png)

`SVGElement`具有**不符**, 而有时,**不存在的**跨浏览器集中管理行为.[更多信息](https://allyjs.io/tutorials/focusing-in-svg.html).试着打电话`svgElement.focus()`在IE11上将导致异常.还有其他问题:

-   应用`aria-*`到了`<svg>`有未知的屏幕阅读器含义.
-   不符`tabindex`旧浏览器中的行为

其中一个核心价值观`react-beautiful-dnd`是可访问性

> 美丽,**无障碍**使用React.js拖放列表

## 但我想用一个拖动`<svg>`!

### 选项1:包装`HTMLElement`

为了向消费者提供最佳的可访问性和跨浏览器体验,我们强制执行`SVGElement`需要包裹在一个`HTMLElement`如`<span>`要么`<div>`如果你想把它们作为你的`Draggable`要么*拖动手柄*.

```js
// ❌ not supported
<Draggable draggableId="not-supported" index={0}>
  {provided => (
    <svg
      {...provided.draggableProps}
      {...provided.dragHandleProps}
      ref={provided.innerRef}
      {/* other SVG stuff */}
    />
  )}
</Draggable>
```

```js
// ✅ supported
<Draggable draggableId="supported" index={0}>
{provided => (
  <span
    {...provided.draggableProps}
    {...provided.dragHandleProps}
    ref={provided.innerRef}
    >
      <svg {/* other SVG stuff */} />
  </span>
)}
</Draggable>
```

### 选项2:使用`<img>`标签

你可以使用`src`一个`<img>`标签(这是一个`HTMLElement`)有一个可拖动的SVG.

```js
// ✅ supported
<Draggable draggableId="supported" index={0}>
  {provided => (
    <img
      {...provided.draggableProps}
      {...provided.dragHandleProps}
      ref={provided.innerRef}
      src="my-cool-image.svg"
    />
  )}
</Draggable>
```

> 您可以阅读有关此方法的更多信息[CSS-技巧](https://css-tricks.com/using-svg/)

### 选项3:使用`background-image`

或者,您也可以将SVG应用为`background-image`到另一个`HTMLElement`.

```css
.item {
  background-image: url(my-cool-image.svg);
}
```

```js
// ✅ supported
<Draggable draggableId="supported" index={0}>
  {provided => (
    <div
      {...provided.draggableProps}
      {...provided.dragHandleProps}
      ref={provided.innerRef}
      className="item"
    />
  )}
</Draggable>
```

> 您可以阅读有关此方法的更多信息[CSS-技巧](https://css-tricks.com/using-svg/)
