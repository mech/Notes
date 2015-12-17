# Rails API

Microservices:

* High cohesion
* Separation of concerns
* Loose coupling
* Uniform interface

Large software projects stand a slim chance of ever being finished. Build for composability and disposability.

* [Simple Rails APIs with Stitches](http://multithreaded.stitchfix.com/blog/2015/11/04/simple-rails-apis-with-stitches/)
* [**React + Flux Part 1**](https://fancypixel.github.io/blog/2015/01/28/react-plus-flux-backed-by-rails-api/)
* [**React + Flux Part 2**](https://fancypixel.github.io/blog/2015/01/29/react-plus-flux-backed-by-rails-api-part-2/)
* [Got some CORS example](http://slides.com/alanpeabody/breaking-up-with-the-asset-pipeline)
* [**Building a JSON API with Rails 5**](http://blog.codeship.com/building-a-json-api-with-rails-5/)
* [**How to build a Rails 5 API only app**](http://wyeworks.com/blog/2015/6/11/how-to-build-a-rails-5-api-only-and-backbone-application)
* [**React + Flux backed by Rails API**](http://fancypixel.github.io/blog/2015/01/28/react-plus-flux-backed-by-rails-api/)
* [**Proposal for v1.0 rc2 of json-api**](https://github.com/json-api/json-api/pull/341)
* [**normalizr - Flat structure for JSON schema**](https://github.com/gaearon/normalizr)
* [Using Rails for API-only Apps - wycats](https://github.com/rails/rails/blob/efd557a60cd976ac17be9e238111a551599caeb5/railties/guides/source/api_app.textile)
* [State of Rails API](http://hawkins.io/2012/03/state_of_rails_apis/)
* [RESTful thinking considered harmful](http://www.shopify.com/technology/5898287-restful-thinking-considered-harmful)
* [Project Jellyfish API example](https://github.com/projectjellyfish)
* [The Rails API mini guide](http://www.yoniweisbrod.com/rails-api-mini-guide/)
* [Fake JSON server - Good for testing](https://github.com/typicode/json-server)
* [Consumer-Driven Contracts](http://martinfowler.com/articles/consumerDrivenContracts.html)
* [**Designing REST + JSON APIs**](https://stormpath.com/blog/designing-rest-json-apis/)
* [Understanding Rails Authenticity Token](http://stackoverflow.com/questions/941594/understand-rails-authenticity-token?rq=1)
* [Comply with JSON API specification](https://github.com/cerebris/jsonapi-resources)
* [Convert to/from camel case and underscores](https://gist.github.com/timruffles/2780508)

## API Wrapper and Serialisation

* [Ruby API wrapper using Virtus](http://www.nickdesteffen.com/blog/ruby-api-wrapper-using-virtus-and-typhoeus)


## Rails ORM/ActiveModel attributes

* [Hashie Considered Harmful - An Ode to Hash and OpenStruct](http://www.schneems.com/2014/12/15/hashie-considered-harmful.html)
* [Struct inheritance is overused](http://thepugautomatic.com/2013/08/struct-inheritance-is-overused/)
* [Right way to override a setter in Rails](http://stackoverflow.com/questions/10464793/what-is-the-right-way-to-override-a-setter-method-in-ruby-on-rails)
* [Overwriting default accessor for ActiveRecord model](http://api.rubyonrails.org/classes/ActiveRecord/Base.html#class-ActiveRecord%3a%3aBase-label-Overwriting+default+accessors)
* [Avoid Rails when generating JSON responses with Postgres](https://dockyard.com/blog/2014/05/27/avoid-rails-when-generating-json-responses-with-postgresql)

```ruby
def questions=(value)
  super('hijack')
  
  # Or
  
  self[:questions] = 'hijack'
end
```

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
* [Is Devise token secure?](http://stackoverflow.com/questions/18605294/is-devises-token-authenticatable-secure)
* [Place API key in headers](http://stackoverflow.com/questions/5517281/place-api-key-in-headers-or-url)
* [A Lesson in Timing Attacks](http://codahale.com/a-lesson-in-timing-attacks/)

Token based authentication is stateless. We are not storing any information about our user on the server or in a session (cookie).

Every single request will require the token. This token should be sent in the HTTP header. Token stored on client side. Completely stateless, and ready to be scaled. Load balancers are able to pass a user along to any of our servers since there is no state or session information anywhere.

There is also token revocation that allows us to invalidate a specific token and even a group of tokens based on the same **authorization grant**.

## ActiveModel::Serializer

* [Serializer with array](http://stackoverflow.com/questions/17542793/how-do-you-initialize-an-activemodelserializer-class-with-an-activerecordrel)

## has_secure_password

* [Validating Users with `has_secure_password`](https://quickleft.com/blog/rails-tip-validating-users-with-has_secure_password/)
* [Why I roll my own authentication](http://www.rvdh.de/2012/01/12/why-i-roll-my-own-authentication/)
* [**Don't use BCrypt**](http://www.unlimitednovelty.com/2012/03/dont-use-bcrypt.html)
* [Taking password storage up a notch](https://blog.8thlight.com/adam-gooch/2012/11/04/taking-password-storage-up-a-notch.html)
* [Some best practices for authentication in Ruby on Rails](http://www.fngtps.com/2015/some-best-practices-for-authentication-in-ruby-on-rails/)

## Sparse Fieldsets

* [json-api](https://github.com/dgeb/json-api/blob/v1rc2/format/index.md#sparse-fieldsets-)

## Sorting

## Pagination

* [Issue #977 - Pagination Serializer](https://github.com/rails-api/active_model_serializers/pull/977)

## Videos

* [Creating RESTful, Hypermedia-based Microservices](https://www.youtube.com/watch?v=zbeMDM-zDNI)