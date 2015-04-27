# Float

Understanding positioning in the web is crucial for RWD, because position depends on everything around it; scrolling, screen size and other factors.

Elements of Layouts:

* Positioning (Static, Absolute, Fixed, Relative)
* Floats
* Inline block
* Margins and paddings
* Flexbox
* Multiple columns
* Grids

---

* [Positioning in Web Design](http://blog.froont.com/positioning-in-web-design/)

## Overflow

`overflow: hidden` can be used to clear floats. Always document it with comment in your style if you are clearing floats with `overflow`.

```
/* Block Formatting Context */
.Bfc {
  overflow: hidden;
  zoom: 1;}
```