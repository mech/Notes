# Flexbox

Global = 92%, Unprefixed = 72%

* [A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
* [**CSS Flexbox**](http://cssflexbox.com/)
* [**Flexbugs** - Curated list of flexbox issues and workarounds](https://github.com/philipwalton/flexbugs)
* [**Enhancing responsiveness with flexbox**](https://vimeo.com/124796320)
* [Flexbox in 5](http://flexboxin5.com/)
* [Solved by flexbox](http://philipwalton.github.io/solved-by-flexbox/)
* [Visual guide to flexbox properties](https://scotch.io/tutorials/a-visual-guide-to-css3-flexbox-properties)

The prime characteristic of the **flex container** is the ability to modify the width or height of its children to fill the available space in the best possible way on different screen sizes.

Flexbox layout algorithm is direction-based unlike the block or inline layout which are vertically and horizontally based.

* Flex container - Parent
* Flex items - Children

## Examples

* [Modal](https://twitter.com/jina/status/591351510803488768)
* [Fixed position header with flexbox](https://teamtreehouse.com/forum/fixed-position-header-with-flexbox)


**Sticky footer example**

```scss
.flex-container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;}

main {
  flex: 1;}
```

```html
<div class="flex-container">
  <header></header>
  <main></main>
  <footer></footer>
</div>
```

**Fallback for nav**

```scss
.list-nav {
  display: flex;
  justify-content: space-between;
  margin: 0;
  padding: 0;
  list-style: none;
  text-align: center; /* fallback */}

.list-nav li {
  display: inline-block; /* fallback */
  padding: 0 .5em; /* fallback */
  text-align: center;}

.list-nav li:first-child { padding-left: 0; }
.list-nav li:last-child { padding-right: 0; }
```

## IE specific

* [Sticker footer in IE](https://github.com/philipwalton/solved-by-flexbox/pull/36/files)

In IE 10-11, flex items ignore their parent container's height if it's set via the `min-height` property.

## display: table

```
table-layout: fixed;
```

* [Sticky footer](http://galengidman.com/2014/03/25/responsive-flexible-height-sticky-footers-in-css/)
* [Flexbox sticky footer and overflowing content area](http://stackoverflow.com/questions/20493621/the-flexbox-sticky-footer-and-the-overflowing-content-area)