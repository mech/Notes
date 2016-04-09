# Flux (CQRS)

**How to deal with data?** This is really up to you.

* Use props and state; store much of the state in the root component. I typically do it this way unless I have reasons not to.
* Need cross, unrelated component communication? (think Facebook notification bar and how the number goes up and down) Use an event emitter like `asyncly/EventEmitter2`
* Need to share state/data across a fairly big app? Use Flux. But Flux is overkill for most small-scale apps/widgets.

> In order to keep modules decoupled from each other, it's helpful to think of events as reports of what has happened, rather than commands for what should happen next. Other modules can listen for the events they care about and decide what to do next on their own.

Facebook originally build web applications using an MVC architecture. As applications grew in size and complexity development slowed down.

Flux is like a game engine. A single, global dispatcher acts like a event bus to broadcast events and allow other components to registers callbacks to listen for those events.

Because if 2-way data-binding it's not clear how the data flows because it can flow in all directions (including from child components to parents) - this makes it hard to understand the app and understand of impact of model changes in one part of the app on another (seemingly unrelated) part of it.

Tightly coupled method invocations are transformed into loosely coupled data flow by actions.

* Actions - Exports functions that the views can call. Talks to the servers. Builds payloads and sends them to the Dispatcher.
* Dispatcher - Takes a payload from the Actions. Passes payload to Stores via registered callbacks.
* Stores - Application state changes here. Takes payloads from Dispatcher and updates state. Tells anyone that cares (likely Views) when it has changed.

Similar issues for Ember:

