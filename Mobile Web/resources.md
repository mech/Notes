# Resources

* [Mobile HTML 5 by Maximiliano Firtman](http://mobilehtml5.org/)
* [**Google Web Starter Kit for multi-device development**](https://developers.google.com/web/starter-kit/)
* [**Mobile web checklist**](http://www.luster.io/blog/9-29-14-mobile-web-checklist.html)
* [Brad Frost responsive pattern library](http://bradfrost.github.io/this-is-responsive/patterns.html)
* [BBC Responsive News](http://responsivenews.co.uk/)
* [Tool: Responsive viewport](http://cobyism.com/shapeshifter/)
* [Make your site work on touch devices](http://www.creativebloq.com/javascript/make-your-site-work-touch-devices-51411644)
* [Responsive design signals larger change](http://www.vanseodesign.com/web-design/responsive-design-signals-larger-change/)
* [Like fastclick.js?](http://filamentgroup.com/lab/tappy.html)
* [Designing Multi-Device Experiences](http://www.nirandfar.com/2014/07/how-successful-companies-design-for-users-multi-device-lives.html)
* [Performance is the key for RWD](http://www.smashingmagazine.com/2014/07/22/responsive-web-design-should-not-be-your-only-mobile-strategy/)
* [RWD Bloat](http://daverupert.com/2014/07/rwd-bloat-part-ii/)
* [How we make RWD sites load fast as heck](http://filamentgroup.com/lab/performance-rwd.html)
* [Some convenient breakpoint methods](http://restivejs.com/)
* [Slash build time on RWD](http://www.creativebloq.com/css3/slash-build-time-proportional-rwd-91412846)
* [Performance testing for RWD](https://github.com/lafikl/RWDPerf)
* [**Instant Click**](http://instantclick.io/)
* [Responsive image polyfill](https://github.com/aFarkas/respimage)
* [Loading web fonts with high performance](http://bdadam.com/blog/loading-webfonts-with-high-performance.html)
* [Wayfinding in mobile web](http://www.smashingmagazine.com/2014/10/13/wayfinding-for-the-mobile-web/)
* [Responsive, performant interfaces](https://github.com/mrmrs/tachyons/)

## List of screen resolution

|   Device  |       Resolution       |  DPI   |
| --------- | ---------------------- | ------ |
| iPhone    | 320 x 480              | 163dpi |
| iPhone 4  | 640 x 960              | 326dpi |
| iPhone 5  | 640 x 1136 (320 x 568) | 326dpi |
|           |                        |        |
| iPad      | 768 x 1024             | 132dpi |
| iPad 3    | 1536 x 2048            | 264dpi |
| iPad Mini | 768 x 1024             |        |
|           |                        |        |
| Nexus 7   | 600 x 960              | 323dpi |
| Nexus 10  | 800 x 1280             | 300dpi |
| Nexus 5   | 360 x 598              | 445dpi |

## Frameworks for Mobile Web

* [App.js](http://code.kik.com/app/2/index.html)
* [Ionic](http://ionicframework.com/)

## Process and Workflow

* [Content Structure - Source Order](https://vimeo.com/89535832)
* [A matter of workflow - Nathan Ford](http://www.iaskyouanswer.co.uk/nathan-ford.php)

> You can't design a good layout if you don't know the content.

> Introducing new layouts for screen sizes where the content loses it's integrity.

> An early trap for us that I see many other falling into is the idea of "screen size" targeting. Setting breakpoints before you build can lead to some real pain when trying to squeeze in content later.

## Touch Events

* [Custom gesture](https://developers.google.com/web/fundamentals/input/touch-input/touchevents/)

## Responsive Typography

* [FitText](http://fittextjs.com/)
* [Responsive line height](http://viljamis.com/blog/2014/responsive-line-height/)

## Media Queries

Style sheets with media queries attached to their `<link>` tags will still download even if it evaluate to `false`.

* [Good resource for knowing the logical operators of media queries](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Media_queries)
* [Responsive JavaScript](http://www.csskarma.com/blog/responsive-javascript/)
* [Responsive design tool for Brackets](http://www.leebrimelow.com/responsive-design-with-adobe-brackets/)
* [Essential considerations for crafting quality media queries](http://zomigi.com/blog/essential-considerations-for-crafting-quality-media-queries/)
* [Logic in media queries](http://css-tricks.com/logic-in-media-queries/)
* [Another take](http://sassmeister.com/gist/1a0a43f1511b9bd75adf)

Use [Respond.js](https://github.com/scottjehl/Respond) for IE6-8. It supports only `min-width` and `max-width`, but that is enough to kick started.

```
<!--[if (lt IE 9)&(!IEMobile 7)]>
<script src="respond.min.js"></script>
<![endif]-->
```

```
if (window.matchMedia("(min-width: 40em)").matches) {
	// load stuff}
```

### Mobile-first

```
// Mobile-first style
@media screen and (min-width: 50em) {
	.col {
		float: left;
		width: 50%;
	}
}

// Do not do desktop-first
.col {
	float: left;
	width: 50%;
}

@media screen and (max-width: 50em) {
	.col {
		float: none;
		width: auto;
	}
}
```

Get your thinking right first. Just because you develop using a desktop browser does not mean you need to think desktop-first!

## Meta Viewport

* [Opera's introduction to meta viewport](http://dev.opera.com/articles/view/an-introduction-to-meta-viewport-and-viewport/)

## Retina

* [Retina for web workflow](http://michieldegraaf.com/post/retina-for-web-workflow/)
* [Optimizing graphics for retina display](http://www.studiopress.com/design/css-background-size-graphics.htm)
* [WWDC - Delivering web content on high resolution displays](https://developer.apple.com/videos/wwdc/2012/?id=602)
* [json2css-sprite-mixins](https://github.com/bensmithett/json2css-sprite-mixins)
* [How I design for retina](https://medium.com/p/e905c9106a56)
* [Responsive retina blog design](http://paulstamatiou.com/responsive-retina-blog-design/)

```
.logo {
  width: 200px;
  height: 60px;
  background-image: url(logo.png) no-repeat;
  background-size: 100% 100%;

  // Or half it
  background-size: 100px 100px, 100% 100%;
}

@media only screen and (-webkit-min-device-pixel-ratio: 2) {
  .logo {
    background-image: url(logo@2x.png) no-repeat;

    // Or half it
    background-size: 50px 50px;
  }
}
```

Notice the `background-size` is set to `100%` for both width and height. This makes it easier to change our real `width` and `height`.

```
@media (min--moz-device-pixel-ratio: 1.5),
       (-o-min-device-pixel-ratio: 3/2),
       (-webkit-min-device-pixel-ratio: 1.5),
       (min-resolution: 1.5dppx) {
}
```

## Responsive Images

* [Figuring responsive images](http://css-tricks.com/video-screencasts/133-figuring-responsive-images/)

## Favicon

16px for standard screens and 32px for retina screens.

* [Retina version](http://xiconeditor.com/)