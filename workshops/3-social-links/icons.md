# Icons & SVG Guide

SVGs (Scalable Vector Graphics) are XML-based vector images that scale seamlessly to any display resolution without losing quality. Because they are part of the DOM, you can style and animate them directly with CSS.

If most icons come from 1–2 packs, it will result in a more consistent theme and professional feel!

## What is an SVG?

An `<svg>` uses elements like `<path>`, `<circle>`, and `<rect>` to define shapes and lines using math.

Here is a simple hamburger menu (three horizontal lines).

```xml
<svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
  <g stroke="#000" stroke-width="1.5" stroke-linecap="round">
    <path d="M20 7L4 7" />
    <path d="M20 12L4 12" />
    <path d="M20 17L4 17" />
  </g>
</svg>
```

## Modifying Fill and Stroke Colors

In CSS, SVG colors are controlled using two primary properties:

- `fill`: Sets the interior color of filled shapes within the SVG.
- `stroke`: Sets the outline or line color of paths and shapes within the SVG.

### Using currentColor (Recommended)

Setting `fill="currentColor"` or `stroke="currentColor"` inside your SVG allows it to inherit the text `color` from its parent element (like an `<a>` or `<button>`).

```css
.icon-link {
  color: #666;
}

/* The SVG inside will adopt the gray color automatically */
.icon-link svg {
  width: 24px;
  height: 24px;
}
```

Some icon packs add these properties to the SVGs for you.

### Direct Styling of `fill` and `stroke`

You can also target the SVG or its path elements directly:

```css
svg {
  fill: #f40;
  stroke: #222;
}
```

## Interactive Colors: `:hover`, `:focus-visible`, and `:active`

When adding interactivity-based styles, group `:hover`, `:focus-visible`, and `:active` to cover mouse, keyboard, and mobile interactions.

```css
.icon-link:hover,
.icon-link:focus-visible,
.icon-link:active {
  color: #ffb23e;
}
```

Other focus options like `:focus` or `:focus-within` are also available if your layout requires custom focus behavior for container elements.

## Additional Resources

**SVG & Color Docs**

- [SVG](https://developer.mozilla.org/en-US/docs/Web/SVG)
- [fill](https://developer.mozilla.org/en-US/docs/Web/CSS/fill)
- [stroke](https://developer.mozilla.org/en-US/docs/Web/CSS/stroke)
- [currentColor](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Values/color_value#currentcolor_keyword)

**CSS Pseudo-classes Docs**

- [:hover](https://developer.mozilla.org/en-US/docs/Web/CSS/:hover)
- [:focus-visible](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Selectors/:focus-visible)
- [:active](https://developer.mozilla.org/en-US/docs/Web/CSS/:active)
- [:focus](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus)
- [:focus-within](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus-within)
