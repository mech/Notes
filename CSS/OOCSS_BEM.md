# OOCSS, SMACSS, BEM

Classes shouldn't describe content when content describes itself.

HTML semantics differs from *developer* semantics. We should write classes that are useful for developers; classes that are highly reusable, that don't couple themselves to specific types of content, and classes that describe the *styling's* function rather than the *content's* function.

* [CSS and SASS styleguide](http://www.sitepoint.com/css-sass-styleguide/)
* [Naming UI components in OOCSS](http://csswizardry.com/2014/03/naming-ui-components-in-oocss/)

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