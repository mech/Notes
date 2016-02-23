# Pure React

> The most brilliant principle behind React is functional composition, not VDOM.

Pure function has no side effects. It's hard to violate Single Responsibility Principle, because pure function has obviously only one purpose - to transform input to output. Testing is super easy.

Classes are dirty. One simple method call can mutate them. Who did it? And why? We never know (until we debug)...

* [Mostly adequate guide to FP](https://github.com/MostlyAdequate/mostly-adequate-guide)

## Stateless Components

* [**ES6 classes or stateless functional components?**](http://jamesknelson.com/should-i-use-react-createclass-es6-classes-or-stateless-functional-components/)
* [babel-plugin-react-pure-components](https://github.com/thejameskyle/babel-plugin-react-pure-components)
* [Issue#5677 - Stateless functional components and shouldComponentUpdate](https://github.com/facebook/react/issues/5677)
* [Issue#1176 - Redux + React with only stateless functions](https://github.com/rackt/redux/issues/1176)
* [thisless-react](https://github.com/jas-chen/thisless-react)

Stateless functions don't have a `this` object. If you need anything defined on `this` other than `props`, you'll need a component class. Meaning no `this.state` or `this.refs`.

Functional component cannot have `ref` assigned to it. This is a good thing since `ref` is always meant as a jQuery-like way to look up it's children which is very imperative approach.

Functional component also cannot have state attached to them.

```js
const Profile = ({avatar, name}) => {
  return (
    <div>
      <img src={avatar} />
      <span>{name}</span>
    </div>
  );
}
```

```js
function App({ items }) {
  return (
    <ul>
      {items.map(item => <li>{item}</li>)}
    </ul>
  );
}
```

```js
export default function Light(props) {
  const { light, toggleLight, id } = props
  const status = light.state.on ? 'one' : 'off'

  return (
    <div>
      {light.name}
      <button onClick={() => toggleLight({ ...light, id })}>
        {status}
      </button>
    </div>
  )
}
```

```js
const FilterLink = ({
  filter,
  children
}) => {
  return (
    <a href="#"
      onClick={e => {
        e.preventDefault();
        store.dispatch({
          type: 'SET_VISIBILITY_FILTER,
          filter});
      }}
    >
      {children}
    </a>
  );
}
```

You could still use stateless functional components if all you want to do with `this` is to get a handle to the DOM node:

```js
const AddTodo = ({
  onAddClick
}) => {
  let input;
  
  return (
    <div>
      <input ref={node => {
        input = node;
      }} />
      <button onClick={() => {
        onAddClick(input.value);
        input.value = '';
      }}>
        Add Todo
      </button>
    </div>
  );
}
```

## Immutable

Instead of object, we have Map.

```js
import { Map } from 'immutable';
	
const map1 = new Map({a: 1, b: 2, c: 3});
const map2 = map1.set('b', 50);
map1.get('b'); // 2map2.get('b'); // 50
```

Instead of Array, we have List.

```js
import { List } from 'immutable';

const list1 = List(['a', 'b']);
const list2 = list1.push('c');
list1 === list2; // false
```

Immutable or Mori better utilize memory by implementing persistent data structures using structuring sharing.