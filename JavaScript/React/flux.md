# Flux

* [Flux comparison](https://github.com/voronianski/flux-comparison)
* [Stores are not models](https://medium.com/@jetupper/hello-react-js-b87c63526e3a)
* [Facebook flux-chat example](https://github.com/facebook/flux/tree/master/examples/flux-chat/js)
* [Cortex - centrally managing data with React](https://github.com/mquan/cortex/)
* [Flocks.js](http://www.flocks.rocks/what_is_flocks.html)
* [Writing complex app using Flux and React](http://madebymany.com/blog/beyond-the-to-do-app-writing-complex-applications-using-flux-react-js)
* [What is the Flux application architecture?](https://medium.com/brigade-engineering/what-is-the-flux-application-architecture-b57ebca85b9e)
* [flux-react-router-example](https://github.com/gaearon/flux-react-router-example/)

> Manipulation of state should be restricted to the Stores and if there's a need to enqueue atomic updates based on previous values, it can be done within the callback of `this.setState`, and never directly on `this.state`. The latter should only be read from and never manipulated on.
> 
> Maintain a discipline to only read from state and to never manipulate state objects, this will save us a lot of headaches.

## Authentication with Flux

* [Adding authentication to your React Flux app](https://auth0.com/blog/2015/04/09/adding-authentication-to-your-react-flux-app/)

## Flummox

* [Why Flux component is better than Flux mixin](https://github.com/acdlite/flummox/blob/v3.5.1/docs/docs/guides/why-flux-component-is-better-than-flux-mixin.md)