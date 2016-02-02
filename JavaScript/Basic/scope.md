# Scope

## Execution Context, Lexical, Scope

* [What is execution context in JavaScript](http://davidshariff.com/blog/what-is-the-execution-context-in-javascript/)

JavaScript engine has "**Syntax Parser**" which is basically a program that read your code and determines if its grammar is valid.

"**Lexical environment**" is where something sits physically in the code your write. "Lexical" means "having to do with words or grammar". A lexical environment exists in programming languages in which **where** you write something is *important*.

When you see the word lexical, just remember it means your code position: Where it is written and what is surrounding it.

"**Execution context**" is a wrapper to help manage the code that is running. There are lots of lexical environments. Which one is currently running is managed via execution contexts.

Global is one of the wrapper. And its current context is called `this`. This is the "global context".

There is also "function context" where flow of execution enters a function body.

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

## Closure

* [LostTechies: JavaScript Closures Explained](https://lostechies.com/derekgreer/2012/02/17/javascript-closures-explained/)
* [Brief history of closures](http://www.battersea-locksmith.co.uk/briefings/closures.html)
