# Redux

Flux == Unidirectional data flow with changes described as plain objects.

Just like Docker, but for React data. Immutable snapshot of state.

Falcor as solving data fetching problem and Redux as predictable state management library.

```js
(state, action) => state
```

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

## Single Store Concept (Root Store?)

You App need to hold states. Where should you "store" it? Redux and Flux both has the "Store" concept where states are resided.
	
## Single State Tree

* [Umbrella: Externalize the State Tree (or alternatives)](https://github.com/facebook/react/issues/4595)

## Middleware

Intercept action.

## Selector and Memoization



## Actions Mutate States

Action is just plain JS object:

```js
{ type: 'INCREMENT' }
```