# Router

In React Router, unlike Ember, nested route do not correspond to nested URL. It gives you complete freedom of what your URL look like. Just because you nest a route doesn't mean you need to append a segment to the URL to match.

* [Original React Router code by Ryan Florence](https://gist.github.com/ryanflorence/491d482d2ff1071ac020)
* [Fluxxor React Router Guide](http://fluxxor.com/examples/react-router.html#/)
* [Does Relay routing replace react-router?](https://gist.github.com/wincent/598fa75e22bdfa44cf47#What_about_routing)
* [Support React version 0.13 #638](https://github.com/rackt/react-router/issues/638)

## Overview

> Nested route is nested UI

1. You declare your view hierarchy with nested `<Route />`
2. React Router will match the deepest route against the URL and activate the entire tree of routes on that branch, nesting all the UI.
3. You simply use the `<RouteHandler />` component and it will render the active child route.

```
<Route name="app" path="/" handler={App}>
  <Route name="inbox" handler={Inbox} />
  <Route name="calendar" handler={Calendar} />
  <DefaultRoute handler={Dashboard} />
</Route>

Router.run(routes, function(Handler) {
  React.render(<Handler />, document.body);});
```

Whenever a hash change, a callback will be called. This callback is being registered and setup at `Router.run()`. It just pass in a `Handler` to be inserted into the view's `<RouteHandler />`.

It is just like the `{{outlet}}` in Ember. Can we have multiple `<RouteHandler />`?

## Dynamic Segments

Explicit static paths match more closely than dynamic paths.

## Transition

```
transition.redirect('/login');
transition.retry();
transition.abort();
```

## DFA and NFA?

* [Rex, Rexical and Rails routing](http://blog.bigbinary.com/2013/02/01/rex-rexical-and-rails-routing.html)
* [Aaron Patterson - Journey](https://vimeo.com/38916678)