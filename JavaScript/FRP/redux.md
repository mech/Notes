# Redux

> Data dominates. Data Structures, not algorithms, are central to programming - Rob Pike

Flux == Unidirectional data flow with changes described as plain objects.

Just like Docker, but for React data. Immutable snapshot of state.

Falcor as solving data fetching problem and Redux as predictable state management library.

```js
(state, action) => state
```

Data lives outside of React view hierarchy. I can easily reason about my view layer. How I want to also easily reason about my data. And that is where Redux with single state tree comes in.

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

**Starter Kits**

* [react-slingshot](https://github.com/coryhouse/react-slingshot)
* [react-starter-kit](https://github.com/kriasoft/react-starter-kit)
* [react-router-redux](https://github.com/rackt/react-router-redux)

## Libraries

* [react-router-redux](https://github.com/rackt/react-router-redux)
* [normalizr](https://github.com/gaearon/normalizr)

## Single Store Tree (Root Store?)

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

**Shape of your data**

It's a good idea to think of its shape of your data. Typically we need to store data as well as UI state.

## Actions

* [FSA - Flux Standard Action](https://github.com/acdlite/flux-standard-action)

Actions mutate states.

Action is just plain JS object:

```js
{ type: 'TAKE_LEAVES', leaves: [{}, {}] }
```

Actions are like newspaper, reporting on something has happened in the world.

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

## Reducer

* [Issue#328 - Cost of immutability](https://github.com/rackt/redux/issues/328)
* [Issue#758 - Why can't state be mutated?](https://github.com/rackt/redux/issues/758)

Where the action happen. Where the mutation occurs. In Flux, it is called the STORE. In Redux, it is just a pure function called REDUCER.

Redux assumes you never mutate your data. Since it is JavaScript, it can only assume. With Elm, it is enforced!

> Finally, nothing per se prevents you from mutating your Redux state tree. It is actively discouraged, and you will lose a lot of debugging benefits if you mutate your data, but for performance critical pieces you can write impure reducers that mutate the state in place. (Only do that if you're sure that's where the lag comes from—not likely to be an issue in real apps.)

**Things not to do in reducer:**

* Don't perform side effects like API calls and routing transitions. These should happen before an action is dispatched. (??)
* Calling non-pure functions like `Date.now()` or `Math.random()`
* No surprises. No side effects. No API calls. No mutations. Just calculation.

**Reducer Composition to split your logics**

## Middleware

Intercept action. Middleware transforms async actions before they reach the reducer. This is so that reducer will not have to deal with non-pure functional operations.

## Selector and Memoization

## I/O, Effects, Async

* [redux-saga, redux-effects, redux-side-effects, redux-loop](https://twitter.com/dan_abramov/status/689639582120415232)
* [From actions creators to sagas](http://riadbenguella.com/from-actions-creators-to-sagas-redux-upgraded/)

Async action creators are suboptimal.

Sync state transition??

## React Component Integration

After the action, the reducer will give you a new state. You can get back the new state using `store.getState()`. You use this new state to re-render your component using `component.setState(newState)`.

Only top-level components of your app (such as route handler) are aware of Redux. The rest are Presentational Components and receive all data via props.

Presentational components don't know WHERE the data comes from, or HOW to change it. They only render what's given to them.

