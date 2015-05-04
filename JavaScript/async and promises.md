# Async and Promises

A promise is a proxy for a value from another time or place. The promise interface allows us to interact with that value consistently, regardless of whether the value comes from the past or the future, whether that value is near by or far away, or even if the value is demonstrably unavailable.

User uncertainty. Promises is not for async only. It is good to model user flow also. API for all your async.

Promises is write-once. Once it is resolved, it cannot be resolved again. But for event stream, you can.

The point of promises:

* Eventual value
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

![Promises/A+](https://dl.dropboxusercontent.com/u/6815194/Notes/abstraction.png)

```
// Composition with promises - Parallelism
$Q.all([step1, step2, step3]).then(step4);
```


```
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

```
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

```
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

```
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

## Functional Reactive Programming

Imperative - OOP

Spreadsheet is FRP already. You declare the formula, and you change the data to see the result.

* [Netflix JavaScript - Async JavaScript with Reactive Extensions](http://www.youtube.com/watch?v=XRYN2xt11Ek)
* [RxJS](https://github.com/Reactive-Extensions/RxJS)
* [Bacon.js](https://github.com/baconjs/bacon.js)
* [JavaScript Jabber recording of FRP](http://javascriptjabber.com/061-jsj-functional-reactive-programming-with-juha-paananen-and-joe-fiorini/)
* [mercury.js - An interesting framework](https://github.com/Raynos/mercury)

RX:

* Map - Transforms data. Replace loop.
* Filter - Narrows collections. Boolean comparison. Replace `if`.
* Reduce - Turns a collection into a single value.
* Zip - Combines two collections.
* merge - combines items in a collection as each item arrives
* concat - combines collections in the order they arrived
* switchLatest - switches to the latest collection

### Autocomplete in Netflix

[Adding even more fun to functional programming with RXJS](http://www.youtube.com/watch?v=8EExNfm0gt4)

```
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


