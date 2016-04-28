# Form

HTML form elements are very stateful!

React helps you move the state out of the DOM into your components. 

* [Designing more efficient forms structure](https://uxplanet.org/designing-more-efficient-forms-structure-inputs-labels-and-actions-e3a47007114f#.ama7nvnk4)
* [**Forms in React and Redux**](http://x-team.com/2016/02/tutorial-forms-in-react-and-redux/)
* [formsy-react](https://github.com/christianalfoni/formsy-react)
* [tcomb-form](https://github.com/gcanti/tcomb-form)
* [newforms](https://github.com/insin/newforms)
* [Disable submit button when making Ajax requests](https://medium.com/@collardeau/to-react-from-jquery-disable-a-button-f5f6cc0ea885)
* [react-json](https://github.com/arqex/react-json)
* [react-radio-group](https://github.com/chenglou/react-radio-group)
* [zxcvbn - Password strength estimation](https://blogs.dropbox.com/tech/2012/04/zxcvbn-realistic-password-strength-estimation/)
* [RESTful forms with React, Part 1](http://blog.littleblimp.com/post/124492420923/restful-forms-with-react-part-1)
* [Complex, validated JSON-based forms in React](https://github.com/andrewhathaway/Winterfell)
* [Form validation tutorial with React](https://html5hive.org/reactjs-form-validation-tutorial/)

Either store the form state within the component or Flux store.

See http://jsbin.com/copiqakisu/1/edit?js,output
See https://github.com/christianalfoni/formsy-react/issues/120

```jsx
<select value={this.state.selected} onChange={this.onChange}>
  <option value="SG">Singapore</option>
  <option value="UK">United Kingdom</option>
</select>
```

## Controlled and Uncontrolled Components

Uncontrolled components are rarely good to use. They don't allow you to render based on the current value of inputs, and your code is written in a DOM-centric way rather than in a data-centric way. They also make composition more difficult because there's no standard way to get the value of an input in a composite component.

* [Controllables](https://jquense.github.io/react-widgets/docs/#/controllables)

## Synthetic Event

For elements that have children, you need to use `e.currentTarget`.

To get the underlying event, use `e.nativeEvent`, but it is rarely needed.

## Refs

Refs is an escape hatch for React's declarative nature.

Keep in mind that although `refs` and `findDOMNode` are powerful, they should only be used when there is no other way to achieve the functionality you need. Using them hinders React's ability to optimize performance and increases the complexity of your application, so you should only reach for them when conventional techniques fall short of the capabilities you need.

Works only in `componentDidMount` and any event handlers.

* [How should refs work?](https://github.com/facebook/react/issues/3234)

```js
handleClick: function() {
  // Wanting to focus is a very example of when to use refs
  // Unique only in this component the refs `nameInput`
  this.refs.nameInput.focus();},

render: function() {
  return(
    <div>
      <input type="text" ref="nameInput" />
      <button onClick={this.handleClick}>Focus</button>
    </div>
  );}
```

Before using `ref`, exhaust your options of using the reactive data flow approach. `ref` is a way to talk to the "backing instance" of the real DOM element.

Refs are a great way to send a message to a particular child instance in a way that would be inconvenient to do via streaming Reactive `props` and `state`. They should, however, not be your go-to abstraction for flowing data through your application. By default, use the Reactive data flow and save `refs` for use cases that are inherently non-reactive.

Refs are automatically destroyed for you. No worrying about memory leaking unless you do something crazy to retain a reference.

Take a moment and think more critically about where `state` should be owned in the component hierarchy.

```js
// Other uses
<input type="text" ref={(input) => this._author = input} />

// On your handler you can use it
_handleSubmit(e) {
  let author = this._author;
  this.props.addComment(author.value);
}
```

## Form State

* [2-way data binding with `LinkedStateMixin`](http://facebook.github.io/react/docs/two-way-binding-helpers.html)

## Validations

* [Thinking outside the DOM](http://www.sitepoint.com/thinking-outside-dom-concepts-setup/)
* [Validating children](http://www.mattzabriskie.com/blog/react-validating-children)
* [blur-input](https://github.com/Khan/react-components/blob/master/js/blur-input.jsx)
* [Video - Form validation made simple](https://www.youtube.com/watch?v=FqscLiODo5c)
* [vacuumlabs/validation](https://github.com/vacuumlabs/validation)

Hack the console.log to show validation also.