# Module

* [Library best practices](https://github.com/volojs/volo/wiki/Library-best-practices)
* [JavaScript Modules](http://jsmodules.io/)
* [Scalable maintainable JavaScript](http://www.innoarchitech.com/scalable-maintainable-javascript/)

## ES6 Module Transpiler

ES6 Module specification has 2 things:

* Module syntax
* Module loader

Traceur is a Google's ambitious project. Another one is Square's es6-transpiler.

* [**6to5**](http://6to5.org/)
* [ES6 coding style](https://github.com/elierotenberg/coding-styles/blob/master/es6.md)
* [ES6 and io.js](http://davidwalsh.name/es6-io)
* [ES6 modules: the final syntax](http://www.2ality.com/2014/09/es6-modules-final.html)
* [ESLint](http://eslint.org/)
* [Replace CoffeeScript with ES6](http://robots.thoughtbot.com/replace-coffeescript-with-es6)
* [**Understanding ES6**](https://leanpub.com/understandinges6/read)
* [Using Grunt and the ES6 Module Transpiler](http://www.thomasboyt.com/2013/06/21/es6-module-transpiler)
* [Square's ES6 module transpiler](https://github.com/square/es6-module-transpiler)
* [Some deep discussion on interop](https://github.com/square/es6-module-transpiler/issues/85)
* [ES6 Tools](https://github.com/addyosmani/es6-tools)
* [**es6-module-loader**](https://github.com/ModuleLoader/es6-module-loader)
* [systemjs](https://github.com/systemjs/systemjs)
* [estraverse](https://github.com/Constellation/estraverse)
* [esprima](http://esprima.org/)
* [Choc](http://www.fullstack.io/choc/)
* [**es6-promise**](https://github.com/jakearchibald/es6-promise)
* [ES6 on Node.js](http://h3manth.com/new/blog/2013/es6-on-nodejs/)
* [JS.next](http://chimera.labs.oreilly.com/books/1234000001623/index.html)
* [Google Traceur features](https://github.com/google/traceur-compiler/wiki/LanguageFeatures)
* [Modules the ES6 way](http://24ways.org/2014/javascript-modules-the-es6-way/)

## Browserify

* [A list of Browserify resources](http://learnjs.io/blog/2013/11/24/browserify-resources/)
* [voxel.js](http://voxeljs.com/)
* [List of game modules](https://github.com/hughsk/game-modules/wiki/Modules)
* [brfs - Loading static assets](https://github.com/substack/brfs)
* [Browserify and the UMD](http://dontkry.com/posts/code/browserify-and-the-universal-module-definition.html)
* [browserify-shim](https://github.com/thlorenz/browserify-shim)
* [gulp-browserify](https://github.com/deepak1556/gulp-browserify)
* [Using react with browserify](https://medium.com/publish-what-you-learn/a1ea2dd606b)
* [And just like that Grunt and RequireJS are out, it's all about Gulp and Browserify now](http://www.100percentjs.com/just-like-grunt-gulp-browserify-now/)
* [Angular + Gulp + Browserify?](https://github.com/dcartertwo/gulp-angular-browserify-seed)

## uRequire

* [uRequire home page](http://urequire.org/)

# Some ES 6

```
[3, 1, 10].sort((a, b) => a - b);

[3, 1, 10].sort(function(a, b) {
  return a - b;
}.bind(this));

function max(a, ...rest) {
  rest.forEach(x => { if (x > a) a = x; });
  return a;
}

function max(a) {
  var rest = Array.prototype.slice.call(argument, 1);
  rest.forEach(function(x) { if (x > a) a = x; }.bind(this));
  return a;
}

domNode.addEventListener('click', () => {
  this.handleClick(); // `this` not shadowed
});
```

### Class

Prototype based. Mostly syntactic sugar. Working `super()`. Class side inheritance.

```
function ColorPoint(x, y, color) {
  Point.call(this, x, y); // super(x, y)
  this.color = color;
}
ColorPoint.prototype = Object.create(Point.prototype);
ColorPoint.prototype.constructor = ColorPoint;
ColorPoint.prototype.toString = function() {
  return this.color + ' ' + Point.prototype.toString.call(this);
};

// In ES6, it will simply be:

class ColorPoint extend Point {
  constructor(x, y, color) {
    super(x, y);
    this.color = color;
  }
  
  toString() {
    return this.color + ' ' + super();
  }
}
```