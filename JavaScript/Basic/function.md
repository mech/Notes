# Function

* [The `bind` operator](https://medium.com/@matthewwithanm/api-design-the-bind-operator-5a22d255bb18)
* [What is the use of `bind()`](http://stackoverflow.com/questions/2236747/bind-method-of-javascript)
* [`apply` vs `call` vs `bind`](http://stackoverflow.com/questions/15455009/js-call-apply-vs-bind)

`bind` wrap up, change context and make a new function. Whilst `call` and `apply` do not make a new function.

```jsx
<button onClick={alert.bind(this, 'some message')}>Hey</button>
```

Executing a function is called *invoking*, *calling*, or *applying* it.

## Higher-Order Functions

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

## Partial Functions

```js
var partial = function(fn, a) {
  return function(b) {
    fn(a, b);  }}

var greet = function(greeting, name) {
  return greeting + ', ' + name + '!';}

var hello = partial(greet, 'Hello');

hello('mech'); // 'Hello, mech!'
```

