# Object

Numbers, strings, and booleans are all *immutable*.

Object, by their very nature is very mutable. And it has to.

```
typeof null // "object"
```

## Prototype

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

## Inheritance

```js
function RTextCell(text) {
  TextCell.call(this, text); // like super()}

RTextCell.prototype = Object.create(TextCell.prototype);
RTextCell.prototype.draw = function() {}
```