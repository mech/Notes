# Resources

JavaScript dynamic duo (static type is overrated):

* Loose typing
* Object extension
* [globtester](http://www.globtester.com/)

## People

* [Ariya Hidayat](http://ariya.ofilabs.com/)
* [Axel Rauschmayer](http://www.2ality.com/)
* [Kyle Simpson](http://blog.getify.com/)
* [Rob Richardson](http://robrich.org/)

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