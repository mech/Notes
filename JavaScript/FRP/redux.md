# Redux

> React is not reactive because it does not observe the data


If you don't have synchronization problem and don't really need single source of truth, you don't need Redux. Local component is perfectly fine for other cases.

Redux is where interaction happens like `onClick`, `onMouseOver`, etc.

To give a bit of perspective on complex front-end application, let's consider Google Docs. Every time a user presses a key, a number of things need to happen (doing them all before returning to the event queue would be a recipe for an unresponsive app):

* the new character has to be displayed on the screen
* the caret has to be moved
* the action has to be pushed to the local undo history
* spell-check may have to run
* word count and page count may need to be updated

We want to use **distributed events**, where a single incident can trigger reactions throughout our application. Event emitter is how you can distribute events.

> Data dominates. Data Structures, not algorithms, are central to programming - Rob Pike

Flux == Unidirectional data flow with changes described as plain objects.

Just like Docker, but for React data. Immutable snapshot of state.

Falcor as solving data fetching problem and Redux as predictable state management library.

```js
(state, action) => state


// Some usage example:

const store = createStore(counter);

<Counter
  value={store.getState()}
  onIncrement={() => store.dispatch({ type: 'INC' })}
  onDecrement={() => store.dispatch({ type: 'DEC' })} />
```

Data lives outside of React view hierarchy. I can easily reason about my view layer. How I want to also easily reason about my data. And that is where Redux with single state tree comes in.