```js
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

```js
// Using Facebook own Dispatcher library
var AppDispatcher = new Dispatcher();
```

Some example from [London React Meetup](https://www.youtube.com/watch?v=3wcouW5lXto)

```js
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
* [Beyond the to-do app: Writing complex apps using Flux](https://madebymany.com/blog/beyond-the-to-do-app-writing-complex-applications-using-flux-react-js)
* [**A cartoon guide to Flux**](https://code-cartoons.com/a-cartoon-guide-to-flux-6157355ab207#.i8mmjizk3)
* [**React+Flux can do in just 137 lines what jQuery can do in 10**](http://swizec.com/blog/reactflux-can-do-in-just-137-lines-what-jquery-can-do-in-10/swizec/6740)
* [Which Flux should I use with React?](http://jamesknelson.com/which-flux-implementation-should-i-use-with-react/)
* [React + Flux backed by Rails API](https://fancypixel.github.io/blog/2015/01/28/react-plus-flux-backed-by-rails-api/)
* [Simplifying Flux using CSP FRP](https://github.com/juliangamble/simplifying-flux-using-csp-frp)
* [**The React.js Way: Flux Architecture with Immutable.js**](https://blog.risingstack.com/the-react-js-way-flux-architecture-with-immutable-js/)
* [**Flux: Getting data from an API**](https://medium.com/@tribou/flux-getting-data-from-an-api-b73b6478c015)
* [**Why make a framework on React and Flux?**](http://gunnariauvinen.com/why-make-a-framework-on-react-and-flux/)
* [**Flux solutions compared by example**](http://pixelhunter.me/post/110248593059/flux-solutions-compared-by-example)
* [**Flux from scratch**](http://ryanfunduk.com/articles/flux-from-scratch/)
* [**The case for Flux**](https://medium.com/@dan_abramov/the-case-for-flux-379b7d1982c6)
* [**Flux: Actions and the Dispatcher**](http://facebook.github.io/react/blog/2014/07/30/flux-actions-and-the-dispatcher.html)
* [**Flux comparison**](https://github.com/voronianski/flux-comparison)
* [Stores are not models](https://medium.com/@jetupper/hello-react-js-b87c63526e3a)
* [Facebook flux-chat example](https://github.com/facebook/flux/tree/master/examples/flux-chat/js)
* [**Cortex - centrally managing data with React**](https://github.com/mquan/cortex/)
* [Flocks.js](http://www.flocks.rocks/what_is_flocks.html)
* [Writing complex app using Flux and React](http://madebymany.com/blog/beyond-the-to-do-app-writing-complex-applications-using-flux-react-js)
* [What is the Flux application architecture?](https://medium.com/brigade-engineering/what-is-the-flux-application-architecture-b57ebca85b9e)
* [**flux-react-router-example**](https://github.com/gaearon/flux-react-router-example/)
* [React and Flux interview](http://ianobermiller.com/blog/2014/09/15/react-and-flux-interview/)
* [The React.js Way: Flux Architecture with Immutable.js](http://blog.risingstack.com/the-react-js-way-flux-architecture-with-immutable-js/)
* [React + Flux backed by Rails API](http://fancypixel.github.io/blog/2015/01/28/react-plus-flux-backed-by-rails-api/)
* [**FluxRecorder - Record and replay actions**](https://github.com/nextminds/FluxRecorder/)
* [Flux in practice](https://medium.com/@garychambers108/flux-in-practice-ec08daa9041a)
* [Understanding Flux](https://medium.com/@garychambers108/understanding-flux-f93e9f650af7)
* [React Reflux example](https://ochronus.com/react-reflux-example/)
* [Normalizes nested JSON according to schema for Flux Stores](https://github.com/gaearon/normalizr)
* [Flux architecture step by step](http://blogs.atlassian.com/2014/08/flux-architecture-step-by-step/)
* [Flux in Depth. Overview and Components](http://blog.mgechev.com/2015/05/15/flux-in-depth-overview-components/)
* [???](https://github.com/gaearon/redux/issues/6)
* [Event bus vs `this.props`](https://github.com/BinaryMuse/chrome-fast-tab-switcher/commit/a64f9dbbfc1879470a3c0f3d81b12ed00fa13b6a)
* [Some Hacker News discussion on Flux](https://news.ycombinator.com/item?id=7721292)
* [Flux and Adobe Brackets](http://www.kevindangoor.com/2014/09/intro-to-the-new-brackets-project-tree/)
* [**Avoiding Event Chains in SPA**](http://www.code-experience.com/avoiding-event-chains-in-single-page-applications/)
* [**Async requests with Flux**](http://www.code-experience.com/async-requests-with-react-js-and-flux-revisited/)
* [Flux over the wire](https://blog.rotenberg.io/flux-over-the-wire-3/)
* [Flux without Flux: Using Flux in plain React](http://gbanis.com/blog/flux-without-flux-using-flux-architecture-plain-react/)
* [Define the data to fetch in a declarative way with React](http://arqex.com/1058/define-the-data-to-fetch-declaratively-with-react)
* [Getting to know Flux](https://scotch.io/tutorials/getting-to-know-flux-the-react-js-architecture)
* [Combining Flux and FRP](https://medium.com/@milankinen/combining-flux-and-frp-hello-ffux-b04ff20fcbc6)
* [A simple web architecture using Flux, CSP, and FRP concepts](http://codrspace.com/allenkim67/a-simpler-web-architecture-using-flux-csp-and-frp-concepts/)
* [Adding a Service Layer to the Flux Architecture](https://medium.com/developers-writing/adding-a-service-layer-to-the-flux-architecture-410bc7661c45#.o1eamk32v)
* [Going isomorphic with React and Flux](https://medium.com/@fteissier/going-isomorphic-with-reactjs-and-flux-73873a2f7f8#.hnxnht6nn)

> Manipulation of state should be restricted to the Stores and if there's a need to enqueue atomic updates based on previous values, it can be done within the callback of `this.setState`, and never directly on `this.state`. The latter should only be read from and never manipulated on.
> 
> Maintain a discipline to only read from state and to never manipulate state objects, this will save us a lot of headaches.

Components send Actions and listen to Stores. Have a top-level "controller" component so your child components can be stateless and easy to test. Your controller component may not be so easy to test.

Interfaces should be predictable; there should be a deterministic process that governs how application state is presented to the user.

* Predictable interfaces (UI)
* Data flow unilaterally through an application
* Use explicit data instead of derived data
* Avoid cascading effects by preventing nested updates

What problem does Flux solve?

* Code has no structure, very imperative
* Code has to be under the right condition
* Lose code intention

If you treat every input as an action you can see what behaviors are possible in your app.

## The FLOW

1. User click a button that will result in XHR server request. Here an action is created.
2. Our API object listen for that action and perform the actual XHR request.
3. When promise resolved, a new action is published.
4. Any views that are interested in that action will listen for it and update it's UI states.

## Actions

```
publishAction( actionName, arg1, arg2... )
```

## Stores

Make store synchronous!

## Videos

* [Rethinking Web App Development at Facebook](https://www.youtube.com/watch?v=nYkdrAPrdcw)

## Flux Libraries

* [React Flux libraries](https://gist.github.com/epeli/167e7258a3f9ac626c8e)
* [**Original Flux by Facebook**](https://github.com/facebook/flux)
* [**Alt** - A library for managing data within JavaScript applications](http://alt.js.org/)
* [**Flummox** - Idiomatic, modular, testable, isomorphic Flux. No singletons required.](http://acdlite.github.io/flummox)
* [**Fluxy**](https://github.com/jmreidy/fluxy)
* [**Reflux**](https://github.com/spoike/refluxjs)
* [**Fluxify**](https://github.com/arqex/fluxify)
* [Fluxible - By Yahoo](http://fluxible.io/)
* [Fluxxor](http://fluxxor.com/)
* [Barracks - Event dispatcher for Flux](https://github.com/yoshuawuyts/barracks)
* [DeLorean](http://deloreanjs.com/)
* [McFly](http://kenwheeler.github.io/mcfly/)
* [Geiger](https://github.com/netgusto/Geiger)
* [**NuclearJS - Reactive Flux built with ImmutableJS**](https://github.com/optimizely/nuclear-js)
* [**Redux**](https://github.com/gaearon/redux)
* [react-transmit - Relay-inspired](https://github.com/RickWong/react-transmit)
* [**Lux.js**](http://www.smashingmagazine.com/2015/06/22/qualities-of-good-flux-implementations/)
* [Postal.js - Pub/Sub library](https://github.com/postaljs/postal.js)
* [Arch - SPA framework inspired by Om](https://github.com/arch-js/arch)
* [Miniflux](http://jorin.me/miniflux/)

**Others**

* [backbone.radio???](https://github.com/marionettejs/backbone.radio)
* [event-api - Reduce event hell](https://github.com/benaston/event-api)

## The case for Flux

Use it:

* If your data changes over time. And persisted to server. And you want to reflect immediately changes in UI while you slowly persist to server. Think optimistic rendering.
* If you want to cache data in memory, but it can change while cached. This happens a lot in a master-detail layout where you have a list of items. You want to cache this list even when user drilled down to the detail item and make changes. Scroll position is preserved. Global entity cache and caching IDs of items.
* If your data is relational and models include and depend on each other.
* If the same data is assembled from different sources and can be rendered in several places throughout the UI.

**The Flux solution: No fat models, separating writing and reading (CQRS) as it gets more sophisticated**

JSON data from server is not your model. Treat JSON as just another input. A single JSON can spring into multiple convenient models if you want.

Caching, invalidation, optimistic updates, aggregation, pagination and a lot of other things get much easier when models are plain objects and don't try to manage complex updates of each other.

**API responses are also Actions**, as they serve as inputs to Store.

Flux opens up a lot of possibilities such as recording and replaying UI state just by re-dispatching serialised *actions*.

## Problem with Facebook's Flux

* Multiple stores, sharing states between stores, `waitFor`, circular dependencies, etc. Can be solved with single state tree like Baobab or Redux.
* Async operations?
* Verbose
* Immutability

## Authentication with Flux

* [Adding authentication to your React Flux app](https://auth0.com/blog/2015/04/09/adding-authentication-to-your-react-flux-app/)

## Alt

* [Alt.js - Flux for fun](http://s3.jrw.fi/wwweeklies-altjs/index.html#/)

## Flummox

* [Why Flux component is better than Flux mixin](https://github.com/acdlite/flummox/blob/v3.5.1/docs/docs/guides/why-flux-component-is-better-than-flux-mixin.md)

## Reflux

* [Reflux example](https://ochronus.com/react-reflux-example/)
* [Deconstructing React.js Flux](http://spoike.ghost.io/deconstructing-reactjss-flux/)
* [The Reflux data flow model](http://blog.krawaller.se/posts/the-reflux-data-flow-model/)
* [Flux vs Reflux](http://blog.krawaller.se/posts/react-js-architecture-flux-vs-reflux/)
* [Building components with React.js and Reflux](https://reactjsnews.com/building-components-with-react-js-and-flux/)

**Key features:**

* No singleton dispatcher. Favour letting every action act as dispatcher.
* Stores listen to actions.
* Store don't need to have big switch statements that do action type checking.
* Stores may listen to other stores, i.e. it is possible to create stores that can aggregate data further, similar to a map/reduce.
* `waitFor` is replaced in favour to handle serial and parallel data flows.
* Action creators not needed.

## Simpler Examples

```js
class Slide extends Component {
  componentDidMount() {
    // Component get its data from Store so you don't
    // these parent to child, child to parent silly thing
    Store.addListener('change', function() {
      this.setState(Store.gimme(this.props.id))
    });
  }

  render() {
    return (
      <div onClick={Actions.reticulateSplines}>
        {data.text}
      </div>
    )
  }
}

// Store can just be a simple object with getter/setter
// that emit event once done
var Store = {
  gimme: function() {},
  set: function() {
    // save data, then...
    this.emit('change');
  }
};

mixInEventEmitter(Store);

// Action, again can be a simple object
// Notice here there is no type
var Actions = {
  reticulateSplines: function() {
    var data = ''; // massage, XHR, etc
    Store.set(data);
  }
}

// The parent view subscribe to the store
// Acts as controller/container?
class App extends Component {
  componentDidMount() {
    Store.addListener('change', this.forceUpdate);
  }
}
```

## Old Examples

```js
var ContactsStore = require('stores/ContactsStore');
var ViewActionCreators = require('actions/ViewActionCreators');

var App = React.createClass({
  getInitialState() {
    return ContactsStore.getState();  },
  
  componentDidMount() {
    // Subscribe to the store to listen for changes
    ContactsStore.addChangeListener(this.handleStoreChange);
    
    // User interaction
    ViewActionCreators.loadContacts();  },
  
  componentWillUnmount() {
    ContactsStore.removeChangeListener(this.handleStoreChange);  },
  
  handleStoreChange() {
    this.setState(ContactsStore.getState());  },
  
  renderContacts() {
    return this.state.contacts.map((contact) => {
        });  }});
```

This is `ViewActionCreators`

```js
var ViewActionCreators = {
  loadContacts() {
    AppDispatcher.handleViewAction({
      type: ActionTypes.LOAD_CONTACTS    });
    
    // In addition to create an Action, we also go to Api
    // and ask server for data. While data return, you again
    // create another Action
    Api.loadContacts();  }};

var Api = {
  loadContacts() {
    $.getJSON(url, (err, res) => {
      ServerActionCreators.loadedContacts(res.contacts);    });  }}

var ServerActionCreators = {
  loadedContacts(contacts) {
    AppDispatcher.handleServerAction({
      type: ActionTypes.CONTACTS_LOADED,
      contacts: contacts    });  }}

// See if anyone care about CONTACTS_LOADED action

var assign = require('react/lib/Object.assign');
var events = new EventEmitter();

var state = {
  contacts: [],
  loaded: false};

var setState = (newState) => {
  assign(state, newState);
  events.emit('CHANGE');}

var ContactsStore = {
  addChangeListener(fn) {
    events.addListener('CHANGE', fn);  },
  
  removeChangeListener(fn) {
    events.removeListener('CHANGE', fn);  },
  
  getState() {
    return state;  }};

ContactsStore.dispatchToken = AppDispatcher.register((payload) => {
  var { action } = payload;
  if (action.type === ActionTypes.CONTACTS_LOADED) {
    setState({
      loaded: true,
      contacts: action.contacts    });  }});
```

**TicketStore example**

```js
export default React.createClass({
  updateState() {
    this.setState(TicketStore.getAll());  },
  
  componentDidMount() {
    TicketStore.addChangeListener(this.updateState);  },
  
  componentWillUnmount() {
    TicketStore.removeChangeListener(this.updateState);  },
  
  render() {
    let {recording} = this.props;
    let {quotes} = this.state;   
    return <Ticket transactions={quotes} recording={recording} />;  }});
```