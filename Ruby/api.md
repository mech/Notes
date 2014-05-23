# API

* [How to design a good API and why it matters](http://www.youtube.com/watch?gl=SG&hl=en-GB&v=aAb7hSCtvGw)
* [Writing an API wrapper in Ruby with TDD](http://code.tutsplus.com/articles/writing-an-api-wrapper-in-ruby-with-tdd--net-23875)
* [Useful tricks & tips for Grape and Rails APIs](http://codetunes.com/2014/grape-part-II/)
* [Effective developer experience](https://uxmag.com/articles/effective-developer-experience)
* [Microservice?](http://www.infoq.com/news/2014/05/nano-services)
* [Scalable Internet Architectures](http://www.infoq.com/presentations/Scalable-Internet-Architectures)

API design (UX)

* Persona - Who are my API users?
* Affordance
* Utilitarian
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

```
// Good - using noun
/payslips
/payslips/2014

// Bad - using verbs
/getAllPayslips
/getAllPayslipsByYear/2014
```

You use verb only if it is non-resource API like in finance industry like `/convert?SGD-USD`

## Application State (Client) and Resource State (Server)

Understanding these 2 states is the key to understand REST's statelessness concept.

[REST, where's my state?](http://ruben.verborgh.org/blog/2012/08/24/rest-wheres-my-state/)

The notion of statelessness is defined from the perspective of the server. The constraint says that the server should not remember the state of the application. As a consequence, the client should send all information necessary for execution along with each request.


## Partial Response

```
/payslips?fields=id,amount,timestamp
```

## API and Rails

* [Token based authentication in Rails](http://blog.envylabs.com/post/75521798481/token-based-authentication-in-rails)
* [simple_token_authentication](https://github.com/gonzalo-bulnes/simple_token_authentication)
* [Is Devise's token safe?](https://gist.github.com/josevalim/fb706b1e933ef01e4fb6)

## Caching

* [Fast JSON APIs](http://hawkins.io/2012/07/advanced_caching_part_6-fast_json_apis/)


## Hypermedia

* Application state
* State transfer
* [Glenn Block on Hypermedia](https://www.youtube.com/watch?v=vp-Na5wKlig)
* [HAL: Building hypermedia APIs in Rails](http://devblog.reverb.com/post/47197560134/hal-siren-rabl-roar-garner-building-hypermedia)
* [DHH's getting hyper about hypermedia](http://signalvnoise.com/posts/3373-getting-hyper-about-hypermedia-apis)
* [REST APIs must be hypertext driven](http://roy.gbiv.com/untangled/2008/rest-apis-must-be-hypertext-driven)

Links to go to other resource for navigation.

Think of your client as not a browser. How do you design an extensible system of navigation for your application?

Don't hardcode workflow. Twitter API is not a hypermedia API because there is no links.

"approve": "https://host/leaves/:leave_id/approve"

```
{
  "id": "UUID",
  "state": "draft",
  "links": [
    {
      "href": "https://www.jobline.com.sg/api/v1/leaves/UUID/approve",
      "del": "approve",
      "method": "POST"
    }
  ]
}
```

When approve is no longer valid for this resource, then you won't find it at the JSON file.

Client is reactive to the changes.

## Error Messages

Throw exception at the same level of abstraction. Don't throw SQLException. What happen if you change your data store?

Think of TDD, consumer developer try out your API through error message (failed test), so design it.

## Ruby Libraries

* [Grape - Micro-framework for REST-like APIs](https://github.com/intridea/grape)
* [Faraday](https://github.com/lostisland/faraday)
* [HTTParty](https://github.com/jnunemaker/httparty)
* [Ox - Fast SAX XML parser](https://github.com/ohler55/ox)
* [Hashie](https://github.com/intridea/hashie)
* [JSON generator - if you want some sample](http://www.json-generator.com/)

## Authentication

* API Key
* Token
* JWT - JSON Web Token
* [Cookies vs Tokens](https://auth0.com/blog/2014/01/07/angularjs-authentication-with-cookies-vs-token/)
* [Authentication with Ember.js](http://coderberry.me/blog/2013/07/08/authentication-with-emberjs-part-1/)
* [Ember auth?](http://ember-auth.herokuapp.com/docs)
* [Secure your REST API](https://stormpath.com/blog/secure-your-rest-api-right-way/)
* [Two-factor authentication in Rails](https://coderwall.com/p/qw7hwq)
* [And how you can screw up 2FA](http://blog.meldium.com/home/2013/8/23/screw-up-two-factor-authentication)

```
curl -X PUT \
  -H "X-CP-REST-API-Key: ABC" \
  -d '{"score":123}' \
  https://host/api/score
```


## API Examples

* [Dribbble API](http://dribbble.com/api)
* [Xero API](http://developer.xero.com/documentation/api/)
* [GitHub API v3](http://developer.github.com/v3/)
* [Smart Recruiters API - Good for HR](http://dev.smartrecruiters.com/)
* [Trello API](https://trello.com/docs/)
* [Uploadcare](https://uploadcare.com/documentation/rest/)
* [Hull](http://hull.io/docs/references/api)
* [PayPal hypermedia](https://developer.paypal.com/docs/api)

## Videos

* [Designing a beautiful REST+JSON API](http://www.youtube.com/watch?v=5WXYw4J4QOU)
* [How to design great APIs - Parse Developer Day 2013](http://www.youtube.com/watch?v=qCdpTji8nxo)