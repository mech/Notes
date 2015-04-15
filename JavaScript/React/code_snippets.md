# Code Snippets

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