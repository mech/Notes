# React (by Facebook)

## People

* Christopher Chedeau
* Tom Occhino

> "Given the extremely tight coupling between the template and it's context (a controller/component), the concerns are the same, and splitting the DOM into a template is an arbitrary separation of technologies rather than a legit separation of concerns." - Hence in React, everything is a component. There is no template. Just define a `render` function.

---
> "The React alternative is programming like you are throwing away your entire component and re-rendering it every time because it is simpler and easier to reason about. Event-based and data binding approaches frequently run into timing problems keeping track of which callback gets called first as well as make it difficult to understand how a small change in state will affect performance."

http://facebook.github.io/react/index.html

---
> Mutable state and 2-way bindings made it hard to reason about.

**React replaces an imperative mutating API with a declarative one that favors immutability.**

Declarative -> Predictable -> Confidence -> Reliability

* Components rather than templates
* State is hard to manage
* DOM insertion is painful!
* No controller in React
* No template in React
* The single source of truth is all at the Component
* All the stuffs that live on the Ember controller live in React component
* Developed by Facebook
* Predictable Web Framework
* Expressive and modular
* Just the "V"
* Component ownership pattern (iOS-like?) - Top-level components, higher hierarchy tell children how they should render.
* Components can be stateful
* Encouraged 1-way data flow
* Highly performant
* Good practices of creating very very small components

React don't like 2-way data binding and template. It like one-way data flow and no template.

