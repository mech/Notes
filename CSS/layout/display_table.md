# Display Table

Supported in IE8.

* [`table-layout`](https://developer.mozilla.org/en-US/docs/Web/CSS/table-layout)
* [Sticky footer](http://galengidman.com/2014/03/25/responsive-flexible-height-sticky-footers-in-css/)
* [Flexbox sticky footer and overflowing content area](http://stackoverflow.com/questions/20493621/the-flexbox-sticky-footer-and-the-overflowing-content-area)
* [**The Anti-hero of CSS Layout**](http://colintoh.com/blog/display-table-anti-hero)

Elements that are part of a table have relationship to each other, so you can have full height layout with 2 `<div>` side by side.

Don't use table layout for macro layouts, use it for small UI widget (micro layouts) like forms or property lists that need to have right-aligned labels.

```css
.layout-table {
  display: table;
  width: 100%;}

.layout-table > * {
  display: table-cell;
  vertical-align: bottom;}
```