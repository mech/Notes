# Flux

* [**The case for Flux**](https://medium.com/@dan_abramov/the-case-for-flux-379b7d1982c6)
* [**Flux: Actions and the Dispatcher**](http://facebook.github.io/react/blog/2014/07/30/flux-actions-and-the-dispatcher.html)
* [Flux comparison](https://github.com/voronianski/flux-comparison)
* [Stores are not models](https://medium.com/@jetupper/hello-react-js-b87c63526e3a)
* [Facebook flux-chat example](https://github.com/facebook/flux/tree/master/examples/flux-chat/js)
* [Cortex - centrally managing data with React](https://github.com/mquan/cortex/)
* [Flocks.js](http://www.flocks.rocks/what_is_flocks.html)
* [Writing complex app using Flux and React](http://madebymany.com/blog/beyond-the-to-do-app-writing-complex-applications-using-flux-react-js)
* [What is the Flux application architecture?](https://medium.com/brigade-engineering/what-is-the-flux-application-architecture-b57ebca85b9e)
* [flux-react-router-example](https://github.com/gaearon/flux-react-router-example/)
* [React and Flux interview](http://ianobermiller.com/blog/2014/09/15/react-and-flux-interview/)
* [The React.js Way: Flux Architecture with Immutable.js](http://blog.risingstack.com/the-react-js-way-flux-architecture-with-immutable-js/)
* [React + Flux backed by Rails API](http://fancypixel.github.io/blog/2015/01/28/react-plus-flux-backed-by-rails-api/)
* [**FluxRecorder - Record and replay actions**](https://github.com/nextminds/FluxRecorder/)
* [Flux in practice](https://medium.com/@garychambers108/flux-in-practice-ec08daa9041a)
* [Understanding Flux](https://medium.com/@garychambers108/understanding-flux-f93e9f650af7)
* [React Reflux example](https://ochronus.com/react-reflux-example/)
* [Normalizes nested JSON according to schema for Flux Stores](https://github.com/gaearon/normalizr)
* [Flux architecture step by step](http://blogs.atlassian.com/2014/08/flux-architecture-step-by-step/)

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

## Videos

* [Rethinking Web App Development at Facebook](https://www.youtube.com/watch?v=nYkdrAPrdcw)

## Flux Libraries

* [**Original Flux by Facebook**](https://github.com/facebook/flux)
* [**Alt** - A library for managing data within JavaScript applications](http://alt.js.org/)
* [**Flummox** - Idiomatic, modular, testable, isomorphic Flux. No singletons required.](http://acdlite.github.io/flummox)
* [**Fluxy**](https://github.com/jmreidy/fluxy)
* [**Reflux**](https://github.com/spoike/refluxjs)
* [**Fluxify**](https://github.com/arqex/fluxify)
* [Fluxible - By Yahoo](http://fluxible.io/)
* [Fluxxor](http://fluxxor.com/)
* [Barracks - Event dispatcher for Flux](https://github.com/yoshuawuyts/barracks)
* [Delorean](http://deloreanjs.com/)
* [McFly](http://kenwheeler.github.io/mcfly/)
* [Geiger](https://github.com/netgusto/Geiger)

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



## Authentication with Flux

* [Adding authentication to your React Flux app](https://auth0.com/blog/2015/04/09/adding-authentication-to-your-react-flux-app/)

## Flummox

* [Why Flux component is better than Flux mixin](https://github.com/acdlite/flummox/blob/v3.5.1/docs/docs/guides/why-flux-component-is-better-than-flux-mixin.md)

## Reflux

* [Reflux example](https://ochronus.com/react-reflux-example/)
* [Deconstructing React.js Flux](http://spoike.ghost.io/deconstructing-reactjss-flux/)

Key features:

* No singleton dispatcher. Favour letting every action act as dispatcher.
* Stores listen to actions.
* Store don't need to have big switch statements that do action type checking.
* Stores may listen to other stores, i.e. it is possible to create stores that can aggregate data further, similar to a map/reduce.
* `waitFor` is replaced in favour to handle serial and parallel data flows.
* Action creators not needed.



## Examples

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