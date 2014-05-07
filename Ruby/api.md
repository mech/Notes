# API

* [How to design a good API and why it matters](http://www.youtube.com/watch?gl=SG&hl=en-GB&v=aAb7hSCtvGw)
* [Writing an API wrapper in Ruby with TDD](http://code.tutsplus.com/articles/writing-an-api-wrapper-in-ruby-with-tdd--net-23875)
* [Useful tricks & tips for Grape and Rails APIs](http://codetunes.com/2014/grape-part-II/)
* [Effective developer experience](https://uxmag.com/articles/effective-developer-experience)

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

## Videos

* [Designing a beautiful REST+JSON API](http://www.youtube.com/watch?v=5WXYw4J4QOU)