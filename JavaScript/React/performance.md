# Performance

Virtual DOM (difference algorithm), event delegation, batched DOM updates all contribute to make React fast out of the box. But if rendering many items, it can still lag! To counter that we can use Immutable.js or RxJS observable.

* [React+Performance=? by Paul Lewis](https://aerotwist.com/blog/react-plus-performance-equals-what/)
* [Preventing layout thrashing](http://wilsonpage.co.uk/preventing-layout-thrashing/)
* [**Perf audit for reddit-mobile**](https://github.com/reddit/reddit-mobile/issues/247)
* [Rendering large datasets with AngularJS and React](http://www.bennadel.com/blog/2864-rendering-large-datasets-with-angularjs-and-reactjs.htm)
* [Using MOBservable for FRP](https://www.mendix.com/tech-blog/making-react-reactive-pursuit-high-performing-easily-maintainable-react-apps/)
* [**Optimizing React performance using keys, component lifecycle, and performance tools**](http://jaero.space/blog/react-performance-1/)

## Keys

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