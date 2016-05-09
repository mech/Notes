# Selectors

> Selects are matched against everything in the DOM. You need naming strategies to combat against this and keep things efficient (which are hard to enforce and easy to break) - Chris Coyier

* [Keep your selectors short](http://csswizardry.com/2012/05/keep-your-css-selectors-short/)
* [Don't use ID in CSS selector?](http://oli.jp/2011/ids/)
* [CSS 4 Selectors](http://css4-selectors.com/)

Only ever use [selectivizr](http://selectivizr.com/) for IE6-8! **We strongly advice not to use IE8!**

```css
div[id] {} /* select all div with an id attribute */
```

Types of selectors:

* Element or Type
* Class
* ID
* Combinator (Descendant, Child, Adjacent Sibling, General Sibling) == "Complex Selectors"
* Attribute
* Qualified ??
* Key ??
* [Owl - `* + * {}`](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls)

Note the first 3 are "Simple Selectors". The rest are "Complex Selectors".

Use child selector, rather than descendant selector to reduce depth of applicability.

```css
/* Reduce depth of applicability */
.comment > a { color: #900; }
.nav > a { color: #333; }

/* BAD - descendant selector */
.nav a {}
```

## Nesting is BAD (Just don't use it, even in CSSNEXT)

CSS (Poop) is an append-only language.

Nesting can reduce the portability and maintainability of styles, since selectors are tied to the HTML structure.

```css
/* git grep 'div:last-child p' == found nothing as it was nested */
form {
  p {
    margin-bottom: 8px;
  }
  
  div {
    &:last-child {
      p {
        margin-bottom: 0; /* killer nesting, heard to grep to maintain */
      }
    }
  }
}
```

## Combinator Selectors

Combinators are character sequences that express a relationship between the selectors on either side of it.

There are 4 combinators:

* Descendant
* Child
* Adjacent Sibling
* General Sibling - Keep in mind that the general sibling combinator may create some unintended side effects in a large code base, **so use with care**.

```css
/*
Adjacent Sibling Combinator 
<p> is immediately preceded by <h2> on same level of document tree
*/
h2 + p {}

/*
General Sibling Combinator
Same as above, but regardless of if it is immediately adjacent
*/
h2 ~ p {}
```

## Attribute Selectors

Apple rules that match elements based on their attributes or attribute values.

```css
/* Simple Attribute Selector */
a[href] {}

/* Exact Attribute Value Selector */
a[rel='friend'] {}
/* Partial Attribute Value Selector */
a[rel~='friend'] {}
/* Beginning Substring Attribute Value Selector */
a[title^='image'] {}
	
/* Ending Substring Attribute Value Selector */
a[href$='.pdf'] {}

/* Arbitrary Substring Attribute Value Selector */
a[href*='.pdf'] {}

/* Case insensitive with the `i` operator */
a[href^="http" i] {}
```

## Pseudo-classes

* [An Ultimate Guide To CSS Pseudo-Classes And Pseudo-Elements](https://www.smashingmagazine.com/2016/05/an-ultimate-guide-to-css-pseudo-classes-and-pseudo-elements/)

Pseudo-classes/elements remove the need for you to created non-semantic elements to act as hooks to hang your styles on.

Pseudo-classes are a way to select a whole piece of your HTML element.

A pseudo-class selector acts as if you have added a class to an element in your markup.

```
a:link
a:hover
div:first-child
div:nth-child(3)
:target //CSS level 3, so only IE9+ or use selectivizr of IE6-8
```

`:hover` will be activated when user mouses over an element. `:target` will be activated when fragment identifier changes. Specifically the hashtag like `http://host/articles#article4`

`:target` pseudo-class can be used for tabbed interface or image slideshow [example](http://designshack.net/articles/css/targetcss/).

**Warning**: `first-child` will only work if the element is really the FIRST child. Between the element and the parent there cannot be any other different element.

### nth

* [nth-test](http://nth-test.com/)

## Pseudo-elements

A pseudo-element acts as if a whole new element was inserted, then CSS applied.

Pseudo-elements can be used to select a sub-part of an element.

```css
p::first-letter {}
p::first-line {}
::selection {}
```

The double colon `::` notation was introduced in CSS3 in order to discriminate between pseudo-classes and pseudo-elements. Most browser also accept `:before` esp. for IE 8 and lower.

```css
a::before { content: 'hello world'; }
.required::after { content: ' (Required) '; }
```

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

## Quantity Query

* [A very straight approach](http://alistapart.com/article/quantity-queries-for-css)
* [Styling elements based on sibling count](http://lea.verou.me/2011/01/styling-children-based-on-their-number-with-css3/)

## ??

```scss
// Clear after every 3rd item
.flex-car-list li:nth-child(3n+1) {
  clear: both;}
```

```css
:nth-last-child(-n+6):first-child,
:nth-last-child(-n+6):first-child ~ * {
  // Styles sibling elements if there are 6 or more of them in quantity
}
```