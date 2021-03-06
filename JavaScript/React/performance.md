# Performance

> The techniques that make React fast are not new. We've known for a long time that touching the DOM is expensive, you should batch write and read operations, event delegation is faster...

> People still talk about them because in practice, they are very hard to implement in regular JavaScript code. What makes React stand out is that all those optimizations happen by default. This makes it hard to shoot yourself in the foot and make your app slow.

> The performance cost model of React is also very simple to understand: every `setState` re-renders the whole sub-tree. If you want to squeeze out performance, call setState as low as possible and use `shouldComponentUpdate` to prevent re-rendering an large sub-tree.

Virtual DOM (difference algorithm), event delegation, batched DOM updates all contribute to make React fast out of the box. But if rendering many items, it can still lag! To counter that we can use Immutable.js or RxJS observable.

**Example:**

http://binarymuse.github.io/react-primer/build/index.html?6

* [Make your React app 15x faster](http://reactuniversity.com/how-to-make-your-react-apps-15x-faster/)
* [Optimize ES6 Code For Output Minification (Ninja Tricks Included)](https://medium.com/modus-create-front-end-development/optimize-es6-output-size-performance-ninja-tricks-included-d4fc2d313f66#.d51n5pchx)
* [**why-did-you-update**](https://github.com/garbles/why-did-you-update)
* [React+Performance=? by Paul Lewis](https://aerotwist.com/blog/react-plus-performance-equals-what/)
* [Preventing layout thrashing](http://wilsonpage.co.uk/preventing-layout-thrashing/)
* [**Perf audit for reddit-mobile**](https://github.com/reddit/reddit-mobile/issues/247)
* [Rendering large datasets with AngularJS and React](http://www.bennadel.com/blog/2864-rendering-large-datasets-with-angularjs-and-reactjs.htm)
* [Using MOBservable for FRP](https://www.mendix.com/tech-blog/making-react-reactive-pursuit-high-performing-easily-maintainable-react-apps/)
* [**Optimizing React performance using keys, component lifecycle, and performance tools**](http://jaero.space/blog/react-performance-1/)
* [Adventures in React Performance Debugging](http://blog.siftscience.com/blog/2016/browser-dgaf-that-you-use-react)
* [How to Make Your React Apps 15x Faster](https://reactjsnews.com/how-to-make-your-react-apps-10x-faster)
* [Performance optimisations for React applications](https://medium.com/@alexandereardon/performance-optimisations-for-react-applications-b453c597b191#.km9z9z6nh)
* [**A DEEP DIVE INTO REACT PERF DEBUGGING**](http://benchling.engineering/deep-dive-react-perf-debugging/)

## How to determine if you have a performance bottleneck?

* [PERFORMANCE ENGINEERING WITH REACT](http://benchling.engineering/performance-engineering-with-react/)

---

1. Browser should render at 60fps which give you 16ms to work with.
2. [Forced synchronous layouts](https://developers.google.com/web/tools/chrome-devtools/profile/rendering-tools/forced-synchronous-layouts)

## Keys

* [Do not use array index as key!](http://jaero.space/blog/react-performance-1)

Keys are defined in parent components, not in child components.

```js
class StoogeList extends Component {
  render() {
    return (
      <ul>
        {this.props.stooges.map (stooge) => {
          return <Stooge key={stooge.id} />
        }}
      </ul>
    )
  }
}

class Stooge extends Component {
  render() {
    return <li>{ this.props.stooge.name }</li>
  }
}
```

`StoogeList` has to specify the keys of each of its children. The `Stooge` component doesn't need to worry about keys at all, because **it's only rendering a single element**.

## Mobile Performance with Text Input

* [pure-render-decorator](https://github.com/felixgirault/pure-render-decorator)
* [Advanced Performance @React blog](https://facebook.github.io/react/docs/advanced-performance.html)
* [Rendering from the top is bad!](https://github.com/reactjs/redux/issues/1176)

```js
var shallowEqual = require('shallowEqual')

shouldComponentUpdate(nextProps, nextState) {
  return (
    !shallowEqual(this.props, nextProps) ||
    !shallowEqual(this.state, nextState)
  )
}
```

Or

```js
import shallowCompare from 'react-addons-shallow-compare'

shouldComponentUpdate(nextProps, nextState) {
  return shallowCompare(this, nextProps, nextState)
}
```

`shallowEqual` compare the value of the key on first-level only. Deeply nested object cannot use this equality check. Better to Immutable.js for that.

Be mindful of these 2 things:

1. Callback handlers that are bound in `render()` will always fail `shallowEqual`. Define your callback in the constructor instead.
2. In addition to event handlers bound in `render()`, it is probably also worth mentioning that any component which takes jsx children will also always fail `shallowEqual`, since the children elements will be re-created for every render.

## Videos

* [Speed up Server Side Rendering - Sasha Aickin](https://www.youtube.com/watch?v=PnpfGy7q96U)