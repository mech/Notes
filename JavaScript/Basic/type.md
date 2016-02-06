# Type

JavaScript is dynamically typed. You don't need to tell the engine what type your variable is.

6 Primitive types:

* `undefined` - represents lack of existence
* `null` - represents lack of existence (Use this to set variable only)
* `Boolean`
* `Number` - A floating point number really
* `String`
* `Symbol` - New primitive in ES6

`Object` and `Array` are reference types.

```js
// Right-to-left Associativity
a = b = c;
```

## Coercion

Converting a value from one type to another.

Since JavaScript is dynamically typed, coercion happen a lot.

```js
3 < 2 < 1; // Warning: Weird part
false < 1;
Number(false) < 1
```

Double equality will do coercion. Strict equality will not!

`Object.is` is even better than strict equality.

[Equality comparisons and sameness](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Equality_comparisons_and_sameness)

```js
Boolean(undefined); // false
Boolean(null);      // false
Boolean("");        // false
Boolean(0);         // Warning: Also false

// Thus if you want to check for undefined, null or empty string
// you can safely use double equality for coercion.
// But beware of ZERO.
```