# Higher-order Components

> You can use HOC in various situations like authentication: `requireAuth({ role: 'admin' })(MyComponent)` (check for a user in higher component and redirect if the user is not logged in) or connecting your component with Flux/Redux store.
> 
> You can also separate data fetching and controller-like logic to higher order components and keep our views as simple as possible.

How do you wrap your components? What does wrapping even mean?

A higher-order component is merely a function that takes an existing component and returns a new component that wraps it with useful functionalities. The wrapping component will take care to render the wrapped component and also forwards the props to it, but also adds some useful behavior.

* [**HOC in depth**](https://medium.com/@franleplant/react-higher-order-components-in-depth-cf9032ee6c3e#.ofucbtu54)
* [Higher Order React Components](http://natpryce.com/articles/000814.html)
* [Structuring React Applications: Higher-Order Components](http://jamesknelson.com/structuring-react-applications-higher-order-components/)
* [Higher-order components?](https://gist.github.com/sebmarkbage/ef0bf1f338a7182b6775)
* [Mixins are dead. Long live composition.](https://medium.com/@dan_abramov/mixins-are-dead-long-live-higher-order-components-94a0d2f9e750)
* [Functional UI and Components as Higher Order Functions](http://blog.risingstack.com/functional-ui-and-components-as-higher-order-functions/)
* [Sideways data loading](https://github.com/facebook/react/issues/3398)
* [See Flummox's custom rendering](https://github.com/acdlite/flummox/blob/v3.5.1/docs/docs/api/fluxcomponent.md#custom-rendering)

React 0.14 switches to [parent-based context](https://github.com/facebook/react/pull/3615).

**Note**: Lambdas are frequently confused with anonymous functions, closures, first-class functions, and higher-order functions. The concepts are all similar, but they mean different things.

Not all lambdas are closures, and not all closures are lambdas. A closure is created when a function references data that is contained outside the function scope. A lambda is a function that is used as a value.

> HoCs are very similar to higher-order functions. In higher-order functions you pass one function to another function which returns a function. How does that help us? Well, with higher-order components, you pass a component (which as we know is just a function) to another function, which returns a component (again, is just a function).

## Examples

* [React loadable component with spinner example](https://gist.github.com/BurntCaramel/a60029d22257291799cd)

```js
// This is a higher-order container component accepting
// a presentation component which is a pure-function.
// The container component just handle all the states logic.
const ContainerHoC = function(PresentationComponent) {
  return React.createClass({
    componentDidMount() {
      const success = (notifications) => {
        this.setState({ notifications: notifications });
      };

      $.ajax({ url: '/notifications', success: success });
    },

    onMarkAsRead(id) {},

    render() {
      return (
        <PresentationComponent
          notification={this.state.notifications}
          onMarkAsRead={this.onMarkAsRead} />
      );
    }
  });
}

const Notifications = ContainerHoC(React.createClass({
  renderNotification({notification}) {
    const { id, date, message } = notification;

    return (
      <div>
        <span>{message} - {date}</span>
        <button onClick={this.props.onMarkAsRead.bind(null, id)}>Mark as Read</button>
      </div>
    );
  },

  render() {
    return <div>{this.props.notifications.map(renderNotification)}</div>;
  }
}));

const App = React.createClass({
  render() {
    return <Notifications />
  }
});
```

## Decorators

