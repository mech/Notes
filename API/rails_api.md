# Rails API

Microservices:

* High cohesion
* Separation of concerns
* Loose coupling
* Uniform interface

Large software projects stand a slim chance of ever being finished. Build for composability and disposability.

* [**React + Flux backed by Rails API**](http://fancypixel.github.io/blog/2015/01/28/react-plus-flux-backed-by-rails-api/)
* [**Proposal for v1.0 rc2 of json-api**](https://github.com/json-api/json-api/pull/341)
* [Using Rails for API-only Apps - wycats](https://github.com/rails/rails/blob/efd557a60cd976ac17be9e238111a551599caeb5/railties/guides/source/api_app.textile)
* [State of Rails API](http://hawkins.io/2012/03/state_of_rails_apis/)
* [RESTful thinking considered harmful](http://www.shopify.com/technology/5898287-restful-thinking-considered-harmful)
* [Project Jellyfish API example](https://github.com/projectjellyfish)
* [The Rails API mini guide](http://www.yoniweisbrod.com/rails-api-mini-guide/)
* [Fake JSON server - Good for testing](https://github.com/typicode/json-server)
* [Consumer-Driven Contracts](http://martinfowler.com/articles/consumerDrivenContracts.html)

## API Gateway

* [Optimizing Netflix API](http://techblog.netflix.com/2013/01/optimizing-netflix-api.html)

Single point of entry into microservice architecture. Simplify the client by moving logic for calling multiple services from the client to API gateway.

An event-driven, reactive approach. Each many services are invoked in parallels on local network and slotted in to a single endpoint to be presented to the API gateway.

Asynchronous requests are composed together via the reactive framework.

With a collapsed single request optimized for client, we pay the price of WAN latency only.

## Token Based API

* [The ins and outs of token based authentication](https://scotch.io/tutorials/the-ins-and-outs-of-token-based-authentication)
* [Getting to know JSON Web Tokens](https://scotch.io/tutorials/the-anatomy-of-a-json-web-token)
* [Token based authentication in Rails](https://www.codeschool.com/blog/2014/02/03/token-based-authentication-rails/)
* [Why Devise remove token authentication](http://blog.plataformatec.com.br/2013/08/devise-3-1-now-with-more-secure-defaults/)

Token based authentication is stateless. We are not storing any information about our user on the server or in a session (cookie).

Every single request will require the token. This token should be sent in the HTTP header. Token stored on client side. Completely stateless, and ready to be scaled. Load balancers are able to pass a user along to any of our servers since there is no state or session information anywhere.

There is also token revocation that allows us to invalidate a specific token and even a group of tokens based on the same **authorization grant**.

## has_secure_password

* [Validating Users with `has_secure_password`](https://quickleft.com/blog/rails-tip-validating-users-with-has_secure_password/)
* [Why I roll my own authentication](http://www.rvdh.de/2012/01/12/why-i-roll-my-own-authentication/)

## Sparse Fieldsets

* [json-api](https://github.com/dgeb/json-api/blob/v1rc2/format/index.md#sparse-fieldsets-)

## Sorting

## Pagination

## Videos

* [Creating RESTful, Hypermedia-based Microservices](https://www.youtube.com/watch?v=zbeMDM-zDNI)