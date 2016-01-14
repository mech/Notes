# NPM

* [NPM documentation](https://docs.npmjs.com/folders)

```js
exports.setup = function() {};
exports.enable = function() {};
exports.ready = true;

// Can't later do exports again!
module.exports = {
  setup: function() {},
  ready: true
};

// To save guard yourself from exporting again
exports = module.exports = {
};
```