# Design

1. Model around business domain. See DDD. Bounded context and sub-domain.
2. Embrace culture of automation.
3. Hide implementation details. Hide your database. Always use API service to affect your database.
4. Decentralise all the things
5. Deploy independently. Consumer-Driven Contracts.
6. Consumer first
7. Isolate failure. Don't do distributed point of failure!
8. Highly observable

> Always separate thinking about real-world things from the documents which describe those things. Resource before representation. - Mike Atherton

Document-driven development. Test-driven also! Code style-guide. Code review. Pair-programming.

One of the central notions of the Web is that we separate the identity of a resource from its representation and implementation.

* [Humane Registry](http://martinfowler.com/bliki/HumaneRegistry.html)
* [Distributed Systems and the End of the API](http://writings.quilt.org/2014/05/12/distributed-systems-and-the-end-of-the-api/)
* [**Caring doesn't scale**](https://www.oreilly.com/ideas/caring-doesnt-scale)
* [**Best practices for a pragmatic RESTful API**](http://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api)
* [HTTP API design guide extracted from work on the Heroku Platform API](https://github.com/interagent/http-api-design)
* [Heroku's HTTP API Design Guide](http://www.infoq.com/news/2014/08/heroku-http-design-guide)
* [API Evangelist](http://101.apievangelist.com/)
* [JSON API 1.0 Released](http://www.cerebris.com/blog/2015/06/04/jsonapi-1-0/)
* [A well-designed API approach](https://www.airpair.com/rest/posts/a-well-designed-api-approach)
* [OAuth.io blog](http://blog.oauth.io/)
* [REST API concept](https://www.youtube.com/watch?v=7YcW25PHnAA)
* [**JSON Graph: Reactive REST at Netflix**](http://applicative.acm.org/speaker-JafarHusain.html)
* [Single Page Apps in Depth](http://singlepageappbook.com/index.html)
* [Endpoints Framework](http://endpointsjs.com/)
* [React.js and Spring Data REST](http://spring.io/blog/2015/09/15/react-js-and-spring-data-rest-part-2-hypermedia)

You can't design the API well if you don't know the product well.

Design for intent. Know what the intent of the endpoint is. Don't be clever for your API. It has to be clear and straightforward.

* [Designing a Beautiful REST+JSON API](https://www.youtube.com/watch?v=5WXYw4J4QOU)
* [Workshop: Developer-focused API Design](https://www.youtube.com/watch?v=8p10bGFM9dg)

```
// BAD design, verb
https://api.jobline.com.sg/getAccount

// Better and make use of HTTP method instead
https://api.jobline.com.sg/account
```

## Platform

It makes more sense to build platforms instead of just products or applications. Platforms are like ecosystems interconnecting different applications, services, users, developers and partners.

## Problem + Abstraction

Every model is just an approximation of reality, able to produce an outcome (i.e. a solution to a problem).

Everything can be a problem space in which you find solution.

## Web

The Web represents an abstraction of HTTP. REST represents an abstraction of the Web. The Web is an application and it respects the "constraints" by REST.

## Constraints

Constraints may be imposed for technical, policy, or other reasons.

Architectural constraints for REST:

* **Orthogonal** - Clear separation of concerns and functions between client and server. Server components are kept simple to improve scalability while client are complex and ever-changing. Components can be developed and evolved independently.
* **Stateless** - Requests are treated independently. Requests must carry all necessary information. The message is self-descriptive, meaning all the information needed to complete the task is actually contained in the message.
* **Cacheable**
* **Layered and hierarchical** - Like OSI model. Each component "sees" and operates only with the layer with which it is immediately interacting.
* **Code-on-demand** - Control state. The control state resides in the requested resource representation. Therefore obtaining the "first" representation is top priority. Links are flow control.

For example in a HR application for CA, the Leave is a resource representation that is the initial request and is of top priority. From this first representation, we can link to other state like "cancel" state, "approve" state, etc.
	
## Error Handling

Everything is distributed and asynchronous. Many potential breaking points! How do you handle it gracefully? Retry? Re-authentication?

# Resource

Resource representation. Topology of connected components. Draw a map of your resources, your components.

## Collection Resource

```
{
  "offset": 0,
  "limit": 25,
  "first": {},
  "previous": null,
  "next": {"href": ""},
  "last": {},
  "items": [
    {"href": ""},
    {}
  ]}
```

## Instance Resource

## Date

Use ISO 8601

## Use camelCase

```
{
  'userName': 'mech'
  'createdTimestamp': '2012-07-10T18:02:23.345Z'}
```

## Linking

Hypermedia is paramount. Linking is fundamental to scalability. Always link to one-self.

```
GET /accounts/123?expand=directory

200 OK
{
  "href": "https://api.jobline.com.sg/accounts/123",
  "givenName": "mech",
  "directory": {
    "href": "https://api.jobline.com.sg/directories/234",
    "name": "interviews"  }
}
```

Use `?expand=directory` to pull in more data and cache it.

Use `?_body=false` to skip body response when POST to create a new resource.

## Pagination

* [GitHub: Traversing with Pagination](https://developer.github.com/guides/traversing-with-pagination/)
* [Pagination done the Postgres Way](https://wiki.postgresql.org/images/3/35/Pagination_Done_the_PostgreSQL_Way.pdf)
* [Kaminari recipes](https://github.com/amatsuda/kaminari/wiki/Kaminari-recipes)
* [How does Kaminari paginate?](http://patshaughnessy.net/2011/9/10/how-does-kaminari-paginate)

```
?offset=50&limit=25
```

## Usage Patterns

Always track your API usage patterns. How many calls to each endpoint.

