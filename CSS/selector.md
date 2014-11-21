# Selector

* [Don't use ID in CSS selector?](http://oli.jp/2011/ids/)

Only ever use [selectivizr](http://selectivizr.com/) for IE6-8!

```
div[id] // select all div with an id attribute
```

## Pseudo-classes

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

