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

## npm@3

* [It's finally here!](https://github.com/npm/npm/releases/tag/v3.0.0)

Q: How would it handle if 2+ dependencies require different versions of the same dependency?

A: In that case, each dependency with a conflicting version on the same dependency would get its own, nested copy of that conflicting dependency. That's why we describe the install tree as maximally flat - it will still allow nesting in the case of conflict.

## CLI

```
▶ npm config ls -l
▶ npm info nodemon
```