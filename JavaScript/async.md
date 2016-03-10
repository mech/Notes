# Async

* Callbacks
* Node-style callbacks
* Promises
* Generators
* Async/Await
* Fibers
* Observables

[**A General Theory of Reactivity**](https://github.com/kriskowal/gtor/blob/master/README.md)

> Callbacks: lol, async spaghetti guaranteed.
> 
> Promises: mainstream, swallow errors, no cancel.
> 
> Observables: heaven. - @andrestaltz

---

> Observables are overkill if you need only single value.

To give a bit of perspective on complex front-end application, let's consider Google Docs. Every time a user presses a key, a number of things need to happen (doing them all before returning to the event queue would be a recipe for an unresponsive app):

* the new character has to be displayed on the screen
* the caret has to be moved
* the action has to be pushed to the local undo history
* spell-check may have to run
* word count and page count may need to be updated

We want to use **distributed events**, where a single incident can trigger reactions throughout our application. Event emitter is how you can distribute events.

* Distributing events - Event emitter
* Single task - Promises
* Iteration and flow control - Async.js and RxJS. Essentially an Underscore.js for async code.

**What problem does Async.js or RxJS solves?** We want to read I/O which is async operation and predictable construct result back in an orderly fashion. For example reading a DIR of text file and construct a concatenated string in an orderly way. If we read the file synchronously, we can use normal array's `filter`, `map` to construct the final concatenated string, but that will be terribly inefficient.

---

##  Promises

Can't be abort. But standard want to change this. Not easy though.

Event target???

A Promise is an object that represents a task with 2 possible outcomes (success or failure).

A promise is a proxy for a value from another time or place. The promise interface allows us to interact with that value consistently, regardless of whether the value comes from the past or the future, whether that value is near by or far away, or even if the value is demonstrably unavailable.

User uncertainty. Promises is not for async only. It is good to model user flow also. API for all your async.

Promises is write-once. Once it is resolved, it cannot be resolved again. But for event stream, you can.

The point of promises:

* Eventual value
* Stackable callbacks (`.then().then()`)
* Implicit exception propagation
* Control flow correspondence
* Decoupling space and time
* Pipelined message passing
* A debugging primitive
* Object capability programming
* Remote object? (Inversion of control??)
* Indefinite Promise Queues
* Semaphores
* Asynchronous iterators
* Generators
* Promise streams
* Back pressure
* Limiting parallelism
* State machine
* Streaming parsers
* Reactive bindings
* [Promises, promises](http://wibblycode.wordpress.com/2012/11/21/promises-promises/)
* [Task.js](http://taskjs.org/)
* [The Promised Land](https://www.youtube.com/watch?v=mZHO1ZTsoFk#t=2439)
* [Callbacks are imperative, promises are functional](https://blog.jcoglan.com/2013/03/30/callbacks-are-imperative-promises-are-functional-nodes-biggest-missed-opportunity/)
* [Event loop and done callback](http://blog.namangoel.com/breadthfirstlog-with-the-event-queue)
* [Staying sane with promises and generators](http://colintoh.com/blog/staying-sane-with-asynchronous-programming-promises-and-generators)
* [Cancellable Promises](https://annevankesteren.nl/2015/02/cancelable-promises)
* [Returning a FetchPromise from fetch()](https://github.com/slightlyoff/ServiceWorker/issues/625)
* [Generators are like Arrays](https://gist.github.com/jkrems/04a2b34fb9893e4c2b5c)
* [**We have a problem with Promises**](http://pouchdb.com/2015/05/18/we-have-a-problem-with-promises.html)
* [Asynchronous control flow in JavaScript](http://dparise.svbtle.com/asynchronous-control-flow-in-javascript)
* [Debugging async callbacks](http://www.html5rocks.com/en/tutorials/developertools/async-call-stack/)

### Deferred vs Promises

A Deferred is a superset of Promise with one critical addition: you can trigger a Deferred directly. A pure Promise only lets you add more callbacks; someone else has to trigger them.

```js
var readFile = function() {
  return new Promise(function(resolve, reject) {
    fs.readFile('./package.json', function(err, file) {
      return err ? reject(err) : resolve(file.toString());
    });
  });
};

// Composition with promises - Parallelism
$Q.all([step1, step2, step3]).then(step4);
```

```js
function getProfileImage(username) {
  var promise = new Promise();
  var image = new Image();
  
  image.addEventListener('load', function(event) {
    promise.resolve(this);
  });
  
  image.addEventListener('error', function(event) {
    promise.reject(new Error('Failed to load image'));
  });
  
  return promise;
}
```

Using generator with promises

```js
var FS = require('q-io/fs');
var readJsonPromise = Q.async(function *(path) {
  var text = yield FS.read(path);
  return JSON.parse(text); // Look synchronous code, but actually the above line yield it and resume later
});

// Or if you only have promise and no generator, you still can do this
var FS = require('q-io/fs');
function readJsonPromise(path) {
  return FS.read(path)
    .then(JSON.parse);
}

// The old nodeback method
var FS = require('fs');
var readJsonWithNodebacks = function(path, nodeback) {
  FS.readFile(path, 'utf-8', function(error, content) {
    var result;
    if (error) {
      return nodeback(error);
    }
    
    try {
      result = JSON.parse(result);
    } catch (error) {
      return nodeback(error);
    }
    
    nodeback(null, result);
  });
}
```

Nested promises

```js
return getUsername()
.then(function(username) {
  return getUser(username);
})
// chained because we will not need the user name in the next event
.then(function(user) {
  return getPassword()
  // nested because we need both user and password next
  .then(function(password) {
    if (user.passwordHash !== hash(password)) {
      throw new Error('Can't authenticate');
    }
  });
});
```

ES6

```js
import {denodeify} from 'rsvp'
module fs from 'fs'

var writeFile = denodeify(fs.writeFile)

writeFile('file.txt', 'content!')
  .then(() => {
    console.log('done!');
  });
```

## CSP - Communicating Sequential Processes

* [Taming the Asynchronous Beast with CSP Channels in JavaScript](http://jlongster.com/Taming-the-Asynchronous-Beast-with-CSP-in-JavaScript)
* [js-csp](https://github.com/ubolonton/js-csp)
* [CSP and transducers in JavaScript](http://phuu.net/2014/08/31/csp-and-transducers.html)
* [Transducers.js benchmarks](http://jlongster.com/Transducers.js-Round-2-with-Benchmarks)

### Autocomplete in Netflix

[Adding even more fun to functional programming with RXJS](http://www.youtube.com/watch?v=8EExNfm0gt4)

```js
var keyups = Observable.fromEvent(searchInput, 'keypress');

var searchResultsSets = keyups
  .filter(function(e) {
    return input.value.length > 1;
  })
  .map(function(e) {
    return Observable.getJSON('/search?' + input.values);
  }).
  switchLatest();
```

## Generators

* [Generators vs Callbacks](https://github.com/creationix/js-git#generators-vs-callbacks)

Very powerful for infinite list. Can be combined with Promises.

* [Asynchronous I/O with Generators and Promises](https://ponyfoo.com/articles/asynchronous-i-o-with-generators-and-promises)
* [Generator in Depth](https://ponyfoo.com/articles/es6-generators-in-depth)

## Async Await

> Async/await is still Promises (even if you don't call then() yourself) - @dan_abramov

Async/await is Promises under the hood with synchronous appearance and try/catch works.