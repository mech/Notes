# Object

A collection of name/value pairs.

> Program to an interface, not an implementation - GoF

Numbers, strings, and booleans are all *immutable*.

Object, by their very nature is very mutable. And it has to.

```
typeof null // "object"
```

* Member Access - dot notation
* Computed Member Access - Using dynamic string

## Prototype

* [A plain english guide to JavaScript prototypes](http://sporto.github.io/blog/2013/02/22/a-plain-english-guide-to-javascript-prototypes/)

Don't confuse prototype chain with scope chain.

A prototype is just a working sample.

A prototype is just another object that is used as a fallback source of properties. Such a prototype object will itself have a prototype, often `Object.prototype`.

```js
Object.getPrototypeOf(isNaN) == Function.prototype
var obj = Object.create({number: 10});
```

Most object don't directly have `Object.prototype` as their prototype, but instead have another object, which provides its own default properties. Functions derive from `Function.prototype` and arrays derive from `Array.prototype`.

The purpose of prototype is for shared properties and inheritance.
	
**Note**: The `prototype` property of a constructor function is different from the what you get from `Object.getPrototypeOf(ConstructorFunction)` as it will return `Function.prototype`.

```js
var array = [1, 2, 3];
array.toString(); // "1,2,3"
Object.prototype.toString.call(array) // "[object Array]"
```

If you absolutely do not want `Object.prototype` to get in the way of your data structure, you can use `var map = Object.create(null);`

A prototype is an object intended to model other objects after. It is similar to a class in that you can use it to construct any number of object instances. There are 2 ways that prototypes can be used:

1. Delegate Prototype - Object literal `{}` automatically get `Object.prototype`. You can also use `Object.create()` to customise your own. It just mean you delegate property lookup to another object.
2. Prototype Cloning - Sometimes you don't want to share data on a prototype property. You want each instance to have its own unique copy. Use `$.extend`, `_.extend` or ES6's `Object.assign`. Mixin-style. Concatenate.

This is `Object.create` polyfill:
	
```js
if (!Object.create) {
  Object.create = function(o) {
    function F() {}
    F.prototype = o;    return new F();  };}
```

**Warning**: Do not share state on prototype property. It can be mutated or replaced easily. Instead only share method on prototype property. Replace member objects and arrays rather than mutate them in place if you want your changes to be instance safe.

```js
_.extend = function(obj) {
  each(slice.call(arguments, 1), function(source) {
    for (var prop in source) {
      obj[prop] = source[prop];    }  });
  return obj;}
```

The difference between cloning and delegation is that cloning will copy the properties and delegation is more memory efficient.

As it turns out, people mix both techniques - using the delegate prototype to share public methods between objects and cloning for data that can't be safely shared between instances.

## Inheritance

```js
function RTextCell(text) {
  TextCell.call(this, text); // like super()}

RTextCell.prototype = Object.create(TextCell.prototype);
RTextCell.prototype.draw = function() {}
```

## Prototypal

* [Differential inheritance in JavaScript](https://developer.mozilla.org/en/docs/Differential_inheritance_in_JavaScript)
* [Differential inheritance == Prototypal inheritance](http://stackoverflow.com/questions/17771734/what-is-differential-inheritance-in-javascript)

JavaScript is not a classical OO language, it's a prototypal language.

Constructor functions are bad. Dynamic object extension and prototypal inheritance combined to form a more powerful and flexible way to reuse code than classical inheritance.

**Dynamic Object Extension** using mixins, composition, and aggregation for code reuse.

```js
// Without using constructor function to create instances of objects
var enemyPrototype = {
  position: { x: 0, y: 0},        // Override
  setPosition: function(x, y) {}, // Reuse, save memory
  health: 20,                     // Override  bite: function() {}             // Reuse, memory efficient};

// Factory to create object
var spawnEnemyFactory = function() {
  return Object.create(enemyPrototype);};
```

## Extend

```js
_.extend(object, ...sources) // obj[key] = source[key]
jQuery.extend()
```

## GoF and Design Patterns

* [Design Principles from Design Patterns](http://www.artima.com/lejava/articles/designprinciples.html)

Because JavaScript's object system is so powerful and expressive, most of the OO patterns melts away in JavaScript. Like the Singleton pattern is just an object literal:

```js
// Singleton
var highlander = {
  name: 'McLeod',
  catchphrase: 'There can be only one'
};
```

## `Object.create`

```js
var person = {
  firstName: 'Default',
  lastName: 'Default',
  getFullName: function() {}
}

// Much nicer and pure inheritance than using Function Constructor
// Some people prefer this to Function Constructor as it let them
// think more in line with prototypal than classes. They like to
// see Object.create than `new F()`
var john = Object.create(person);
```# ES6 Class

`extends` set the Prototype!