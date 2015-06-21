# OOCSS, SMACSS, BEM

* [MVCSS??](http://mvcss.github.io/resources/)
* [Can CSS be too modular - We need to find the sweet spot](http://csswizardry.com/2015/03/can-css-be-too-modular/)
* [Single Responsibility Principle applied to CSS](http://csswizardry.com/2012/04/the-single-responsibility-principle-applied-to-css/)
* [CSS for Grownups, SXSW 2012](https://www.youtube.com/watch?v=ZpFdyfs03Ug)
* [Respect the global css namespace](http://blog.kaelig.fr/post/44554267597/please-respect-the-global-css-namespace)
* [**Pros and cons of modular CSS**](https://github.com/staltz/cycle/issues/128)
* [BEM - Tech pick of the week](http://futurice.com/blog/tech-pick-of-the-week-bem)

Naming convention (BEM, SUIT) really come into their own when viewed in HTML.
	
> Tying your class name semantics tightly to the nature of the content has already reduced the ability of your architecture to scale or be easily put to use by other developers. - Nicolas Gallagher
>
> We should use sensible names but we should avoid using classes which describe the exact nature of the content and/or its use cases. Using a class name to describe content is redundant because content describes itself.

* `.masthead` is better than `.home-page-panel`
* `.primary-nav` is better than `.site-nav`
* `.primary-button` is better than `.btn-login`
* `.btn--positive` is even better
* `.component-title` instead of `.component .title`


**Visual pattern vs Content**

It is better to keep context in the CSS code. Do not fall into the trap of Atomic CSS where you are creating classes for single CSS property.

Classes shouldn't describe content when content describes itself.

HTML semantics differs from *developer* semantics. We should write classes that are useful for developers; classes that are highly reusable, that don't couple themselves to specific types of content, and classes that describe the *styling's* function rather than the *content's* function.

* [CSS and SASS styleguide](http://www.sitepoint.com/css-sass-styleguide/)
* [What do you do when your design pattern breaks down?](http://css-tricks.com/design-pattern-breaks/)
* [Naming UI components in OOCSS](http://csswizardry.com/2014/03/naming-ui-components-in-oocss/)
* [DoCSSa](http://docssa.info/)
* [OOCSS and the pagification of modules](http://www.edenspiekermann.com/blog/oocss-and-the-pagification-of-modules)
* Object = Structure or the skeleton. OOCSS teaches us to abstract the shared styles out into a base object and then *extend* this information with more specific classes to add the unique treatments.
* Extension = Skin. The unique treatments.
* Be explicit; target the element you want to affect, not its parent. Do not do this: `.sidebar ul {}`
* Overly-specific location-dependent selectors is BAD: `.sidebar h2 {}`
* [Attribute Module CSS - AMCSS](http://glenmaddern.com/articles/introducing-am-css)
* [Beware of selector nesting SASS](http://www.sitepoint.com/beware-selector-nesting-sass/)
* [OOSASS](http://thesassway.com/intermediate/using-object-oriented-css-with-sass)
* [**Stop the cascade**](http://markdotto.com/2012/03/02/stop-the-cascade/)

```
<div class="media media--large" data-ui-component="mini-bio"></div>

<div class="box box--promo"></div>
```

To debug, we can:

```
[data-ui-component] {
  outline: 5px solid yellow;
}
```

Ensure any objects or abstractions are very vaguely named to allow for greater reuse. Like `.ui-list` or `.media`. Extensions of objects should be much more explicitly named like `.user-avatar-link`.

## Component-level vs Page-level

Don't build page specific CSS.

```scss
// Bad: .library-nav-bar, .home-nav-bar (Can't reuse)
// Good: .nav-bar (Generic, sounds like reusable component, rather than specific page)
// Should be in modules/_nav.scss
.nav-bar {
  width: 100%;
}

```

Namespacing should be done at the component-level, never at the page-level. Namespacing should be made at a descriptive, functional level, not at a page location level.

## SUIT CSS

* [Medium styles](https://gist.github.com/fat/a47b882eb5f84293c4ed)
* [About HTML semantics and front-end architecture](http://nicolasgallagher.com/about-html-semantics-front-end-architecture/)

Rely on *structured class name* and *meaningful hyphens* (i.e., not using hyphens merely to separate words)

* Utilities - Low-level structural and positional traits. Utilities exist because certain CSS properties and patterns are used frequently like floats, containing floats, vertical alignment, text truncation. Act as a philosophical alternative to functional (i.e. non-polyfill) mixins.

```scss
// Here you can easily see how `btn` component will be hard to use
// in the `uilist` component
.btn {}
.uilist {}
.uilist a {}
```

In the HTML

```html
<nav class="uilist">
  <a href="#">Home</a>
  <a href="#">About</a>
  <a class="btn" href="#">Login</a>
</nav>
```

Because the specificity of `.btn` is less than that of `.uilist a`, it will not be applied.

## OOCSS

OOCSS is a technique, not a technology.

Look for patterns, not how the layout is laid out.

Grids are a gateway to OOCSS. With grid frameworks, you realise it has generic class names. So too can your components.

OOCSS is fantastic in that it teaches us to abstract out the repetitive, shared, and purely structural aspects of a UI into reusable objects. Non-cosmetic styles that handle the skeletal aspect of a lot of UI components, without ever actually looking like designed 'things'.

Based on 2 main principles:

* Separate structure (functional style) and skin (visual style). Find visual patterns.
* Separate container and content. Prevent location dependent styles.

OOCSS avoids IDs and especially descendant selectors, which tightly couple HTML and CSS.

```
.contentlist
.contentlist_grid
.distinct         // hairline, separator
.module           // padding, margin, edgeless
.module_contained // padding, margin, with edge
```

## BEM

* Block - The declaration of independence.
* Element (sub-component) - Element cannot exist outside of its parent block's context. Detachable elements should become blocks instead.
* Modifier (sub-module) - A modifier is a property of a block or element that alters its look or behavior.
* [CSSWizardry introducing BEM](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)
* [multiple classes vs `@extend`](http://bensmithett.com/bem-modifiers-multiple-classes-vs-extend/)
* [A BEM syntax with UX in mind](http://simurai.com/blog/2013/10/24/BEM-syntax-with-ux-in-mind/)
* [**More transparent UI code with namespaces**](http://csswizardry.com/2015/03/more-transparent-ui-code-with-namespaces/)
* [BEM your JavaScript components](https://medium.com/seek-ui-engineering/block-element-modifying-your-javascript-components-d7f99fcab52b)
* [BEM 101](https://css-tricks.com/bem-101/)

```css
/* Harry Robert's BEM */
.module-name {}               // Root node
.module-name--submodule {}    // Sub-modules (variants)
.module-name__subcomponent {} // Sub-components (children)
```

The trick with BEM is knowing when something falls into a relevant category. One of the hardest parts of BEM is deciding when to start and stop scope, and when (or not) to use it. It's a case of 'you'll just know when you know'.

```html
<div class="modal  modal--large">
  <h1 class="modal__title">Sign into your account</h1>
  
  <div class="modal__content">
    <!-- form-login is a brand new context -->
    <form class="form-login"></form>
  </div>
</div>
```

```css
.site-logo {} // This is not BEM and no need to be!
```

```css
/* primary-nav is a better name than .nav, more reusable */
.primary-nav
.primary-nav__item
.primary-nav__link
.primary-nav__trigger

.primary-nav__sub-nav

/* sub-links is a better name than .footer-links, more reusable */
.sub-links {}
```

```
.room {}
.room__door {}
	
.room--kitchen {}.person {}
.person__head {}
.person__eye {} /* Good */
.person__head__eye {} /* BAD: Too much nesting *//* To denote a .person inside a .room, we use */
.room .person {}

/* NOT this as it is totally separate scope */	
.room__person {}
```
	
It is important to know when BEM scope starts and stops. As a rule, BEM applies to self-contained, discrete parts of the UI.


You can use `avatar` elsewhere, but `profile__image` belongs to the `profile` component. You may not use `profile__image` elsewhere but you can use `avatar` at other places.

```
<div class="box profile">
  <img class="avatar profile__image" />
</div>
```## Dave Shea's Argon

```scss
.swift-project.-activeProject ._filterField {}

.swift-project {
  ._filterList {}

  &.-activeProject {}

  ._filterField {}}
```

```html
<div class="swift-project -activeProject">
  <div class="_filterList">
    <input type="text" class="_filterField" />
    <input type="text" class="_filterField" />
  </div>
  <button type="submit" class="_filterApply">Okay</button>
</div>
```

V.S the BEM

```scss
.swift-project__filterList {}

.swift-project--activeProject__filterList {}

.swift-project__filterField--conditionValue {}
``````html
<div class="swift-project--activeProject">
  <div class="swift-project--activeProject__filterList">
    <input type="text" class="swift-project--activeProject__filterField" />
    <input type="text" class="swift-project--activeProject__filterField" />
  </div>
  <button type="submit" class="swift-project--activeProject__filterApply">Okay</button>
</div>```