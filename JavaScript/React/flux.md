# Flux

* [Flux comparison](https://github.com/voronianski/flux-comparison)
* [Stores are not models](https://medium.com/@jetupper/hello-react-js-b87c63526e3a)

> Manipulation of state should be restricted to the Stores and if there's a need to enqueue atomic updates based on previous values, it can be done within the callback of `this.setState`, and never directly on `this.state`. The latter should only be read from and never manipulated on.
> 
> Maintain a discipline to only read from state and to never manipulate state objects, this will save us a lot of headaches.

## Authentication with Flux

* [Adding authentication to your React Flux app](https://auth0.com/blog/2015/04/09/adding-authentication-to-your-react-flux-app/)

