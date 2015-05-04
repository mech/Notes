# Display Table

* [`table-layout`](https://developer.mozilla.org/en-US/docs/Web/CSS/table-layout)
* [Sticky footer](http://galengidman.com/2014/03/25/responsive-flexible-height-sticky-footers-in-css/)
* [Flexbox sticky footer and overflowing content area](http://stackoverflow.com/questions/20493621/the-flexbox-sticky-footer-and-the-overflowing-content-area)

```scss
.layout-table {
  display: table;
  width: 100%;}

.layout-table > * {
  display: table-cell;
  vertical-align: bottom;}
```