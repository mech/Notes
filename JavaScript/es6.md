# ES6

* [TC39 ECMA262 status and process](https://github.com/tc39/ecma262)
* [Babel 5.0 released on March 2015](http://babeljs.io/blog/2015/03/31/5.0.0/)
* [ES6 Features](https://github.com/lukehoban/es6features#enhanced-object-literals)

`indexOf` uses Strict Equality Comparison. See SameValueZero comparison.

Objects in JavaScript have reference equality.

```
{error: error} === {error}
```

## React

```js
class Person extends React.Component {
  constructor(props) {
    super(props);
    // No more getInitialState
    this.state = { name: props.name };  }
  
  setName(name) {
    this.setState({ name: name });  }    
  render() {
    return();  }}

// No more getDefaultProps
Person.defaultProps = { name: 'anonymous' };
```

## Async and Await

* [ecmascript-asyncawait](https://github.com/lukehoban/ecmascript-asyncawait)

# DOM

* [`DOMStringList`](https://developer.mozilla.org/en-US/docs/Web/API/DOMStringList)
* []()
