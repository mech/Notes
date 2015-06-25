# States and Props

> Debugging mutable state is a brainteaser: "The butcher lives in the red house on Wed. The odd houses were painted on Sunday..."

---

> An instance of the Go's `Board` class has several attributes that describe what a game of Go looks like at a particular moment in time. This is a common paradigm in React: get familiar with the snapshot concept.

Every serious applications need to represent states *over time*. Root of all evil is state changing over time.

Human mind is not good at keeping track of state changing over time.

**The root of all evil in an interactive application is managing state**

State flows down the components, and events flow up. While properties should never be changed, state is mutable.

Properties can't be changed because they are inherited every time the component is rendered, so any changes will be lost.

There's a deeper reason why it's so important to make data flow clear and simple: it encourages you to keep state in as few places as possible and make most of your components stateless.

* [Communicate between components](http://facebook.github.io/react/tips/communicate-between-components.html)
* [Expose component functions](http://facebook.github.io/react/tips/expose-component-functions.html)
* [Best Practices for Component State](http://brewhouse.io/blog/2015/03/24/best-practices-for-component-state-in-reactjs.html)
* [What the Flux](https://ochronus.com/react-what-the-flux/)
* [Simpler UI reasoning with unidirectional data flow and immutable data](http://omniscientjs.github.io/guides/01-simpler-ui-reasoning-with-unidirectional/)

> Once you've grokked the basics, this is perhaps the most important thing to know about React. To think in React is to find the minimal amount of state necessary to represent your app, and calculate everything based on that. This is because state is unpredictable. Props are, for the most part, derived from other props and state, but state can be anything. The more state in your application, the harder it is to reason about it. As much as possible, state in React should be an implementation detail — a necessary evil, not a crutch.

**Warning**: The worst thing you can do is call `setState` right after a `render()` in `componentDidMount()` or `componentDidUpdate()`. It means most `render()` will be called twice!

You can have instance properties for state that do not control how a component renders like `this._timer`

**Note**: Data flow down the component hierarchy. Event typically flow upstream to the owner component so they can make the decision to re-render child components.

* Data only flows from parents to the children.
* Children thus only have the logic to display the data, not modify it.
* Children also handle events and then inform parents via callback or events. Parents then modify their own state.

## Child to Parent Communication

* [2-way data-binding is one way](http://voidcanvas.com/react-tutorial-two-way-data-binding/)
* [Why Flux is better than firing events back and forth](http://www.code-experience.com/avoiding-event-chains-in-single-page-applications/)
* [Context in React.js](https://www.tildedave.com/2014/11/15/introduction-to-contexts-in-react-js.html)

If you're not using the Flux pattern (where the parent widget listens to Stores that are affected by Action Creators invoked by the child elements), the idiomatic way to do this is to pass callbacks that affect the overall widget through `props` - this can be a bit awkward when you are passing a callback down several levels.

## Sub-tree

The performance cost model of React is very simple to understand: every `setState` re-renders the whole sub-tree. If you want to squeeze out performance, call `setState` as low as possible and use `shouldComponentUpdate` to prevent re-rendering an large sub-tree.

## State

**Warning**: Do not sync states, you will screw it up and make it out of sync! Because you need a single source of truth.

## PropTypes

```javascript
model: React.PropTypes.instanceOf(Backbone.Model).isRequired
```

## Undo / Redo

* [StateHistory.coffee](https://github.com/jjt/TwiStrug/blob/697dfe756cf40e551ea6ebe1c8e69a587c8de595/src/libs/StateHistory.coffee)