* [Why I'm tired of using and teaching flux](https://gist.github.com/justinwoo/08f9f8fcdcf865025f18)
* [A simple way to route with Redux](http://jlongster.com/A-Simple-Way-to-Route-with-Redux)
* [**Nothing new in React and Flux**](http://staltz.com/nothing-new-in-react-and-flux-except-one-thing.html)
* [**Why React/Redux is an inferior paradigm**](http://staltz.com/why-react-redux-is-an-inferior-paradigm.html)
* [**Why we use Om, and why we're excited for Om Next**](http://blog.circleci.com/why-we-use-om-and-why-were-excited-for-om-next/)
* [**Awesome Redux Course Note**](https://github.com/tayiorbeii/egghead.io_redux_course_notes)
* [**Flux vs Single State Tree**](http://www.christianalfoni.com/articles/2015_11_16_Flux-vs-Single-State-Tree)
* [Interview with Dan Abramov](http://softwareengineeringdaily.com/2015/09/18/flux-redux-and-react-hot-loader-with-dan-abramov/)
* [**Full-stack Redux tutorial**](http://teropa.info/blog/2015/09/10/full-stack-redux-tutorial.html)
* [**A cartoon guide to Redux**](https://code-cartoons.com/a-cartoon-intro-to-redux-3afb775501a6#.isxvwd9em)
* [**Understanding Redux (how I fell in love with a state container)**](http://www.youhavetolearncomputers.com/blog/2015/9/15/a-conceptual-overview-of-redux-or-how-i-fell-in-love-with-a-javascript-state-container)
* [**James Long's Redux Blog**](http://jlongster.com/The-Seasonal-Blog-Redux)
* [awesome-redux](https://github.com/xgrommx/awesome-redux)
* [Redux isomorphic example](https://github.com/coodoo/react-redux-isomorphic-example)
* [Simplest redux + react example](https://github.com/jackielii/simplest-redux-example)
* [Issue#20](https://github.com/gaearon/react-redux/issues/20#issuecomment-127168519)
* [Universal infinite scrolling stars Redux](http://react.rocks/blog/post/roundup-2015-Aug-09/)
* [What the Flux?! Let's Redux](https://blog.andyet.com/2015/08/06/what-the-flux-lets-redux)
* [Handcrafting an isomorphic Redux application](https://medium.com/@bananaoomarang/handcrafting-an-isomorphic-redux-application-with-love-40ada4468af4)
* [redux-devtools](https://github.com/gaearon/redux-devtools)
* [react-redux-starter-kit](https://github.com/davezuko/react-redux-starter-kit)
* [redux-requests - Manages in-flight requests](https://github.com/idolize/redux-requests)
* [**redux-blog-example**](https://github.com/GetExpert/redux-blog-example)
* [react-reversi](https://github.com/jhewlett/react-reversi)
* [**State Management with Redux**](http://konkle.us/state-management-with-redux/)
* [redux-store-visualizer](https://github.com/romseguy/redux-store-visualizer)
* [redux-undo](https://github.com/omnidan/redux-undo)
* [Redux interview by Survive.js](http://survivejs.com/blog/redux-interview/)
* [redux-tutorial](https://github.com/happypoulp/redux-tutorial)
* [Redux best practices](https://medium.com/lexical-labs-engineering/redux-best-practices-64d59775802e#.g7ayoa8i6)
* [redux-thunk - Middleware](https://github.com/gaearon/redux-thunk)
* [Is Redux too much?](https://medium.com/@davidvlsea/react-without-undue-complications-f3490403fdc0#.qncruotht)
* [Tracker 2.0: The evolution of Tracker and solutions to its core problem](https://medium.com/@faceyspacey/the-evolution-of-tracker-solutions-to-its-core-problems-4b9cb90d479a#.x3o7lt78t)
* [Issue#155 - Redux's relation to cursors](https://github.com/rackt/redux/issues/155)

**Starter Kits**

* [**Shasta - Simple opinionated toolkit for building applications on top of React, Redux, and immutable.js**](https://github.com/shastajs/shasta)
* [react-slingshot](https://github.com/coryhouse/react-slingshot)
* [react-starter-kit](https://github.com/kriasoft/react-starter-kit)
* [react-router-redux](https://github.com/rackt/react-router-redux)
* [redux-easy-boilerplate](https://github.com/anorudes/redux-easy-boilerplate)

## Libraries

* [react-router-redux](https://github.com/rackt/react-router-redux)
* [normalizr](https://github.com/gaearon/normalizr)

## Single Store Tree (Root Store?) - Single Source of Truth - Single State Atom

* [Issue#140 - Rename store to reducer](https://github.com/rackt/redux/pull/140)

> Om Now was one of the early influencers for the single atom app state idea. The only difference is that, instead of using cursors, Redux uses Flux-style actions for mutations.

You App need to hold states. Where should you "store" it? Redux and Flux both has the "Store" concept where states are resided.
	
Redux has single state tree.

State === Model

* [Umbrella: Externalize the State Tree (or alternatives)](https://github.com/facebook/react/issues/4595)

See Om Next approach on changing a state tree to a graph one, sort of like GraphQL and Falcor.

> The tree is really a graph

A single state tree (i.e. Baobab) can be easily navigated by a cursor. However, visited different branch of a tree prove tedious.

With graph, you can sort of visit anywhere you like! Query let you navigate the graph of your data in all sorts of directions.

Your data is a graph, but what your UI sees is a tree.

**Shape of your application state**

It's a good idea to think of its shape of your data. Typically we need to store data as well as UI state.

## Actions

* [FSA - Flux Standard Action](https://github.com/acdlite/flux-standard-action)

Actions mutate states.

Action is just plain JS object:

```js
{ type: 'TAKE_LEAVES', leaves: [{}, {}] }
```

Actions are like newspaper, reporting on something has happened in the world.

The component itself do not know how to deal with the action. For example, the component event handler do not ever take upon itself to process business or application logic. For example, a very simple act of paging through a list can be described by this action:

```js
{ type: 'SET_PAGE_NUMBER', page_number: 12}
```

So `page_number` here is a state, and the only way to change this read-only state is to dispatch an action.

Actions are the change in your app. Actions represent mutations of your app state. Explicit, easy to find the places that could trigger a particular action, I can search for it.

In Cycle, it is `intent()` which interpret DOM events as user's intended actions:

```js
// intent() is Cycle.js's way of Action
// It's input is the DOM source where the UI world is at
// It has 2 observables here that interpret 2 DOM events
function intent(DOM) {
  return {
    changeWeight$: DOM.select('#weight').events('input').map(ev => ev.target.value),
    changeHeight$: DOM.select('#height').events('input').map(ev => ev.target.value)
  };
}
```

Action don't do anything. It don't mutate states. It only describe something has happen and ask Reducer to go deal with it.

### Action Creators (Where async can happen)

Action creators are just function that create action.

```js
// This is a simple synchronous dispatch. The UI will render immediately!!
dispatch({
  type: ADD_ITEM,
  status: 'start',
  name: 'James'
})

// This is a asynchronous dispatch.
function addItem(name) {
  return dispatch => {
    dispatch({
      type: ADD_ITEM,
      status: 'start',
      name: name
    });

    setTimeout(() => { // Just a fake XHR request
      dispatch({
        type: ADD_ITEM,
        status: 'finish',
        name: name
      });
    }, 100);
  }
}

// Or using some other promise middleware
const { PROMISE } = require('<promise-middleware>');

function addItem(name) {
  return {
    type: ADD_ITEM,
    name: name,
    [PROMISE]: api.addItem(name)
  }
}
```

**More examples of Action Creators**

```js
function addTodo(text) {
  const trimmedText = text.trim();
  return {
    type: 'ADD_TODO',
    text: trimmedText
  };
}

<button onClick={ dispatch(addTodo('Call Mom')) }>Add Todo</button>

// Or directly use XHR
export function addTodo(todo) {
  return (dispatch) => {
    dispatch({type: 'SAVING_TODO'}); // spinner?
    
    ajax.post('/todos', todo)
      .then(() => {
        dispatch({type: 'SAVED_TODO'}); // stop spinner?
        dispatch({
          type: 'ADD_TODO',
          todo: todo
        });
      });
  };
};
```

```js
export function login(email, password) {
  return ({fetch}) => ({
    types: [LOGIN, LOGIN_SUCCESS, LOGIN_ERROR],
    payload: {
      promise: fetch('auth/login', {
        body: JSON.stringify({email, password})
      })
    }
  })
};
```

## Reducer

```
   Source ------> Handler ------> Sink
(don't care)                  (don't care)
```

Reducers are synchronous! Data logic is 100% separated from view logic.

Redux manages state by separating it into different reducers. Each reducer managing a little piece of a different branch of the global state tree.

* [Issue#328 - Cost of immutability](https://github.com/rackt/redux/issues/328)
* [Issue#758 - Why can't state be mutated?](https://github.com/rackt/redux/issues/758)

Where the action happen. Where the mutation occurs. In Flux, it is called the STORE. In Redux, it is just a pure function called REDUCER.

Redux assumes you never mutate your data. Since it is JavaScript, it can only assume. With Elm, it is enforced!

> Finally, nothing per se prevents you from mutating your Redux state tree. It is actively discouraged, and you will lose a lot of debugging benefits if you mutate your data, but for performance critical pieces you can write impure reducers that mutate the state in place. (Only do that if you're sure that's where the lag comes from—not likely to be an issue in real apps.)

Each reducer computes a separate piece of state, which is then all composed together to form the whole application.

**Things not to do in reducer:**

* Don't perform side effects like API calls and routing transitions. These should happen before an action is dispatched. (middleware??)
* Calling non-pure functions like `Date.now()` or `Math.random()`
* No surprises. No side effects. No API calls. No mutations. Just calculation.

**Reducer Composition to split your logics**

Depending on your state tree shape, you can have different reducer working on one part of the state for example.

```js
// This is your single state tree
{
  todos: [],
  visibilityFilter: 'SHOW_ALL'
}

// You can have 2 reducers, one for todos management and the
// other to take care of visibility filter logic

const todoApp = (state = {}, action) => {  
  return {
    todos: todos(state.todos, action),
    visibilityFilter: visibilityFilter(state.visibilityFilter, action)
  }
}

// Or use combineReducers
const todoApp = combineReducers({ todos, visibilityFilter })

const todos = (state = [], action) => {
  // This is a one part of the reducer that take care of the todos management.
  // Notice that it's state is an array
}

const visibilityFilter = (state = 'SHOW_ALL', action) => {
  // This is another part of the reducer that deal with filtering.
  // Notice that its default state is a string
}
```

## Transducer

* [Transducer Protocol](https://github.com/cognitect-labs/transducers-js)
* [Issue#176 - Transducers in Redux](https://github.com/rackt/redux/issues/176)
* [Issue#569 - Proposal: API for explicit side effects](https://github.com/rackt/redux/pull/569)
* [Issue#1139 - An alternative side effect model based on Generators and Sagas](https://github.com/rackt/redux/issues/1139)

## Middleware

* [Understanding Redux middleware](https://medium.com/@meagle/understanding-87566abcfb7a#.pv692to4s)

Intercept action. Middleware transforms async actions before they reach the reducer. This is so that reducer will not have to deal with non-pure functional operations.

## Selector and Memoization

* [A brief history of Reselect](http://blog.startifact.com/posts/a-brief-history-of-reselect.html)
* [Issue#47 - Handling derived data](https://github.com/rackt/redux/issues/47)

## I/O, Effects, Async

* [redux-saga, redux-effects, redux-side-effects, redux-loop](https://twitter.com/dan_abramov/status/689639582120415232)
* [**From actions creators to sagas**](http://riadbenguella.com/from-actions-creators-to-sagas-redux-upgraded/)
* [Why do we need middleware for async flow in Redux?](http://stackoverflow.com/questions/34570758/why-do-we-need-middleware-for-async-flow-in-redux/34623840#34623840)

Async action creators are suboptimal.

Sync state transition??

## Thunk

* [Callback + Continuable](https://gist.github.com/creationix/b9557dd1dceba7aa90b5)

## Router

* [Redial - Route lifecycle management??](https://github.com/markdalgleish/redial)
* [#637 - Usage with React Router](https://github.com/rackt/redux/issues/637)
* [Issue#1362 - RFC: syncHistoryWithStore()](https://github.com/rackt/redux/pull/1362)

Angular 2 Router exposes route change as an Observable which you can leverage to keep route state synchronized with your Redux Store.

> Dispatching an action instead of using directly `history.pushState()` is really important. The action will go through the chain of middlewares, meaning (for example) automatic analytics, etc.
> 
> About `browserHistory` singleton, singletons and server side = bad idea. Actions and middleware are giving me an easy way to use history without propagating it through context/props on client side.

```js
// You listen for browser change event and dispatch an action to handle it
// browserHistory is a singleton??
import { browserHistory } from 'react-router';
browserHistory.subscribe(location => store.dispatch({ type: 'NAVIGATE', location }));
```

Provide ability to change URL location within an action creator. This is very useful because it's not uncommon to have a workflow in an action creator that is something like "authenticate user -> if successful, redirect to /admin".

## React Component Integration

After the action, the reducer will give you a new state. You can get back the new state using `store.getState()`. You use this new state to re-render your component using `component.setState(newState)`.

Only top-level components of your app (such as route handler) are aware of Redux. The rest are Presentational Components and receive all data via props.

Presentational components don't know WHERE the data comes from, or HOW to change it. They only render what's given to them.

### Context and Provider

> Learning all this React environment and Redux is dragging me down. The connects and mapState make no sense to me and you have to do it for every container?

Convention over configuration is lost JavaScript's obsession with composability.

```js
import { createStore } from 'redux';
import { Provider } from 'react-redux';
import todoApp from './reducers';

let store = createStore(todoApp);

ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById('#app')
);


// App.jsx
import { connect } from 'react-redux';

const App = ({dispatch, state}) => {
  return (
    <button onClick={ dispatch(addTodo('Buy Milk')) }>Add Todo</button>
  );
};

export default connect(App);
```

### Connect

Or just do your own `store.subscribe()`.

* [redux-connected-proptypes](https://github.com/conorhastings/redux-connected-proptypes)

`connect()` from Redux React does a ton of trickery to be very optimized. It tries hard to be fast whereas functional components don't try at all.

When you always render from the top you are coupling parent components too hard to what child components need to render. You're essentially passing many props that are only required by children, and changing them can involve painful refactoring.

Instead as soon as you see that component passes props down without using it, we suggest generating a "container" component using `connect()`.

```js

```

## Relay Style?

> That's what I’d do. (But I'm pretty sure one can take Redux + Normalizr and build something more Relay-like around it.)