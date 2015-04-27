# Selectors

* [Don't use ID in CSS selector?](http://oli.jp/2011/ids/)

Only ever use [selectivizr](http://selectivizr.com/) for IE6-8!

```
div[id] // select all div with an id attribute
```

Types of selectors:

* Class
* Type
* Attribute
* Combinator
* Descendant
* Child
* Qualified
* Key
* [Owl - `* + * {}`](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls)

Use child selector, rather than descendant selector to reduce depth of applicability.

```
/* Reduce depth of applicability */
.comment > a { color: #900; }
.nav > a { color: #333; }

/* BAD - descendant selector */
.nav a {}
```

## Attribute Selectors

Apple rules that match elements based on their attributes or attribute values.

```
// Simple Attribute Selector
a[href] {}

// Exact Attribute Value Selector
a[rel='friend'] {}
// Partial Attribute Value Selector
a[rel~='friend'] {}
// Beginning Substring Attribute Value Selector
a[title^='image'] {}
	
// Ending Substring Attribute Value Selector
a[href$='.pdf'] {}

// Arbitrary Substring Attribute Value Selector
a[href*='.pdf'] {}
```

## Combinator Selectors

```
// Adjacent Sibling Combinator
// <p> is immediately preceded by <h2> on same level of document tree
h2 + p {}

// General Sibling Combinator
// Same as above, but regardless of if it is immediately adjacent
h2 ~ p {}
```

## Pseudo-classes

Pseudo-classes/elements remove the need for you to created non-semantic elements to act as hooks to hang your styles on.

Pseudo-classes are a way to select a whole piece of your HTML element.

```
a:link
a:hover
div:first-child
div:nth-child(3)
:target //CSS level 3, so only IE9+ or use selectivizr of IE6-8
```

`:hover` will be activated when user mouses over an element. `:target` will be activated when fragment identifier changes. Specifically the hashtag like `http://host/articles#article4`

`:target` pseudo-class can be used for tabbed interface or image slideshow [example](http://designshack.net/articles/css/targetcss/).

## Pseudo-elements

Pseudo-elements can be used to select a sub-part of an element.

```
p::first-line
p::first-letter
a::before { content: 'hello world'; }
```

The `::before` notation was introduced in CSS3 in order to discriminate between pseudo-classes and pseudo-elements. Most browser also accept `:before`.

## Greedy Selectors

To style main navigation.

```css
header ul {} /* Bad selector intent, too greedy */
.site-nav {} /* Good */
```

## Qualified Selectors

```css
.error {
  color: red;}

/* Sometimes justifiable to use a qualified selector */
div.error {
  padding: 10px;}```

