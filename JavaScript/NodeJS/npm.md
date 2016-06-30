# NPM

* [NPM documentation](https://docs.npmjs.com/folders)
* [How to build and public ES6 NPM module today](https://booker.codes/how-to-build-and-publish-es6-npm-modules-today-with-babel/)
* [How to use npm as a build tool](http://blog.keithcirkel.co.uk/how-to-use-npm-as-a-build-tool/)

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
▶ npm list --depth=0
▶ npm list -g --depth=0
▶ npm view eslint dependencies
▶ 
▶ 
▶ 
```