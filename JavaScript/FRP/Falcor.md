# Falcor

> Most data is not a tree.

> The specs for JSON Graph and JSON-LD have some overlap, and likewise Falcor has some overlap with the JSON-LD implementations. How do Falcor and JSON Graph relate to JSON-LD? It appears to me they are very similar, except Falcor requires more changes to the backend server but also provides more control over data shape and caching than is currently provided by JSON-LD framing.

* [The future of web development - React, Falcor, and ES6](http://engineering.widen.com/blog/future-of-the-web-react-falcor/)
* [REST orthodoxy?](https://news.ycombinator.com/item?id=9473519)
* [David Nolan on HATEOAS through Falcor lens](https://twitter.com/swannodette/status/642701397813776384)

Released on Aug 2015.

Data must be efficiently retrieved from the network and intelligently cached on the client.

```js
JSON.stringify(response, null, 2)
```

* JSON Graph - Fix hierarchical nature of traditional JSON objects. Fix duplicates. Customises data to application's view.

This is bad RPC API:

```
http://www.netflix.com/genreLists?pageSize=10x15&titleprops=id,boxshot
```

UI team vs Server team. When UI people want a particular fields, they need to discuss with Server people to serialise that JSON in.

One of the key problems that Falcor solves is the fact that HTTP wasn't designed and really isn't optimized for how web applications should ideally request data. With HTTP, only a single resource can be retrieved per request. One resource, one endpoint, one result. Since web applications tend to need to request many small resources, many HTTP requests are often required to get all the data the application needs.

## Cache Coherence

Falcor lets us cache data intelligently on the client's device. The cache won't duplicates data.

How to make it transparent to the developer? When we request some data, the first 20 records may be in the cache and the next 10 records need to be pulled down from the server. How do we make this sync and async operation transparent to developer? We will use Observable. Observable is essential a stream of data. When it is done, you will know it and close the stream connection.

Observable is a push-pull problem, not sync-async problem.

## Data Source

Data source is how we tie JSON Graph information from the back-end to our model.

The DataSource implements a Router interface that lets us build Routes on the server that we can wire up to respond with data.

The interface for DataSource are: `get`, `set` and `call`

## Router and route

## JSON Graph

JSON objects traditionally represent data hierarchically, as trees. But data is much more often a graph.

Falcor essentially customises data to application's view. Falcor does this through its JSON Graph convention, which is used to model graph information as a JSON object.

JSON Graph benefits: Serializable and Partitionable



## JavaScript Path

A sequence of keys that refer to a specific location within a JSON object and can be of type `string`, `boolean`, `number`, or `null`.

No `object` or `array` here! Data within arrays or objects often tend to become arbitrarily large over time, so Falcor makes it illegal for us to access them directly, to force us to craft our paths more thoughtfully and only retrieve the data that we actually need.

# Videos

* [Reactive REST](http://www.infoq.com/presentations/netflix-reactive-rest)
* [Falcor and Angular 2](https://www.youtube.com/watch?v=WL54eYbTJUw)
* [Jafar Husain's Falcor playlist](https://www.youtube.com/watch?list=PL-7Rk5Igg3dfdxlNKNSMJHfK_yG5ceiZf&v=xby_MUlBOw0)
* [Falcor: Simplifying your data](https://www.youtube.com/watch?v=nCksc3tdM-A)
