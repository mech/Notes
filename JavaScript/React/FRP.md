# Functional Reactive Programming

In JavaScript we typically deal with asynchronous interactions by observing some object for an event and firing a callback whenever that event occurs. However, when there is a more complex set of interactions (e.g. wait for event A, then wait for event B, ...) things start to become more complex. You can quickly end up in what is affectionately known as callback hell.

Reactive programming is a programming paradigm which attempts to address this inherent complexity in asynchronous systems. It does so by modelling the flow of data between the parts of a system using data structures called streams.

Rather than dealing with discrete events, you can think of streams as a continuous flow of data. Streams are first-class values and can be manipulated using all of your usual functional programming tools (e.g. `map`, `reduce`, `filter`, etc). They are also like little garden hoses which can be split, joined, and interleaved.

* [**Reactive Streams**](http://www.reactive-streams.org/)
* [Swarm.js](http://swarmjs.github.io/)
* [react-nexus](https://github.com/elierotenberg/react-nexus)
* [**Reactive stream with Bacon.js**](http://joshbassett.info/2014/reactive-uis-with-react-and-bacon/)
* [Mori - Persistent data structures](https://github.com/swannodette/mori)
* [Avoid forEach](http://aeflash.com/2014-11/avoid-foreach.html)
* [Cycle - Reactive framework](https://github.com/staltz/cycle)
* [Functional Reactive React.js](https://medium.com/@garychambers108/functional-reactive-react-js-b04a8d97a540)
* [javascript-allonge - Book](https://leanpub.com/javascript-allonge)
* [Read JavaScript Allonge](https://leanpub.com/javascript-allonge/read)
* [Persistent and optionally immutable data tree with cursors](https://github.com/Yomguithereal/baobab)
* [Immutability in React](http://www.sitepoint.com/immutability-react/)
* [Reactive React using Reactive Streams](http://aryweb.nl/2015/02/16/Reactive-React-using-reactive-streams/)
* [Functional Programming on Front-end with React and ClojureScript](http://blog.scalac.io/2015/04/02/clojurescript-reactjs-reagent.html)
* [**Reactive MVC and Virtual DOM**](http://futurice.com/blog/reactive-mvc-and-the-virtual-dom)
* [react-cursor](https://github.com/dustingetz/react-cursor)
* [RxMarbles??](http://rxmarbles.com/)
* [**Functional React**](https://github.com/aickin/functional-react)
* [Atom-React - Inspired by Om, but in JavaScript](https://github.com/stample/atom-react)
* [Simpler UI reasoning with unidirectional data flow and immutable data](http://omniscientjs.github.io/guides/01-simpler-ui-reasoning-with-unidirectional/)
* [Elegant functional architecture for React](https://medium.com/@gilbox/an-elegant-functional-architecture-for-react-faa3fb42b75b)

If you have an object or an array. Changing the object's properties or pushing a new element into the array will not constitute a change since the original references is still the same. This is why immutable.js or Mori are helpful to get a "pure" function.

Or just don't use objects in `props` and `state`.

## Baobab

* [Performance of `push`](https://github.com/Yomguithereal/baobab/issues/268)
* [Plant a Baobab tree in your Flux application](http://christianalfoni.github.io/javascript/2015/02/06/plant-a-baobab-tree-in-your-flux-application.html)

## Zipper

* [Getting acquainted with Clojure zippers](http://josf.info/blog/2014/03/21/getting-acquainted-with-clojure-zippers/)
* [neith - JavaScript zipper library](https://github.com/mattbierner/neith)

## Examples

* [react-immutable-demo](https://github.com/pk11/react-immutable-demo)

## Videos

* [The Language of the System - Rich Hickey](https://www.youtube.com/watch?v=ROor6_NGIWU)
* [Boundaries - Gary Bernhardt](https://www.destroyallsoftware.com/talks/boundaries)
* [Async JavaScript with Reactive Extensions at Netflix](https://www.youtube.com/watch?v=XRYN2xt11Ek)