# Style Guides

Why style guide?

* BEFORE: What markup/CSS do I need to write?
* AFTER: Which components is this page made of?

Generic style guides for components for easy styling. Lego, abstract CSS, make it reusable.

Fully designed components aren't reusable cross-project. This is where OOCSS is a good idea.

* [Apple iOS styleguide, sort of.](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/UIKitUICatalog/index.html#//apple_ref/doc/uid/TP40012857)
* [CSS framework vs UI toolkit](https://vimeo.com/95734680)
* [Cardinal](http://cardinalcss.com/)
* [About HTML semantics and front-end architecture](http://nicolasgallagher.com/about-html-semantics-front-end-architecture/)
* [GitHub styleguide](https://github.com/styleguide/css)
* [Chris Coyier's Sass styleguide](http://css-tricks.com/sass-style-guide/)
* [Front-end style guides - Anna Debenham](http://24ways.org/2011/front-end-style-guides/)
* [Typesetting your CSS objects](http://www.edenspiekermann.com/blog/typesetting-your-css-objects)
* [CSS Guidelines](https://github.com/csswizardry/CSS-Guidelines)
* [Selector intent](http://csswizardry.com/2012/07/shoot-to-kill-css-selector-intent/)
* [Depth of applicability](http://smacss.com/book/applicability)
* [Hologram - Ruby gem to generate style guide](http://trulia.github.io/hologram/)
* [CSS at Lonely Planet](http://ianfeather.co.uk/css-at-lonely-planet/)
* [CodePen's CSS](http://codepen.io/chriscoyier/blog/codepens-css)

## Checklist

* [Decouple **functional CSS** from **visual CSS**](http://www.colmtuite.com/a-more-flexible-development-framework)
* Make use of selector grouping
* No `ul.nav {}`, just `.nav {}`. Browsers read rules from right to left.
* No `.header ul {}`, just `.main-nav {}`.
* No `.widget h2 {}`, just `.widget-title`.
* No `article > p:first-child {}`, just `.intro {}`.
* One selector per line, one rule per line
* `@extend` first, then `@include`, then nested selectors last
* `@mixin` all vendor prefixes. Not using autoprefixer?
* Inception rule - only 3-level deep. Too reliant on HTML structure (fragile), overly specific (too powerful) and not very reusable (not useful).
* Max nested is 50 lines or 1 screenful of editor
* Avoid [contextual styles](http://thesassway.com/intermediate/avoid-nested-selectors-for-more-modular-css), but sometimes they are needed like RWD and themes design.
* Modules, not pages
* Developing a system, rather than individual pages.

## CSS Frameworks

* [SUIT CSS](http://suitcss.github.io/)
* [Topcoat](http://topcoat.io/)
* [Pure](http://purecss.io/)

## Architecture

* [Architecting Sass project](http://www.sitepoint.com/architecture-sass-project/)
* [Pears](http://pea.rs/)
* [Barebones](http://barebones.paulrobertlloyd.com/)

## Examples

* [Style guides and pattern libraries](https://gimmebar.com/collection/4ecd439c2f0aaad734000022/front-end-styleguides-and-pattern-libraries)
* [Code for America](http://style.codeforamerica.org/)
* [Mapbox](https://www.mapbox.com/base/)
* [Github CSS](http://markdotto.com/2014/07/23/githubs-css/)
* [Louder than Ten Manual](http://manual.louderthanten.com/)

## Naming Convention

Structured components consist of the following elements:

* Components - A page module that has a certain purpose and is a wrapper for it's children. Make it as independent as possible.
* Nested elements - Parts of which a component can consist, sometimes similar across components.
* Variants - A component and its containing elements which are modified in a certain way.
* States - The state of a component or nested element is modified by user interaction.

```
// Components
.component-name {}      // .inspector {}

// Variants
.component--variant {}  // .inspector--without-border {}

// Nested elements
// Instead of .component .link {}, we use double underscore
.component__link {}     // .inspector__header {}

// Modifiers or state
.component.is-active {}
.component-name.has-children {}
.component-name.js-selected {}
	
.btn {}
.btn-large {}
.btn-is-active {} // instead of .is-active or .is-btn-active
```

OOCSS has many in non-semantic classes. One of the cited downsides of OOCSS is that these classes don't tell you anything about the content. However, semantic is a fallacy. We should write classes that are useful for developers; classes that are:

* Highly reusable
* Don't couple to specific types of content
* Describe the styling's function rather than the content's function.

```
ui-list
ui-inspector
ui-modal
```

All these describe content, thus is not scalable:

    <ul class="jobs">
    <ul class="candidates">

When you describe the content, you cannot reuse the class name. Rather, derive class name semantics from repeating structural and functional patterns in a design.

> The most reusable components are those with class names that are independent of the content - Nicolas Gallagher

The aim of a component/template/object-oriented architecture is to be able to develop a **limited number** of reusable components that can contain a range of different content types.


## Typography

## Button

```
// This is functional CSS and not visual CSS!
%button {
	display: inline-block;
	-webkit-appearance: button; // remove iOS style
	white-space: nowrap;        // prevent text wrapping
	vertical-align: middle;
	text-align: center;
	cursor: pointer;
	user-select: none;
	overflow: visible;          // fixes odd inner spacing in IE7}
```

## Table

## List

## Form

## Menu

