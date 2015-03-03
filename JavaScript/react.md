# React (by Facebook)

Why SPA? Imagine using Facebook where every like and every comment made you refresh the page.

https://github.com/reactjs/react-future/blob/master/09%20-%20Reduce%20State/01%20-%20Declarative%20Component%20Module.js

## Browser Support

If you need IE8 support, you need to include [es5-shim](https://github.com/kriskowal/es5-shim) yourself to make use of several `Array` and `Date` functions.

You are need to include [html5shiv](https://github.com/aFarkas/html5shiv) for IE8.

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
* Re-render everything on every change

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

* [Why React? (2013 articles)](http://facebook.github.io/react/blog/2013/06/05/why-react.html)
* [React Conf roundup](http://facebook.github.io/react/blog/2015/02/18/react-conf-roundup-2015.html)
* [A comprehensive guide to building apps with React](http://tylermcginnis.com/reactjs-tutorial-a-comprehensive-guide-to-building-apps-with-react/)
* [**Why React is awesome**](http://jlongster.com/Removing-User-Interface-Complexity,-or-Why-React-is-Awesome)
* [**Awesome React**](https://github.com/enaqx/awesome-react)
* [60fps mobile web](http://engineering.flipboard.com/2015/02/mobile-web/)
* [React.js and ES6 classes](http://www.reactbook.org/blog/reactjs-es6-classes.html)
* [Takeaways from React.js Conf 2015](http://kevinold.com/2015/01/31/takeaways-from-reactjs-conf-2015.html)
* [Tweet on Michael Jackson's react](https://twitter.com/mjackson/status/466286956989542400)
* [Why React Native matters](http://joshaber.github.io/2015/01/30/why-react-native-matters/)
* [**React Future??**](https://github.com/reactjs/react-future)
* [**React Components - Searchable database**](http://react-components.com/)
* [**Presenting the most over-engineered blog ever - Pretty insightful**](http://jlongster.com/Presenting-The-Most-Over-Engineered-Blog-Ever)
* [**React.js UI framework for hybrid mobile apps**](http://touchstonejs.io/)
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
* [Do it myself or callback](https://gist.github.com/jamesgpearce/53a6fc57677870f93248)
* [React.rb using Opal](https://github.com/zetachang/react.rb)
* [Some useful React utils](https://github.com/facebook/react/tree/master/src/utils)

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

## Webpack

Webpack uses "loaders" to preprocess files while browserify uses "transforms".

* [React with Webpack](http://jslog.com/2014/10/02/react-with-webpack-part-1/)
* [Webpack presentation](https://unindented.github.io/webpack-presentation)
* [react-starterkit](https://github.com/wbkd/react-starterkit)
* [react-starter](https://github.com/webpack/react-starter)
* [webpack_assets](https://github.com/knomedia/webpack_assets)
* [Browserify vs Webpack JS Drama](http://blog.namangoel.com/browserify-vs-webpack-js-drama)
* [Browserify for webpack users](https://gist.github.com/substack/68f8d502be42d5cd4942)
* [Browserify vs Webpack](http://mattdesl.svbtle.com/browserify-vs-webpack)
* [Creating a workflow with WebPack](http://christianalfoni.github.io/javascript/2014/12/13/did-you-know-webpack-and-react-is-awesome.html)
* [Good issue discussion](https://github.com/webpack/webpack/issues/378)
* [Browserify Handbook](https://github.com/substack/browserify-handbook)
* [Single page modules with Webpack](http://dontkry.com/posts/code/single-page-modules-with-webpack.html)

## Component - React Element

In v0.12, you no longer call it as React Component, but rather call it as React Element.

React is functional. Components are just like functions. [They take in `props` and `state` and render HTML](http://facebook.github.io/react/docs/displaying-data.html#components-are-just-like-functions).

```
f(state, props) = UI Fragment

React.createElement('a', {href: 'http://host'}, 'Hello!')

// In JSX
<a href="http://host">Hello!</a>
```

Well-written components don't even need state, so:

`f(props) = UI Fragment`

This introduces the concept of idempotency and immutability.

* [Learn from Web Component gallery](http://customelements.io/)
* [Khan Academy reusable components](http://khan.github.io/react-components/)
* [Touchstone](https://github.com/jedwatson/touchstonejs)
* [material-ui](http://material-ui.com/#/)
* [**Reapp**](http://reapp.io/)
* [hv-react-calendar](https://github.com/HireVue/hv-react-calendar)
* [react-nexus](https://github.com/elierotenberg/react-nexus)

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

Components are state machines. They have properties (determined by their parent) and state (which they can change themselves, perhaps based on user actions).

## Component Events

```
// Enable touch events for mobile devices
React.initializeTouchEvents(true);
```

## JSX

JSX is the key to React and it's purpose is to build composable tree/hierarchical UI.

**Scale by composition** - Build it small, compose it and scale it big.

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

* Props - Constant and immutable. Likely fixed from the on-set. Supplies as component attributes like `<Hello name="mech" />`. Try to use `props` as the source of truth where possible.
* States - Can change. Mutable. You should design your component to not use state as much as possible. Try to keep as many of your components as possible stateless. Use state when you need to respond to user input, a server request or the passage of time. State should contain data that a component's event handlers may change to trigger a UI update (such as JSON request). Think of the UI as a state machine. By thinking of a UI as being in various states and rendering those states, it's easy to keep your UI consistent.

Props and states collectively represent the Model.

The final rendered DOM can have events. And once the events are triggered, the state can change which trigger another render.

If a component need to change and the cause of the change is the component's parent, then the parent can simply change the child's props and re-render.

If a component need to change due to some other component, then it need to use state.

Avoid states as much as possible. Instead push the event handling and state management up toward the top of your component hierarchy.

Note: Spread operator `{...}` deprecate `this.transferPropsTo`
	
* [JSX Spread Attributes](https://gist.github.com/sebmarkbage/07bbe37bc42b6d4aef81)

> A common pattern is to create several stateless components that just render data, and have a stateful component above them in the hierarchy that passes its state to its children via props. The stateful component encapsulates all of the interaction logic, while the stateless components take care of rendering data in a declarative way.

## Refs

* [How should refs work?](https://github.com/facebook/react/issues/3234)

```
handleClick: function() {
  // Wanting to focus is a very example of when to use refs
  this.refs.nameInput.getDOMNode().focus();},

render: function() {
  return(
    <div>
      <input type="text" ref="nameInput" />
      <button onClick={this.handleClick}>Focus</button>
    </div>
  );}
```

Before using `ref`, exhaust your options of using the reactive data flow approach. `ref` is a way to talk to the "backing instance" of the real DOM element.

Refs are a great way to send a message to a particular child instance in a way that would be inconvenient to do via streaming Reactive `props` and `state`. They should, however, not be your go-to abstraction for flowing data through your application. By default, use the Reactive data flow and save `refs` for use cases that are inherently non-reactive.

Refs are automatically destroyed for you. No worrying about memory leaking unless you do something crazy to retain a reference.

Take a moment and think more critically about where `state` should be owned in the component hierarchy.

## CSS

* [Radium - inline styles on React elements](http://projects.formidablelabs.com/radium/)
* [Applying CSS transitions on initial render](https://web-design-weekly.com/2015/02/05/applying-react-js-css-transitions-initial-render/)

## React Mount Runtime

## React Router

* [Ryan Florence's and Michael Jackson's brainchild](https://github.com/rackt/react-router)
* [React nested router](https://www.youtube.com/watch?v=P6xTa3RRzfA#t=2300)

## Flux (CQRS)

Facebook originally build web applications using an MVC architecture. As applications grew in size and complexity development slowed down.

Flux is like a game engine. A single, global dispatcher acts like a event bus to broadcast events and allow other components to registers callbacks to listen for those events.

Because if 2-way data-binding it's not clear how the data flows because it can flow in all directions (including from child components to parents) - this makes it hard to understand the app and understand of impact of model changes in one part of the app on another (seemingly unrelated) part of it.

* Actions - Exports functions that the views can call. Talks to the servers. Builds payloads and sends them to the Dispatcher.
* Dispatcher - Takes a payload from the Actions. Passes payload to Stores via registered callbacks.
* Stores - Application state changes here. Takes payloads from Dispatcher and updates state. Tells anyone that cares (likely Views) when it has changed.

Similar issues for Ember:

```
this.set('controllers.foo.something', 'lol');
this.set('parentView.something', 'lol');

// No computed properties and observer?
// So data flow in one direction? How?
userIsOldEnough: function() {
  return this.get('user.age') == this.get('minAge');}.property('user.age', 'minAge'),

doSomething: function() {
  // stuff}.observes('userIsOldEnough');
```

Like the CSS cascade, if you change some data somewhere in the app, predicting what will happen gets more and more impossible.

```
// Using Facebook own Dispatcher library
var AppDispatcher = new Dispatcher();
```

Some example from [London React Meetup](https://www.youtube.com/watch?v=3wcouW5lXto)

```
// TopBarComponent.jsx
SearchActions.search(query, that.state.hdOnly? 'high' : 'any');

// SearchActions.js
search: function(q, videoDef) {
  AppDispatcher.handleViewAction({
    actionType: Constants.QUERY,
    response: {
      query: q    }  });
  
  Api.searchForVideos(q, videoDef);}

// Api.js
searchForVideos: function(q, videoDef) {
  var key = Constants.SEARCH_SUCCESS;
  
  request
    .get('https://www/googleapis.com/youtube/v3/search')
    (...)
    .end(function() {
      dispatch(key, {items: response.body.items});    });}
	
// SearchStore.js
AppDispatcher.register(function() {
  var action = payload.action;
  
  switch(action.actionType) {
    case Constants.SEARCH_SUCCESS:
      searchReturned(action.response.items);
      SearchStore.emitChange();  }});
```

* [Fluxible](http://fluxible.io/quick-start.html)
* [Flocks.js](https://github.com/StoneCypher/flocks.js)
* [Relieving Backbone Pain with Flux and React](http://dev.hubspot.com/blog/moving-backbone-to-flux-react)
* [Flux for stupid people](http://blog.andrewray.me/flux-for-stupid-people/)
* [Reflux data flow model?](http://blog.krawaller.se/posts/the-reflux-data-flow-model/)
* [Getting to know flux](https://scotch.io/tutorials/getting-to-know-flux-the-react-js-architecture)
* [Simple data flow in React apps using Flux and Backbone](http://www.toptal.com/front-end/simple-data-flow-in-react-applications-using-flux-and-backbone)
* [NuclearMail - An example app with Flux architecture](https://github.com/ianobermiller/nuclearmail)
* [Firefox Hello Desktop](https://blog.mozilla.org/standard8/2015/02/09/firefox-hello-desktop-behind-the-scenes-flux-and-react/)
* [Avoiding event chains in SPA](http://www.code-experience.com/avoiding-event-chains-in-single-page-applications/)
* [RxFlux](https://github.com/fdecampredon/rx-flux)
* [The case for Flux](https://medium.com/@dan_abramov/the-case-for-flux-379b7d1982c6)
* [Learn React and Flux](https://www.youtube.com/watch?v=Pd6Ub7Ju2RM)

## Relay

Replacement for Flux?

* [Unofficial Relay FAQ](https://gist.github.com/wincent/598fa75e22bdfa44cf47?)

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

## Re-render

Re-render the entire application on every change.

* No observers
* No magical data binding
* No model dirty checking
* No `$apply()` or `$digest()`

BUT: You can't just throw out the DOM and rebuild on every update? Lose form state, lost scroll position?

## Director

* [Router for React](https://github.com/flatiron/director)
* [Example of router](https://github.com/andreypopp/react-router-component)

## Mithril

* [Mithril - with Virtual DOM diff](http://lhorie.github.io/mithril/)

## Animation

* [Applying React.js CSS Transitions on initial render](http://web-design-weekly.com/2015/02/05/applying-react-js-css-transitions-initial-render/)

## Examples

* [React tutorial](https://github.com/phaedryx/react-tutorial)
* [5 practical examples for learning React](http://tutorialzine.com/2014/07/5-practical-examples-for-learning-facebooks-react-framework/)
* [Firebase Vulcan - A chrome extension tool](https://github.com/firebase/vulcan)
* [Using TDD with React](https://reactjsnews.com/using-tdd-with-reactjs/)
* [Hacker News App](https://github.com/reapp/hacker-news-app)
* [React Magician](https://github.com/SanderSpies/react-magician)
* [Great.dj](https://github.com/ruiramos/greatdj)
* [Building a multi-step registration form](http://viget.com/extend/building-a-multi-step-registration-form-with-react)

## Companies using React

* [Real life at Codecademy](http://www.infoq.com/articles/reactjs-codecademy)
* [Netflix likes React](http://techblog.netflix.com/2015/01/netflix-likes-react.html)
* [Atlassian - Rebuild HipChat with React](https://developer.atlassian.com/blog/2015/02/rebuilding-hipchat-with-react/)

## Videos

* [Pete Hunt - Rethinking Best Practices](https://www.youtube.com/watch?v=x7cQ3mrcKaY)
* [Pete Hunt - Rethinking Best Practices (updated) 2013](https://www.youtube.com/watch?v=DgVS-zXgMTk)
* [Functional Web Development](https://www.youtube.com/watch?v=Elr_RNt2R5Q)
* [Secret of the Virtual DOM](https://www.youtube.com/watch?v=1h2G20A-AvY)
* [Alt.Net Jan 2015](http://youtu.be/kNVatRjnU7U)
* [Thinking in Components: Building Powerful UIs in React.js](https://www.youtube.com/watch?v=xSGuffp0o6E)

## Twitter

* [@jingc](https://twitter.com/jingc)
* [@Vjeux](https://twitter.com/Vjeux)
* [@sebmarkbage](https://twitter.com/sebmarkbage)
* [@jordwalke](https://twitter.com/jordwalke)
* [@ryanflorence](https://twitter.com/ryanflorence)
* [@browserify](https://twitter.com/browserify)
* [@geteslint](https://twitter.com/geteslint)