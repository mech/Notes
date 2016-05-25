# Authentication

* [Rails Tutorial - Chapter 8 - Log in, log out](https://www.railstutorial.org/book/log_in_log_out)
* [**How to do stateless & cookie-less authentication**](http://stackoverflow.com/questions/20588467/how-to-do-stateless-session-less-cookie-less-authentication)
* [MailChimp API v3.0 OAuth2](http://kb.mailchimp.com/api/article/about-oauth2)
* [Gems you might not need! AdminController and Forbid pattern](https://vimeo.com/39498553)
* [proof - Secure Authentication for SPA](https://github.com/undercase/proof)
* [How to handle users with a Rails API and JS front-end](https://www.reddit.com/r/rails/comments/3dzvha/how_to_handle_users_with_a_rails_api_and_js/)
* [OAuth and JavaScript](http://alexbilbie.com/2014/11/oauth-and-javascript/)
* [How to do auth with a REST API right?](http://stackoverflow.com/questions/15051712/how-to-do-authentication-with-a-rest-api-right-browser-native-clients)
* [Building a Stateless Rails API with React](http://fredguest.com/2015/03/06/building-a-stateless-rails-api-with-react-and-twitter-oauth/)
* [**See the shortcoming part!**](http://emberigniter.com/implementing-authentication-with-ember-services/)
* [Reflux: Authentication Flow - Some useful JWT examples](https://preact.gitbooks.io/react-book/content/flux/auth.html)
* [How to do authentication with a REST API right?](http://stackoverflow.com/questions/15051712/how-to-do-authentication-with-a-rest-api-right-browser-native-clients)

Provider is at https://api.jobline.com.sg/v1. Consumer will be:

* Jobline Web (React.js): https://www.jobline.com.sg
* Jobline Mobile (iOS and Android)
* Companies? Maybe some access
* Candidates? Maybe not!

The de-facto practice for API authentication is to provide an API Key/Secret combination to the consumer of your API and have them submit as the `Authorization` header on every request.

## Re-login with a Modal

* [Implementing a smart Login Modal with Redux, reselect and ReactJS](https://medium.com/@dorsha/implement-login-modal-with-redux-reselect-and-reactjs-668c468bcbe3#.10s6j3h97)

```
Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==
```

The header will be sent on every request. Assuming you use HTTPS, this is a secure way to authenticate users.

## Resource Owner Password Credential Grant

A temporary transitional phase.

Authenticate the "resource owner" with credential (username/password) in order to exchange for a token.

The token returned can be random Bearer token or JSON Web Tokens (JWT).

## Separate Logins Table

```sql
CREATE TABLE logins(
  id bigint PRIMARY KEY DEFAULT id_generator(),
  user_id bigint NOT NULL,
  provider VARCHAR(50) NOT NULL DEFAULT 'local',
  provider_key VARCHAR(255), -- email
  provider_token VARCHAR(255) NOT NULL -- password
);

ALTER TABLE logins
ADD CONSTRAINT logins_users
FOREIGN KEY (user_id) REFERENCES users(id)
ON DELETE CASCADE;
```

## The flow

* [OAuth 2 Resource Owner Password Credentials flow](http://stackoverflow.com/questions/19912551/oauth2-resource-owner-password-credentials-flow)

Visit https://api.jobline.com.sg/token to login

```
curl -X POST https://api.jobline.com.sg/token --data "email=xxx&password=yyy&grant_type=password"
```

Server returns `access_token`.

```
{
  "access_token": "???",
  "token_type": "Bearer",
  "expires_in": 10,
  "scope": ""
}
```

With the `access_token`, use it to make protected requests.

```
curl -X POST -H "Authorization: Bearer ???" -H "Content-Type: application/json;charset=UTF8" -d '{"title":"demo"}' https://api.jobline.com.sg/protected/resources
```

## Token Based API

* [10 Things You Should Know about Tokens](https://auth0.com/blog/2014/01/27/ten-things-you-should-know-about-tokens-and-cookies)
* [**The Problem with Securing SPA**](https://stormpath.com/blog/secure-single-page-app-problem/)
* [The ins and outs of token based authentication](https://scotch.io/tutorials/the-ins-and-outs-of-token-based-authentication)
* [Getting to know JSON Web Tokens](https://scotch.io/tutorials/the-anatomy-of-a-json-web-token)
* [Token based authentication in Rails](https://www.codeschool.com/blog/2014/02/03/token-based-authentication-rails/)
* [Why Devise remove token authentication](http://blog.plataformatec.com.br/2013/08/devise-3-1-now-with-more-secure-defaults/)
* [Is Devise token secure?](http://stackoverflow.com/questions/18605294/is-devises-token-authenticatable-secure)
* [Place API key in headers](http://stackoverflow.com/questions/5517281/place-api-key-in-headers-or-url)
* [A Lesson in Timing Attacks](http://codahale.com/a-lesson-in-timing-attacks/)
* [Stateless Authentication with REST API](http://www.kaleidos.net/blog/295/stateless-authentication-with-api-rest/)
* [How Rails Sessions Work](http://www.justinweiss.com/articles/how-rails-sessions-work/)
* [Where to store your JWT? Cookies vs Web Storage](https://stormpath.com/blog/where-to-store-your-jwts-cookies-vs-html5-web-storage/)
* [simple_token_authentication](https://github.com/gonzalo-bulnes/simple_token_authentication)
* [**Auth token from Devise**](https://gist.github.com/gonzalo-bulnes/7659739). See also [**Original gist from Jose Valim**](https://gist.github.com/josevalim/fb706b1e933ef01e4fb6)

Token based authentication is stateless. We are not storing any information about our user on the server or in a session (cookie).

Every single request will require the token. This token should be sent in the HTTP header. Token stored on client side. Completely stateless, and ready to be scaled. Load balancers are able to pass a user along to any of our servers since there is no state or session information anywhere.

There is also token revocation that allows us to invalidate a specific token and even a group of tokens based on the same **authorization grant**.

## XSS, CSRF?

Forged requests are nasty attacks. They rely on the fact that browser automatically adds cookies to HTTP requests if it has cookies associated with the target domain and path. That include session cookies.

CSRF target state-changing requests, not theft of data, since attacker has no way to see the response to the forged request.

CSRF is not the same as XSS. It only work if target is logged in and thus have a small attack footprint.

Without the browser to automatically attach cookie, there will be no CSRF attack!

* [CSRF Protection Bypass in Rails 3.0.2](http://weblog.rubyonrails.org/2011/2/8/csrf-protection-bypass-in-ruby-on-rails/)
	
## Bcrypt

Using `has_secure_password` and `has_secure_token`

```
BCrypt::Engine::DEFAULT_COST = 10
```

`has_secure_password` already checks for existence and confirmation on create.

* [**Don't use BCrypt**](http://www.unlimitednovelty.com/2012/03/dont-use-bcrypt.html)
* [**How we cracked millions of AM bcrypt hashes efficiently**](http://cynosureprime.blogspot.sg/2015/09/how-we-cracked-millions-of-ashley.html)
* [How to safely store a password](http://codahale.com/how-to-safely-store-a-password/)
* [**Simple Authentication with BCrypt**](https://gist.github.com/thebucknerlife/10090014)
* [With Rails 4.1](http://robert-reiz.com/2014/04/12/has_secure_password-with-rails-4-1/)* [Validating Users with `has_secure_password`](https://quickleft.com/blog/rails-tip-validating-users-with-has_secure_password/)
* [Why I roll my own authentication](http://www.rvdh.de/2012/01/12/why-i-roll-my-own-authentication/)
* [Taking password storage up a notch](https://blog.8thlight.com/adam-gooch/2012/11/04/taking-password-storage-up-a-notch.html)
* [Some best practices for authentication in Ruby on Rails](http://www.fngtps.com/2015/some-best-practices-for-authentication-in-ruby-on-rails/)

## Hack Study

* [How I hacked GitHub again](http://homakov.blogspot.sg/2014/02/how-i-hacked-github-again.html)