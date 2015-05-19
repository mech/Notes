# Float

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
* [An `inline-block` intervention](https://medium.com/@drewisthe/an-inline-block-intervention-6ce18a3f7edf)

## Overflow

`overflow: hidden` can be used to clear floats. Always document it with comment in your style if you are clearing floats with `overflow`.

```scss
/* Block Formatting Context */
.Bfc {
  overflow: hidden;
  zoom: 1;}
```

## Grid

* [Build web layouts easily with Susy](https://css-tricks.com/build-web-layouts-easily-susy/)
* [A simple mixin alternative to standard CSS grids](http://webdesign.tutsplus.com/tutorials/a-simple-mixin-alternative-to-standard-css-grids--webdesign-16958)