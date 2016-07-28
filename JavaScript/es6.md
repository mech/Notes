# ES6

**Proposals**

* [ECMAScript Current Proposals](https://github.com/tc39/ecma262/blob/master/README.md)

---

* [Code styleguide](https://github.com/netshoes/styleguide)
* [**ES6: New features**](http://es6-features.org/#Constants)
* [**ES6 Overview in 350 bullet points!!!**](https://ponyfoo.com/articles/es6)
* [**JavaScript Modules**](http://jsmodules.io/)
* [ES6 Modules: The Final Syntax](http://www.2ality.com/2014/09/es6-modules-final.html)
* [**CoreJS**](https://github.com/zloirock/core-js)
* [**Exploring ES6**](https://leanpub.com/exploring-es6/read)
* [TC39 ECMA262 status and process](https://github.com/tc39/ecma262)
* [Babel 5.0 released on March 2015](http://babeljs.io/blog/2015/03/31/5.0.0/)
* [**ES6 Features**](https://github.com/lukehoban/es6features#enhanced-object-literals)
* [.eslintrc example](https://github.com/jquery/esprima/blob/master/.eslintrc)
* [Another .eslintrc example](https://gist.github.com/ericelliott/ce988c1a808ad903a528#file-eslintrc)
* [**Eric Elliott's eslintrc example**](https://github.com/ericelliott/react-hello/blob/master/.eslintrc)
* [Babel call for contributors](https://github.com/babel/babel/issues/1347)
* [eslint-config-strict](https://github.com/keithamus/eslint-config-strict)
* [**The Boolean Trap**](http://ariya.ofilabs.com/2011/08/hall-of-api-shame-boolean-trap.html)
* [**JS Rocks**](http://jsrocks.org/)
* [React on ES6+](http://babeljs.io/blog/2015/06/07/react-on-es6-plus/)
* [**Why Babel Matters**](http://codemix.com/blog/why-babel-matters)
* [Function Bind](https://github.com/zenparsing/es-function-bind)
* [Elegant React with ES6](https://www.youtube.com/watch?v=GzChMXy-Es0)
* [Functions without "function"](https://medium.com/@ryanflorence/functions-without-function-bc356ed34a2f#.pi6gbh2r3)
* [super() considered hmmm-ful](http://raganwald.com/2015/12/23/super-considered-hmmmful.html)

---

**Tools**

* [estraverse](https://github.com/estools/estraverse)
* [esmangle](https://github.com/estools/esmangle)

`indexOf` uses Strict Equality Comparison. See SameValueZero comparison.

Objects in JavaScript have reference equality.

```
{error: error} === {error}
```

## String

```js
String.prototype.includes
String.prototype.startsWith(txt, start)
String.prototype.endsWith(txt, end)
String.prototype.repeat(count)
String.prototype.trim()
```


## Import and Export

```js
class Radio {}

export { Radio as Player };

import { Player as SportsPlayer } from 'radio';
var basketball = new SportsPlayer();
```

## Killer Features is Multiple Exports

* [d3-jsnext](https://github.com/rollup/d3-jsnext)

CJS and AMD can only export one thing. Historically, we've worked around that by exporting an object with lots of things - for example, Underscore exports the `_` object with lots of functions attached:

```js
var _ = {
  where: fn,
  memoize: fn,
  pluck: fn
};
```

This single export make it hard to do tree-shaking and choose only the right amount of modules to bundle to decrease file size.

## Class

Class, unlike function is not hoisted, so you have to declared it before using it.

You have to call `super` before you can use access `this`.

* [How to use classes and sleep at night](https://medium.com/@dan_abramov/how-to-use-classes-and-sleep-at-night-9af8de78ccb4)
* [Not Awesome: ES6 Classes](https://github.com/joshburgess/not-awesome-es6-classes/)
* [JavaScript Factory Functions vs Constructor Functions vs Classes](https://medium.com/javascript-scene/javascript-factory-functions-vs-constructor-functions-vs-classes-2f22ceddf33e#.xiackfspp)

## Template String

Can be a security concern if you allow user to input template string.

## Block scope

```js
if (x > y) {
  var tmp = x;
  x = y;
  y = tmp;}
console.log(tmp === x); // true

if (x > y) {
  let tmp = x;
  x = y;
  y = tmp;}
console.log(tmp === x); // ReferenceError: tmp is not defined
```

## Destructuring

* [ES6 Destructuring in depth](https://hacks.mozilla.org/2015/05/es6-in-depth-destructuring/)
* [ES6 JavaScript Destructuring in Depth](https://ponyfoo.com/articles/es6-destructuring-in-depth)

**Extract data** from <u>arrays</u> or <u>objects</u> using syntax that "mirrors" the construction of array and object literals.

```js
// Array destructuring
let [x, y] = ['a', 'b']; //=> x=a, y=b

let [x, y, ...rest] = ['a', 'b', 'c', 'd']; //=> rest = ['c', 'd']

[x, y] = [y, x]; // swap values
```

```js
// Object destructuring
var o = {p: 42, q: true};
var {p, q} = o; // Means o.p and o.q

const { visible, className, tag } = this.props
let { city: c, state: s } = getAddress(); //=> c will be obj.city

// Can also used in function with default value
function random({ min=1, max=200 } = {}) {
  return Math.floor(Math.random() * (max - min)) + min;
}

// Rest Properties
let { x, y, ...z } = { x: 1, y: 2, a: 3, b: 4 };
x; // 1
y; // 2
z; // { a: 3, b: 4 }
```

```js
// Destructuring in module loading
const {clone, assign} = require('lodash'); // Means _.clone and _.assign

function makeRequest(url, method, params) {
  var config = {url, method, params};

  // Same as  var config = {
    url: url,
    method: method,
    params: params  }}```

## Spread Operator

A better `apply` and a better `push`.

```js
// Easier concatenation
[1, 2, ...[3, 4, 5], 6, 7]
```

* [ecmascript-rest-spread](https://github.com/sebmarkbage/ecmascript-rest-spread)

Can be used for destructuring also.

```js
[..."abc"] // Will become [ 'a', 'b', 'c' ]
[...document.querySelectorAll('div')] // Same, will give you [<div>, <div>, <div>]

// Which is a better apply, because console.log() function take in argument with comma
console.log(...[1, 2, 3])

var a = [1, 2, 3];
var b = [...a, 4, 5];

// For destructuring
var a, b, c;
[a, b, ...c] = [1, 2, 3, 4, 5];

// With function

function bar(a, b, c) {}

var args = [1, 2, 3];
bar(...args);

function bar(a, ...params) {}

// Spread Properties
let n = { x, y, ...z }
n; // { x: 1, y: 2, a: 3, b: 4 }

// Unknown props example
// See https://facebook.github.io/react/warnings/unknown-prop.html
function MyDiv(props) {
  // We filter out the layout property
  const { layout, ...rest } = props;
  return <div {...rest} style="demo">Test</div>
}
```

## Object.assign, Cloning, Extending

* [Merging objects via `Object.assign()`](http://www.2ality.com/2014/01/object-assign.html)
* [deep-extend](??)

```js
// If you want to remove irrelevant props
render() {
  switch(this.props.size) {
    // do something with size prop
  }
  
  var attrs = Object.assign({}, this.props); // shallow clone
  delete attrs.size;
  
  return <a {...attrs}>{this.props.children}</a>;
}

// Or you can use ES7
render() {
  var {size, ...attrs} = this.props;

  switch(this.props.size) {
    // do something with size prop
  }
  
  return <a {...attrs}>{this.props.children}</a>;
}

// 
deleteComment(comment) {
  $.ajax.delete(comment);

  // clone using spread operator  
  const comments = [...this.state.comments];
  const commentIndex = comments.indexOf(comment);
  comments.splice(commentIndex, 1);
  this.setState({ comments });
}
```

```js
<Something {...propsA} propB="B" />

// Spread attributes actually use Object.assign

React.createElement(Something, Object.assign({}, propsA, {propB: 'B'}))
```

## Reduce

```js
var a = Object.keys(toggleStates).reduce((newStates, key) => {
	newStates[key] = !toggleAll;
	return newStates;}, {});

// Same as
var six = [1, 2, 3].reduce((sum, n) => {
	return sum + n;}, 0);
```

## Decorators

* [Exploring ES2016 Decorators](https://medium.com/google-developers/exploring-es7-decorators-76ecb65fb841)
* [Real Mixins with JavaScript Classes](http://justinfagnani.com/2015/12/21/real-mixins-with-javascript-classes/)
* [Using ES.later Decorators as Mixins](http://raganwald.com/2015/06/26/decorators-in-es7.html)
* [Method Advice](http://raganwald.com/2015/08/05/method-advice.html)
* [mixwith.js](https://github.com/justinfagnani/mixwith.js)
* [Command Pattern](http://raganwald.com/2016/01/19/command-pattern.html)

Mixin is just metaobject?

Mixin application should create a new class (metaclass) by composing existing ones.

## Iterators

## forEach, for-in, for-of and iterators

* [for-of and Iterators](https://hacks.mozilla.org/2015/04/es6-in-depth-iterators-and-the-for-of-loop/)



## React

* [React on ES6+](https://babeljs.io/blog/2015/06/07/react-on-es6-plus)

```js
import React from 'react';
import autobind from 'autobind-decorator';

let { PropTypes, Component } = React;

@autobind
class Person extends Component {
  // Use constructor instead of componentWillMount()
  constructor(...args) {
    super(...args);
    // No more getInitialState
    this.state = {      name: props.name
    };
    
    // If you do not want to use ES8 to bind event
    this.handleClick = this.handleClick.bind(this)  }
  
  // ES7 property initializers
  state = { isEditing: false };
  
  static defaultProps = { initialCount: 0 };
  static propTypes = {
    user: React.PropTypes.object.isRequired  }
  
  // ES8 - Good for event handler and callback which need binding
  // See https://daveceddia.com/avoid-bind-when-passing-props/  change = env => this.setState({isEditing: true});
  
  // Combining 2 features: Arrow function + property initializers
  handleClick = (e) => this.setState()
  
  setName(name) {
    this.setState({ name: name });  }
  
  handleChange(name, e) {
    var newState = {};
    newState[name] = e.target.value;
    this.setState(newState);
    
    // Or you can
    this.setState({
      [name]: e.target.value
    });
  }    
  render() {
    return();  }}

// ES6, not ES7
Person.propTypes = {
  items: PropTypes.array.isRequired};

// No more getDefaultProps
Person.defaultProps = { name: 'anonymous' };

export default Person;
```
	
## Generator

* [CO - Control flow goodness](https://github.com/tj/co)

A generator is basically a function whose execution can be paused and then resumed later, remembering its state.

ES7 introduce the `async` and `await` keywords, removing the need for a generator library altogether.

Generators don't have to terminate which make it very useful.

```
function *myGen(x) {
  yield x;}

var iterator = myGen();
iterator.next();
```

## Async and Await

* [ecmascript-asyncawait](https://github.com/lukehoban/ecmascript-asyncawait)

```js
// Using Alt.js
async login(data) {
  try {
    const response = await axios.post('/login', data);
    this.dispatch({ok: true, user: response.data});  } catch (err) {
    this.dispatch({ok: false, error: err.data});  }}
```

## Reflect and Proxy

* [Reflect](https://github.com/tvcutsem/harmony-reflect/wiki)

```js
Function.prototype.apply.call(f, obj, args);

Reflect.apply(f, obj, args);
```

## Concise Methods and Lexical Identifier

* [Concise methods](http://blog.getify.com/es6-concise-methods-lexical-or-not/)

# DOM

* [`DOMStringList`](https://developer.mozilla.org/en-US/docs/Web/API/DOMStringList)
* []()
