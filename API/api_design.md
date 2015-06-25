# Design

* [HTTP API design guide extracted from work on the Heroku Platform API](https://github.com/interagent/http-api-design)
* [Heroku's HTTP API Design Guide](http://www.infoq.com/news/2014/08/heroku-http-design-guide)
* [API Evangelist](http://101.apievangelist.com/)
* [JSON API 1.0 Released](http://www.cerebris.com/blog/2015/06/04/jsonapi-1-0/)
* [A well-designed API approach](https://www.airpair.com/rest/posts/a-well-designed-api-approach)
* [OAuth.io blog](http://blog.oauth.io/)
* [REST API concept](https://www.youtube.com/watch?v=7YcW25PHnAA)

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

```
?offset=50&limit=25
```

## Error


## Usage Patterns

Always track your API usage patterns. How many calls to each endpoint.

