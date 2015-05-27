# API

API driven. Treat data as content package and not as rows in a spreadsheet. Make it testable. Make it trackable.

* [**An Introduction to APIs**](https://zapier.com/learn/apis/)
* [API Evangelist](http://apievangelist.com/)
* [How to design a good API and why it matters](http://www.youtube.com/watch?gl=SG&hl=en-GB&v=aAb7hSCtvGw)
* [Writing an API wrapper in Ruby with TDD](http://code.tutsplus.com/articles/writing-an-api-wrapper-in-ruby-with-tdd--net-23875)
* [Useful tricks & tips for Grape and Rails APIs](http://codetunes.com/2014/grape-part-II/)
* [Effective developer experience](https://uxmag.com/articles/effective-developer-experience)
* [Microservice?](http://www.infoq.com/news/2014/05/nano-services)
* [Scalable Internet Architectures](http://www.infoq.com/presentations/Scalable-Internet-Architectures)
* [**HTTPie**](https://github.com/jakubroztocil/httpie)
* [**resty**](https://github.com/micha/resty)
* [**jq**](http://stedolan.github.io/jq/)
* [RESTful API design](http://restful-api-design.readthedocs.org/en/latest/)
* [Hypermedia APIs the new wild west](http://decomplecting.org/blog/2012/05/30/hypermedia-apis-the-new-wild-west/)
* [Roar and Representable - Strange API libraries](https://github.com/apotonick/roar)
* [JSON Schema](http://json-schema.org/)
* [MessagePack](http://msgpack.org/)
* [JSON for Linking Data](http://json-ld.org/)

## OAuth

* [WRAP and the demise of the OAuth community](http://hueniverse.com/2009/11/23/wrap-and-the-demise-of-the-oauth-community/)

## API Testing (TDD)

* [RSpec API](https://github.com/zipmark/rspec_api_documentation)
* [Test driving a JSON API](http://commandercoriander.net/blog/2014/01/04/test-driving-a-json-api-in-rails/)

For timestamp only use ISO 8601. And use UTC!

API design (UX)

* Persona - Who are my API users?
* Affordance
* Utilitarian
* Less is more, always start with the least functionality
* Find API use cases
* Passive usability testing - You may already have the metrics. API usage. Examine support requests.
* A great API can be among a company's greatest assets or liabilities.
* Good API tends to get reuse and is modular.
* It should be easy to evolve.
* API aims at its audience. DSL for HR!
* Start your API design with a small short spec. Agility trumps completeness. Bounce spec off as many people as possible. If you keep the spec short, it's easy to modify. Flesh it out as you gain confidence.
* API should do one thing and do it well.
* Don't let implementation details leak into your API.
* Document your API
* Don't do method-driven API like verbs all over the place
* World is big, don't look at thing in isolation
* Security, rate limiting, routing, and so on can and should be hidden in the HTTP headers
* Actions are cheap, vocabulary is expensive.

```
// Good - using noun
/payslips
/payslips/2014

// Bad - using verbs
/getAllPayslips
/getAllPayslipsByYear/2014
/insertNewItem
/insertNewItemIntoWishList
```

You use verb only if it is non-resource API like in finance industry like `/convert?SGD-USD`

## Testing

* [Effectively testing services](https://vimeo.com/103601557)

`WebMock.disable_net_connect!`

## API Vision

* What's your end-state, business objectives?
* What are you delivering?
* Foster innovation?
* What's your key metrics?
* Expose job posting API so customer can use it for their own career site
* Expose job application API so customer can pull in candidate to their own list comparison view

> A platform for recruiter
>
> Delivering talents

We have standard API for resume viewer, candidate profile API, etc. Stabilize those API modules and we can tweak the UI and delivery platform how we like it (through web or mobile). 

## Base URL and Versioning

To achieve a versionless API, a significant discipline and foresight is required.

If you choose to go versionless, you need to be careful with your JSON format and be generic and flexible, like

```
// Use this format for versionless API
{
  "phone_number": [
    { type: "Mobile", number: "98787675" }
  ]
}

// Rather than this inflexible format:
{
  "mobile_phone_number": "98787675"
}
```

```
https://api.jobline.com.sg/v1
https://apidev.jobline.com.sg/v1
application/jobline+json;application&v=1
```

## Application State (Client) and Resource State (Server)

Understanding these 2 states is the key to understand REST's statelessness concept.

[REST, where's my state?](http://ruben.verborgh.org/blog/2012/08/24/rest-wheres-my-state/)

The notion of statelessness is defined from the perspective of the server. The constraint says that the server should not remember the state of the application. As a consequence, the client should send all information necessary for execution along with each request.

The server sends a representation describing the state of a resource. The client sends a representation describing the state it would like the resource to have. That's representational state transfer.

## Behavior

* GET - Give me a *representation* of this *resource*
* PUT - Is idempotent, so you need to do full replacement. Must include all the data!
* POST - If successfully, `201 Created` + Location. For update, return `200 OK`. Not idempotent.
* DELETE - `204 No Content`, `200 OK`, `202 Accepted`. Not safe method but is idempotence.
* HEAD
* PATCH - RFC 5789
* LINK
* UNLINK
* Collection Resource
* Instance Resource

POST, GET, PUT and DELETE do not have 1:1 with CRUD

GET request is a request for a representation. It's not intended to change any resource state on the server.

## Partial Response

```
/payslips?fields=id,amount,timestamp

GET /accounts/x7y8z9?expand=directory

GET /accounts/x7y8z9?fields=givenName,directory(name)
```

## API and Rails

* [Token based authentication in Rails](http://blog.envylabs.com/post/75521798481/token-based-authentication-in-rails)
* [simple_token_authentication](https://github.com/gonzalo-bulnes/simple_token_authentication)
* [Is Devise's token safe?](https://gist.github.com/josevalim/fb706b1e933ef01e4fb6)
* [Minimal API authentication on Rails](http://resistor.io/blog/2013/08/07/mimimal-api-authentication-on-rails/)
* [Timing attack on API token?](https://gist.github.com/josevalim/fb706b1e933ef01e4fb6)
* [Timing attack](http://codahale.com/a-lesson-in-timing-attacks/)
* [rack-attack for blocking and throttling API](https://github.com/kickstarter/rack-attack#how-it-works)
* [SOA in Rails](http://www.youtube.com/watch?v=L1B_HpCW8bs)
* [OAuth for Rails](http://www.octolabs.com/blogs/octoblog/2014/04/22/service-oriented-authentication-railsconf/)
* [OAuth provider](https://github.com/doorkeeper-gem/doorkeeper)
* [Doorkeeper - Using Resource Owner Password Credentials flow ](https://github.com/doorkeeper-gem/doorkeeper/wiki/Using-Resource-Owner-Password-Credentials-flow)
* [Client Credentials flow](https://github.com/doorkeeper-gem/doorkeeper/wiki/Client-Credentials-flow)

## JSON API

* [URI Template](https://tools.ietf.org/html/rfc6570)
* [Restpack serializer example](https://github.com/RestPack/restpack_serializer)
* [HAL - Hypertext Application Language](http://stateless.co/hal_specification.html)
* [Oat](https://github.com/ismasan/oat)
* [JSON API - Steve Klabnik](https://www.youtube.com/watch?v=RzMswWbGrpI)

## Caching

API caching is not the same as asset caching as it involve dynamic content and HTTPS sensitive data. You really need to plan what API data can or can't be cached.

Private content that need to be authenticated requires even more assessment for caching. When in doubt, it is safe to not cache these API items at all.

There are 2 primary cache headers, `Cache-Control` and `Expires`. They tell the browser **when** to retrieve the resource. Other headers specify **how** to retrieve like the `ETag` (Content-based) and `Last-Modified` (Time-based).

* Response `Last-Modified` => Request `If-Modified-Since`
* Response `ETag` =>  Request `If-None-Match`

For all assets just cache to 1 year = 31536000 seconds

```
Cache-Control: public; max-age=31536000
Expires: Mon, 1 Jan 2014 00:00:00 GMT
```

* [Fast JSON APIs](http://hawkins.io/2012/07/advanced_caching_part_6-fast_json_apis/)
* [HTTP caching](https://devcenter.heroku.com/articles/http-caching-ruby-rails)
* [HTTP cache header](https://devcenter.heroku.com/articles/increasing-application-performance-with-http-cache-headers)
* Cache API that are the slowest, most frequently accessed and does not change very often. To do that you need to measure first!
* Don't forget invalidation when `PUT` or `DELETE`.
* A cache with a low hit rate does nothing for performance and might even make it worse.
* Incorrect caching can cause users to see out-of-date content and hard to debug issues. So plan your caching!
* Use private caching: `Cache-Control: private` for APIs
* Explicit no caching: `Cache-Control: no-cache, no-store`
* [Using `Rack::Cache` with memcached in Rails 4](https://devcenter.heroku.com/articles/rack-cache-memcached-rails31)
* [Fast JSON APIs in Rails](http://robots.thoughtbot.com/fast-json-apis-in-rails-with-key-based-caches-and)
* [Evaluate your JSON API for performance improvements](http://robots.thoughtbot.com/how-to-evaluate-your-rails-json-api-for-performance-improvements)

## Hypermedia

* Application state
* State transfer
* [Designing Hypermedia APIs](http://www.designinghypermediaapis.com/)
* [Glenn Block on Hypermedia](https://www.youtube.com/watch?v=vp-Na5wKlig)
* [HAL: Building hypermedia APIs in Rails](http://devblog.reverb.com/post/47197560134/hal-siren-rabl-roar-garner-building-hypermedia)
* [DHH's getting hyper about hypermedia](http://signalvnoise.com/posts/3373-getting-hyper-about-hypermedia-apis)
* [REST APIs must be hypertext driven](http://roy.gbiv.com/untangled/2008/rest-apis-must-be-hypertext-driven)
* Focus on tasks and not objects
* Expose tasks/use cases rather than objects and functions
* Favors evolvability
* WebAPI

Links to go to other resource for navigation.

Hypermedia is a strategy. Hypermedia is a way for the server to tell the client what HTTP requests the client might want to make in the future.

Think of your client as not a browser. How do you design an extensible system of navigation for your application?

Don't hardcode workflow. Twitter API is not a hypermedia API because there is no links.

"approve": "https://host/leaves/:leave_id/approve"

```
// Conveying application semantic of 'approve'
{
  "id": "UUID",
  "state": "draft",
  "links": [
    {
      "href": "https://www.jobline.com.sg/api/v1/leaves/UUID/approve",
      "rel": "approve",
      "method": "POST"
    }
  ]
}
```

When approve is no longer valid for this resource, then you won't find it at the JSON file.

Client is reactive to the changes.

### HATEOAS

Most of today's API once deployed, can't be changed. But RESTful architectures are *designed for managing change*.

![Media-type](https://dl.dropboxusercontent.com/u/6815194/Notes/hypermedia.png)

### Link Relation

By themselves, `rel="east"` don't mean anything. But Maze+XML standard defines meaning for "east" and developers can program those definitions into their clients.

A link relation is a magical string associated with a hypermedia control. It explains the change in application state (for safe requests) or resource state (for unsafe requests) that will happen if the client triggers the control.

See [IANA registry](http://www.iana.org/assignments/link-relations/link-relations.xhtml) for a list of link relations.

## Error Messages

Throw exception at the same level of abstraction. Don't throw SQLException. What happen if you change your data store?

Think of TDD, consumer developer try out your API through error message (failed test), so design it.

```
409 Conflict
{
  "status": 409,
  "code": 40924,
  "property": "name",
  "message": "A directory named '' already exists.",
  "moreInfo": "https://host/docs/api/errors/40924"
}
```

## Ruby Libraries

* [Grape - Micro-framework for REST-like APIs](https://github.com/intridea/grape)
* [Faraday](https://github.com/lostisland/faraday)
* [HTTParty](https://github.com/jnunemaker/httparty)
* [Ox - Fast SAX XML parser](https://github.com/ohler55/ox)
* [Hashie](https://github.com/intridea/hashie)
* [JSON generator - if you want some sample](http://www.json-generator.com/)

## Authentication

Give your application an API key, even if it is for internal private API, so that we can track API usage.

* Avoid sessions when possible. Authenticate every request if necessary. Stateless!
* Authorize based on resource content, not URL!
* OAuth 2, Basic over SSL only!
* Use API keys instead of username/passwords
* API Key - API key is not an authentication tool? Think of the Google Maps use-case. Google give application developer API key, but the end-user of the application is not known to Google. Google only know the application developer.
* 401 (unauthenticated) vs 403 (unauthorized)
* Challenge-response?
* Token
* JWT - JSON Web Token
* Do content transformation based on authorization
* [Cookies vs Tokens](https://auth0.com/blog/2014/01/07/angularjs-authentication-with-cookies-vs-token/)
* [Authentication with Ember.js](http://coderberry.me/blog/2013/07/08/authentication-with-emberjs-part-1/)
* [Ember auth?](http://ember-auth.herokuapp.com/docs)
* [Two-factor authentication in Rails](https://coderwall.com/p/qw7hwq)
* [And how you can screw up 2FA](http://blog.meldium.com/home/2013/8/23/screw-up-two-factor-authentication)
* [rails-csrf](https://github.com/abuiles/rails-csrf)
* [API Security](http://devcenter.kinvey.com/rest/guides/security)
* [Rack OAuth2 Sample](https://github.com/nov/rack-oauth2-sample)
* [Resource Owner Password Credentials](http://tools.ietf.org/html/draft-ietf-oauth-v2-15#section-4.3)

```
curl -X PUT \
  -H "X-CP-REST-API-Key: ABC" \
  -d '{"score":123}' \
  https://host/api/score
```

## Faraday

* [Faraday: Advanced HTTP requests made easy](http://mislav.uniqpath.com/2011/07/faraday-advanced-http/)
* [multi_xml](https://github.com/sferik/multi_xml)
* [`SSLError`](http://mislav.uniqpath.com/2013/07/ruby-openssl/)

Can we write a Faraday middleware that parse XML coming from FileMaker's `fmresultset`?

```
FaradayMiddleware::ParseFileMakerXml

response.body['metadata']
```

## Security

Do not trust incoming JSON input for Writable APIs! If your API accepts incoming parameters via HTTP POST, you must defend against many types of data attacks, including large inputs, payloads or attachments, header bombs, replay attacks, message tampering and more.

* [Secure your REST API](https://stormpath.com/blog/secure-your-rest-api-right-way/)

## Metrics (Operational)

If you serve API, it makes sense to capture usage patterns and provide metrics around them.

After that, feed the data to production management, sales, and performance tuning to make the product better.

You must capture granular metrics and you co-relate them later through various graphs like a scatterplot. For example, co-relate page views with other metrics like job applications on the same timescale.

You can ask:

* What function is the most used in which platform device? Mobile or desktop? (e.g. search for job on mobile at 6pm after office hours or 1pm during lunch-break?)
* Error rates, types of errors, system performance, latencies in request handling, timeouts, etc.
* Latencies break down by regions?
* Audit trails
* Metering reports
* Adoption rate (members)

**Ultimately, you want to know: What the numbers really meant?**

Track user interaction flow. For example, CA_A's action will be logged and we can grep their supposed user_id or IP to construct a user journey and display it to out customer support staffs. Use Ember Table to display hierarchical logs sort of like the Console syslog of Mac OS X :)

## API Examples

Look at their Content Model. What is their Content System?

API is all about data. It is essential data sharing. Think of your data first.

* [Dribbble API](http://dribbble.com/api)
* [Basecamp API](https://github.com/basecamp/bcx-api/)
* [Xero API](http://developer.xero.com/documentation/api/)
* [GitHub API v3](http://developer.github.cnom/v3/)
* [Smart Recruiters API - Good for HR](http://dev.smartrecruiters.com/)
* [Trello API](https://trello.com/docs/)
* [Uploadcare](https://uploadcare.com/documentation/rest/)
* [Hull](http://hull.io/docs/references/api)
* [PayPal hypermedia](https://developer.paypal.com/docs/api)
* [AccuWeather API](http://api.accuweather.com/)
* [The New York Times API](http://developer.nytimes.com/docs)
* [Kanbanize](https://kanbanize.com/ctrl_integration)
* [Yelp](http://www.yelp.com/developers/documentation)
* [DN](https://github.com/layervault/dn_ruby_client)
* [Dribbble new API](http://developer.dribbble.com/v1/)
* [Hacker News API](http://blog.ycombinator.com/hacker-news-api)
* [NYTimes](http://developer.nytimes.com/docs/read/article_search_api_v2)

## Videos

* [Designing a beautiful REST+JSON API](http://www.youtube.com/watch?v=5WXYw4J4QOU)
* [How to design great APIs - Parse Developer Day 2013](http://www.youtube.com/watch?v=qCdpTji8nxo)
* [Beautiful REST and JSON APIs](https://www.youtube.com/watch?v=ItXLn7diNAk)

