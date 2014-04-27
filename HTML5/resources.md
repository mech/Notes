# Resources

* [Design System](http://css-tricks.com/design-systems-building-future/)
* [Build flexible modules, not pages. Design a system. Make it modular.](http://nicolasgallagher.com/about-html-semantics-front-end-architecture/)
* [The Art of HTML Semantics](http://kevinsuttle.com/posts/the-art-of-html-semantics-pt1/)
* [Need for speed - Some nice nginx config](http://jonsuh.com/blog/need-for-speed/)
* [Landscaping with front-end development tools](https://github.com/codylindley/frontend-tools)
* [Make the web accessible](http://thechangelog.com/we-make-the-web-lets-make-it-accessible/)
* [Big background video popular on Facebook Paper](https://news.layervault.com/stories/19508-fullscreen-background-html5-video-best-practices)
* [Detect bandwidth using Networking API](http://www.csskarma.com/blog/detecting-for-bandwidth/)

## Videos

* [A rendering performance guide](http://www.youtube.com/watch?v=9xjpmpX4NJE)

```
function onScroll(evt) {
  // Store the scroll value for later
  lastScrollY = window.scrollY;
  
  // Prevent multiple rAF callbacks
  if (scheduledAnimationFrame)
    return;
    
  scheduledAnimationFrame = true;
  requestAnimationFrame(updatePage);
}

window.addEventListener('scroll', onScroll, false);
```



## HTML/CSS/JavaScript Style Guide

* [@mod Code Guide](http://mdo.github.io/code-guide/)
* [Idiomatic CSS](https://github.com/necolas/idiomatic-css)
* [GitHub Style Guide](https://github.com/styleguide)
* [SHORTTAG NETENABL IMMEDNET or whatever](http://www.colorglare.com/2014/02/03/to-close-or-not-to-close.html)
* [Google Style Guide](http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml)
* [CSS and SASS styleguide](http://www.sitepoint.com/css-sass-styleguide/)
* [Monterail.com guidelines](https://github.com/monterail/guidelines)
* [JavaScript style guide - The Zen Approach](https://github.com/Nijikokun/the-zen-approach)
* [Styleguide Driven Development](http://getflexin.com/styleguide-driven-development/)
* [Styleguide Driven Development - Video](http://www.stubbornella.org/content/2014/04/09/style-guide-driven-development/)
* [Popular coding convention on GitHub](http://sideeffect.kr/popularconvention)
* [JavaScript, the winning style](https://github.com/Seravo/js-winning-style)
* [Idiomatic JS](https://github.com/rwaldron/idiomatic.js)

## HTML Boilerplate

* [HTML5 Bones](http://html5bones.com/)

## Normalize.css

Provides better cross-browser consistency in the default styling of HTML elements.

[About normalize css](http://nicolasgallagher.com/about-normalize-css/)

* Preserves useful defaults rather than "un-styling" everything. Does not impose a visual starting point upon you.
* Corrects some common bugs. Fix display settings for HTML5 block elements. Fix lack of `font` inheritance by `form` element. Correct `font-size` rendering for `pre`, SVG overflow in IE9. Fix `button` styling bug in iOS.
* No large inheritance chain displayed in Chrome dev tool.
* More modular. You can remove sections (like the form normalizations) if you know they will never be needed by your website.


## Content Strategy

It would be a shame to come up with all these fancy layouts if it turns out there isn't content for them to support in the first place.

* [Lorem Ipsum gone wrong - Content-first or you'll be embarrassed](http://www.elezea.com/2014/02/lorem-ipsum-gone-wrong/)

## Site Generator

* [Metalsmith - Everything is a plugin](http://www.metalsmith.io/)


## Tools

* [BrowserSync](http://www.browsersync.io/)
* [I Want to Use - Powered by caniuse.com](http://www.iwanttouse.com/)
* [Rails and Livereload or Codekit](http://blog.55minutes.com/2013/01/lightning-fast-sass-reloading-in-rails-32/)
* [Fireshell - like Yeoman](http://getfireshell.com/)