```
f(d) = v
f(d`) = v`
diff(v, v`) = changes
diff(v`, v) = undo # Go back in time, getting undo for free

d = data
v = virtual DOM
```

`renderComponentToString() // Isomorphic applications`

The initial HTML can be generated on the server. React handles the "view" but not with templates in the usual sense. React views are not dumb, they are "virtual DOM".

Using a [difference algorithm](http://calendar.perfplanet.com/2013/diff/) to calculate the fewest number of steps required to render each state.

Render (and re-render) a view hierarchy to any sort of backend you want. It is DOM agnostic.

What makes UI so hard? State changing over time is evil.
Model your UI as pure function.

* [**Why React is awesome**](http://jlongster.com/Removing-User-Interface-Complexity,-or-Why-React-is-Awesome)
* [Takeaways from React.js Conf 2015](http://kevinold.com/2015/01/31/takeaways-from-reactjs-conf-2015.html)
* [Tweet on Michael Jackson's react](https://twitter.com/mjackson/status/466286956989542400)
* [Why React Native matters](http://joshaber.github.io/2015/01/30/why-react-native-matters/)
* [**React Future??**](https://github.com/reactjs/react-future)
* [**React Components - Searchable database**](http://react-components.com/)
* [**Presenting the most over-engineered blog ever - Pretty insightful**](http://jlongster.com/Presenting-The-Most-Over-Engineered-Blog-Ever)
* [**React.js UI framework for hybrid mobile apps**](http://touchstonejs.io/)
* [Netflix likes React](http://techblog.netflix.com/2015/01/netflix-likes-react.html)
* [Pete Hunt: High performance functional programming with React and Meteor](http://www.youtube.com/watch?v=qqVbr_LaCIo)
* [**React: RESTful UI Rendering**](https://www.youtube.com/watch?v=IVvHPPcl2TM)
* [Building robust web apps with React](http://maketea.co.uk/2014/03/05/building-robust-web-apps-with-react-part-1.html)
* [Using react with browserify](https://medium.com/publish-what-you-learn/a1ea2dd606b)
* [Example](https://github.com/aslansky/react-stack-playground)
* [Gulpfile example for reactify](https://github.com/callum/tool-test/blob/master/gulpfile.js)
* [Client side layout engines: React vs FruitMachine](http://labs.ft.com/2013/10/client-side-layout-engines-react-vs-fruitmachine/)
* [React vs Angular](http://stackoverflow.com/questions/21111217/react-vs-angular)
* [The question of having DOM in JavaScript](https://twitter.com/jo_liss/status/459101670656708608)
* [Faster AngularJS rendering with ReactJS](http://www.williambrownstreet.net/blog/2014/04/faster-angularjs-rendering-angularjs-and-reactjs/)
* [Improving AngularJS long list rendering performance using ReactJS](http://mono.software/posts/Improving-AngularJS-long-list-rendering-performance-using-ReactJS/)
* [Quickcoin nice React programming](http://quickcoin.co/tech/responsive-design-and-multi-platform-live-coding/)
* [Why you might not need MVC with React.js](http://www.code-experience.com/why-you-might-not-need-mvc-with-reactjs/)
* [Introduction to React.js](https://vimeo.com/106261417)
* [Goya](https://github.com/jackschaedler/goya)
* [Rendering React Components on the server](http://www.crmarsh.com/react-ssr/)
* [Om - too mind blow!](https://github.com/swannodette/om)
* [Facebook's Immutable.js](https://github.com/facebook/immutable-js)
* [React.js and how does it fit in with everything else?](http://www.funnyant.com/reactjs-what-is-it/)
* [Pete Hunt response to side-by-side AngularJS comparison](http://www.quora.com/Pete-Hunt/Posts/Facebooks-React-vs-AngularJS-A-Closer-Look)
* [Isomorphic React app with Rails](https://medium.com/@olance/isomorphic-reactjs-app-with-ruby-on-rails-part-1-server-side-rendering-8438bbb1ea1c)
* [React for stupid people](http://blog.andrewray.me/reactjs-for-stupid-people/)
* [Creating a workflow with WebPack](http://christianalfoni.github.io/javascript/2014/12/13/did-you-know-webpack-and-react-is-awesome.html)

```
var gulp = require('gulp');
var browserify = require('gulp-browserify]');
var concat = require('gulp-concat');

gulp.task('scripts', function() {
  gulp.src(['./src/main.js'])
      .pipe(browserify({
        transform: ['reactify']
      }))
      .pipe(concat('main.js'))
      .pipe(gulp.dest('./build'));
});
```

## Component - React Element

In v0.12, you no longer call it as React component, but rather call it as React Element.

* [Learn from Web Component gallery](http://customelements.io/)
* [Khan Academy reusable components](http://khan.github.io/react-components/)
* [Touchstone](https://github.com/jedwatson/touchstonejs)
* [material-ui](http://material-ui.com/#/)

```
React.renderComponent();   // Deprecated
React.render();            // Use this

React.isValidComponent();  // Deprecated
React.isValidElement();    // Use this

React.PropTypes.component  // Deprecated
React.PropTypes.element    // Use this

React.PropTypes.renderable // Deprecated
React.PropTypes.node       // Use this
```

Components are hierarchical. Without this you won't be able to represent HTML. To access the children:

`this.props.children`

## Component Events

```
// Enable touch events for mobile devices
React.initializeTouchEvents(true);
```

## JSX

Note: In v0.12, no more `/** @jsx React.DOM */`

```
<Component /> === React.createElement(Component)
```

Solved cross-site scripting?

Allow to create composite component. Component is the proper separation of concern for us. Not the 3-legged stool of HTML, CSS and JavaScript. But a single JavaScript all the way. More composable?

* [Live JSX compiler for testing](https://facebook.github.io/react/jsx-compiler.html)
* [JSX: E4X The Good Parts](http://blog.vjeux.com/2013/javascript/jsx-e4x-the-good-parts.html)
* [Draft: JSX Specification](http://facebook.github.io/jsx/)

```
class HelloMessage extends React.Component {
  tick() {
    this.setState({count: this.state.count + 1});  }
  
  render() {
    // No autowinding for tick() in v0.13.0
    return <div onClick={this.tick.bind(this)}>Hello {this.props.name}</div>;  }}
	
React.render(<HelloMessage name="mech" />, mountNode);

// Equivalent to this old ES3 module pattern?
function HellMessage(initialProps) {
  return {
    state: { value: initialProps.initialValue },
    render: function() {
      return <div>Hello {this.state.value}</div>;    }  };}
```

## Props and States

In Backbone, you are coding imperatively to specify when something changes, certain things should happen through it various view events setup.

In React, things are more declarative. You specify how your UI should look like at the `render()` and through `props` and `states` changes, the UI will change.

Declarative style require developer to think through at the start how the whole component UI look like and how they will interact.

```
---------     ---------
| Props |     | State |
---------     ---------
     +           +
      ----------
      | Render |
      ----------
           |
        -------   
        | DOM |
        -------
```

* Props - Constant and immutable. Likely fixed from the on-set. Supplies as component attributes like `<Hello name="mech" />`
* States - Can change. Mutable. You should design your component to not use state as much as possible.

Props and states collectively represent the Model.

The final rendered DOM can have events. And once the events are triggered, the state can change which trigger another render.

If a component need to change and the cause of the change is the component's parent, then the parent can simply change the child's props and re-render.

If a component need to change due to some other component, then it need to use state.

Avoid states as much as possible. Instead push the event handling and state management up toward the top of your component hierarchy.

Note: Spread operator `{...}` deprecate `this.transferPropsTo`
	
* [JSX Spread Attributes](https://gist.github.com/sebmarkbage/07bbe37bc42b6d4aef81)

> A common pattern is to create several stateless components that just render data, and have a stateful component above them in the hierarchy that passes its state to its children via props. The stateful component encapsulates all of the interaction logic, while the stateless components take care of rendering data in a declarative way.
	
## React Mount Runtime

## React Router

* [Ryan Florence's and Michael Jackson's brainchild](https://github.com/rackt/react-router)

## Flux

Flux is like a game engine. A single, global dispatcher acts like a event bus to broadcast events and allow other components to registers callbacks to listen for those events.

```
// Using Facebook own Dispatcher library
var AppDispatcher = new Dispatcher();
```

* [Fluxible](http://fluxible.io/quick-start.html)
* [Flocks.js](https://github.com/StoneCypher/flocks.js)
* [Relieving Backbone Pain with Flux and React](http://dev.hubspot.com/blog/moving-backbone-to-flux-react)
* [Flux for stupid people](http://blog.andrewray.me/flux-for-stupid-people/)
* [Reflux data flow model?](http://blog.krawaller.se/posts/the-reflux-data-flow-model/)
* [Getting to know flux](https://scotch.io/tutorials/getting-to-know-flux-the-react-js-architecture)
* [Simple data flow in React apps using Flux and Backbone](http://www.toptal.com/front-end/simple-data-flow-in-react-applications-using-flux-and-backbone)
* [NuclearMail - An example app with Flux architecture](https://github.com/ianobermiller/nuclearmail)

## Composition (Composable)

Combine *simple* functions to build more *complicated* ones. One way to manage complexity.

Just build simple interfaces. Makes it easier to predict what will happen.

How React enable nested component? By having a clear Input (properties) and Output (render() callback function), nested components is a very common outcome.

## Idempotence

Certain operations that can be applied multiple times without changing the result beyond the initial application.

Easy to predict output for a given input. Immutability gets you idempotence for free.

## Virtual DOM

Dirty-checking model can be slow. Virtual DOM is using tree, as we all know, tree can be fast.

DOM operation is very expensive! Because modifying the DOM will also apply and calculate CSS styles, layouts, etc.

* [A Virtual DOM and diffing algorithm](https://github.com/Matt-Esch/virtual-dom)
* [Issues/3](https://github.com/Matt-Esch/virtual-dom/issues/3)

## Director

* [Router for React](https://github.com/flatiron/director)
* [Example of router](https://github.com/andreypopp/react-router-component)

## Mithril

* [Mithril - with Virtual DOM diff](http://lhorie.github.io/mithril/)

## Examples

* [React tutorial](https://github.com/phaedryx/react-tutorial)

## Videos

* [Pete Hunt - Rethinking Best Practices](https://www.youtube.com/watch?v=x7cQ3mrcKaY)
* [Pete Hunt - Rethinking Best Practices (updated) 2013](https://www.youtube.com/watch?v=DgVS-zXgMTk)
* [Functional Web Development](https://www.youtube.com/watch?v=Elr_RNt2R5Q)
* [Secret of the Virtual DOM](https://www.youtube.com/watch?v=1h2G20A-AvY)
* [Alt.Net Jan 2015](http://youtu.be/kNVatRjnU7U)
* [Thinking in Components: Building Powerful UIs in React.js](https://www.youtube.com/watch?v=xSGuffp0o6E)