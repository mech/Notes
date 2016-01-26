# Rails API

Microservices:

* High cohesion
* Separation of concerns
* Loose coupling
* Uniform interface

Large software projects stand a slim chance of ever being finished. Build for composability and disposability.

* [**Building a modern bridge between Ember 2 and Rails 5 with JSON API**](http://emberigniter.com/modern-bridge-ember-and-rails-5-with-json-api/)
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

```
▶ curl -H "Content-Type: application/json; charset=utf-8" -d '{"user": {"name":"mech"}}' http://localhost:3000/users

▶ curl -H "Accept: application/json" -H "Content-Type: application/json" 'http://localhost:3000/users' -d '{??}'
```

## API Wrapper and Serialisation

* [Ruby API wrapper using Virtus](http://www.nickdesteffen.com/blog/ruby-api-wrapper-using-virtus-and-typhoeus)
* [transit-ruby - Better than JSON. From Cognitect.](https://github.com/cognitect/transit-ruby)
* [MessagePack - It's like JSON but fast and small](http://msgpack.org/)


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

## ActiveModel::Serializer

* [Serializer with array](http://stackoverflow.com/questions/17542793/how-do-you-initialize-an-activemodelserializer-class-with-an-activerecordrel)
* [**jsonapi-resources**](https://github.com/cerebris/jsonapi-resources)
* [**WIP - Deserializer implementation**](https://github.com/rails-api/active_model_serializers/pull/950)

> Right now AMS can serialize JSON API but can't deserialize it so it won't work correctly. AMS is making progress on that regard and we should be seeing a new version supporting JSON API in both directions soon. - Santiago Pastorino

```ruby
class PostSerializer < ActiveModel::Serializer
  # Fragment caching title only
  cache key: 'post', expires_in: 3.hours, only: [:title]
  attributes :title, :body
end
```

## ParamsParser

* [Mostly remove the ParamsParser middleware](https://github.com/rails/rails/commit/38d2bf5fd1f3e014f2397898d371c339baa627b1)



## Sparse Fieldsets

* [json-api](https://github.com/dgeb/json-api/blob/v1rc2/format/index.md#sparse-fieldsets-)

## Sorting

## Pagination

* [Issue #977 - Pagination Serializer](https://github.com/rails-api/active_model_serializers/pull/977)

## HTTP Status Code

* **201 - :created**
* 202 - :accepted
* **204 - :no_content**
* 205 - :reset_content
* 206 - :partial_content
* 
* 301 - :moved_permanently
* 302 - :found
* 303 - :see_other
* **304 - :not_modified**
* 305 - :use_proxy
* 307 - :temporary_redirect
* 
* 400 - :bad_request
* **401 - :unauthorized**
* 402 - :payment_required
* 403 - :forbidden
* **404 - :not_found**
* 405 - :method_not_allowed
* 406 - :not_acceptable
* 408 - :request_timeout
* 409 - :conflict
* 410 - :gone
* **422 - :unprocessable_entity**
* 423 - :locked
* 
* 500 - :internal_server_error
* 501 - :not_implemented
* 502 - :bad_gateway
* 503 - :service_unavailable

```ruby
# Always use the correct status code. 202 is job accepted for processing, but not yet finished.
class ReportsController < ApplicationController
  def create
    ReportJob.perform_later
    head 202
  end
end
```

## API Tests

API is not the time nor place to test business logic. You should leave that for Unit Tests.

Test only these 3 things for API:

1. Status Code
2. Mime Types
3. Authentication

Requesting endpoints and verifying responses. That's all. Do your business logic testing at Unit Tests.

Use integration test for API testing.

```ruby
require 'test_helper'

class ListingProjectsTest < ActionDispatch::IntegrationTest
  setup { host! 'api.example.com' }

  test 'returns list of projects' do
    get '/projects', {}, { Authorization: "Token token=#{@user.auth_token}" }
    assert_equal 200, response.status
    assert_equal Mime::JSON, response.content_type
    refute_empty response.body
  end
end
```

## Videos

* [Creating RESTful, Hypermedia-based Microservices](https://www.youtube.com/watch?v=zbeMDM-zDNI)
* [RailsConf 2015 - AMS, API, Rails and a developer, a love story](https://www.youtube.com/watch?v=PqgQNgWdUB8)