# Functional Programming (FP)

> The whole OOP paradigm is based on sending messages to objects as the only means to interact with their state, therefore making state **distributed**.

We're still stuck with mostly "von Neumann" style languages that talk about state and assignment and memory and stuff.

> Functional units of small size are key to evolvable code. This makes for a fine grained "code sand" which can be brought into ever changing shapes.

* Pure functions everywhere
* Immutable values
* Composition over inheritance
* Records over classes
* Taming side-effects

## Recursion and Loop

If we are not allowed to use for-loop, how are we going to access every item in a list. Say hello to your new friend, recursion!

```js
// Notice we're accepting two values, the list and the current total
function totalForArray(currentTotal, arr) {
  
  currentTotal += arr[0]; 

  // Note to experienced JavaScript programmers, I'm not using Array.shift on 
  // purpose because we're treating arrays as if they are immutable.
  var remainingList = arr.slice(1);

  // This function calls itself with the remainder of the list, and the 
  // current value of the currentTotal variable
  if(remainingList.length > 0) {
    return totalForArray(currentTotal, remainingList); 
  }
  
  // Unless of course the list is empty, in which case we can just return
  // the currentTotal value.
  else {
    return currentTotal;
  }
}
```

Another example of async by hand:

```js
var fs = require('fs');process.chdir('recipes'); // change the working directory
var concatenation = '';fs.readdir('.', function(err, filenames) {
  if (err) throw err;  function readFileAt(i) {    var filename = filenames[i];
    fs.stat(filename, function(err, stats) {      if (err) throw err;      if (! stats.isFile()) return readFileAt(i + 1);      
      fs.readFile(filename, 'utf8', function(err, text) {
        if (err) throw err;        concatenation += text;        if (i + 1 === filenames.length) {          // all files read, display the output          return console.log(concatenation);
        }        readFileAt(i + 1);      });    });
  }  readFileAt(0);});
```

## Programming Paradigms - Styles

* Unstructured - Assembly languages, linear sequence of instructions interrupted with occasional jump.
* Structured - ALGOL, Pascal, Ada. Procedural and OOP can consider as structured programming.
* Procedural - Derived from Structured Programming, based on routines, subroutines, or functions. A "von Neumann" style of programming where memory location and loading of instructions is very common. Procedural code can have side-effect as it can store state between calls.
* Functional
* Object Oriented
* Data-flow
* Query

---

* [**SOLID: The next step is Functional**](http://blog.ploeh.dk/2014/03/10/solid-the-next-step-is-functional/)
* [Functional is not procedural](http://thesmithfam.org/blog/2010/01/05/functional-is-not-procedural/)
* [Understanding the difference between procedural and functional](http://stackoverflow.com/questions/5226055/truly-understanding-the-difference-between-procedural-and-functional)
* [Why the debate on OO vs Functional is all about composition](http://zeroturnaround.com/rebellabs/why-the-debate-on-object-oriented-vs-functional-programming-is-all-about-composition/)
* [Don't be scare of FP](https://www.smashingmagazine.com/2014/07/dont-be-scared-of-functional-programming/)
* [Julia Lang](http://julialang.org/)

## Side Effects

If you have assignment, you have side effect.

## Videos

* [Robert C Martin - Functional Programming; What? Why? When?](https://www.youtube.com/watch?v=7Zlp9rKHGD4)
* [Lean and Functional Programming](https://www.youtube.com/watch?v=5s55LA2Renc)
* [Bret Victor - Inventing on Principle](https://vimeo.com/36579366)
* [Functional programming design patterns by Scott Wlaschin](https://vimeo.com/113588389)
* [Hello, declarative world](https://skillsmatter.com/skillscasts/6523-hello-declarative-world)