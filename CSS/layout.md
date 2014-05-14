# Layout

Steps to do layout:

1. Do semantic HTML outline first.
2. Mindful of margin, padding and their collapsing behavior.
3. em and percentage and their containing parent.
4. Any extra wrapper/grouping to use or not.
5. Always use normal document flow to layout and only use float when necessary.

Types of layout: Fixed, Fluid, Elastic, Hybrid, Responsive.

* [Learn CSS Layout](http://learnlayout.com/)

Purpose of layouts:

1. **Sequential Order**. What user want to do first, and next. Business goals.
2. **Visual Hierarchy**. Guide the eye. Size, color, spacing, etc.
3. **Associative Connection**. What goes with what?

## GSS (Re-thinking CSS Layout - Math heavy)

* [Grid Style Sheet](http://gridstylesheets.org/)
* [Cassowary, Cocoa Autolayout, and enaml constraints](http://stacks.11craft.com/cassowary-cocoa-autolayout-and-enaml-constraints.html)

Using Solver to compute layout.

Cassowary Linear Arithmetic Constraint Solver - Resolves cyclic dependencies in layout arithmetic.

Greg Badros - Constraint CSS

Constraint programming. I strong want this.
Constraints are 2-way. Takes practice thinking in constraints.

VFL - Visual Format Language

https://github.com/slightlyoff/cassowary.js


## Media Queries

```
// Mobile first
article, aside { width: 100%; }
@media screen and (min-wdith: 480px) {
  article { float: left; width: 68%; }
  aside { float: right; width: 30%; }
}
@media screen and (min-wdith: 800px) {
  article { padding: 20px; }
}
```

### Resolution media queries

```
1 device pixel == 1dppx
4 device pixel (iPhone4) == 2dppx
9 device pixel (HTC One) == 3dppx

@media (screen and min-resolution: 2dppx) {
  body {
    background-size: 50% !important;
  }
}
```

## Flexible Layout

Remember margins and padding calculate their value as a percentage of the PARENT element! Especially for nested container.

* Percent: relative to the containing block.
* Em: relative to the containing block's font size.

Use of `min-width` and `max-width` common.

* [FlexGRID](http://www.volumethemes.com/flexgrid)

## Grids

* [Responsive Dirty Little Secret](http://www.palantir.net/blog/responsive-design-s-dirty-little-secret)
* [Grid stylesheets](http://gridstylesheets.org/)
* [Susy](http://susy.oddbird.net/)
* [Breakpoint](http://breakpoint-sass.com/)
* [The Grid System](http://www.thegridsystem.org/)
* [Design by Grid](http://www.designbygrid.com/)
* [Inspiration for grids](http://grid-based.com/)
* [Building your own fluid grid](http://designshack.net/articles/css/rolling-your-own-grid-layouts-on-the-fly-without-a-framework/)
* [Grid calculator?](http://instacalc.com/?d=&c=NCAvL251bWJlciBvZiBjb2x1bW5zfDQgLy9tYXJnaW4gfChSMS0xKSpSMiAvL3RvdGFsIG1hcmdpbiB8KDEwMC1SMykvUjEgLy9jb2x1bW4gd2lkdGh8fChSNCoyKSsoUjIqMSkgLy8gY29tYmluZSB0d28gY29sdW1uc3woUjQqMykrKFIyKjIpIC8vY29tYmluZSB0aHJlZSBjb2x1bW5zfHx8fHx8fHw&s=sssssssssssssss&v=0.9)
* [Web Typography](http://webtypography.net/intro/)
* [Layers](http://eiskis.net/layers/)
* [Unit Grid System](http://unit.gs/)
* [Flow](http://flow.gs/)


## Flexbox

Supported in Chrome 21+, Safari 6.1+, Firefox 22+, Opera 12.1+, IE 11+, and Blackberry 10+.

* [Complete guide to flexbox](http://css-tricks.com/snippets/css/a-guide-to-flexbox/)
* [Flexgrid](http://ptb2.me/flexgrid/)
* [Dive into flexbox](http://weblog.bocoup.com/dive-into-flexbox/)
* [Design flexible layouts](http://www.wpmemorize.com/2013/css-flexbox-to-design-flexible-layouts/)
* [Flexbox example](http://devbryce.com/site/flexbox/)
* [Flexbox - Next-generation CSS Layout has arrived](http://blog.teamtreehouse.com/flexbox-next-generation-css-layout-arrived)

## Masonry

* [Salvattore - A jQuery Masonry alternative with CSS-driven configuration](http://salvattore.com/)

## Collapsing Margins

* [SitePoint's collapsing margins](http://reference.sitepoint.com/css/collapsingmargins)

These are some cases where margins do not collapsed:

* Floated elements
* Absolutely positioned elements
* `inline-block` elements
* Elements with `overflow` set to anything other than `visible`
* Cleared elements (they do not collapse their top margins with their parent block's bottom margin)
* The root element

Margins only collapse vertically. Horizontal margins will just combined.

A simple `border` or `padding` on the parent block is enough to prevent collapsing. You can use `1px` padding and `9px` margin for a effect of `10px` margin.

In IE7 and below, no margin will collapse if the element `hasLayout`.

But why collapsing margins? It does make life easier in the case of multiple nested elements, where the behavior is often desirable. Take for example this `<p>` style:

```
p { margin: 10px 0; }
```

The top and bottom margins will combine give `20px`, but because of collapsing, the paragraph will look ok with just `10px`.

## Float

* [PPK's clearing float using `overflow:auto`](http://www.quirksmode.org/css/clearing.html)
* [The very latest new new way to do clearfix](http://www.css-101.org/articles/clearfix/latest-new-clearfix-so-far.php)
* [Which method of clearfix is best? - SO](http://stackoverflow.com/questions/211383/which-method-of-clearfix-is-best)

If you don't support IE6/7, then don't bother clearing floats in these browsers. `zoom: 1` is only for IE6, so don't bother.

Floating elements mean they are remove from *normal document flow*, so their containing parent thinks they are not there and so collapses itself. The problem you get will be disappearing background and overlapping content.

```
<!--[if lt IE 8]>
<style>
  .clearfix { zoom: 1; }
</style>
<![endif]-->
```

Using SASS placeholder to `extend` clearfix.

```
%clearfix {
  &:after {
    content: "";
    display: table;
    clear: both;
  }
}
```

## Positioning

`static` and `relative` are considered to be in normal document flow.

`relative` - can be offset and following elements react as if the element were not offset. They think it is still there. So why would you want to use `relative`?:

1. For slight tweaking, to move something up a little bit here and there.
2. To provide positioning value for container elements, more for `absolute` positioning. Serve as the offset point.

`absolute` - Removed from normal flow. Absolute also allow clipping like `clip: rect(50px, 200px, 150px, 50px)`

## Overflow

`overflow` only ever work with a defined `width` and `height`.


## List

List are block by default. Use it as inline.

    li { display: inline; }

## inline-block

* [For IE6/IE7](http://blog.mozilla.org/webdev/2009/02/20/cross-browser-inline-block/)

This is what Compass will give you:

```
.incline-block {
  display: -moz-inline-stack;
  display: inline-block;
  vertical-align: middle;
  *vertical-align: auto;
  zoom: 1;
  *display: inline;
}
```


## Hacks

* [Equal height using JavaScript! Really?](http://benhowdle.im/2014/01/29/easy-peasy-equal-heights/)