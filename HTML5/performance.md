# Performance

* [Jank Free - Let's make the web silky smooth!](http://jankfree.org/)
* [Sitespeed.io](http://www.sitespeed.io/)
* [PNG Mini](http://pngmini.com/)
* [Pixels are expensive](http://aerotwist.com/blog/pixels-are-expensive/)
* [Preventing layout thrashing](http://wilsonpage.co.uk/preventing-layout-thrashing/)
* Only 3D transforms qualify for their own layer; 2D transforms don't.
* Speed Index = Aim for 1000
* Jank is missed frame
* [Critical rendering path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/)
* 10ms to GC is too long!
* [Writing fast memory efficient JavaScript](http://www.smashingmagazine.com/2012/11/05/writing-fast-memory-efficient-javascript/)
* [Paul Lewis](http://aerotwist.com/blog/)
* [How the browser preloader makes pages load faster](http://andydavies.me/blog/2013/10/22/how-the-browser-pre-loader-makes-pages-load-faster/)
* [Optimizing 60fps everywhere in JavaScript](https://engineering.gosquared.com/optimising-60fps-everywhere-in-javascript)
* [High Performance Browser Networking](http://chimera.labs.oreilly.com/books/1230000000545/ch02.html#OPTIMIZING_TCP)
* [Navigation Timing 2 and User Timing](https://github.com/Comcast/Surf-N-Perf)
* [CSS Triggers - Layout, Paint, and Composite](http://csstriggers.com/)
* [Prebrowsing?](http://alistapart.com/article/one-step-ahead-improving-performance-with-prebrowsing)
* [Perfbar](http://lafikl.github.io/perfBar/)
* [Analyze CSS](https://github.com/macbre/analyze-css)
* [Improving Smashing Magazine performance](http://www.smashingmagazine.com/2014/09/08/improving-smashing-magazine-performance-case-study/)
* [**Performance tooling today**](http://perf-tooling.today/)
* [Measuring events with Chrome DevTool](http://web-design-weekly.com/2014/09/18/understanding-measuring-events-with-chrome-devtools/)
* [async vs defer](http://www.growingwiththeweb.com/2014/02/async-vs-defer-attributes.html)

Perceived = f(Expected Performance, UX, Actual Performance)

```
-webkit-backface-visibility: hidden;
-webkit-transform: translateZ(0);
```

```
// This transition is bad (JANK)
// Stick to transform
.expanded {
  height: 400px;
  transition: height 0.4s ease-out;	}
```

## Page load

* [Script-injected "async scripts" considered harmful](https://www.igvita.com/2014/05/20/script-injected-async-scripts-considered-harmful/)
* Incremental HTML delivery. Partial rendering.

## Terms

* Forced synchronous layouts (the yellow chrome alert)
* Layout == Firefox's reflow
* Layout thrashing