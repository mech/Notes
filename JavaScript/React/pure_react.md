# Pure React

> The most brilliant principle behind React is functional composition, not VDOM.

Pure function has no side effects. It's hard to violate Single Responsibility Principle, because pure function has obviously only one purpose - to transform input to output. Testing is super easy.

Classes are dirty. One simple method call can mutate them. Who did it? And why? We never know (until we debug)...

* [Mostly adequate guide to FP](https://github.com/MostlyAdequate/mostly-adequate-guide)

## Stateless Components Syntax

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