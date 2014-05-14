# API

* [How to design a good API and why it matters](http://www.youtube.com/watch?gl=SG&hl=en-GB&v=aAb7hSCtvGw)
* [Writing an API wrapper in Ruby with TDD](http://code.tutsplus.com/articles/writing-an-api-wrapper-in-ruby-with-tdd--net-23875)
* [Useful tricks & tips for Grape and Rails APIs](http://codetunes.com/2014/grape-part-II/)
* [Effective developer experience](https://uxmag.com/articles/effective-developer-experience)
* [Microservice?](http://www.infoq.com/news/2014/05/nano-services)

API design (UX)

* Persona - Who are my API users?
* Passive usability testing - You may already have the metrics. API usage. Examine support requests.
* A great API can be among a company's greatest assets or liabilities.
* Good API tends to get reuse and is modular.
* It should be easy to evolve.
* API aims at its audience. DSL for HR!
* Start your API design with a small short spec. Agility trumps completeness. Bounce spec off as many people as possible. If you keep the spec short, it's easy to modify. Flesh it out as you gain confidence.
* API should do one thing and do it well.
* Don't let implementation details leak into your API.
* Document your API

## API and Rails

* [Token based authentication in Rails](http://blog.envylabs.com/post/75521798481/token-based-authentication-in-rails)
* [simple_token_authentication](https://github.com/gonzalo-bulnes/simple_token_authentication)
* [Is Devise's token safe?](https://gist.github.com/josevalim/fb706b1e933ef01e4fb6)


## Hypermedia

* Application state
* State transfer
* [Glenn Block on Hypermedia](https://www.youtube.com/watch?v=vp-Na5wKlig)
* [HAL: Building hypermedia APIs in Rails](http://devblog.reverb.com/post/47197560134/hal-siren-rabl-roar-garner-building-hypermedia)
* [DHH's getting hyper about hypermedia](http://signalvnoise.com/posts/3373-getting-hyper-about-hypermedia-apis)

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