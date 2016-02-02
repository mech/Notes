# Components

UI are fundamentally tree. Dealing with REST endpoint introduces complexity. Whatever comes out from that endpoint is typically not in the shape my UI expected.

UI components should define what they need. Use a recursive description (JSON, EDN, Transit, etc). Falcor, JSON Graph.

> Any Cycle.js app can be reused as a component in a larger Cycle.js app.

Cycle.js treat every component as a mini-program of its own. We should also do that in React. Every React component we built, we should treat it as our `main()` program!

Remember, components in React are pretty much like functions, you can spit a function into many and compose or combine in any way you want.

By having taken the data out and put all actions elsewhere, your components should be pure function to take in props and render HTML output. That's it!

* [**Component Brick and Mortar**](https://medium.com/making-internets/component-brick-and-mortar-8bde51899b00#.6mnu551fs)
* [JavaScript Application Architecture on the road to 2015](https://medium.com/google-developers/javascript-application-architecture-on-the-road-to-2015-d8125811101b#.5tt9t7j05)
* [**Component is what you should be doing now for modern UI**](http://derickbailey.com/2015/08/26/building-a-component-based-web-ui-with-modern-javascript-frameworks/)
* [**Building React plugins**](https://nylas.com/blog/react-plugins)
* [Composition](https://medium.com/dev-channel/javascript-application-architecture-on-the-road-to-2015-d8125811101b)
* [Some component example from Eric Elliott](https://gist.github.com/ericelliott/7e05747b891673eb704b#file-react-reusable-component-md)
* [Coding with React like a Game Developer](https://medium.com/@PhilPlckthun/coding-with-react-like-a-game-developer-e39ffaed1643)
* [Truly encapsulated React components?? Avoid classes?](https://github.com/anvaka/maco)
* [Many ways to write React component without using ES6 classes](https://gist.github.com/jquense/47bbd2613e0b03d7e51c)
* [react-class](https://github.com/zippyui/react-class/blob/master/README.md)
* [**Best example of distributed component: react-soundplayer**](http://labs.voronianski.com/react-soundplayer/)
* [End-to-end hypermedia](https://lostechies.com/jimmybogard/2015/07/01/end-to-end-hypermedia-building-a-react-client/)
* [**How to write a React Component**](http://theghostin.me/2015/07/06/how-to-write-a-react-component.html)
* [Controller View Pattern](http://blog.andrewray.me/the-reactjs-controller-view-pattern/)
* [Autobind using core-js](https://github.com/andreypopp/autobind-decorator)
* [Experimenting with higher-order components in React](http://www.bennadel.com/blog/2888-experimenting-with-higher-order-components-in-reactjs.htm)
* [**Interacting with the DOM**](http://jamesknelson.com/react-js-by-example-interacting-with-the-dom/)
* [Recompose - A microcomponentization toolkit for React](https://github.com/acdlite/recompose)

```js
// This is a quick component in file Note.jsx
import React from 'react'
export default () => <div>A very simple component</div>

// To use
<Note />

// Essentially it is just returning a React Element
export default function() {
  return <div>A very simple component</div>;
};
```

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

Try passing in components to other components if you have similar components that have slightly different displays. Or you can use `this.props.children` and put it inside.

### State Machines

Components are just state machines. React thinks of UIs as simple state machines. By thinking of a UI as being in various states and rendering those states, it's easy to keep your UI consistent.

DOM is stateful. Input focus and selection, scroll position, etc.

Unintentional side effects are the bane of code reuse. They occur when multiple functions depend on and manipulate the values of the same variables or object properties. In this situation, it becomes much more difficult to refactor code, because your functions assume too much about the state of the program.

> Remember that components don't have to emit DOM. They only need to provide composition boundaries between UI concerns. - See Smart and Dumb components

A state machine always have initial state as model by `getInitialState`.

## Mistakes and Best Practices

For EVA mistake, the `<Editor>` is too heavy and we did not break it down into even smaller components. The `<Editor>` itself is the DnD container which should not be the case. Whenever there is a drag event, the whole `<Editor>` will be affected and the `<AddPreview>` will be unnecessarily wasted in its rendering effort.

**Always break your component down into single responsibility! And break it down further after that!**

* Components are just views, don't place business logic in it. For example, in a Todo app, if a button creates a Todo item for each click event, you are doing it wrong. A better way is to ship that code off to another object or Action.
* A component shouldn't worry about networking.
* Composable. Self-contained and stateless. In order to be self-contained, the component cannot rely on any other specific components. But of course it can be and must "composed" of other components.
* Component should be stateless. Most components should not maintain its own state. Instead it should defer state-management to a parent container sometimes called container components.
* Container components should not have any styling! Leave it to the presentation components.
* Don't be clever and pass a giant object which is consumed by a child component.
* Don't pass in whole collection object, pass in the `fetch` method as prop and call that prop within `componentWillMount` instead. Then you can do spinner at that component instead of knowing when to spin from the parent.

> Remember, components don't have to emit DOM. They only need to provide composition boundaries between UI concerns.

## Controller View? Container Components? Presentation Components?

* [Container Components](https://medium.com/@learnreact/container-components-c0e67432e005#.ddbg3nt33)
* [Smart and Dumb Components - ViewController](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0)
* [Container Components](https://medium.com/@learnreact/container-components-c0e67432e005)
* [JSX, a year in](https://gist.github.com/chantastic/fc9e3853464dffdb1e3c)

You will often hear React developers refer to controller views - a React component that typically sits at or near the top of a section of the page, which listens to one or more stores for changes in their state. As stores emit change events, the controller view updates with the new state and passes changes down to its children via props.

Controller view must be capable of:

* Publishing actions
* Listening to stores

Creating a good container components will take you awhile to really get the hang of.

If different parts of your app require fetching a model, create one container component for fetching data, then pass that state down into any number of different presentation components. From there, handle any interactions your user might cause.

Container component separates data-fetching and rendering concerns. Or components can't be concerned with both presentation and data-fetching.

> If you decide to split your components into Data Component and Presentational Component, you might as well write functional stateless components.

## Pure Functions

* [babel-plugin-react-pure-components](https://github.com/thejameskyle/babel-plugin-react-pure-components)

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

## Lifecycle

* [Understanding the React Component Lifecycle](http://busypeoples.github.io/post/react-component-lifecycle/)

### Initialization

`defaultProps`

### componentDidMount

Great for setting up interval

```js
componentDidMount() {
  this.interval = setInterval(this.tick, 1000);}

componentWillUnmount() {
  clearInterval(this.interval);}
```

### componentWillUpdate

Great for triggering animation. You cannot use `this.setState()` here!

```js
componentWillUpdate(nextProps, nextState) {
  if (nextProps.visibility) {
    $(??).velocity('slideFadeIn');  } else {
    $(??).velocity('reverse');  }}
```

### componentDidUpdate

* [Scroll position with React](http://blog.vjeux.com/2013/javascript/scroll-position-with-react.html)

Happens every time the element is re-rendered. Good for maintaining scroll position.

```js
componentDidUpdate() {
  var node = this.getDOMNode();
  node.scrollTop = node.scrollHeight;}
```

## Owner-Ownee and Parent-Child

* [Ownership and children in React](http://ctheu.com/2015/02/10/ownership-and-children-in-reactjs/)

Child component receive immutable properties from their parent. Such an relationship is called ownership. Components that set `props` of other components are owners but not necessarily direct parents in terms of DOM structure. This is one-way data flow.

It is important to draw a distinction between ownership and parent-child relationship.

## Playground

* [component-playground](http://projects.formidablelabs.com/component-playground/)
* [reactview](https://github.com/zackify/reactview)
* [react-heatpack: Quick React development with webpack hot reloading](https://github.com/insin/react-heatpack)

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

> HoCs are very similar to higher-order functions. In higher-order functions you pass one function to another function which returns a function. How does that help us? Well, with higher-order components, you pass a component (which as we know is just a function) to another function, which returns a component (again, is just a function).

```js
// This is a higher-order container component accepting
// a presentation component which is a pure-function.
// The container component just handle all the states logic.
const ContainerHoC = function(PresentationComponent) {
  return React.createClass({
    componentDidMount() {
      const success = (notifications) => {
        this.setState({ notifications: notifications });
      };

      $.ajax({ url: '/notifications', success: success });
    },

    onMarkAsRead(id) {},

    render() {
      return (
        <PresentationComponent
          notification={this.state.notifications}
          onMarkAsRead={this.onMarkAsRead} />
      );
    }
  });
}

const Notifications = ContainerHoC(React.createClass({
  renderNotification({notification}) {
    const { id, date, message } = notification;

    return (
      <div>
        <span>{message} - {date}</span>
        <button onClick={this.props.onMarkAsRead.bind(null, id)}>Mark as Read</button>
      </div>
    );
  },

  render() {
    return <div>{this.props.notifications.map(renderNotification)}</div>;
  }
}));

const App = React.createClass({
  render() {
    return <Notifications />
  }
});
```

## Render function

* [react-pure-render](https://github.com/gaearon/react-pure-render)
* [A quick look at rendering whitespace using JSX](http://www.bennadel.com/blog/2880-a-quick-look-at-rendering-white-space-using-jsx-in-reactjs.htm)
* [Is render() being called too many times?](http://www.bennadel.com/blog/2905-setstate-shouldcomponentupdate-and-render-timing-in-reactjs.htm)

It is generally recommended that you funnel all your complex processing through the `render()` method. Event handlers just `setState()` while `render()` is the hub for all of your core logic.

Decide everything in the `render()` functions. This means all calculations and conditionals! Make use of helper functions if you can like `renderFullName()` etc. Of course for CPU intensive calculations, use [memoization function](https://lodash.com/docs#memoize).

```js
var memoize = require('lodash.memoize');
```

Data binding is a hack around re-rendering.

### Key

* [Why `key` attribute is important](http://stackoverflow.com/questions/30346348/reactjs-manipulating-state-doesnt-render-child-components-properly)
* [Dynamic children - Why the keys are important](http://blog.arkency.com/2014/10/react-dot-js-and-dynamic-children-why-the-keys-are-important/)

## Libraries

* [React Components](http://react-components.com/)
* [React Parts](http://react.parts/web)
* [React Rocks](http://react.rocks/)
* [UI Components](https://github.com/facebook/react/wiki/Complementary-Tools#ui-components)
* [Build your own component libraries](https://medium.com/@yamalight/building-modular-javascript-applications-in-es6-with-react-webpack-and-babel-538189cd485f)

---

* [classie](https://github.com/desandro/classie)
* [**React Rocks - A list of useful components**](http://react.rocks/)
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
* [react-onclickoutside](https://github.com/Pomax/react-onclickoutside)
* [react-list-view](https://github.com/Morhaus/react-list-view)
* [react-text-filter](https://github.com/nkbt/react-text-filter)
* [react-popup](https://github.com/minutemailer/react-popup)
* [react-date-picker](http://zippyui.com/react-date-picker/)
* [react-springs](https://github.com/threepointone/react-springs)
* [react-autocomplete](https://github.com/synapsestudios/react-autocomplete)
* [react-pikaday](https://github.com/thomasboyt/react-pikaday)
* [**react-day-picker**](http://www.gpbl.org/react-day-picker/)
* [**Task Calendar**](http://hilary-l.github.io/)
* [react-select-search](https://github.com/tbleckert/react-select-search)
* [react-avatr](https://github.com/studiofrenetic/react-avatr)
* [react-absolute-grid](https://github.com/jrowny/react-absolute-grid)
* [instatype - Simple React Typeahead](https://github.com/gragland/instatype)
* [react-mentions](https://github.com/effektif/react-mentions)
* [react-ux-password-field - Using zxcvbn](https://seethroughtrees.github.io/react-ux-password-field/)
* [**react-soundplayer**](http://labs.voronianski.com/react-soundplayer/)
* [**Amazing constraint-base grid system**](https://github.com/jxnblk/rgx)
* [Spectacle - Presentation with good PDF support](https://github.com/FormidableLabs/spectacle)
* [sliding-window](https://github.com/gre/sliding-window)
* [hv-react-calendar](https://github.com/HireVue/hv-react-calendar)
* [react-nexus](https://github.com/elierotenberg/react-nexus)
* [react-popups](https://github.com/Radivarig/react-popups)
* [Format.js](http://formatjs.io/react/)
* [Joi - Validation](https://github.com/hapijs/joi)
* [react-contextmenu](https://github.com/vkbansal/react-contextmenu)
* [cpr-select](https://github.com/CanopyTax/cpr-select)
* [react-sparklines](https://github.com/borisyankov/react-sparklines)
* [react-progress-button](https://github.com/mathieudutour/react-progress-button)
* [react-table-sorter](https://github.com/bgerm/react-table-sorter-demo)
* [react-ui-tree](http://pqx.github.io/react-ui-tree/example/)
* [react-object-inspector](https://github.com/xyc/react-object-inspector)
* [react-render-visualizer](https://github.com/redsunsoft/react-render-visualizer)
* [react-tunnel](https://github.com/gnoff/react-tunnel)
* [**react-inline-grid**](http://broucz.github.io/react-inline-grid/)
* [trello-react](https://github.com/mgiulio/trello-react)
* [react-hammerjs](https://github.com/JedWatson/react-hammerjs)
* [react-selectize](https://github.com/furqanZafar/react-selectize)
* [react-joyride](https://github.com/gilbarbara/react-joyride)
* [react-text-trail](https://github.com/trevorsenior/react-text-trail)
* [react-autosuggest](https://github.com/moroshko/react-autosuggest)
* [Chosen](http://harvesthq.github.io/chosen/)
* [react-data-grid](https://github.com/adazzle/react-data-grid)
* [react-list - Infinite scroll](https://github.com/orgsync/react-list)
* [react-input-slider](https://github.com/wangzuo/react-input-slider)
* [react-fa - Can study it](https://github.com/andreypopp/react-fa)

### Pagination

* [react-paginator-box](https://github.com/abaddonGIT/react-paginator-box)
* [react-paginate](https://github.com/Mosho1/react-paginate)
* [react-pagify](http://bebraw.github.io/react-pagify/)
* [react-paginate](https://github.com/eliseumds/react-paginate)

### D3 or just Victory.js

* [**Victory.js**](https://github.com/FormidableLabs/victory)
* [d-Threeact](http://blog.siftscience.com/blog/2015/4/6/d-threeact-how-sift-science-made-d3-react-besties)
* [Integrating D3.js visualizations in a React app](http://nicolashery.com/integrating-d3js-visualizations-in-a-react-app/)
* [Scalable Data Visualization](https://www.youtube.com/watch?v=2ii1lEkIv1s)
* [react-d3](https://github.com/esbullington/react-d3)
* [D3 with React.js](http://busypeoples.github.io/post/d3-with-react-js/)
* [d3-react-squared](https://github.com/bgrsquared/d3-react-squared)
* [React and D3 Part 1: Layout](http://formidablelabs.com/blog/2015/05/21/react-d3-layouts/)
* [Pyxley: Python Powered Dashboards](http://multithreaded.stitchfix.com/blog/2015/07/16/pyxley/)
* [On D3, React, and a little bit of Flux](https://medium.com/@sxywu/on-d3-react-and-a-little-bit-of-flux-88a226f328f3)
* [Visualizing data in React.js](https://www.codementor.io/reactjs/tutorial/visualizing-data-react-js-cross-filtering-hover-interaction-histogram)
* [**Building D3-inspired charts with React**](http://blog.scottlogic.com/2015/09/03/d3-without-d3.html)
* [D3 with React the right way](http://oli.me.uk/2015/09/09/d3-within-react-the-right-way/)

## Integrate with jQuery

```js
var Datepicker = React.createClass({
  render() {
    return React.createElement('input', {type: 'text'});  }
  	
  runJQ() {
    $(React.findDOMNode(this)).datepicker(this.props);  }  
  componentDidMount() {
    this.runJQ();  }
  
  componentDidUpdate(prevProps) {
    if (!propsEqual(this.props, prevProps)) {
    	this.runJQ();    }  }});
```

```js
$.fn.react = function(component, props) {
  React.render(
    React.createElement(component, props),
    this.get(0)
  );};

$('body').react(TodoList, {items: ['Get milk']});
```

## Examples

```js
class link { // No need extends?
  render() {
    var className = this.props.highlighted ? 'highlight' : '';
    var children = this.props.children;
    
    return (
      <a
        className={'link-button ' + className}
        href={this.props.href}
        rel="prefetch">
        {children}
      </a>
    );
  }
}

// Use it as
<Link highlighted />
```