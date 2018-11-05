# 拖拽`<svg>`

> 摘要:`react-beautiful-dnd`不支持，让`<svg>`(`SVGElement`) 成为一个`Draggable`或者*拖动控制*它，但您仍然可以使用下面列出的许多不同策略，来拖动 SVG

## 背景:[`HTMLElement`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement)

我们要求一个`Draggable`和它的拖动控制是一个`HTMLElement`。您在浏览器中创建的几乎所有元素都是`HTMLElement`.[查看 MDN 上的巨大列表](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)。一个`HTMLElement`是扩展了[`Element`](https://developer.mozilla.org/en-US/docs/Web/API/Element)

![HTMLElement](https://user-images.githubusercontent.com/2182637/42302315-9150d4e0-805d-11e8-8345-71bc32135203.png)

## 使用焦点-focus

如果有需要,我们会在拖动过程中,使用并操纵焦点。对于依赖于焦点管理的键盘拖动尤其如此.

一个元素在移动到一个[`React Portal`](https://reactjs.org/docs/portals.html)时，会失去焦点.我们可以检测到什么时候`Draggable`进入到 Portal，我们在 portal 焦点中提供`.focus()`给新元素。此外,我们还会在您`Draggable`从一个列表搬到另一个列表时，使用`.focus()`保持专注，如果它在拖动时有焦点。键盘拖动时,元素始终具有焦点.

## 进入[`SVGElement`](https://developer.mozilla.org/en-US/docs/Web/API/SVGElement)🖼

一个`SVGElement`并没有实现`HTMLElement`,和它是`Element`的直接延伸.

![SVGElement](https://user-images.githubusercontent.com/2182637/42304424-8360143e-8069-11e8-9693-64f5e9763315.png)

`SVGElement`具有**不符合**, 且有时,**不存在**跨浏览器焦点管理行为。[更多信息](https://allyjs.io/tutorials/focusing-in-svg.html)。若试着运行`svgElement.focus()`在 IE11 上，将导致异常。还有其他问题:

- 应用`aria-*`到了`<svg>`，会有未知的屏幕阅读器含义.
- 旧浏览器中的不合适`tabindex`行为

`react-beautiful-dnd`其中一个核心价值观是无障碍

> 美丽,**无障碍**使用 React.js 拖放列表

## 但我想用一个拖动`<svg>`!

### 选项 1:包装`HTMLElement`

为了向消费者提供最佳的无障碍和跨浏览器体验,我们强制让`SVGElement`包裹在一个`HTMLElement`，如`<span>`要么`<div>`将把它们作为你的`Draggable`要么*拖动控制*.

```js
// ❌ 不 支持
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
// ✅ 支持
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

### 选项 2:使用`<img>`标签

你可以使用一个`<img>`标签的`src`(这是一个`HTMLElement`)，去拥有一个可拖动的 SVG.

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

> 您可以阅读有关此方法的更多信息，都在[CSS-技巧](https://css-tricks.com/using-svg/)

### 选项 3:使用`background-image`

或者,您也可以将 SVG 应用为`background-image`，变成另一个`HTMLElement`的一部分.

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

> 您可以阅读有关此方法的更多信息，都在[CSS-技巧](https://css-tricks.com/using-svg/)
