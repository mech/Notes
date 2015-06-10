# Components

* [Smart and Dumb Components - ViewController](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0)
* [Container Components](https://medium.com/@learnreact/container-components-c0e67432e005)
* [JSX, a year in](https://gist.github.com/chantastic/fc9e3853464dffdb1e3c)
* [Composition](https://medium.com/dev-channel/javascript-application-architecture-on-the-road-to-2015-d8125811101b)
* [Some component example from Eric Elliott](https://gist.github.com/ericelliott/7e05747b891673eb704b#file-react-reusable-component-md)
* [Coding with React like a Game Developer](https://medium.com/@PhilPlckthun/coding-with-react-like-a-game-developer-e39ffaed1643)

**A good rule of thumb in React is that everything that can be expressed as a component, should be.** Think React-Router and DragDropContext wrapping - [Component vs Mixin](https://github.com/acdlite/flummox/blob/v3.5.1/docs/docs/guides/why-flux-component-is-better-than-flux-mixin.md)

```js
// FluxComponent is the wrapper component
render() {
  <div>
    <SiteNavigation />
    <MainContentArea>
      <FluxComponent connectToStores={{}}>
        <BlogPost />
      </FluxComponent>
    </MainContentArea>
    <SiteSidebar />
    <SiteFooter />
  </div>}
```

Components are just state machines. React thinks of UIs as simple state machines. By thinking of a UI as being in various states and rendering those states, it's easy to keep your UI consistent.

DOM is stateful. Input focus and selection, scroll position, etc.

Unintentional side effects are the bane of code reuse. They occur when multiple functions depend on and manipulate the values of the same variables or object properties. In this situation, it becomes much more difficult to refactor code, because your functions assume too much about the state of the program.

> Remember that components don't have to emit DOM. They only need to provide composition boundaries between UI concerns. - See Smart and Dumb components

## Playground

* [component-playground](http://projects.formidablelabs.com/component-playground/)
* [reactview](https://github.com/zackify/reactview)

## Higher-order Components

How do you wrap your components? What does wrapping even mean?

A higher-order component is a function that takes an existing component and returns another component that wraps it. The wrapping component will take care to render the wrapped component and also forwards the props to it, but also adds some useful behavior.

* [Higher-order components?](https://gist.github.com/sebmarkbage/ef0bf1f338a7182b6775)
* [Mixins are dead. Long live composition.](https://medium.com/@dan_abramov/mixins-are-dead-long-live-higher-order-components-94a0d2f9e750)
* [Functional UI and Components as Higher Order Functions](http://blog.risingstack.com/functional-ui-and-components-as-higher-order-functions/)
* [Sideways data loading](https://github.com/facebook/react/issues/3398)
* [See Flummox's custom rendering](https://github.com/acdlite/flummox/blob/v3.5.1/docs/docs/api/fluxcomponent.md#custom-rendering)

React 0.14 switches to [parent-based context](https://github.com/facebook/react/pull/3615).

**Note**: Lambdas are frequently confused with anonymous functions, closures, first-class functions, and higher-order functions. The concepts are all similar, but they mean different things.

Not all lambdas are closures, and not all closures are lambdas. A closure is created when a function references data that is contained outside the function scope. A lambda is a function that is used as a value.

## Render function

Decide everything in the `render()` functions. This means all calculations and conditionals! Make use of helper functions if you can like `renderFullName()` etc. Of course for CPU intensive calculations, use [memoization function](https://lodash.com/docs#memoize).

```js
var memoize = require('lodash.memoize');
```

Data binding is a hack around re-rendering.

### Key

* [Why `key` attribute is important](http://stackoverflow.com/questions/30346348/reactjs-manipulating-state-doesnt-render-child-components-properly)
* [Dynamic children - Why the keys are important](http://blog.arkency.com/2014/10/react-dot-js-and-dynamic-children-why-the-keys-are-important/)

## Libraries

* [**Elemental UI**](http://elemental-ui.com/)
* [**TouchstoneJS**](https://github.com/jedwatson/touchstonejs)
* [Nuka Carousel](http://kenwheeler.github.io/nuka-carousel)
* [React DnD](https://github.com/gaearon/react-dnd)
* [React HotKeys](https://github.com/Chrisui/react-hotkeys)
* [react-aria-menubutton](http://davidtheclark.com/building-react-aria-menubutton/)
* [Griddle - Data Table](http://griddlegriddle.github.io/Griddle/)
* [FixedDataTable](https://facebook.github.io/fixed-data-table/)
* [react-quill - Editor](https://github.com/zenoamaro/react-quill)
* [PropTypes with validator.js](https://github.com/pwmckenna/react-validator-prop-types)
* [react-select](http://jedwatson.github.io/react-select/)
* [react-waypoint - Infinite Scrolling](https://github.com/brigade/react-waypoint)
* [See also here for more react-waypoint](https://medium.com/brigade-engineering/to-infinity-and-beyond-with-react-waypoint-cb5ba46a9150)
* [Autocomplete example](https://gist.github.com/ryanflorence/ba2f061764e0d2895259)
* [react-markdown](https://github.com/rexxars/react-markdown)
* [react-tags](https://github.com/prakhar1989/react-tags)
* [react-icons](http://jxnblk.com/react-icons/)
* [react-web-sdk](https://github.com/necolas/react-web-sdk)

### D3

* [d-Threeact](http://blog.siftscience.com/blog/2015/4/6/d-threeact-how-sift-science-made-d3-react-besties)
* [Integrating D3.js visualizations in a React app](http://nicolashery.com/integrating-d3js-visualizations-in-a-react-app/)
* [Scalable Data Visualization](https://www.youtube.com/watch?v=2ii1lEkIv1s)
* [react-d3](https://github.com/esbullington/react-d3)
* [D3 with React.js](http://busypeoples.github.io/post/d3-with-react-js/)
* [d3-react-squared](https://github.com/bgrsquared/d3-react-squared)