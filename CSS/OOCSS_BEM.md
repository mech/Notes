# OOCSS, SMACSS, BEM

* [MVCSS??](http://mvcss.github.io/resources/)

Classes shouldn't describe content when content describes itself.

HTML semantics differs from *developer* semantics. We should write classes that are useful for developers; classes that are highly reusable, that don't couple themselves to specific types of content, and classes that describe the *styling's* function rather than the *content's* function.

* [CSS and SASS styleguide](http://www.sitepoint.com/css-sass-styleguide/)
* [Naming UI components in OOCSS](http://csswizardry.com/2014/03/naming-ui-components-in-oocss/)
* [DoCSSa](http://docssa.info/)
* [OOCSS and the pagification of modules](http://www.edenspiekermann.com/blog/oocss-and-the-pagification-of-modules)
* Object = Structure or the skeleton. OOCSS teaches us to abstract the shared styles out into a base object and then *extend* this information with more specific classes to add the unique treatments.
* Extension = Skin. The unique treatments.
* Be explicit; target the element you want to affect, not its parent. Do not do this: `.sidebar ul {}`
* Overly-specific location-dependent selectors is BAD: `.sidebar h2 {}`

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

## BEM

* Block - The declaration of independence.
* Element (sub-component) - Element cannot exist outside of its parent block's context. Detachable elements should become blocks instead.
* Modifier (sub-module)
* [CSSWizardry introducing BEM](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)

The trick with BEM is knowing when something falls into a relevant category. One of the hardest parts of BEM is deciding when to start and stop scope, and when (or not) to use it. It's a case of 'you'll just know when you know'.

```
.site-logo {} // This is not BEM and no need to be!
```