# Object

Numbers, strings, and booleans are all *immutable*.

Object, by their very nature is very mutable. And it has to.

```
typeof null // "object"
```

## Prototype

A prototype is just another object that is used as a fallback source of properties. Such a prototype object will itself have a prototype, often `Object.prototype`.

```
Object.getPrototypeOf(isNaN) == Function.prototype
var obj = Object.create({number: 10});
```
	
**Note**: The `prototype` property of a constructor function is different from the what you get from `Object.getPrototypeOf(ConstructorFunction)` as it will return `Function.prototype`.

