# Performance

Don't look at code, measure it! It is very hard to tell from code where the performance is.

```
▶ npm install -g sitespeed.io
▶ npm install -g psi
```

* [**Sitespeed**](https://www.sitespeed.io/)
* [**Performance Calendar**](http://calendar.perfplanet.com/2014/)
* [**Rendering Performance**](https://developers.google.com/web/fundamentals/performance/rendering/)
* [**Better data from Good UI**](http://www.goodui.org/betterdata/)
* [CSS Triggers](http://csstriggers.com/)
* [**Perf.Rocks**](http://www.perf.rocks/)
* [**Measure, Optimize, Automate**](http://ponyfoo.com/articles/measure-optimize-automate)
* [**Awesome Web Performance Optimization**](https://github.com/davidsonfellipe/awesome-wpo)
* [**Google - Make the Web faster**](https://developers.google.com/speed/)
* [**Jank Free - Let's make the web silky smooth!**](http://jankfree.org/)
* [**Frame Timing Explainer**](https://github.com/w3c/frame-timing/wiki/Explainer)
* [**What does my site cost?**](http://whatdoesmysitecost.com/)
* [**More weight doesn't mean more wait**](https://www.filamentgroup.com/lab/weight-wait.html)
* [How we make RWD sites load fast as heck](https://www.filamentgroup.com/lab/performance-rwd.html)
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
* [Scroll problem](http://aerotwist.com/blog/some-gotchas-that-got-me/)
* [Web Performance Matters](http://www.perf.rocks/)
* [loadCSS](https://github.com/filamentgroup/loadCSS)
* [Solving rendering perf puzzles](http://jakearchibald.com/2013/solving-rendering-perf-puzzles/)
* [fastdom](https://github.com/wilsonpage/fastdom)
* [The script loader pattern](http://www.lognormal.com/blog/2012/12/12/the-script-loader-pattern/)

```html
<!-- Unblock fonts -->
<script>
  function loadCSS(url) {}
  loadCSS('//cloud.typography.com/7773243.css');
</script>
```

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

## Webpage Test

Automate it! Measure early. Measure often. Use `npm install psi`.

FOIT - Flash of Invisible Text

## Cache

* [**Things Caches Do**](http://2ndscale.com/rtomayko/2008/things-caches-do)

---

1. Cache as much on the client-side and server-side. Use CDN + browser caching. User reverse proxy cache on the server-side.
2. Queuing - Do not delay user experience for tasks that can be executed in the background.
3. Async - Optimize work to execute concurrently / asynchronously


## High Speed UX

**Synthetic measurement is bad and not accurate, we need RUM (Real User Measurement)**

```
curl 'https://eva.jobline.com.sg/' -H 'If-None-Match: W/"babaa3198f3c8a816f88d06340b79500"' -H 'DNT: 1' -H 'Accept-Encoding: gzip, deflate, sdch' -H 'Accept-Language: en-US,en;q=0.8,pt;q=0.6,ja;q=0.4,de;q=0.2,zh-TW;q=0.2,zh;q=0.2,zh-CN;q=0.2,fr;q=0.2' -H 'Upgrade-Insecure-Requests: 1' -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/46.0.2490.71 Safari/537.36' -H 'Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8' -H 'Cache-Control: max-age=0' -H 'Cookie: __utma=202529802.1875141668.1423443808.1445477289.1445528994.375; __utmz=202529802.1423443808.1.1.utmcsr=(direct)|utmccn=(direct)|utmcmd=(none); _EVA_session=bEpwQmxSVjRNcSt5aWxyRkRCRmV6dXBjRHR4aU5tZG5MR2tONkZvbUtkWEJsbGFVRHI0ZkVnZStoRFJ3WTdRODhjc0NPelRYRXRaZ1p3ZzdITWdJQVU0SnJkOHgvRUlmRDYyeXd0Y2k5czNuYXE5Zk1GL1V1VVZqeXpkNnJCWlJBRlM4bGIwck56Sk9TVUVBbE5ySkR4VEhvZzZoK21RcTlueEVqQytteHBGWFpyVHZoL1hMRnVQejZZL3lOUmtCcEtMclQ2MTNJVnNFRTUxRzg1amdYUT09LS1yL3BBdWtlRG4wNVd6d2VRbnFBZ1F3PT0%3D--d67fda257ed4031dab126991d80803b6d707f9a9' -H 'Connection: keep-alive' --compressed -w "\ndownload response time = %{time_total} seconds\n"
```

**Cheap window.onload RUM**

```
<script>
var t_top = new Date().getTime();
window.onload = function() {
  var t_onload = new Date().getTime();
  new Image().src = "beacon.gif?loadtime=" + (t_onload - t_top);}
</script>
```

First Page View = DNS Resolution time + Cache + ..?

## Using Web Performance Timing

Load a new page in Incognito and at the console, type `performance.timing`

```
performance.timing

loadEventStart: 1445657264694


```

## Set your performance budget

* [Setting a performance budget](http://timkadlec.com/2013/01/setting-a-performance-budget/)
* [Performance Budget Metrics](http://timkadlec.com/2014/11/performance-budget-metrics/)
* [How to make a performance budget](http://danielmall.com/articles/how-to-make-a-performance-budget/)

```
window.performance.mark('foo-bar');
```

## Page load

* [Script-injected "async scripts" considered harmful](https://www.igvita.com/2014/05/20/script-injected-async-scripts-considered-harmful/)
* Incremental HTML delivery. Partial rendering.

## Browser Performance

Cmd+E to start/stop profiling.

Usually in order:

1. Function call (Yellow) - Usually kick off by JavaScript
2. Recalculate style - Get all style rules, evaluate the selectors and match against DOM and calculate the computed style for every element. Anytime you change the CSS class names, you have thus invalidate style and the browser will have to do a little bit more work to recalculate
3. Layout - Laying out the geometric of the page. How many nodes that needed layout. The layout scope. 20ms is too long for layout.
4. Paint (Green) - Painting hurts on low-end devices. Locate with "Show Paint Rects", then "continuous paint mode" or "paint profiler"
5. Composite layers

"Frames mode" change the summary to look like taller vertical bars heights. The taller the worst because it has lower FPS.

"Tracing mode"

## Videos

* [Building the next-generation of theguardian.com](https://vimeo.com/125545018)
* [Paul Lewis on Making a Silky Smooth Web](https://vimeo.com/125121010)

## Terms

* Forced synchronous layouts (the yellow chrome alert)
* Layout == Firefox's reflow
* Layout thrashing