# Promises

A promise is a proxy for a value from another time or place. The promise interface allows us to interact with that value consistently, regardless of whether the value comes from the past or the future, whether that value is near by or far away, or even if the value is demonstrably unavailable.

User uncertainty. Promises is not for async only. It is good to model user flow also. API for all your async.

The point of promises:

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