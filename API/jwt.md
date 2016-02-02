# JWT

Is JWT just a re-implementation of Rails signed cookie?

* [**Using JSON Web Tokens to authenticate JavaScript front-ends on Rails**](http://zacstewart.com/2015/05/14/using-json-web-tokens-to-authenticate-javascript-front-ends-on-rails.html)
* [Authentication with Rails, JWT and ReactJS](http://nebulab.it/blog/authentication-with-rails-jwt-and-react/)
* [Cookie-free authentication with JWT](http://www.toptal.com/web/cookie-free-authentication-with-json-web-tokens-an-example-in-laravel-and-angularjs)
* [Draft IETF](http://self-issued.info/docs/draft-ietf-oauth-json-web-token.html)
* [Decode JWT in iOS](http://popdevelop.com/2013/12/decode-json-web-token-jwt-in-ios-objective-c/)
* [Where to store your JWTs - Cookies vs localStorage](https://stormpath.com/blog/where-to-store-your-jwts-cookies-vs-html5-web-storage/)
* [Use JWT the Right Way](https://stormpath.com/blog/jwt-the-right-way/)
* [Discuss JWT at Auth0 Forum](https://ask.auth0.com/c/jwt)
* [rails-angular-jwt-example](https://github.com/Foxandxss/rails-angular-jwt-example)

JWT give you a structured and stateless way to declare a user and what they can access (their scope).

JWT is cryptographically signed and encrypted to prevent tampering on the client side.

JWT is given to your users after they present some credentials like username and password, but they can also provide API keys, or even tokens from another service.

The most important thing about JWT is that they are signed. This ensures the claims have not been tampered with when stored and passed between your service and another service. So if the claims say it need to expire in 20 mins, then your server can be sure that has not been tampered with.

If you want the claims to be further encrypted, you need to use JSON Web Encryption (JWE).

## Vulnerabilities

* [Critical vulnerabilities in JWT libraries](https://www.chosenplaintext.ca/2015/03/31/jwt-algorithm-confusion.html)
* [Does JWT put your web app at risk?](http://blog.prevoty.com/does-jwt-put-your-web-app-at-risk)

### Expiration

Must expire token, you can't let attacker use old token.

## Where to store JWT?

For Web app, you got 2 options:

* HTML5 Web Storage `localStorage` and `sessionStorage`
* Cookies with HTTPS and HttpOnly (immune to XSS, but not CSRF).

To safely use Web Storage, you must 100% ensure your web app is immune to XSS attacks. That is you sanitize all user inputs and all your `params` are checked. However, this is harder for modern web apps nowadays as many rely on third-party libraries. What happen if those JS libraries are compromised?

[OWASP do not recommend Web Storage to store JWT](https://www.owasp.org/index.php/HTML5_Security_Cheat_Sheet#Local_Storage) and so is [this advice](https://blog.whitehatsec.com/web-storage-security/).

This left HTTPS cookies with HttpOnly flag as the only viable secured way to store token and transport them across to your API server.

Modern developers are hesitant to use cookies because they traditionally required state to be stored on the server, thus breaking the RESTful best practices.

However, cookies are a storage mechanism do not require state to be stored on the server if you are storing a JWT in the cookie. This is because JWT is "self-contained".

But cookies are susceptible to CSRF attacks. To prevent this, you need to synchronize additional CSRF token for server to check through. This mean enabling `protect_from_forgery`.

### Rails API

In rails-api, controller do not have layouts, templates rendering, cookies, sessions, flash, assets, etc.

Why would you need both `cookies` and `session` hash in Rails? They are similar but not the same. `session` is an entire hash that gets put in the secure session cookie that expires when the user closes the browser. Whilst `cookies` get stored individually and not as a whole.

CORS has the `Origin` header. Can that be enough to prevent CSRF? Unlikely.

If we use `protect_from_forgery`, Rails will store the token in the session, to which the attacker does not have access.

Strictly speaking, a default Rails session is now mostly stateless as well, as all the data in the session is stored on the client side, in cookies. The default Rails session store, the cookie store, stores a maximum of 4k of data.

* [Sessions and Cookies in Rails](http://pothibo.com/2013/09/sessions-and-cookies-in-ruby-on-rails/)
* [All about cookies](http://www.allaboutcookies.org/)

Cookie is not encrypted prior to Rails 4.

Rails uses a `CookieStore` to handle sessions. What it means is that all the informations needed to identify a user's session is sent to the client and nothing is stored on the server.

By default, Rails does not store the session id on the server.