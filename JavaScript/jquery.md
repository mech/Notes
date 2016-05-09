# jQuery

* [**You don't need jQuery for Ajax**](http://blog.garstasio.com/you-dont-need-jquery/ajax/)
* [Beyond jQuery](https://leanpub.com/beyondjquery)
* [Don't download the full version of jQuery](http://www.jqueryconfig.com/)
* [jQuery's browser bug workarounds](https://docs.google.com/document/d/1LPaPA30bLUB_publLIMF0RlhdnPx_ePXm7oW02iiT6o/edit)
* [129 fixes](https://gist.github.com/rwaldron/8720084#file-reasons-md)
* [Coding standards & best practices](http://lab.abhinayrathore.com/jquery-standards/)
* [Complete beginners guide](https://ihatetomatoes.net/jquery-complete-beginners-datatypes-selectors/)
* [**jQuery Recipes Your Mom Should Know**](https://github.com/AllThingsSmitty/jquery-your-mom-should-know)

```js
jQuery.fn.init
jQuery.fn = jQuery.prototype

jQuery.fn.jquery // Find version
```

## You don't need jQuery

* [**bling.js**](https://gist.github.com/paulirish/12fb951a8b893a454b32)
* [You might not need jQuery](http://youmightnotneedjquery.com/)
* [diy.js](http://diy.lab.io/)
* [Why you might need jQuery](https://docs.google.com/document/d/1LPaPA30bLUB_publLIMF0RlhdnPx_ePXm7oW02iiT6o/edit#)
* [jQuery vs raw JavaScript](http://www.sitepoint.com/jquery-vs-raw-javascript-1-dom-forms/)

## Plugins and Libraries

* [jQuery boilerplate for plugins development](https://jqueryboilerplate.com/)
* [Fluidbox - Medium-like lightbox](http://terrymun.github.io/Fluidbox/)
* [Animated sorting and filtering of list](https://mixitup.kunkalabs.com/)
* [Stripe's credit card payment](https://github.com/stripe/jquery.payment)
* [jQuery++](http://jquerypp.com/)
* [iCheck - custom checkboxes](http://fronteed.com/iCheck/)
* [jQuery input mask](https://github.com/RobinHerbots/jquery.inputmask)
* [jQuery.extendy](https://github.com/NathanRutzky/jQuery.extendy)
* [jQuery plugins 2014](http://speckyboy.com/2014/12/08/jquery-plugins-2014/)

```
git checkout tags/2.0.3
```

```js
$.fn.plugin.defaults.something = false;

$.fn.plugin = function(options) {
  var settings = $.extend({}, $.fn.plugin.defaults, options);
  
  // You can use `this` inside here which refer to
  // jQuery object
  
  // For you loop, you need to use `$(this)`
  return this.each(function() {
    $(this).xxx
  });
  
  // If you have callback, it is better to use `call`
  // and pass in the desired object for `this`
  settings.onChange.call(this)
}
```

Some examples of plugin

```js
;(function($) {
  $.fn.removeWhitespace = function() {
    this.contents().filter(function() {
      return (this.nodeType === 3 && !/\S/.test(this.nodeValue))
    }).remove();
    return this;
  };
})(jQuery);
```

## History

* [**jQuery original annotation**](http://genius.it/ejohn.org/files/jquery-original.html)
* [window.onload(again)](http://dean.edwards.name/weblog/2006/06/again/)
* [JavaScript CSS selector engine timeline](http://www.paulirish.com/2008/javascript-css-selector-engine-timeline/)
* [Event selector showdown](http://ejohn.org/blog/event-selector-showdown/)
* [XPath and CSS selectors](http://ejohn.org/blog/xpath-css-selectors/)
* [Very old Prototype.js code walkthrough](http://www.sergiopereira.com/articles/prototype131.js.html)