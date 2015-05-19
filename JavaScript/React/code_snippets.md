# Code Snippets

```
Perf.printWasted()
```

```
// Can't use mixin, use fat arrow
render() {
  return (
    <input type="text"
      value={this.state.inputText}
      onChange={e => this.setState({inputText: e.target.value})}
      onKeyPress={this.handleKeyPress} />
  );}
```

```
// Weird ES6
moveBox(id, left, top) {
  this.setState(update(this.state, {
    boxes: {
      [id]: {
        $merge: {
          left: left,
          top: top        }      }    }  }));}
```

```
// Iterating
return (
  <div>
    {this.props.list.map(function(data, idx) {
      return <Component data={data} key={idx} />;    })}
  </div>
);
```

```
<RouteHandler {...this.props} />
```