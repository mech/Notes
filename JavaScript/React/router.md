# Router

* [**Original router code**](https://gist.github.com/ryanflorence/21ce8cb052eebbe7dac3)
* [React Router's Future to 2.0](https://medium.com/rackt-and-roll/react-router-s-future-c026c0f2874f#.y0m3xcsbi)
* [**React Router Changes**](https://github.com/rackt/react-router/pull/1158)
* [React Router Component - Another solution](http://strml.viewdocs.io/react-router-component)
* [rrouter - A newer version](https://github.com/andreypopp/rrouter)
* [react-crossroads](https://github.com/react-crossroads/react-crossroads)
* [monorouter](https://github.com/matthewwithanm/monorouter)
* [nested-router - New experiment](https://github.com/ryanflorence/nested-router)
* [**A React Router with Hasher?**](https://medium.com/@collardeau/a-react-router-a058a05ded46)
* [**Passing props with React Router**](http://blog.pavan.io/post/122405568754/passing-props-with-react-router-a-beginners)
* [**Server-side rendering with React and React Router**](http://ifelse.io/2015/08/27/server-side-rendering-with-react-and-react-router/)
* [Ryan Florence's and Michael Jackson's brainchild](https://github.com/rackt/react-router)
* [React nested router](https://www.youtube.com/watch?v=P6xTa3RRzfA#t=2300)
* [Dynamically placed outlets vs Ember portal?](https://twitter.com/ryanflorence/status/572992231239372800)
* [React Router Overview](https://github.com/rackt/react-router/blob/master/docs/guides/overview.md)
* [Support React 0.13 GitHub issue](https://github.com/rackt/react-router/issues/638)

In React Router, unlike Ember, nested route do not correspond to nested URL. It gives you complete freedom of what your URL look like. Just because you nest a route doesn't mean you need to append a segment to the URL to match.

Routing is just data: `location.hash.substr(1)`

* [Original React Router code by Ryan Florence](https://gist.github.com/ryanflorence/491d482d2ff1071ac020)
* [Fluxxor React Router Guide](http://fluxxor.com/examples/react-router.html#/)
* [Does Relay routing replace react-router?](https://gist.github.com/wincent/598fa75e22bdfa44cf47#What_about_routing)
* [Support React version 0.13 #638](https://github.com/rackt/react-router/issues/638)
* [Server-side rendering landed in React Router](https://github.com/rackt/react-router/commit/1b1a62b04b73f01eb64b3a0983c9c6781e65b6b9?diff=unified)
* [react-router vs react-router-component](https://groups.google.com/forum/#!msg/reactjs/WFwti82PWx4/GEPXdS_FvBsJ)

## Examples

* [Kitematic routes](https://github.com/kitematic/kitematic/blob/master/src/Routes.js)
* [Percolate Studio's routes file](https://github.com/percolatestudio/percolatestudio.com/blob/master/app/components/Routes.jsx)
* You can use `react-async` if you want to fetch XHR before perform a route switch. Like blurring the list view before switching or abort.
* [RequelPro](https://github.com/jmdobry/RequelPro/blob/master/src/RequelPro/app.jsx)

## Overview

> Nested route is nested UI. You should only nest your routes if your UI is nested. - [From Ember](http://fromrailstoember.com/9-nested-routes-equals-nested-ui/)

1. You declare your view hierarchy with nested `<Route />`
2. React Router will match the deepest route against the URL and activate the entire tree of routes on that branch, nesting all the UI.
3. You simply use the `<RouteHandler />` component and it will render the active child route.

```
<Router>
  <Route name="app" path="/" component={App}>
    <Route name="inbox" component={Inbox} />
    <Route name="calendar" component={Calendar} />
    <DefaultRoute component={Dashboard} />
  </Route>
</Router>

Router.run(routes, function(Handler) {
  React.render(<Handler />, document.body);});
```

Whenever a hash change, a callback will be called. This callback is being registered and setup at `Router.run()`. It just pass in a `Handler` to be inserted into the view's `<RouteHandler />`.

It is just like the `{{outlet}}` in Ember. Can we have multiple `<RouteHandler />`?

Think of Router as describing your interface rather than a URL structure. Routes are completely independent from the URL of API resources. Even if your API URLs are nested, it does not necessarily mean that your React routes should be.

## Dynamic Segments

Explicit static paths match more closely than dynamic paths.

## Transition

```
transition.redirect('/login');
transition.retry();
transition.abort();
```

## Link

## Code Splitting and Partial Application Loading

* [Welcome to Future of Web App Delivery](https://medium.com/@ryanflorence/welcome-to-future-of-web-application-delivery-9750b7564d9f#.92jy4id68)
* [example-react-router-server-rendering-lazy-routes](https://github.com/rackt/example-react-router-server-rendering-lazy-routes)

You no need to define your entire route config up front anymore as 1.0 brings first-class support for code-splitting on routes so that adding routes deep in your app doesn't increase the size of the initial bundle.

## DFA and NFA?

* [Rex, Rexical and Rails routing](http://blog.bigbinary.com/2013/02/01/rex-rexical-and-rails-routing.html)
* [Aaron Patterson - Journey](https://vimeo.com/38916678)