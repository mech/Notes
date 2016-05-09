# RWD Process

> To think about the web responsively is to think in proportions, not pixels. I traded the control I had in Photoshop for a new kind of control—using flexible grids, flexible images, and media queries to build not a page, but a network of content that can be rearranged at any screen size to best convey a message. - Trent Walton

* Fluid Grid
* Flexible Images
* Media Queries

The Web is Flexible and *Fragile*. We can constraint it as much as we like with fixed-width layout and type in pixels, but the Web will shrug off whatever constraints we place around it.

**To ensure our layouts aren't just responsive, but sustainable - fit to deliver compelling content and rich interfaces**

Let go of your need to control the width and height of your layouts. design for a universal, device-agnostic web. Embrace unpredictability.

> Meet our users wherever they happen to be.

Start with markup that is valid, accessible, and functional on almost any device, and layer enhancements from there.

## Hierarchy

> Did I dismiss hierarchy? No, but "squishy" was the unflattering term I initially used to describe responsive sites. For me, websites take on an increasingly familiar skeletal form as I **mentally map content in proportion to specific areas**. When working with clients that's how we address content. Elements are sized & placed purposefully to create order. I was worried that fluid content would have no visual impact and spinelessly reflow, breaking the established hierarchy. However, I soon found that didn’t have to be the case. While working on our first few responsive projects at Paravel, we used fluid-width images, videos, and even text headlines when appropriate, along with proper planning (content choreography) to maintain strong visual presence. The hierarchy, and thus the message, can be preserved at any view.

## Content

* [Content patterns and Display patterns](http://danielmall.com/articles/content-display-patterns/)

---

1. Identify the type of content (Content pattern).
2. Choose visual option (Display pattern) to render said content.

Content strategists are primarily thinking about Content patterns, designers are primarily thinking about Display patterns, and front-end developers are responsible for bringing the two together.

Clean up and prioritize content.

> We think about how to present a design's content and features across a range of screen sizes and devices.
>
> Do the interface components yield to the content when screen real estate is tight? Are the content and hierarchy easy to parse? Do the line lengths foster readability?

Don't hide content. If it's useful to some people, it's likely useful to everyone. Users want and need the same information on all devices.

> Flabby old content can't be shoved into stretchy new responsive clothes, so your editorial process and workflow must evolve.

### Adaptive Content

Adaptive content is stored as smaller, presentation-independent chunks.

## Breakpoints

> Move into the browser quickly. Deciding in the browser.

While it's tempting to choose breakpoints early in the design process, **the truth is that we shouldn't choose breakpoints at all**.

Instead, we should find them, using our content as a guide.

Start with the small screen first, then expand until it looks like shit. Time for a breakpoint! Or choose a comfortable "measure" (45-75 characters).






