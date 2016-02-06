# Function

Function is just an object. It can have properties and methods attached to it. It even can have functions attached to it. The function body which contain the main code is actually one of the function property that is invocable via `apply`, `call` and `bind`.

* [The `bind` operator](https://medium.com/@matthewwithanm/api-design-the-bind-operator-5a22d255bb18)
* [What is the use of `bind()`](http://stackoverflow.com/questions/2236747/bind-method-of-javascript)
* [`apply` vs `call` vs `bind`](http://stackoverflow.com/questions/15455009/js-call-apply-vs-bind)
* [Functional Programming in JavaScript === Garbage Collection](http://awardwinningfjords.com/2014/04/21/functional-programming-in-javascript-equals-garbage.html)
* [**Transducers.js**](http://jlongster.com/Transducers.js--A-JavaScript-Library-for-Transformation-of-Data)
* [fun.js with lemonad](http://fogus.github.io/lemonad/)
* [jsclass??](http://jsclass.jcoglan.com/comparable.html)
* [**Curry or Partial Application?**](https://medium.com/@yamalight/building-modular-javascript-applications-in-es6-with-react-webpack-and-babel-538189cd485f)
* [Why and how to bind method?](http://reactkungfu.com/2015/07/why-and-how-to-bind-methods-in-your-react-component-classes/)
* [Function name in ES6](http://www.2ality.com/2015/09/function-names-es6.html)

In JavaScript, function context is defined while *calling* the function, not while defining it! Such late binding is a powerful mechanism which allows us to re-use loosely coupled functions in variety of contexts.

`bind` wrap up, change context and make a new function. Whilst `call` and `apply` do not make a new function.

```jsx
<button onClick={alert.bind(this, 'some message')}>Hey</button>
```

Executing a function is called *invoking*, *calling*, or *applying* it.

As useful as `call` and `apply` can be, they have one serious drawback: they impermanently bind the context to the target method. You have to remember to use them every time you invoke the method, and you have to have access to the context object in scope. That's not always easy, particularly in event handlers.

The `bind` method is used to permanently set the value of `this` inside the target function to the passed in context object. It was first popularised by Prototype library and added to ES5 later.

```js
var c = {
  name: 'The c object',
  log: function() {
    this.name = 'Updated c object';
    
    var setName = function(newName) {
      this.name = newName; // Error, will be in global window object
    }

    setName('Updated again! BUT name will be in global');
  }
};
```

## Function Statements and Function Expressions and IIFE

Expression is a unit of code that results in a value. It doesn't have to save to a variable.

```js
// These are expression that return value
a = 3;
1 + 2;

// This is function expression as Function object is being returned
// Will have "undefined is not a function" if invoke prematurely
// Function expression will not be hoisted
var greet = function() {};

// These are statements
if (a === 3) {}

// This is function statement as it does not return value
// The interpreter look at this and just make it note and move on
// Will be hoisted
function greet() {}
```
**IIEF**

```js
(function(us, bb) {
  // Inside an IIEF!
  // The parenthesis trick the parser to let the function become
  // an expression

  var safeCode = 'I am safe from outside world';
})(_, Backbone);
```

## Data Thinking - Data as Abstraction

Transform and move data through the assembly lines.

There is a beautiful symmetry between function programming and data.

## Higher-Order Functions

Functional programming is a style of programming that uses higher-order functions (as opposed to objects and data) to facilitate code organization and reuse.

A higher order function treats functions as data, either taking a function as an argument or returning a function as a result.

Functions that operate on other functions, either by taking them as arguments or by returning them, are called higher-order functions. They allow us to abstract over *actions*, not just values.

`forEach`, `filter`, `map`, etc are all higher-order functions. They are higher-order because they somehow apply a function to the elements of an array.

All are pure functions because it returned a new array.

```js
function filter(array, test) {
  var passed = [];
  for (var i=0; i<array.length; i++) {
    if (test(array[i])) {
      passed.pushed(array[i]);    }  }
  
  return passed;}

// Same
array.filter(function(element) {});
```

Higher-order functions are good for composability. Instead of tangling logic into a big loop, it is neatly composed.

```js
average(array.filter(male).map(age));
```

It's all about "filling in the gap" and provide your own computation because for sure you cannot predict what other people want.

**Example**

```js
function splat(abc) {
  return function(xyz) {
    // don't care  };}

// splat is a function that return a function!
// I don't care what abc is or what xyz is. Matter of fact is that
// useIt is a variable that point to a function begin returned by
// splat and it require the xyz argument.

var useIt = splat(abc);
useIt(xyz);
```

## Currying

Function currying is creating a copy of a function but with some preset parameters. Very useful in mathematical situations.

`bind` give you a copy of the function.

```js
function multiply(a, b) { return a * b; }

var multiplyByTwo = multiply.bind(null, 2);
var multiplyByThree = multiply.bind(null, 3);
```

## Partial Functions

Partial application wraps a function that takes multiple arguments and return a function that takes fewer arguments. It uses closures to fix one or more arguments so that you only need to supply the arguments that are unknown.

```js
var partial = function(fn, a) {
  return function(b) {
    fn(a, b);  }}

var greet = function(greeting, name) {
  return greeting + ', ' + name + '!';}

var hello = partial(greet, 'Hello');

hello('mech'); // 'Hello, mech!'
```

The following is in F# example. You can see the final `hello` is a much cleaner function to use.

```F#
let name = "Scott"
printfn "Hello, my name is %s" name

let name = "Scott"
(printfn "Hello, my name is %s") name

let name = "Scott"
let hello = (printfn "Hello, my name is %s")
hello name
```

You can also use `Function.prototype.bind` for partial application. The only disadvantage is that you won't be able to override the value of `this` with `call` or `apply`.