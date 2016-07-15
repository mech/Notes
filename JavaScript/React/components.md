# Components

If you go declarative, you have composability.

> Basically treat the app as a game engine, and use a lot of the same techniques.
> 
> You can easily build completely isolated, reusable, and composable UI components. Nested views just become a natural extension of the way React works.

UI are fundamentally tree. Dealing with REST endpoint introduces complexity. Whatever comes out from that endpoint is typically not in the shape my UI expected.

UI components should define what they need. Use a recursive description (JSON, EDN, Transit, etc). Falcor, JSON Graph.

> Any Cycle.js app can be reused as a component in a larger Cycle.js app.

Cycle.js treat every component as a mini-program of its own. We should also do that in React. Every React component we built, we should treat it as our `main()` program!

Remember, components in React are pretty much like functions, you can spit a function into many and compose or combine in any way you want.

By having taken the data out and put all actions elsewhere, your components should be pure function to take in props and render HTML output. That's it!

* [**A Modular Approach to UI Problem Solving**](http://davidtheclark.com/modular-approach-to-interface-components/)
* [**React reconciliation**](http://blog.testdouble.com/posts/2016-02-01-react-reconciliation.html)
* [**React Components, Elements, and Instances**](https://facebook.github.io/react/blog/2015/12/18/react-components-elements-and-instances.html)
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

* Components are just views, don't place business logic in it. For example, in a Todo app, if a button creates a Todo item for each click event, you are doing it wrong. A better way is to ship that code off to another object or Action. Searching through components to determine behaviour is not really something we should be doing anyway.
* A component shouldn't worry about networking.
* Composable. Self-contained and stateless. In order to be self-contained, the component cannot rely on any other specific components. But of course it can be and must "composed" of other components.
* Component should be stateless. Most components should not maintain its own state. Instead it should defer state-management to a parent container sometimes called container components.
* Container components should not have any styling! Leave it to the presentation components.
* Don't be clever and pass a giant object which is consumed by a child component.
* Don't pass in whole collection object, pass in the `fetch` method as prop and call that prop within `componentWillMount` instead. Then you can do spinner at that component instead of knowing when to spin from the parent.

> Remember, components don't have to emit DOM. They only need to provide composition boundaries between UI concerns.

How small should a component be? Take a look at this:

```js
const LatestPostsComponent = props => (
  <section>
    <h1>Latest posts</h1>
    { props.posts.map(post => <PostPreview key={post.slug} post={post} />) }
  </section>
);
```

## Controller View? Container Components? Presentation Components?

> My biggest pet peeve is it is harder to compose, reuse, nest, and generally move around container components because there are two independent hierarchies at the same time (views and reducers). It is also not entirely clear how to write reusable components that either use Redux as implementation detail or want to provide Redux-friendly interface. (There are different approaches.) I’m also not impressed about every action having to go “all the way” upwards instead of short-circuiting somewhere. In other words, I would like to see something like React local state model but backed by reducers, and I would like it to be highly practical and tuned to real use cases rather than a beautiful abstraction. - [Issue#1385](https://github.com/reactjs/redux/issues/1385)

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

## Lifecycle

* [Understanding the React Component Lifecycle](http://busypeoples.github.io/post/react-component-lifecycle/)

### Initialization

`defaultProps`

### componentWillMount

Invoked once, **both on the client and server**, immediately before the initial rendering occurs.

### componentDidMount

**Invoked only on the client!** Great for setting up interval.

**Warning:** Be careful that once it has mounted and if the `props` is going to change, this lifecycle methods won't be invoked again, please see `componentWillReceiveProps`

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

Happens every time the element is re-rendered. Good for maintaining scroll position. You can do paranoid validation here also, but admittedly is not needed (like text length limiting)

```js
componentDidUpdate() {
  var node = this.getDOMNode();
  node.scrollTop = node.scrollHeight;}

// Limiting the text should really be done at event handler, but
// here we are just being paranoid and do additional validation
componentDidUpdate(oldProps, oldState) {
  if (this.state.text.length > 3) {
    this.replaceState(oldState);
  }
}
```

## Owner-Ownee and Parent-Child

* [Ownership and children in React](http://ctheu.com/2015/02/10/ownership-and-children-in-reactjs/)

Child component receive immutable properties from their parent. Such an relationship is called ownership. Components that set `props` of other components are owners but not necessarily direct parents in terms of DOM structure. This is one-way data flow.

It is important to draw a distinction between ownership and parent-child relationship.

## Playground

* [component-playground](http://projects.formidablelabs.com/component-playground/)
* [reactview](https://github.com/zackify/reactview)
* [react-heatpack: Quick React development with webpack hot reloading](https://github.com/insin/react-heatpack)

## Render function

* [Rendering with React](https://www.youtube.com/watch?v=7S8v8jfLb1Q)

1. `render` should be idempotent
2. `render` should not cause side-effects.
3. `render` must be pure, meaning it does not change the state or modify the DOM output.
4. You can return `null` or `false` if you do not want to render anything at all.

You must remember that the result returned from `render()` is not the actual DOM or any action being taking place. If you have a `console.log()` in your `render()`, it will be printed on the console, but do not make the mistake of thinking that your `render()` has been completed, it has not! The returned virtual DOM is just sitting there waiting for its chance to truly render on the screen for the next available clock tick (RAF). While waiting for the next clock tick, React will diff the virtual DOM to determine if it even need to update the real DOM or not.

---

* [**React Pure Render Performance Anti-Pattern**](https://medium.com/@esamatti/react-js-pure-render-performance-anti-pattern-fb88c101332f#.pazfuwypa)
* [react-pure-render](https://github.com/gaearon/react-pure-render)
* [A quick look at rendering whitespace using JSX](http://www.bennadel.com/blog/2880-a-quick-look-at-rendering-white-space-using-jsx-in-reactjs.htm)
* [Is render() being called too many times?](http://www.bennadel.com/blog/2905-setstate-shouldcomponentupdate-and-render-timing-in-reactjs.htm)

It is generally recommended that you funnel all your complex processing through the `render()` method. Event handlers just `setState()` while `render()` is the hub for all of your core logic.

Decide everything in the `render()` functions. This means all calculations and conditionals! Make use of helper functions if you can like `renderFullName()` etc. Of course for CPU intensive calculations, use [memoization function](https://lodash.com/docs#memoize).

```js
var memoize = require('lodash.memoize');
```

Data binding is a hack around re-rendering.

### Re-rendering and `shouldComponentUpdate`

* [Optimizing with `shouldComponentUpdate`](http://buildwithreact.com/article/optimizing-with-shouldcomponentupdate)

When Parent need to re-render, it will also automatically re-render any Child. This is the most basic functionality of React re-rendering logic.

> When `setState` is called, the component rebuilds the virtual DOM for its children. If you call `setState` on the root element, then the entire React app is re-rendered. All the components, even if they didn't change, will have their render method called. This may sound scary and inefficient but in practice, this works fine because we're not touching the actual DOM.
>
> Another important point is that when writing React code, you usually don't call `setState` on the root node every time something changes. You call it on the component that received the change event or couple of components above. You very rarely go all the way to the top. This means that changes are localized to where the user interacts

If you do not want Children to be re-render, you have to use Immutable and compare props at `shouldComponentUpdate`.

Note: `forceUpdate` skip `shouldComponentUpdate`, essentially a full hard refresh.

Once again:

When each component re-renders the children it renders re-render too (unless prevented by `shouldComponentUpdate`).

Re-rendering on every change is impractical unless *all* your component have very strict `shouldComponentUpdate` implementations like those provided by Om.

**Note:** PureRender/`shouldComponentUpdate` really is considered an escape hatch for performance and is not necessarily something that should be blindly applied to every component.

### Key

* [Why `key` attribute is important](http://stackoverflow.com/questions/30346348/reactjs-manipulating-state-doesnt-render-child-components-properly)
* [Dynamic children - Why the keys are important](http://blog.arkency.com/2014/10/react-dot-js-and-dynamic-children-why-the-keys-are-important/)

## Libraries

See http://davidtheclark.com/modular-approach-to-interface-components/ for a nice way to modularize other libraries.

* [**React Widget**](https://jquense.github.io/react-widgets/docs/#/)
* [Strand](https://mediamath.github.io/strand/)
* [React Components](http://react-components.com/)
* [React Parts](http://react.parts/web)
* [React Rocks](http://react.rocks/)
* [UI Components](https://github.com/facebook/react/wiki/Complementary-Tools#ui-components)
* [Build your own component libraries](https://medium.com/@yamalight/building-modular-javascript-applications-in-es6-with-react-webpack-and-babel-538189cd485f)
* [react-component](https://github.com/cd-fe/react-component)
* [React Toolbox with Material Design](http://react-toolbox.com/#/)

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
* [react-select](http://jedwatson.github.io/react-select/)
* [react-waypoint - Infinite Scrolling](https://github.com/brigade/react-waypoint)
* [See also here for more react-waypoint](https://medium.com/brigade-engineering/to-infinity-and-beyond-with-react-waypoint-cb5ba46a9150)
* [Autocomplete example](https://gist.github.com/ryanflorence/ba2f061764e0d2895259)
* [react-markdown](https://github.com/rexxars/react-markdown)
* [react-tags](https://github.com/prakhar1989/react-tags)
* [react-icons](http://jxnblk.com/react-icons/)
* [react-web-sdk](https://github.com/necolas/react-web-sdk)
* [**react-onclickoutside**](https://github.com/Pomax/react-onclickoutside)
* [react-list-view](https://github.com/Morhaus/react-list-view)
* [react-text-filter](https://github.com/nkbt/react-text-filter)
* [react-popup](https://github.com/minutemailer/react-popup)
* [react-date-picker](http://zippyui.com/react-date-picker/)
* [react-springs](https://github.com/threepointone/react-springs)
* [react-autocomplete](https://github.com/synapsestudios/react-autocomplete)
* [react-pikaday](https://github.com/thomasboyt/react-pikaday)
* [**react-day-picker**](http://www.gpbl.org/react-day-picker/)
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
* [react-nexus](https://github.com/elierotenberg/react-nexus)
* [react-popups](https://github.com/Radivarig/react-popups)
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
* [react-rangeslider](https://github.com/whoisandie/react-rangeslider)
* [react-fa - Can study it](https://github.com/andreypopp/react-fa)
* [react-matchmedia-connect](https://github.com/malte-wessel/react-matchmedia-connect)
* [React-Spreadsheet-Component](https://github.com/felixrieseberg/React-Spreadsheet-Component)
* [react-xhr-uploader](https://rma-consulting.github.io/react-xhr-uploader/)
* [react-infinite](https://github.com/seatgeek/react-infinite)
* [react-notification](https://github.com/pburtchaell/react-notification)
* [react-tabs](https://github.com/reactjs/react-tabs)
* [react-tab-panel](https://github.com/zippyui/react-tab-panel)
* [react-swipe-views](https://github.com/damusnet/react-swipe-views)
* [kendo-react-inputs](https://github.com/telerik/kendo-react-inputs)
* [simple-react-button](https://github.com/cdrpro/simple-react-button)
* [react-hoverbox](https://github.com/wix/react-hoverbox)
* [react-autosuggest](https://github.com/moroshko/react-autosuggest)

### Date-picker and Calendar

* [A very nice time picker](http://dapperdeveloper.com/2015/10/19/tutorial-build-a-time-picker-with-react-js/)
* [**Task Calendar**](http://hilary-l.github.io/)
* [hv-react-calendar](https://github.com/HireVue/hv-react-calendar)
* [rc-calendar](http://react-component.github.io/calendar/)
* [**DZDateTimePicker**](https://github.com/DZNS/DZDateTimePicker)

### Drag and Drop

* [react-anything-sortable](https://github.com/jasonslyvia/react-anything-sortable)
* [react-draggable](https://github.com/mzabriskie/react-draggable)

### Resizable

* [How to make a DIV with draggable](http://stackoverflow.com/questions/17855401/how-do-i-make-a-div-width-draggable)
* [react-sizeme](https://github.com/ctrlplusb/react-sizeme)

### Validation

* [PropTypes with validator.js](https://github.com/pwmckenna/react-validator-prop-types)
* [Joi - Validation](https://github.com/hapijs/joi)
* [Format.js](http://formatjs.io/react/)

### Pagination & Infinite scroll

* [react-ingrid](https://github.com/babotech/react-ingrid)
* [react-paginator-box](https://github.com/abaddonGIT/react-paginator-box)
* [react-paginate](https://github.com/Mosho1/react-paginate)
* [react-pagify](http://bebraw.github.io/react-pagify/)
* [react-paginate](https://github.com/eliseumds/react-paginate)

## Text editor

* [react-rte](https://github.com/sstur/react-rte)

### D3 or just Victory.js

Just use Victory.js for new project.

* [react-vis from Uber](https://github.com/uber/react-vis)
* [**Victory.js**](https://github.com/FormidableLabs/victory)
* [Recharts = React + Charts](http://recharts.org/)
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
* [D3 and React - the future of charting components?](http://10consulting.com/2014/02/19/d3-plus-reactjs-for-charting/)
* [D3 for math + ReactJS for rendering](http://formidable.com/blog/2015/05/21/react-d3-layouts/)

```js
import React, { Component } from 'react';
import d3 from 'd3';

export default class Sparkline extends Component {
  render() {
    const { width, data, height, interpolation } = this.props;

    const x = d3.scale.linear()
      .range([0, width])
      .domain(d3.extent(data, (d, i) => i))

    const y = d3.scale.linear()
      .range([height, 0])
      .domain([0, 100])

    const line = d3.svg.line()
      .x((d, i) => x(i))
      .y((d) => y(d))
      .interpolate(interpolation)

    return (
      <svg className="sparkline" width={width} height={height}>
        <path d={line(data)} />
      </svg>
    );
  }
}
```
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

* [Create auto-complete component](http://hackingbeauty.com/create-a-reactjs-component-part1/)

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