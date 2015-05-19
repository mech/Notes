# Components

Components are just state machines. React thinks of UIs as simple state machines. By thinking of a UI as being in various states and rendering those states, it's easy to keep your UI consistent.

DOM is stateful. Input focus and selection, scroll position, etc.

## Higher-order Components

A higher-order component is a function that takes an existing component and returns another component that wraps it.

* [Higher-order components?](https://gist.github.com/sebmarkbage/ef0bf1f338a7182b6775)
* [Mixins are dead](https://medium.com/@dan_abramov/mixins-are-dead-long-live-higher-order-components-94a0d2f9e750)
* [Functional UI and Components as Higher Order Functions](http://blog.risingstack.com/functional-ui-and-components-as-higher-order-functions/)

React 0.14 switches to [parent-based context](https://github.com/facebook/react/pull/3615).

## Render()

Decide everything in the `render()` functions. This means all calculations and conditionals! Make use of helper functions if you can like `renderFullName()` etc. Of course for CPU intensive calculations, use [memoization function](https://lodash.com/docs#memoize).

```js
var memoize = require('lodash.memoize');
```

Data binding is a hack around re-rendering.

## Libraries

* [Nuka Carousel](http://kenwheeler.github.io/nuka-carousel)
* [React DnD](https://github.com/gaearon/react-dnd)
* [React HotKeys](https://github.com/Chrisui/react-hotkeys)
* [react-aria-menubutton](http://davidtheclark.com/building-react-aria-menubutton/)
* [Griddle - Data Table](http://griddlegriddle.github.io/Griddle/)
* [FixedDataTable](https://facebook.github.io/fixed-data-table/)