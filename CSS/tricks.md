# Tricks

* [**CSS Protips**](https://github.com/AllThingsSmitty/css-protips)
* [**Cody House**](https://codyhouse.co/)
* [Skewed hit boxes with CSS transforms](http://viget.com/inspire/skewed-hit-boxes-with-css-transforms)
* [7 things your didn't know you could do with CSS](http://davidwalsh.name/css-facts)
* [Pure CSS slide up and down](http://davidwalsh.name/css-slide)
* [Useful?](http://snippetrepo.com/)
* [Reading position indicator](http://css-tricks.com/reading-position-indicator/)
* [Some components to learn from](http://goratchet.com/components/)
* [Vertical align](http://zerosixthree.se/vertical-align-anything-with-just-3-lines-of-css/)
* [Useful UI ideas from codrops](https://medium.com/@DavidBenPark/the-most-delightful-and-useful-ui-ideas-from-codrops-b7d469026acb)
* [The shapes of CSS](http://css-tricks.com/examples/ShapesOfCSS/)
* [Characters using box-shadow](http://blog.codeschool.com/post/89758324803/designing-characters-with-box-shadow)
* [Simpsons in CSS](https://pattle.github.io/simpsons-in-css/)
* [Responsive background image](http://sixrevisions.com/css/responsive-background-image/)
* [Paper shadow](http://codepen.io/ashleynolan/pen/djpCG/?editors=110)
* [Fading effect using blend modes](http://blogs.adobe.com/webplatform/2014/07/09/fade-transition-effects-using-blend-modes/)
* [Notification styles inspiration](http://tympanus.net/codrops/2014/07/23/notification-styles-inspiration/)
* [Before:After image comparison slider](http://lea.verou.me/2014/07/image-comparison-slider-with-pure-css/#)
* [CSS slide in panel](http://codyhouse.co/gem/css-slide-in-panel/)
* [Colorful CSS](http://www.webcore-it.com/colorful-background/#)
* [Responsive tabbed navigation](http://codyhouse.co/gem/responsive-tabbed-navigation/)
* [Mobile app introduction template](http://codyhouse.co/gem/app-introduction-template/)
* [Pull](http://codepen.io/fbrz/full/bNdMwZ/)
* [Nice button challenge](https://news.layervault.com/stories/41631-css-challenge-how-would-you-markup-this-element)
* [CSS challenge](https://news.layervault.com/stories/41990-css-challenge-2-how-would-you-markup-this-element)
* [Auto-hide sticky header](http://osvaldas.info/auto-hide-sticky-header)
* [`object-fit: cover`](https://medium.com/@chrisnager/center-and-crop-images-with-a-single-line-of-css-ad140d5b4a87)
* [Full screen pushing navigation](http://codyhouse.co/gem/full-screen-pushing-navigation/)
* [Toggle using the :checked pseudo class](http://www.lottejackson.com/blog/building-a-css-toggle-feature-with-checked-and-flexbox)
* [Caret or arrow](http://tutor.lugolabs.com/articles/10-create-a-thin-caret-with-html-and-css)
* [Dropdown caret](http://stackoverflow.com/questions/16738452/bootstrap-adding-a-dropdown-caret)
* [Use CSS `:not()`](https://twitter.com/wesbos/status/606144483562913792)
* [Page scroll effect](http://codyhouse.co/demo/page-scroll-effects/)
* [Some nice CSS](http://demos.creative-tim.com/presentation)
* [Background image opacity](https://www.designernews.co/stories/54294-css-backgroundimageopacity-would-be-great)
* [Berlin layout](http://jonyablonski.com/2014/berlin-layout/)


```
/* do nothing when clicked even through JavaScript */
.disabled { pointer-events: none; }
```

```
* { background-color: rgba(255,0,0,.2); }
* * { background-color: rgba(0,255,0,.2); }
* * * { background-color: rgba(0,0,255,.2); }
* * * * { background-color: rgba(255,0,255,.2); }
* * * * * { background-color: rgba(0,255,255,.2); }
* * * * * * { background-color: rgba(255,255,0,.2); }
```

## Link

```
a {
  text-decoration: none;
  border-bottom: 2px solid transparent;
  transition: color 200ms, border-color 200ms;}

a:not(.hidden-link):hover {
  color: #43acfb;
  border-color: #43acfb;}
```

## Off-Canvas

* [Secondary expandable navigation](http://codyhouse.co/gem/secondary-expandable-navigation/)
* [Off canvas menus with CSS3 transitions and transforms](http://scotch.io/tutorials/off-canvas-menus-with-css3-transitions-and-transforms)
* [Off screen menus transition](http://speckyboy.com/2014/03/28/off-screen-menus-transition-css3/)
* [Off canvas menu animated links](http://thecodeplayer.com/walkthrough/off-canvas-menu-animated-links)

## Sites with tricks to learn

[Sign up shake page](http://www.emojiweather.com/)

```
form.shake-me {
  animation: formShakeAnimation 400ms ease-in-out
}

@keyframes formShakeAnimation {
  0% {
    transform: translateX(0)
  }

  12.5% {
    transform: translateX(-6px) rotateY(-5deg)
  }

  37.5% {
    transform: translateX(5px) rotateY(4deg)
  }

  62.5% {
    transform: translateX(-3px) rotateY(-2deg)
  }

  87.5% {
    transform: translateX(2px) rotateY(1deg)
  }

  100% {
    transform: translateX(0)
  }
}
```

## Centering

```
<link href="//fonts.googleapis.com/css?family=Roboto:400,400italic,700,300" rel="stylesheet" type="text/css">
<link rel="stylesheet" type="text/css" href="//s3-us-west-2.amazonaws.com/assets.atomic.io/styles/main.061d880f.css">

.center-panel {
  position: absolute;
  left: 50%;
  margin-left: -180px; /* 360px / 2 */
  width: 360px;
  top: 20%;
  padding: 25px 30px 18px 30px;
  background-color: #FFF;
  border-radius: 4px;
}

.btn:not(.btn-tool) {
  -webkit-appearance: none;
  background-color: #0E74E6;
  color: #FFF;
  padding: 0;
  border: 0;
  display: inline-block;
  height: 26px;
  padding-left: 20px;
  padding-right: 20px;
  border-radius: 2px;
  font: 400 9px/25px Roboto,Helvetica,Arial,sans-serif;
  letter-spacing: 1px;
  text-transform: uppercase;
  outline: 0!important;
  -webkit-transition: background-color .2s ease-out;
  transition: background-color .2s ease-out;
}
```

## Border radius

* [CSS arrow](http://cssarrowplease.com/)
* Animatable - You can animate between any 2 radii.

```
// Half of a elliptical shape
border-radius: 50% / 100% 100% 0 0;
width: 400px;
height: 420px;

// Quarter
border-radius: 100% 0 0 0;
width: 400px;
height: 420px;

// Animate
.br {
  border-radius: 50% / 100% 100% 0 0;
  // transition: .5s;
  animation: .5s silly_bouncing infinite alternate;
}

.br:hover {
  border-radius: 50%;
}

@keyframes silly_bouncing {
  to {
    border-radius: 50%;
    bottom: 100px;
  }
}
```

## Gradient

```
// Cut-corner shape
background: #f06;
background: linear-gradient(135deg, transparent 20px, #f06 0),
            linear-gradient(225deg, transparent 20px, #f06 0),
            linear-gradient(315deg, transparent 20px, #f06 0),
            linear-gradient( 45deg, transparent 20px, #f06 0);
background-position: top left, top right,
                     bottom right, bottom left;
background-size: 50% 50%;
background-repeat: no-repeat;
```

## Input

```
// See search input from https://slack.zendesk.com/hc/en-us/articles/201723133-Billing-FAQ
input {
  border: 1px solid #CCC;
  box-shadow: inset 0 1px 1px rgba(0,0,0,0.075);
  transition: border linear .2s,box-shadow linear .2s;
  border-radius: 2rem;
  padding: 10px;
}
```

## Drag and Drop

```
[draggable] {
  user-select: none;
  // Required to make elements draggable in old WebKit
  -khtml-user-drag: element;
  -webkit-user-drag: element;
}
```

## Drop-down

```
// See https://vimeo.com/99877232
.nav > li:hover > .nav-dropdown { display: block; }
.nav-dropdown { display: none; }
```

## Choose other input option

```
.input-option {
  display: none;}

input:checked ~ .input-option {
  display: block;}

<input type="checkbox" id="opt">
<label for="opt">Others?</label>

<div class="input-option">
  <input type="text" id="other">
  <label for="other">Please specify:</label>
</div>
```

## Interesting Class Names

```
.wide-hero
.entry-header
.item-summary
.promo-holder
.deck-inner
.sponsor-intro
.sponsor-name
.sponsor-url
.byline
.quick-summary
.feature-grid
.hero
.colored
.stripe
```

## Videos

* [Smarter UI interactions using `:checked`](https://www.youtube.com/watch?v=XAITicOZCdk)