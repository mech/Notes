# Animation

* [The 12 principles of animation](http://the12principles.tumblr.com/)
* [Interaction ProTip](http://aerotwist.com/tutorials/)
* [All the right moves tutorial series](https://vimeo.com/channels/alltherightmoves/)
* [Web apps deserve sexy transitions too!](https://medium.com/design-ux/8068a5e4cb82)
* [Progress button loading animation](http://tympanus.net/Development/ProgressButtonStyles/)
* [CSS3 animation cheat sheet](http://www.justinaguilar.com/animations/)
* [Improve Stripe payment experience with animations](https://medium.com/p/3d1b0a9b810e)
* [Greensock](http://www.greensock.com/)
* [Dudley Storey's blog](http://demosthenes.info/blog)
* [CSS animation screencast](https://vimeo.com/channels/alltherightmoves/)
* [Pretty nice animation library](http://anijs.github.io/)
* [Pure CSS slide up and down](http://davidwalsh.name/css-slide)
* [bounce.js](http://bouncejs.com/)
* [Giving animation life using bounce](https://medium.com/tictail-makers/giving-animations-life-8b20165224c5)
* [Theatre.js](https://github.com/AriaMinaei/theatrejs)
* [`will-change`](http://dev.opera.com/articles/css-will-change-property/)
* Only 3D transforms qualify for their own layer; 2D transforms don't.
* [Capture CSS3 animation in JavaScript](http://www.sitepoint.com/css3-animation-javascript-event-handlers/)
* [Controlling CSS animations and transitions with JavaScript](http://css-tricks.com/controlling-css-animations-transitions-javascript/)
* [May not be good code examples](http://jackonthe.net/css3animateit/examples)

## Velocity.js

* [Velocity.js - a more performant jQuery replacement for `.animate()`](http://css-tricks.com/improving-ui-animation-workflow-velocity-js/)
* [UI pack overview](https://www.youtube.com/watch?v=CdwvR6a39Tg&hd=1)


## Demo

* [Morphing buttons](http://tympanus.net/codrops/2014/05/12/morphing-buttons-concept/)
* [Hover effect ideas](http://tympanus.net/Development/HoverEffectIdeas/)


## Famo.us

* [Future of JavaScript animation](http://blog.percolatestudio.com/engineering/the-future-of-javascript-animation-with-famous/)


## Animate as you scroll

* [WOW.js - Reveal CSS animation as you scroll down a page](https://github.com/matthieua/WOW)
* [Slide in as you scroll like Google+ app](http://css-tricks.com/slide-in-as-you-scroll-down-boxes/)
* [Case study](http://www.justinaguilar.com/)
* [Steady.js](http://lafikl.github.io/steady.js/)
* [The guide to scrolling animation](http://ihatetomatoes.net/guide-scrolling-animation-libraries/)
* [Scrolling progress bar](http://www.webdesigncrowd.com/scrolling-progress-bar/)

## Examples

To move heading down a bit, and paragraph to move up a bit:

```
h2 {
  animation: moveDown 0.6s ease-in-out 0.2s backwards;
}

p {
  animation: moveUp 0.6s ease-in-out 0.2s backwards;
}

@keyframes moveDown {
  0% {
    transform: translateY(-40px);
    opacity: 0;
  }
  
  100% {
    transform: translateY(0px);
    opacity: 1;
  }
}

@keyframes moveUp {
  0% {
    transform: translateY(40px);
    opacity: 0;
  }
  
  100% {
    transform: translateY(0px);
    opacity: 1;
  }
}
```

## Tools

* [Animatron - an online tool to create HTML5 animations](http://animatron.com/)
* [Outracks](http://www.outracks.com/realtime_studio.html)