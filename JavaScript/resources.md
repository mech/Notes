# Resources

JavaScript dynamic duo (static type is overrated):

* [**ES6 Learning**](https://github.com/ericdouglas/ES6-Learning)
* [ES Discuss](http://esdiscuss.org/)
* Loose typing
* Object extension
* [globtester](http://www.globtester.com/)
* [FPS engine](http://www.playfuljs.com/a-first-person-engine-in-265-lines/)
* [JSNice - deobfuscation](http://jsnice.org/)
* [A JavaScript Quality Guide](https://github.com/bevacqua/js/)
* [Regular expression in JavaScript](http://bjorn.tipling.com/state-and-regular-expressions-in-javascript)
* [Mixins, Forwarding, and Delegation in JavaScript](http://raganwald.com/2014/04/10/mixins-forwarding-delegation.html)
* [Variable hoisting](http://malena.github.io/training/#scope)
* [JavaScript for OSX Automation](http://tylergaw.com/articles/building-osx-apps-with-js)
* [5 array methods you should use today](http://colintoh.com/blog/5-array-methods-that-you-should-use-today)
* [Code optimization](http://colintoh.com/blog/avoid-oop)
* [**Drag and Drop interaction ideas**](http://tympanus.net/codrops/2014/11/11/drag-and-drop-interaction-ideas/)
* [Flow - static type checker](https://code.facebook.com/posts/1505962329687926/flow-a-new-static-type-checker-for-javascript/)
* [Flow - Static type checker](http://flowtype.org/)
* [Functional JavaScript](http://osteele.com/sources/javascript/functional/)

## V8

* [Optimization killers](https://github.com/petkaantonov/bluebird/wiki/Optimization-killers)

## People

* [Ariya Hidayat](http://ariya.ofilabs.com/)
* [Axel Rauschmayer](http://www.2ality.com/)
* [Kyle Simpson](http://blog.getify.com/)
* [Rob Richardson](http://robrich.org/)
* [Hugo Giraudel](http://hugogiraudel.com/)
* [Sam Dutton](http://simpl.info/)
* [Volkan](http://volkan.io/)

## Macros

* [Writing your first Sweet.js macro](http://jlongster.com/Writing-Your-First-Sweet.js-Macro)
* [es6-macros](https://github.com/jlongster/es6-macros)

```
macro foo {
  rule { $x plus $y } => {
    $x + $y
  }
}

foo 5 plus 6 // -> 5 + 6
```

```
// ES6 Fat arrow
macro => {
  rule infix { ($value (,) ...) | ($body ...) } => {
    function($value (,) ...) {
      $body ...
    }.bind(this)
  }
  rule infix { ($value (,) ...) | $guard:expr } => {
    function($value (,) ...) {
      return $guard;
    }.bind(this)
  }
  rule infix { $param:ident | $guard:expr } => {
    function($param) {
      return $guard;
    }.bind(this)
  }
}

// To use it
(x, y, z) => {
  return x * y * z;
}
```

## Isomorphic

Use cases:

* Templating
* Routing
* I18n
* Date and currency formatting
* Model validation
* API interaction

Magic happens in the build process: Browserify and Grunt.

## Unicode

* [JavaScript Encoding](http://mathiasbynens.be/notes/javascript-encoding)
* [Countable.js](http://sachaschmid.ch/Countable/)
* [punycode.js](https://github.com/bestiejs/punycode.js)
* [js-escapes](http://mothereff.in/js-escapes)
* [Create Unicode-aware regular expressions](https://github.com/mathiasbynens/regenerate)

Problem with surrogate pair like "pile of poo" U+1F4A9

```
function getSurrogates(codePoint) {
  var high = Math.floor((codePoint - 0x10000) / 0x400) + 0xD800;
  var low = (codePoint - 0x10000) % 0x400 + 0xDC00;
  return [high, low];
}

function getCodePoint(high, low) {
  var codePoint = (high - 0xD800) * 0x400 + low - 0xDC00 + 0x10000;
  return codePoint;
}

// ES6
Array.from(string).length;

function countSymbolsPedantically(string) {
  // Unicode Normalization, NRC form:
  var normalized = string.normalize('NFC');
  // Account for astral symbols / surrogates:
  return Array.from(normalized).length;
}
```