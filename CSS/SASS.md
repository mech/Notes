# Sass

> By writing modular code with a component approach, I do not feel the need for Sass's map and loop feature - cssnext

**Warning**: Avoid Sass nesting. Nesting with preprocessor is a false economy. It makes selectors more specific and creates location dependency and more work for the browser.

Use Sass only for its variable, mixin and imports. Avoid nesting and extend.

* [**A vision for Sass**](http://alistapart.com/article/a-vision-for-our-sass)
* [Sass Guideline](http://sass-guidelin.es/)
* [**An auto-enforceable SCSS styleguide**](http://davidtheclark.com/scss-lint-styleguide/)
* [Scalable CSS reading list](https://github.com/davidtheclark/scalable-css-reading-list)
* [**15 essential SASS mixins**](http://www.developerdrive.com/2014/11/15-essential-sass-mixins/)
* [When to use extend and when to use a mixin](http://csswizardry.com/2014/11/when-to-use-extend-when-to-use-a-mixin/)
* [**Useful SASS mixins**](https://github.com/gillesbertaux/andy)
* [SassDoc](https://github.com/SassDoc/sassdoc)
* [Are we getting too sassy](http://ashleynolan.co.uk/blog/are-we-getting-too-sassy)
* [Utility CSS](https://github.com/seegno/ucss)
* [**Tips**](http://csspre.com/)
* [Understanding SASS lists](http://hugogiraudel.com/2013/07/15/understanding-sass-lists/)
* [A SASS type toolkit](http://ianrose.me/typesettings/)
* [Error handling in SASS](http://webdesign.tutsplus.com/tutorials/an-introduction-to-error-handling-in-sass--cms-19996)
* [Removing duplication using SASS maps](http://robots.thoughtbot.com/removing-sass-duplication)
* [Quite some tips on Sass](http://www.alwaystwisted.com/)
* [Out CSS/Sass Project Architecture and Styleguide](http://blog.groupbuddies.com/posts/32-our-css-sass-project-architecture-and-styleguide)
* [DRY Sass mixins](http://alistapart.com/article/dry-ing-out-your-sass-mixins)
* [Bourbon 4](https://news.layervault.com/stories/21801-bourbon-4-differences)
* [Sass and partials](http://zurb.com/university/library/35)
* [Color variables that don't suck](http://davidwalsh.name/sass-color-variables-dont-suck)
* [Organizing z-index](http://jonsuh.com/blog/organizing-z-index-with-sass/)
* [Inverse trigonometric function with Sass](http://thesassway.com/advanced/inverse-trigonometric-functions-with-sass)
* [List-maps](https://www.codefellows.org/blog/so-you-want-to-play-with-list-maps)
* [Mini Sass mixins](http://codepen.io/chriscoyier/blog/some-mini-sass-mixins-i-like)
* [A Sass component in 10 minutes](http://www.sitepoint.com/sass-component-10-minutes/)
* [Using Sass maps to manage color schemes](http://now.violet.is/color-scheming)
* [Handy Sass mixins](http://web-design-weekly.com/2013/05/12/handy-sass-mixins/)
* [Ampersand](http://www.joeloliveira.com/2011/06/28/the-ampersand-a-killer-sass-feature/)
* [Sass tooltips](http://hackingui.com/front-end/scss-tooltips/)
* [Google Material Design colors???](https://github.com/nickpfisterer/quantum-colors)
* [Increasing SASS compiling performance](https://www.devbridge.com/articles/increasing-sass-compiling-performance-or-when-every-second-counts/)


## Placeholder

* [Mixin or Placeholder](http://www.sitepoint.com/sass-mixin-placeholder/)
* [Cross-media query @extend directives in Sass](http://www.sitepoint.com/cross-media-query-extend-sass/)

```
@mixin center { display: block; margin-left: auto; margin-right: auto; }

.container { @include center; }
.image-cover { @include center; }

// Using mixin will result in duplicate styles! We should use placeholder instead
.container {
	display: block; margin-left: auto; margin-right: auto;}

.image-cover {
	display: block; margin-left: auto; margin-right: auto;}
```

## Map

* [Play with list-maps](http://anotheruiguy.roughdraft.io/10302472-so-you-want-to-play-with-list-maps)
* [Using lists with maps in Sass 3.3](http://benfrain.com/using-lists-with-maps-in-sass-3-3/)


```
$message-types: (
	error: #b94a48,
	valid: #468847) !default;

@each $type, $color in $message-types {
	.message-#{$type} {
		@include message($color);	}}
```

## Tips

```
// Tire of writing width and height?
@mixin size($width, $height: $width) {
	width: $width;
	height: $height;}
```

Variables for various font-weight

```
$hairline-weight: 100;
$thin-weight:     200;
$light-weight:    300;
$normal-weight:   400;
$medium-weight:   500;
$semibold-weight: 600;
$bold-weight:     700;
$xbold-weight:    800;
$black-weight:    900;
```

z-index organisation

```
$z-index: (
  modal:      200,
  navigation: 100,
  triangle:   60
);

@function z-index($key) {
	@return map-get($z-index, $key)}

@mixin z-index($key) {
	z-index: z-index($key);}

.navigation {
	@include z-index(navigation);}
```

```
percentage(target/context)
```