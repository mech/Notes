# Float

Note: Block level elements ignore the `vertical-align` property. Inline elements do respect it thought. And inline elements can add `padding`, but not `top/bottom`.

Understanding positioning in the web is crucial for RWD, because position depends on everything around it; scrolling, screen size and other factors.

Elements of Layouts:

* Positioning (Static, Absolute, Fixed, Relative)
* Floats
* Display table
* Inline block
* Margins and paddings
* Flexbox
* Multiple columns
* Grids

Laying things with floats, every item is going to appear a different height, so you have to impose a `min-height` or fixed `height` to every item to achieve equal height columns.

Having a button anchor to the bottom you'd have to make it position absolute.

---

* [Positioning in Web Design](http://blog.froont.com/positioning-in-web-design/)
* [4 methods for equal height columns](http://www.vanseodesign.com/css/equal-height-columns/)
* [CSS `display` property](https://css-tricks.com/almanac/properties/d/display/)

Margins around floated elements do not collapsed.

Floated elements are `display: block` automatically, even if it is an inline element.

## Overflow

`overflow: hidden` or `overflow: auto` can be used to clear floats. Always document it with comment in your style if you are clearing floats with `overflow`.

```css
/* Block Formatting Context */
.Bfc {
  overflow: hidden;
  zoom: 1;}
```

However you can get unexpected behaviour such as content being cut off (if you use `hidden`) or scrollbars appearing (if you use `auto`). A better way is to use the clearfix hack.

```css
<div class="wrapper clearfix">
  <FloatLayout />
</div>
```

## `inline-block`

* [An `inline-block` intervention. Do not use it for layout as removing whitespace is too much work.](https://medium.com/@drewisthe/an-inline-block-intervention-6ce18a3f7edf)

2008 as part of CSS 2.1

Float does not give you equal height. You can use `display: inline-block` to achieve the Pinterest effect, but beware of whitespace as any spaces between elements will appear in your layout.

Just use `inline-block` for inline link look more like a button.

Since it is inline, `inline-block` does respect the `vertical-align` property.

## Grid

* [Build web layouts easily with Susy](https://css-tricks.com/build-web-layouts-easily-susy/)
* [A simple mixin alternative to standard CSS grids](http://webdesign.tutsplus.com/tutorials/a-simple-mixin-alternative-to-standard-css-grids--webdesign-16958)