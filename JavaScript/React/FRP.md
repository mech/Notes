# Functional Reactive Programming

In JavaScript we typically deal with asynchronous interactions by observing some object for an event and firing a callback whenever that event occurs. However, when there is a more complex set of interactions (e.g. wait for event A, then wait for event B, ...) things start to become more complex. You can quickly end up in what is affectionately known as callback hell.

Reactive programming is a programming paradigm which attempts to address this inherent complexity in asynchronous systems. It does so by modelling the flow of data between the parts of a system using data structures called streams.

Rather than dealing with discrete events, you can think of streams as a continuous flow of data. Streams are first-class values and can be manipulated using all of your usual functional programming tools (e.g. `map`, `reduce`, `filter`, etc). They are also like little garden hoses which can be split, joined, and interleaved.

> The poet always has too many words in his vocabulary, a painter too many colours in his palette, a musician too many notes on his keyboard - Jean Cocteau (Less is More)

* [Small functional problem-solving, event, state-management, and caching utilities.](https://github.com/matthiasak/universal-utils)
* [**A Birds Eye View of Functional Programming**](https://medium.com/making-internets/a-bird-s-eye-view-of-functional-programming-7325853ff9ad#.qxg9iickc)
* [Breaking down FRP](https://blogs.janestreet.com/breaking-down-frp/)
* [**Ember.js - Functional Programming and the Observer Effect**](https://emberway.io/ember-js-functional-programming-and-the-observer-effect-48901c3b84d7#.apqix8835)
* [**Hello, declarative world**](http://codon.com/hello-declarative-world)
* [**Coding with React like a Game Developer**](https://medium.com/@PhilPlckthun/coding-with-react-like-a-game-developer-e39ffaed1643)
* [**A General Theory of Reactivity**](https://github.com/kriskowal/gtor/blob/master/README.md)
* [Life after JavaScript](http://www.sitepoint.com/future-programming-webassembly-life-after-javascript/)
* [**A simpler web architecture using Flux, CSP, and FRP concepts**](http://codrspace.com/allenkim67/a-simpler-web-architecture-using-flux-csp-and-frp-concepts/)
* [**Functional Reactive JS**](http://channikhabra.github.io/frp-with-rxjs-jschannel-conf/#/)
* [What is Reactive Programming?](http://paulstovell.com/blog/reactive-programming)
* [Mostly adequate guide to FP](https://github.com/DrBoolean/mostly-adequate-guide)
* [**The introduction to Reactive Programming you've been missing**](https://gist.github.com/staltz/868e7e9bc2a7b8c1f754)
* [**Reactive Streams**](http://www.reactive-streams.org/)
* [Swarm.js](http://swarmjs.github.io/)
* [react-nexus](https://github.com/elierotenberg/react-nexus)
* [**Reactive stream with Bacon.js**](http://joshbassett.info/2014/reactive-uis-with-react-and-bacon/)
* [Mori - Persistent data structures](https://github.com/swannodette/mori)
* [Avoid forEach](http://aeflash.com/2014-11/avoid-foreach.html)
* [**Cycle - Reactive framework**](https://github.com/staltz/cycle)
* [Cycle.js](http://cycle.js.org/)
* [Functional Reactive React.js](https://medium.com/@garychambers108/functional-reactive-react-js-b04a8d97a540)
* [javascript-allonge - Book](https://leanpub.com/javascript-allonge)
* [Read JavaScript Allonge](https://leanpub.com/javascript-allonge/read)
* [Persistent and optionally immutable data tree with cursors](https://github.com/Yomguithereal/baobab)
* [Reactive React using Reactive Streams](http://aryweb.nl/2015/02/16/Reactive-React-using-reactive-streams/)
* [Functional Programming on Front-end with React and ClojureScript](http://blog.scalac.io/2015/04/02/clojurescript-reactjs-reagent.html)
* [react-cursor](https://github.com/dustingetz/react-cursor)
* [RxMarbles??](http://rxmarbles.com/)
* [**Functional React**](https://github.com/aickin/functional-react)
* [Atom-React - Inspired by Om, but in JavaScript](https://github.com/stample/atom-react)
* [**Elegant functional architecture for React**](https://medium.com/@gilbox/an-elegant-functional-architecture-for-react-faa3fb42b75b)
* [Ramda.js - Functional library for JavaScript](http://ramdajs.com/0.15/index.html)
* [What color is your function?](http://journal.stuffwithstuff.com/2015/02/01/what-color-is-your-function/)
* [Monads: From Web 2.0 to Hardware Drivers](http://www.well-typed.com/blog/105/)
* [**JSON Graph: Reactive REST at Netflix**](http://applicative.acm.org/speaker-JafarHusain.html)
* [Functional programming on front-end with React and ClojureScript](http://blog.scalac.io/2015/04/02/clojurescript-reactjs-reagent.html)
* [Reactive Programming with Kefir.js and React](https://medium.com/@carloM/reactive-programming-with-kefir-js-and-react-a0e8bb3af636)
* [Functional reactive UI library?](https://github.com/Gozala/reflex)
* [Grokking RxJava Part 1](http://blog.danlew.net/2014/09/15/grokking-rxjava-part-1/)
* [Reactive Frontend](https://auth0.com/events/oscon-reactive-frontend)
* [Why should you care about re-frame?](https://github.com/Day8/re-frame#why-should-you-care-about-re-frame)
* [Netflix JavaScript - Async JavaScript with Reactive Extensions](http://www.youtube.com/watch?v=XRYN2xt11Ek)
* [JavaScript Jabber recording of FRP](http://javascriptjabber.com/061-jsj-functional-reactive-programming-with-juha-paananen-and-joe-fiorini/)
* [mercury.js - An interesting framework](https://github.com/Raynos/mercury)

If you have an object or an array. Changing the object's properties or pushing a new element into the array will not constitute a change since the original references is still the same. This is why immutable.js or Mori are helpful to get a "pure" function.

Or just don't use objects in `props` and `state`.

## What exactly is FRP?

* Values "over time". If you do computation over those values, it will also change over time.
* Continuous, not discrete
* FRP is a form of Functional Programming, which is a form of Declarative Programming
* Everything is a stream: variables, user inputs, properties, caches, data structures, etc. You listen to that stream and react accordingly.
* You `combine` the stream, you `filter` the stream, and you generally use functional programming to do whatever you like to the stream to make it consumable.
* The stream is the observable. The official terminology for a stream is "Observable", for the fact that it can be observed.
* The listener is the observer
* And yes, a Promise is an observable

## Spreadsheet Analogy

A spreadsheet cell reacts to changes in other cells (pulls) but doesn't reach out and change others (doesn't push). The end result is that you can change one cell and a zillion others 'independently' update their own displays. The others react to you! You don't manually change them. Let them react  to you!

Spreadsheet is FRP already. You declare the formula, and you change the data to see the result.

## Om

* [Om Next - David Nolan (Blow your mind!)](https://www.youtube.com/watch?v=ByNs9TG30E8)

## Observable

Observable === Collections + Time

Observables are a representation of any collection of values over any amount of time.

```js
// Using traditional Array's filter(), map(), reduce() will kill performance
// as you are iterating the entire set of array!
array.filter(x => x % 2 === 1).map(x => x + '!!!');

// Using observable is different as it is streaming and efficient
// the whole filter and map only happen once
observable.filter(x => x % 2 === 1).map(x => x + '!!!');
```

Able to tell when I am done.

A stream of mouse click events can be an observable, but not an array.

Observables can be merged, concatenated and zipped like any other collection.

Observables are a pattern to:

* Start a data stream
* Emit 0 to N messages
* Teardown the data stream

> If I am interested in the keystroke "a" followed by "b" followed by "c" I can create an event that notifies me when this occurs. The observable pattern has huge benefits for code simplification.

* [**RSS sample app using observable**](https://github.com/channikhabra/yarr/)
* [Cold vs Hot Observables](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/gettingstarted/creating.md#cold-vs-hot-observables)
* [Pure rendering in the light of time and state](https://medium.com/@mweststrate/pure-rendering-in-the-light-of-time-and-state-4b537d8d40b1)

Observable is a concept from the world of Functional Reactive Programming. They are used in other UI framework like Ember and Knockout.

## MobX

* [RFX Stack](https://github.com/foxhound87/rfx-stack)
* [Making React reactive: the pursuit of high performing, easily maintainable React apps](https://www.mendix.com/tech-blog/making-react-reactive-pursuit-high-performing-easily-maintainable-react-apps/)
* [Silent subscriptions](https://discuss.reactjs.org/t/reactjs-mobservable-as-the-easiest-and-fastest-way-to-propagate-changes-to-the-ui/811)
* [Becoming fully reactive: An in-depth explanation of Mobservable](https://medium.com/@mweststrate/becoming-fully-reactive-an-in-depth-explanation-of-mobservable-55995262a254#.pdvu7he6y)
* [Pure rendering in the light of time and state](https://medium.com/@mweststrate/pure-rendering-in-the-light-of-time-and-state-4b537d8d40b1#.cofzcnv4e)
* [The evolution of Tracker](https://forums.meteor.com/t/tracker-2-0-the-evolution-of-tracker-solutions-to-its-core-problems/14941)
* [Some nice discussion on observable](https://forums.meteor.com/t/next-steps-on-blaze-and-the-view-layer/13561/483)
* [mobservable-react-boilerplate](https://github.com/mweststrate/mobservable-react-boilerplate)

## Cerebral

* [Inspired by Baobab and Flux](http://www.christianalfoni.com/articles/2015_05_18_Cerebral-developer-preview)

## RxJS

While Flux suggests using low-level EventEmitter which requires manual event handling, RxJS and similar event processing tools are powerhouses capable of replacing a lot of boilerplate that a typical Flux application contains.

* [A visualizer for reactive streams](http://jaredforsyth.com/rxvision/)
* [Reactive Frontend](https://auth0.com/events/oscon-reactive-frontend)
* [**RxJS version 3.0 on Aug 2015**](https://github.com/Reactive-Extensions/RxJS/releases/tag/v3.0.0)
* [Using RxJS for data flow instead of Flux](http://qiita.com/kimagure/items/22cf4bb2a967fcba376e)
* [irecord - An immutable store that exposes an RxJS observable](https://github.com/ericelliott/irecord)
* [react-rx-component - Yet another RxJS library for React](https://github.com/acdlite/react-rx-component)
* [RxJS at Modern Web UI for Netflix](https://www.youtube.com/watch?v=yk_6eU3Hcwo)
* [Asynchronous JavaScript at Netflix](https://www.youtube.com/watch?v=XE692Clb5LU)
* [**Reactive MVC and Virtual DOM**](http://futurice.com/blog/reactive-mvc-and-the-virtual-dom)
* [2-minute intro to Rx](https://medium.com/@andrestaltz/2-minute-introduction-to-rx-24c8ca793877)
* [react-rx-immutable-example](https://github.com/newtriks/react-rx-immutable-example)
* [Using Rx.js to create a scroll table with adjustable width](https://www.codementor.io/reactjs/tutorial/using-rxjs-to-create-a-scroll-table-with-adjustable-width)
* [Writing marble tests](https://github.com/ReactiveX/RxJS/blob/master/doc/writing-marble-tests.md)
* [JWT with observables](https://auth0.com/blog/2015/09/10/jwt-authentication-with-observables/)
* [A dead-simple Todo with RxJS](http://blog.edanschwartz.com/2015/09/18/dead-simple-rxjs-todo-list/)

```js
// Convert a Promise to an Observable
var stream = Rx.Observable.fromPromise(promise);
```

## Baobab

* [Performance of `push`](https://github.com/Yomguithereal/baobab/issues/268)
* [Plant a Baobab tree in your Flux application](http://christianalfoni.github.io/javascript/2015/02/06/plant-a-baobab-tree-in-your-flux-application.html)
* [Handling states in your React Flux application with Baobab](https://www.codementor.io/reactjs/tutorial/flux-reactjs-state-baobab-library)
* [Declarative data fetching in React with Baobab](https://medium.com/@mistadikay/declarative-data-fetching-in-react-components-with-baobab-e43184c43852)
* [True isomorphic app with baobab](https://www.codementor.io/reactjs/tutorial/true-isomorphic-apps-react-baobab#/)

A cursor is a pointer to some data in your tree. The brilliant thing that cursors give you is the ability to listen for changes, but not only changes to the value the cursor points to.

## Omniscient

* [Simpler UI reasoning with unidirectional data flow and immutable data](http://omniscientjs.github.io/guides/01-simpler-ui-reasoning-with-unidirectional/)

## Zipper

* [Getting acquainted with Clojure zippers](http://josf.info/blog/2014/03/21/getting-acquainted-with-clojure-zippers/)
* [neith - JavaScript zipper library](https://github.com/mattbierner/neith)

## Examples

* [react-immutable-demo](https://github.com/pk11/react-immutable-demo)

## Videos

* [The Language of the System - Rich Hickey](https://www.youtube.com/watch?v=ROor6_NGIWU)
* [Boundaries - Gary Bernhardt](https://www.destroyallsoftware.com/talks/boundaries)
* [Async JavaScript with Reactive Extensions at Netflix](https://www.youtube.com/watch?v=XRYN2xt11Ek)
* [Functional Reactive Programming in Elm](https://www.youtube.com/watch?v=DiZ1CfLQvIU)
* [Asynchronous JavaScript at Netflix](https://www.youtube.com/watch?v=a8W5VVGO-jA)
* [Big retail goes reactive](http://www.typesafe.com/resources/video/big-retail-goes-reactive)
* [Bringing Observable Data to React](https://www.youtube.com/watch?v=wC6BKH4JyO4)
* [Functional Principles in React](https://www.youtube.com/watch?v=1uRC3hmKQnM)