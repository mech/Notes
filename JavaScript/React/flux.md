# Flux

**How to deal with data?** This is really up to you.

* Use props and state; store much of the state in the root component. I typically do it this way unless I have reasons not to.
* Need cross, unrelated component communication? (think Facebook notification bar and how the number goes up and down) Use an event emitter like `asyncly/EventEmitter2`
* Need to share state/data across a fairly big app? Use Flux. But Flux is overkill for most small-scale apps/widgets.

> In order to keep modules decoupled from each other, it's helpful to think of events as reports of what has happened, rather than commands for what should happen next. Other modules can listen for the events they care about and decide what to do next on their own.

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


## Data Management Pattern

* [Making your app faster with high-performance components](https://www.youtube.com/watch?v=KYzlpRvWZ6c&t=1351)
* [Model Management](https://github.com/facebook/react/wiki/Complementary-Tools#model-management)

There are plenty of ways to manage your data:

* Container component (a.k.a Smart component)
* Flux - Store
* Cursor - Clojure Om?
* Relay
* Cortex - Centrally managing data with React



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

## Redux

* [awesome-redux](https://github.com/xgrommx/awesome-redux)
* [Redux isomorphic example](https://github.com/coodoo/react-redux-isomorphic-example)
* [Simplest redux + react example](https://github.com/jackielii/simplest-redux-example)
* [Issue#20](https://github.com/gaearon/react-redux/issues/20#issuecomment-127168519)
* [Universal infinite scrolling stars Redux](http://react.rocks/blog/post/roundup-2015-Aug-09/)
* [What the Flux?! Let's Redux](https://blog.andyet.com/2015/08/06/what-the-flux-lets-redux)
* [Handcrafting an isomorphic Redux application](https://medium.com/@bananaoomarang/handcrafting-an-isomorphic-redux-application-with-love-40ada4468af4)
* [redux-devtools](https://github.com/gaearon/redux-devtools)
* [react-redux-starter-kit](https://github.com/davezuko/react-redux-starter-kit)

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