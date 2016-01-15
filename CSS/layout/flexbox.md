# Flexbox

> Flexbox let the DOM know that elements on the page have a relationship (or relationships).

Basically 4 rules:

1. Direction - row or column
2. Alignment
3. Order
4. Flexibility

Global = 92%, Unprefixed = 72%

IE9, Opera 12 don't support flexbox.

* [**Modern Design Tools: Adaptive Layouts**](https://medium.com/@joshpuckett/modern-design-tools-adaptive-layouts-e236070856e3)
* [A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
* [**CSS Flexbox**](http://cssflexbox.com/)
* [**Flexbugs** - Curated list of flexbox issues and workarounds](https://github.com/philipwalton/flexbugs)
* [**Enhancing responsiveness with flexbox**](https://vimeo.com/124796320)
* [**Using flexbox today**](http://chriswrightdesign.com/experiments/using-flexbox-today/)
* [Flexbox in 5](http://flexboxin5.com/)
* [Solved by flexbox](http://philipwalton.github.io/solved-by-flexbox/)
* [Visual guide to flexbox properties](https://scotch.io/tutorials/a-visual-guide-to-css3-flexbox-properties)
* [Equal height grid using flexbox](http://clearleft.com/thinks/anequalheightgridusingflexbox/)
* [Advanced cross-browser flexbox](https://dev.opera.com/articles/advanced-cross-browser-flexbox/)
* [Modernizr IE10 flexbox test](https://github.com/Modernizr/Modernizr/issues/812)
* [Use as a last resort?](http://cloudfour.github.io/leveller/)
* [Another use as last resort](https://github.com/skrajewski/Equalizer)
* [Harnessing flexbox for today's web app](http://www.smashingmagazine.com/2015/03/02/harnessing-flexbox-for-todays-web-apps/)
* [Flexbox reference](http://tympanus.net/codrops/css_reference/flexbox/)
* [Create the perfect website layout system](http://www.creativebloq.com/web-design/create-perfect-website-layout-system-121518553)

Playground

* [flexplorer](http://bennettfeely.com/flexplorer/)
* [flexbox-tester](http://madebymike.com.au/demos/flexbox-tester/)

Flexbox is all about alignment and ordering. It is a smart layout mode that calculates and distributes space.

The prime characteristic of the **flex container** is the ability to modify the width or height of its children to fill the available space in the best possible way on different screen sizes.

Flexbox layout algorithm is direction-based unlike the block or inline layout which are vertically and horizontally based.

* Flex container - Parent
* Flex items - Children
* Main axis is horizontal and controlled by `justify-content`.
* Cross axis is vertical and controlled by `align-items`
* Main dimension
* Main size

**Note**: Only direct children of a flex container become flex items, not its descendants.

Flexbox will override floats, table-cell and inline-block. It will not override absolute positioning.

## MISTAKES

* In EVA, `main-container` has `flex-direction: row` which is very limiting. What happen if for the next screen you need to style it in column?

## calc() and flexbox

`calc()` and flexbox make for an awesome combo!


```scss
.letter {
  $spacing: .5%;
  flex: 0 1 calc(100% * 1/7 - #{$spacing}*2);}
```

## Grow, Shrink and Basis

* [Understanding how grow and shrink are calculated](http://madebymike.com.au/writing/understanding-flexbox/)

`flex-basis` determines how the other 2 properties behave. It is the "basis" on which the flex item know how much it can grow or shrink to fill missing space. It is the initial size of each flex item, and can be restricted to be the only amount by specifying `0` on grow and shrink.

```scss
flex: 0 0 150px; // Not allowed to grow, stay at 150px (flex-basis)
```

* Flex grow determines how much the flex item will grown relative to the rest of the items when **positive free space** is distributed.
* Flex shrink determines how much the flex item will shrink relative to the rest of the item when **negative free space** is distributed. Flex shrink is applied when there is an overflow in the calculation. It will then squash the item where it needs to.

If the sum of the main sizes of all flex items is greater than the main size of the flex container, you can specify just by how much you want to shrink the flex items. Shrinking only take effect when you have negative free space.

```scss
// `flex` property
flex: flex-grow flex-shrink flex-basis
flex: 0 1 auto;
flex: 1 0 auto;
flex: none; // Same as `0 0 auto`
flex: 1; // Never do this, IE10/11 bugs
```

> I use grow if I want something to fill the space of a missing item, I use shrink if I want items to collapse to make way for new items.

**Important**: When an element is a flex item, `flex` is used instead of the `width` and `height` properties to determine the main size of the element. (citation needed)

## Grid

* [Flexbox Grid](http://flexboxgrid.com/)

## Axis Direction

If you switch axis `flex-direction` from `row` to `column`, you need to be aware of the alignment changes also. Specifically the `justify-content` and `align-items` properties.

* `justify-content` aligns flex items along the **main axis** of the current flex line of the flex container.
* `align-items` aligns flex items in the **cross-axis**.

## Ordering

Use cases:

* News site where you want featured news to maybe not be the most up-to-date news piece.

## Examples

* [Modal](https://twitter.com/jina/status/591351510803488768)
* [Fixed position header with flexbox](https://teamtreehouse.com/forum/fixed-position-header-with-flexbox)
* [Flexbox stretch](http://zomigi.com/demo/flexbox_stretch.html)


**Sticky footer example**

```scss
.flex-container {
  display: flex; // Establish a flex context
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

**With media queries**

```scss
@media screen and (min-width: 40em) {
  .list-item {
    width: 50%; // 2 items per row  }}

@media screen and (min-width: 60em) {
  .list-item {
    width: 33.33%; // 3 items per row  }}
```

## IE specific

* [Sticker footer in IE](https://github.com/philipwalton/solved-by-flexbox/pull/36/files)

In IE 10-11, flex items ignore their parent container's height if it's set via the `min-height` property.

## People

* [Zoe Mickley Gillenwater](http://zomigi.com/blog/)