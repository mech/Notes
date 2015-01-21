# Layout

* [CSS vw and vh](http://www.weareconvoy.com/2014/07/24/css-vw-and-vh-units-are-they-worth-using-yet/)
* [Absolute 100% height with top:0 and bottom:0](http://stackoverflow.com/questions/5070189/css-100-height-with-absolute-positioning-top-0-bottom-0)
* [Make full screen sections with 1 line of CSS](https://medium.com/@ckor/make-full-screen-sections-with-1-line-of-css-b82227c75cbd)
* [Mega site navigation](http://codyhouse.co/gem/css-mega-site-navigation/)
* [Responsive dashboard layout template](http://keen.github.io/dashboards/)
* [calc() for grids](http://webdesign.tutsplus.com/tutorials/calc-grids-are-the-best-grids--cms-22902)
* [`object-fit`](http://demosthenes.info/blog/967/The-Widescreen-Web-Using-CSS-object-fit)
* [Fixed header/footer with dynamic heights and scrollable content](https://news.layervault.com/stories/40715-fixed-header-and-footer-with-dynamic-heights-and-scrollable-content)
* [3D curtain template](http://codyhouse.co/gem/3d-curtain-template/)
* [Float elements with a consistent gutter width and make them drop to next row automatically with cycle](http://corysimmons.github.io/elf/)
* [Golden ratio is actually real?](http://www.designyourway.net/blog/inspiration/using-golden-ratio-in-web-design-is-not-ludicrous-its-actually-ideal/)
* [Content filter UI example](http://codyhouse.co/gem/content-filter/)
* [Responsive grid using calc](http://mintran.com/responsive-grid-using-calc/)

## Example

* [**http://cakedown.alexandredeschamps.ca/**](http://cakedown.alexandredeschamps.ca/)
* [**Grid Lover**](http://www.gridlover.net/app/)
* [CSS layout debugger](https://gist.github.com/addyosmani/fd3999ea7fce242756b1)
* [Why we ditched the good old select element](https://medium.com/@mibosc/responsive-design-why-and-how-we-ditched-the-good-old-select-element-bc190d62eff5)
* [**Check out Foundation for Apps**](http://responsivedesign.is/articles/screencast-zurb-foundation-for-apps)
* [Google News platform design concept](http://googlenews.gkvasnikov.com/)

Key things to Web UI:

* Layout
* Color
* Typography
* Motion/Animation/Transition
* Content/Copywriting
* Hierarchy/Alignment/Proportion

---

* [Example to see for layout](http://cssdeck.com/labs/css-switchboard)

Rather than designing pages, which will inevitably break as our canvas shrinks and grows, we should design modules that can be reconfigured and remixed into various layouts. Create a system rather than treating the layout as a discrete unit. See [Atomic Web Design](http://bradfrostweb.com/blog/post/atomic-web-design/)

Steps to do layout:

1. Do semantic HTML outline first.
2. Mindful of margin, padding and their collapsing behavior.
3. em and percentage and their containing parent.
4. Any extra wrapper/grouping to use or not.
5. Always use normal document flow to layout and only use float when necessary.
6. Always have grid system. Think of it as your shelves. You put up your shelves then fill them with your stuff. By setting up our grids separately to our components you can move components around a lot more easily then if they had dimensions applied to them.
7. Find the content constraint and then use it to determine the grid.

Types of layout: Fixed, Fluid, Elastic, Hybrid, Responsive.

* [Learn CSS Layout](http://learnlayout.com/)
* [Harry's advice on layout](https://github.com/csswizardry/CSS-Guidelines#layout)

Purpose of layouts:

1. **Sequential Order**. What user want to do first, and next. Business goals.
2. **Visual Hierarchy**. Guide the eye. Size, color, spacing, etc.
3. **Associative Connection**. What goes with what?

These are the options for layout:

1. Flexbox
2. `display: table`
3. `inline-block` grid
4. `float` grid

---

* [Web Fundamentals - Multi-device layouts](https://developers.google.com/web/fundamentals/layouts/)
* [Rectangular Web](http://www.vanseodesign.com/web-design/rectangular-web/)
* [Responsive Design Passion](http://www.vanseodesign.com/web-design/responsive-design-passion/)

## Scroll

* [Rise of overflow scroll](http://www.northerndiv.com/hamburger-menu-rise-overflow-scroll/)
* [`UITableView` in JavaScript](http://www.thecssninja.com/javascript/scrolllistview)
* [Everybody scrolls](http://www.hugeinc.com/ideas/perspective/everybody-scrolls)

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

If you put `em` at `margin`, `padding`, `width`, or `height`, the value will be multiply by the `font-size` of the element itself, and not the parent!

Use of `min-width` and `max-width` common.

* [FlexGRID](http://www.volumethemes.com/flexgrid)

## Grids

Nearly every grid system is based on rows and columns, set to 12 or 16 increments to create any layout. However, the web is changing! It's time for Flexbox to shine.

* [**Foundation - A new grid**](http://zurb.com/article/1333/foundation-a-new-grid)
* [Skeleton](http://getskeleton.com/)
* [**Complete guide to grid**](http://css-tricks.com/snippets/css/complete-guide-grid/)
* [Some grids to try](https://news.layervault.com/stories/30928-ask-dn-which-grid-do-you-use)
* [Nicolas Gallagher's `inline-block` grid system](http://necolas.github.io/griddle/)
* [Don't overthink grids](http://css-tricks.com/dont-overthink-it-grids/)
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
* [Jeet](http://jeet.gs/)
* [Responcss](http://responcss.com/)
* [Discover the perfect grid](http://www.webdesignerdepot.com/2014/06/grid-systems-discover-the-perfect-building-blocks-for-your-website-design/)
* [Using inline-block for grid](http://codepen.io/davidicus/pen/vxIra?editors=110)
* [Concise Grid](http://concisecss.com/get-started/getting-started.php)
* [Scut Grid](http://css-tricks.com/introducing-scut-new-sass-utility-library/)
* [flexible.gs](http://flexible.gs/)
* [Griddle - Nicolas Gallagher's grid](http://necolas.github.io/griddle/)
* [Louder than Ten Layout](http://manual.louderthanten.com/layout)
* [ungrid](http://chrisnager.github.io/ungrid/)
* [New Foundation grid](http://zurb.com/article/1333/foundation-a-new-grid)
* [Flexbox Grid](http://flexboxgrid.com/)
* [The subtle magic behind why Bootstrap 3 grid works](http://www.helloerik.com/the-subtle-magic-behind-why-the-bootstrap-3-grid-works)
* [csswizardry-grids](http://csswizardry.com/csswizardry-grids/)
* [Singularity](https://github.com/Team-Sass/Singularity)
* [Simple Grid](http://thisisdallas.github.io/Simple-Grid/)
* [Jeet - A grid system for humans](http://jeet.gs/)
* [Guide Guide](http://guideguide.me/)
* [Re-thinking the Grid](http://snook.ca/archives/html_and_css/rethinking-the-grid)
* [Spacing elements](http://simurai.com/blog/2014/05/25/spacing-elements/)
* [Brockmann](http://jayfreestone.github.io/basic-brockmann/)
* [Susy example](http://www.zell-weekeat.com/context-with-susy/)

Don't be afraid to mix it up and implement a 3 or 5 column grid. No need to always use 12-column layout. Sometimes, simpler really is better.

Because the web is unlike print, you don't have pre-determine dimension. You need to work **content-out**: let the content define the grid.

* Mobile-First
* Content-Out
* Future-Friendly
* System Design
* Offline-First

Grids work on two levels: first perception, then experience. That is, a user feels the grid, then he uses it.

## display: table

* [Nice introduction to `display: table`](http://www.digital-web.com/articles/everything_you_know_about_CSS_Is_wrong/)
* [**display:table Anti-hero**](http://colintoh.com/blog/display-table-anti-hero)
* [See the Designer News comment](https://news.layervault.com/stories/36888-the-antihero-of-css-layout--displaytable-)

## Flexbox

Supported in Chrome 21+, Safari 6.1+, Firefox 22+, Opera 12.1+, IE 11+, and Blackberry 10+.

`viewport-height` to create full page web apps.

Separate it into layout-object and content-object.

* [**Flexbugs - List of flexbox issues and workarounds**](https://github.com/philipwalton/flexbugs)
* [Normalizing cross-browser flexbox bugs](http://philipwalton.com/articles/normalizing-cross-browser-flexbox-bugs/)
* [Flexbox cheatsheet](http://jonibologna.com/flexbox-cheatsheet/)
* [Solved by flexbox](http://philipwalton.github.io/solved-by-flexbox/)
* [Flexbox adventures](http://chriswrightdesign.com/experiments/flexbox-adventures/)
* [Video - Present and future of CSS layout](https://vimeo.com/98746172)
* [Video - Putting flexbox into practice](https://vimeo.com/77176313)
* [Putting flexbox into practice - blog](http://zomigi.com/blog/flexbox-presentation/)
* [Flexy Boxes code generator](http://the-echoplex.net/flexyboxes/)
* [Complete guide to flexbox](http://css-tricks.com/snippets/css/a-guide-to-flexbox/)
* [Flexgrid](http://ptb2.me/flexgrid/)
* [Dive into flexbox](http://weblog.bocoup.com/dive-into-flexbox/)
* [Design flexible layouts](http://www.wpmemorize.com/2013/css-flexbox-to-design-flexible-layouts/)
* [Flexbox example](http://devbryce.com/site/flexbox/)
* [Flexbox - Next-generation CSS Layout has arrived](http://blog.teamtreehouse.com/flexbox-next-generation-css-layout-arrived)
* [Flexbox based responsive equal height](http://osvaldas.info/flexbox-based-responsive-equal-height-blocks-with-javascript-fallback)
* [Kite CSS - Flexible layout helper](http://hiloki.github.io/kitecss/)
* [Flexbox calculator](http://maxsteenbergen.com/fibonacci/)
* [Full height tips](http://www.codelord.net/2014/09/08/css-tip-elements-with-height-100-percent-fixed-amount/)
* [Flexbox cross browser inconsistencies](http://flanneljesus.github.io/web%20design/2014-12-06/flexbox-cross-browser-inconsistencies/)

`flex-wrap` not supported in Firefox, so be careful.

Steps for flexbox:

1. Create flex container using `display:flex`
2. Set its `flex-direction` to control orientation
3. Set its `flex-wrap` to control whether and in which direction to wrap (or `flex-flow` as shorthand for `flex-direction` and `flex-wrap`)

`box-sizing` only takes care of padding and border added on to width, not margin! But with flexbox, it is taken into account.

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

Because block elements typically span 100% of their parent container's width, floating an element **to the right** knocks it down to the next line. To fix it, just reverse the source order.

So what's the limitations of float-based layout?

* Difficulty with containment
* Unwanted wrapping, a.k.a. "float drop"
* Visual location tied to HTML order
* No built-in equal height columns
* No `float:center`

---

* [The secret to designing layouts without CSS floats](http://www.webdesignerdepot.com/2014/07/the-secret-to-designing-website-layouts-without-css-floats/)
* [PPK's clearing float using `overflow:auto`](http://www.quirksmode.org/css/clearing.html)
* [The very latest new new way to do clearfix](http://www.css-101.org/articles/clearfix/latest-new-clearfix-so-far.php)
* [Which method of clearfix is best? - SO](http://stackoverflow.com/questions/211383/which-method-of-clearfix-is-best)
* [**Give floats the flick in CSS layouts**](http://www.sitepoint.com/give-floats-the-flick-in-css-layouts/)
* [CSS float theory](http://www.smashingmagazine.com/2007/05/01/css-float-theory-things-you-should-know/)
* [All about floats](http://css-tricks.com/all-about-floats/)
* [Drawback of CSS: `inline-block` vs `float:left`](http://stackoverflow.com/questions/15172520/drawback-of-css-displayinline-block-vs-floatleft)

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

* [Why use absolute positioning for web UI](http://wiki.sproutcore.com/w/page/12412895/FAQ-AbsolutePositioning)
* [Full-height app layouts](http://blog.stevensanderson.com/2011/10/05/full-height-app-layouts-a-css-trick-to-make-it-easier/)

`static` and `relative` are considered to be in normal document flow.

`relative` - can be offset and following elements react as if the element were not offset. They think it is still there. So why would you want to use `relative`?:

1. For slight tweaking, to move something up a little bit here and there.
2. To provide positioning value for container elements, more for `absolute` positioning. Serve as the offset point.

`absolute` - Removed from normal flow. Absolute also allow clipping like `clip: rect(50px, 200px, 150px, 50px)`

## Overflow

`overflow` only ever work with a defined `width` and `height`.

* [Default for overflow?](http://bocoup.com/weblog/new-overflow-default/)

For many layout tasks collapsing margins really aren't what we want.

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

## Hacks

* [Equal height using JavaScript! Really?](http://benhowdle.im/2014/01/29/easy-peasy-equal-heights/)
* [????](https://app.useoctobox.com/#/collection/animals)