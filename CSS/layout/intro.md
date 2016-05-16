# Introduction to Layout in CSS

## Box Model

HTML elements generate rectangular box called the *element box*.

* CSS 2.1 - Standard Box Model (where total size is element's width + paddings + borders)
* CSS Basic Interface Module Level 3 - Alternate Box Model. Critical for RWD.

User `box-sizing: border-box` to ensure 100% width content won't stick out and ruin the layout.

IE8 supported!

Percentages in `padding` take their measurement from the parent containing element's `width` or the root `<html>`.

Unlike `padding` and `border`, `margin` can have negative values.

```
Value replication
Replaced element (image, form element)
inline non-replaced element
Length value
```

For inline non-replaced element like normal text, `padding-left/right` and `margin-left/right` can have effect whilst `top/bottom` have no effect whatsoever.

## Margin Collapsing

Two or more margins that interact collapse to the largest of the interacting margins.

## CSS Positioning

CSS positioning is not about laying out element, it is more about how elements behave in document flow.

CSS positioning allows you to define where element boxes will appear relative to where they would ordinarily be - or position them in relation to a parent element, another element, or even to the viewport itself.

```
position: static|relative|absolute|fixed|sticky
offset properties: top|right|bottom|left
```

[fixed-sticky - Polyfill for `position: sticky`](https://github.com/filamentgroup/fixed-sticky)

Positive values cause inward offsets, moving the edges toward the center of the containing block, and negative values cause outward offsets.

### Containing Block

Containing block's content-edge = relative/static

Containing block's padding-edge = absolute positioning

Positioned elements can be positioned outside of their containing block. This is very similar to the way in which floated elements can use negative margins to float outside of their parent's content area. It also suggests that the term "containing block" should really be "positioning context".

### Absolute Positioning

Useful when creating smaller parts of your UI.

Taken out of document flow. Need positioning context to work. Will scroll together with positioning context.

## Stacking Order and Context

* [What no one told you about `z-index`](http://philipwalton.com/articles/what-no-one-told-you-about-z-index/)

Only positioned element can have z-index, unpositioned element will have no effect no matter how great the index is.