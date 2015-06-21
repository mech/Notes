# ES6

* [**Exploring ES6**](https://leanpub.com/exploring-es6/read)
* [TC39 ECMA262 status and process](https://github.com/tc39/ecma262)
* [Babel 5.0 released on March 2015](http://babeljs.io/blog/2015/03/31/5.0.0/)
* [ES6 Features](https://github.com/lukehoban/es6features#enhanced-object-literals)
* [.eslintrc example](https://github.com/jquery/esprima/blob/master/.eslintrc)
* [Another .eslintrc example](https://gist.github.com/ericelliott/ce988c1a808ad903a528#file-eslintrc)
* [**Eric Elliott's eslintrc example**](https://github.com/ericelliott/react-hello/blob/master/.eslintrc)
* [Babel call for contributors](https://github.com/babel/babel/issues/1347)
* [eslint-config-strict](https://github.com/keithamus/eslint-config-strict)
* [CoreJS](https://github.com/zloirock/core-js)

`indexOf` uses Strict Equality Comparison. See SameValueZero comparison.

Objects in JavaScript have reference equality.

```
{error: error} === {error}
```

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

```js
// Array destructuring
let [x, y] = ['a', 'b'];

let [x, y, ...rest] = ['a', 'b', 'c', 'd']; // rest = ['c', 'd']

[x, y] = [y, x]; // swap values
```

```js
let {city: c, state: s} = getAddress();
```

## Object.assign, Cloning, Extending

* [Merging objects via `Object.assign()`](http://www.2ality.com/2014/01/object-assign.html)
* [deep-extend](??)

## Reduce

```js
var a = Object.keys(toggleStates).reduce((newStates, key) => {
	newStates[key] = !toggleAll;
	return newStates;}, {});

// Same as
var six = [1, 2, 3].reduce((sum, n) => {
	return sum + n;}, 0);
```

## React

```js
class Person extends React.Component {
  constructor(props) {
    super(props);
    // No more getInitialState
    this.state = { name: props.name };  }
  
  // ES7
  static propTypes = {
    user: React.PropTypes.object.isRequired  }
  
  setName(name) {
    this.setState({ name: name });  }    
  render() {
    return();  }}

// ES6, not ES7
// No more getDefaultProps
Person.defaultProps = { name: 'anonymous' };
```

## Async and Await

* [ecmascript-asyncawait](https://github.com/lukehoban/ecmascript-asyncawait)

# DOM

* [`DOMStringList`](https://developer.mozilla.org/en-US/docs/Web/API/DOMStringList)
* []()
