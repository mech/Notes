# Scope

* [Identifier Resolution and Closures in the JavaScript Scope Chain](http://davidshariff.com/blog/javascript-scope-chain-and-closures/)

## Execution Context, Lexical, Scope

* [What is execution context in JavaScript](http://davidshariff.com/blog/what-is-the-execution-context-in-javascript/)

JavaScript engine has "**Syntax Parser**" which is basically a program that read your code and determines if its grammar is valid.

"**Lexical environment**" is where something sits physically in the code your write. "Lexical" means "having to do with words or grammar". A lexical environment exists in programming languages in which **where** you write something is *important*.

When you see the word lexical, just remember it means your code position: Where it is written and what is surrounding it.

"**Execution context**" is a wrapper to help manage the code that is running. There are lots of lexical environments. Which one is currently running is managed via execution contexts.

Global is one of the wrapper. And its current context is called `this`. This is the "global context".

There is also "function context" when flow of execution enters a function body.

Each function call creates a new context, which creates a private scope where anything declared inside the function cannot be directly accessed from outside.

When your code first loaded, it enter the global execution context. If your global code call a function, it will create a new execution context and push that context to the top of the "**Execution Stack**" and on and on with inner function.

Once a context has finished executing, it pops off the stack and control returns to the context below it until the global context is reached again.

Each function call creates a new execution context, even a call to itself.

There are 2 phases when it comes to creating an execution context:

1. Creation stage - where hoisting happen! Variables are `undefined` and functions are referenced to.
2. Execution stage - where values are assigned and run code line by line.

## Scope Chain

* [Video: Scope Chains and Closures](https://www.youtube.com/watch?v=zRZNb4GDOPI)

Lexical scope

Scope chains and closure underlie:

* many constructor-based patterns
* object definition patterns in many libraries
* events and callbacks
* more advanced async control flow patterns
* modules and dependency management
* functional programming patterns
* promises and other monads
* and much more...

Scope chain is all about how similarly position code (lexical positioning) look up variables.

```js
// b() sit physically with global scope. It's lexical scope is on global.
function b() {
  console.log(myVar);
}

function a() {
  var myVar = 2;
  b();
}

var myVar = 1;
a(); // => 1

// ---
// If we change a() to this, then b() sit physically alongside with
// a()'s scope. It is no longer at the global scope.
function a() {
  function b() {
    console.log(myVar);
  }
  
  var myVar = 2;
  b();
}

var myVar = 1;
a(); // => 2
```

## Closure

* [LostTechies: JavaScript Closures Explained](https://lostechies.com/derekgreer/2012/02/17/javascript-closures-explained/)
* [Brief history of closures](http://www.battersea-locksmith.co.uk/briefings/closures.html)

Every function invocation create a new execution context and add into the stack. Each execution context has access to:

1. Variable environment
2. `this`
3. Outer environment - Must be in same lexical position

Outer environment is where the closure is at. It is where you can find those "free variables" left behind by any previous enclosing function calls.

When the function has ended and pop off the execution stack, the Outer environment is still there for the next available function call to take advantage of.

```js
function makeLabel(language) {
  return function(price) {
    if (language === 'en') return `$${price}`
    if (language === 'uk') return `£${price}`
  };
}

// Remember is 2 different execution context, so we have 2
// outer environments here
var americanLabel = makeLabel('en');
var englandLabel = makeLabel('uk');
```