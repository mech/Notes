# SVG

HTML for graphics! SVG has a DOM structure and you can even use CSS3 and JavaScript!

JavaScript inside SVG is disabled for image-based SVG.

* [Awesome light ray](http://ncase.github.io/sight-and-light/)
* [Control and filter settings using SVG and JavaScript](http://selfiecity.net/selfiexploratory/)
* [Lonely Planet's switch from icon font to SVG](http://ianfeather.co.uk/ten-reasons-we-switched-from-an-icon-font-to-svg/)
* [Chris Coyier's Using SVG](http://css-tricks.com/using-svg/)
* [Icon system with SVG sprites](http://css-tricks.com/svg-sprites-use-better-icon-fonts/)
* [Animated line drawing - Jake Archibald](http://jakearchibald.com/2013/animated-line-drawing-svg/)
* [Polygon PlayStation 4 and Xbox One review animation](http://product.voxmedia.com/2013/11/25/5426880/polygon-feature-design-svg-animations-for-fun-and-profit)
* [D3.js's gallery collection](https://github.com/mbostock/d3/wiki/Gallery#wiki-collections)
* [Nice icon animation](http://tympanus.net/Development/AnimatedSVGIcons/)
* [List animation](http://tympanus.net/Tutorials/ShapeHoverEffectSVG/index.html)
* [ICONIC](https://useiconic.com)
* [Adaptive SVG](http://w3.eleqtriq.com/2014/02/everything-is-relative-the-art-of-the-adaptive-image/)

```
<text>
<circle cx="" xy="">
<ellipse rx="" ry="" fill=""/>
<line>
<polygon fill="" points="350,75 379,161 ...">
<polyline>
<path d="M100,200 C100,100 250,100..."/>
<g fill="rgba(0,0,0,0.3)" transform="rotate()">
  <rect />
</g>
```


## SVG animation

The easiest way to animate SVG is using CSS animations or transitions, but does not work in IE (unless using `requestAnimationFrame`).

The act of "drawing" in an SVG is optical trick caused by manipulating 2 SVG `path` properties: `stroke-dasharray` and `stroke-dashoffset`.

Make the `stroke-dasharray` as long as the path to make it visually invisible. Then use `stroke-dashoffset` to gradually reveal it.

* [Snap.svg](http://snapsvg.io/)
* [Lazy line painter](http://lazylinepainter.info/)
* [Animated SVGs: Custom easing and timing](http://oak.is/thinking/animated-svgs/)
* [Not SVG, but related](http://coding.smashingmagazine.com/2013/03/04/animating-web-gonna-need-bigger-api/)
* [d3 and SVG](http://snips.net/blog/posts/2014/01-10-fast-interactive_prototyping_with_d3_js.html)

## d3.js

```
var svg = d3.select("body")
  .append("svg");

svg.append("circle")
  .attr("cx", 100)
  .attr("cy", 140)
  .attr("r", 10)
  .attr("fill", "#000000");

d3.selectAll("*").remove(); // If you mess it at console
```

### Selection

* [Section](http://bost.ocks.org/mike/selection/)

### Binding data/Joining data

```
// Data joins!
var dataset = [5, 10, 20, 15, 18];
var datasetObject = [{x: 5, y: 20, r: 10}, {x: 460, y: 90, r: 20}];

var svg = d3.select("body")
            .append("svg")
            .attr("width", w)
            .attr("height", h);

d3.select("svg").selectAll("circle") // `selectAll` return empty selection
  .data(dataset) 			// Enough rooms for 5
  .enter()					// Enter the data value
  .append("circle");
  
d3.selectAll("circle")
  .attr("r", function(d) {		// d is the data value, setup by d3
    return d
  });
  
// Benefits of binding data to elements
// 1. Lets you reference values later
// 2. Prevents need to redraw elements
```


## Examples

* [Nice activity graph using SVG and playback](http://well.blogs.nytimes.com/projects/2014/03/accelerometers.html)


## Tools

* [Grunticon - Search your SVG folder to generate CSS with PNG fallback](https://github.com/filamentgroup/grunticon)
* [Minify your SVG, don't trust Illustrator](https://github.com/sindresorhus/grunt-svgmin)
* [Raphael.js](http://raphaeljs.com/)
* [gRaphael](http://g.raphaeljs.com/)
* [Snap.svg](http://snapsvg.io/)