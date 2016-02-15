# Web Application Security

Internet of thing security can kill people. Like insulin injection from a blue-booth device.

* Exposure of user information (email, password, identity theft)
* Direct financial gain
* Creating a botnet
* Denial of service
* Mobile and embedded system all over HTTP!

Might be a kid, might be after your server (botnet), might be after your users. Or found you randomly.

* [**The problem with securing Single Page Applications**](https://stormpath.com/blog/secure-single-page-app-problem/)
* [Pineapple WiFi](https://hakshop.myshopify.com/products/wifi-pineapple)
* [DroidSheep]
* [zANTI]
* [Hash cracker for password](http://www.hash-cracker.com/)
* [Have I been pwned](https://haveibeenpwned.com/)
* [Node Goat](https://github.com/OWASP/NodeGoat)
* [Small Improvements's security docs](https://www.small-improvements.com/documentation/security)
* [Hacking Tricks](http://www.hackingtricks.in/)
* [BSIMM](http://bsimm.com/)
* [SANS Institute](http://www.sans.org/online-security-training/)
* [metasploit - penetration testing software](http://www.metasploit.com/)
* [10 Moist Common Web Security Vulnerabilities](http://www.toptal.com/security/10-most-common-web-security-vulnerabilities)
* [Top 3 biggest mistakes enterprises make in application security](http://www.net-security.org/article.php?id=2362)
* [**Html5sec**](http://html5sec.org/)
* [Cyber Criminals are getting smarter, Organized and Sophisticated](https://medium.com/swlh/cyber-criminals-are-getting-smarter-organized-and-sophisticated-6f348b7fa408#.ng2jfygnu)

## Cross-Site Scripting (XSS)

XSS happen when you have comment box that accept input from others but you did not escape it properly, or it can happen if you are too into CMS.

> Preventing XSS with data inserted between HTML elements is very straightforward. On the other hand, preventing XSS with data inserted directly into JavaScript code is considerably more difficult and sometimes impossible.

```html
<!-- XSS can happen here, even if you quote it -->
<div style="background-color: {userSpecifiedColor}"></div>

<!-- IE loves CSS to be executable -->
<div style="background-color: expression(alert(localStorage))"></div>
```

Fixing XSS once and for all - Using CSP

* [AN Introduction to CSP](http://www.html5rocks.com/en/tutorials/security/content-security-policy/)
* [Towards a Post-XSS world](http://2013.jsconf.eu/speakers/mike-west-towards-a-postxss-world.html)
* [Postcards from the post-XSS world](http://lcamtuf.coredump.cx/postxss/)
* [Making CSP work for you](https://www.youtube.com/watch?v=IIcYRiVyOlw)
* [We're struggling to keep up](https://www.youtube.com/watch?v=mj-U9FlbAl0)
* [An extensible approach to browser security policy](http://yehudakatz.com/2013/05/24/an-extensible-approach-to-browser-security-policy/)
* [ember-cli CSP](https://github.com/rwjblue/ember-cli-content-security-policy#options)
* [**Github: Using CSP with Rails**](https://github.com/blog/1477-content-security-policy)
* [XSS prevention through CSP](http://security.stackexchange.com/questions/38001/xss-prevention-through-content-security-policy)
* [Ambiguous RFC leads to XSS](http://biasedcoin.com/blog/2012/04/12/ambiguous-RFC-leads-to-cross-site-scripting/)
* [XSS concerns in React](https://github.com/facebook/react/issues/3473)
* [XSS via a spoofed React Element](http://danlec.com/blog/xss-via-a-spoofed-react-element)

CSP - HTTP header that allows policies such as:

* No eval and friends
* No inline scripts and no inline styles
* Load scripts only from https://trusted.com
* Enforced by browsers
* Not a silver bullet. Defence in depth.
* CSP stops most forms of script injection, but it does not stop markup injection.
* Use data-xxx attributes for everything

Other client-side security mechanisms

* X-Frame-Options (clickjacking)
* HTTP Strict Transport Security (force SSL)
* X-Content-Type-Options: nosniff;

Untrusted and unsanitized input.

```
<div>[Untrusted Data]</div>
```

OWASP ESAPI is on such encoding.

Input fuzzing?
ReDoS - Regular Expression Denial of Service
http://taylor.fausak.me/2013/02/10/redos-regular-expression-denial-of-service/

Injecting JavaScript into pages viewed by other users. DDOS, bitcoin mining.

### Prevention

* [OWASP's Cheat Sheet](https://www.owasp.org/index.php/XSS_%28Cross_Site_Scripting%29_Prevention_Cheat_Sheet)

## Cross-Site Request Forgery (CSRF/XSRF)

> We're of the belief that, much like its XSS cousin, failure to mitigate this vulnerability through secure coding practices borders on the negligent.
>
> A vulnerability that is so easily prevented can lead to absolute mayhem, particularly when bundled with other attacks. Worse still, identifying the attacker is even more difficult as the attack occurs in the context of the authenticated user.

* [**BREACH - leaking of information**](http://security.stackexchange.com/questions/43669/with-breach-attack-is-session-based-csrf-token-still-secure)
* [**Rails issue#22275 - Per-form CSRF Tokens**](https://github.com/rails/rails/pull/22275)
* [CSRF Demystified](http://www.gnucitizen.org/blog/csrf-demystified/)
* [Anatomy of a CSRF Attack](http://haacked.com/archive/2009/04/02/anatomy-of-csrf-attack.aspx/)
* [DEFCON 17: CSRF! Yeah, It Still Works](https://www.youtube.com/watch?v=5Np8PrSctuM)
* [Do I need CSRF token for Ajax?](http://stackoverflow.com/questions/9089909/do-i-need-a-csrf-token-for-jquery-ajax)
* [CSRF Prevention Cheat Sheet](https://www.owasp.org/index.php/Cross-Site_Request_Forgery_%28CSRF%29_Prevention_Cheat_Sheet)
* [Rails API design without disabling CSRF protection](http://stackoverflow.com/questions/7600347/rails-api-design-without-disabling-csrf-protection)
* [Flaw in CSRF Handling in Django and Rails](https://www.djangoproject.com/weblog/2011/feb/08/security/)
* [Is exposing a session's CSRF-protection token safe?](http://stackoverflow.com/questions/144696/is-exposing-a-sessions-csrf-protection-token-safe)
* [Caching the uncacheable: CSRF Security](https://www.fastly.com/blog/Caching-the-Uncacheable-CSRF-security)

Any tags which fires a request to an external resource can be used to perform a hidden CSRF attack: `<img>`, `<link>`, `<meta>`, `<embed>`, `<object>`, etc.

You won't have CSRF if you use localStorage (but you will have XSS) for token authentication and refuse to use cookie. If you must use cookie, HTTPS it and use `HttpOnly` so that JavaScript cannot read it.

70 ways to encode `>` :( so you can't always filter out using blacklists.

One example:

```js
<a href=”http://www.example.com/#?id='”>
<img/src=”x”onerror=eval(String.fromCharCode(119,105,110,100,111,119,
46,108,111,99,97,108,83,116,111,114,97,103,101,46,115,101,116,
73,116,101,109,40,39,105,100,39,44,39,34,62,60,105,109,103,47,
115,114,99,61,92,34,120,92,34,111,110,101,114,114,111,114,61,
97,108,101,114,116,40,49,41,62,39,41))>
```

The `String.fromCharCode` makes it easier to insert the needed injection code into `localStorage` without excessive quote escaping:

```js
window.localStorage.setItem(‘id’,'”><img/src=\”x\”onerror=alert(1)>’)
```

* DO NOT trust user input
* DO NOT allow GETs to modify state
* DO NOT rely on blacklists
* DO escape and sanitise HTML
* DO use whitelists or a non-HTML format like Markdown
* Do generate anti-CSRF tokens and validate them
* DO validate Referrer headers (but people can fake it)

For SPA, when logging in, we need to have true proper anti-CSRF token from `csurf` (Node) or `protect_from_forgery` (Rails).

### Prevention

Most common prevention is to use Synchronizer Token. You can use the same token over again, but it's better to have it be a nonce (i.e. a one-time use token) to prevent Replay Attacks.

It is challenging to do Synchronizer Token in SPA as SPA templates are typically pre-compiled, static pages. Using a "Double Submit Cookie" we can send the token via cookie only for the client to send back that token via `X-Csrf-Token` header to the server. This can sort of defeat CSRF as evil.com will not be able to set custom header for a site at a different URL.

Synchronizer Token only protect against forged `POST` requests. `GET` request is still vulnerable. Just make sure you do not use `GET` requests to modify server state.

* [NoScript ABE - Application Boundaries Enforcer](https://noscript.net/abe/)
* [Request Policy](https://www.requestpolicy.com/faq.html)
* Ensure 'safe' HTTP operations, such as `GET`, `HEAD`, and `OPTIONS` cannot be used to alter any server-side state. `GET` requests should never modify server state.
* Ensure 'unsafe' HTTP operations, such as `POST`, `PUT`, `PATCH`, and `DELETE` always require a valid CSRF authenticity token.
* CSP - Content Security Policy
* Using tokens for actions that store/update/delete mail information. Can be circumvent using XSS.
* Using `Referrer` or `Origin` check. Can be spoof (Flash). Proxy strips `Origin` header. `<img>` request do not contain `Origin` header.
* Using CAPTCHAS. UX problem!
* X-Requested-With? Problematic with CORS since it is not part of simple headers?

```js
// X-Requested-With header
// For cross-domain requests, seeing as conditions for a preflight are
// akin to a jigsaw puzzle, we simply never set it to be sure.
// (it can always be set on a per-request basis or even using ajaxSetup)
// For same-domain requests, won't change header if already provided.
if ( !s.crossDomain && !headers["X-Requested-With"] ) {
  headers[ "X-Requested-With" ] = "XMLHttpRequest";
}
```

Some implementation of CSRF Token can use the same token multiple times in multiple request/response cycle. We can call this session-based CSRF Token. This may be a problem when it comes to such attacks like BREACH. It is recommended to have crypto-nonce to establish token per request/response.

* [Rails adds the token to the session cookie under the `_csrf_token` key](https://github.com/rails/rails/blob/0450642c27af3af35b449208b21695fd55c30f90/actionpack/lib/action_controller/metal/request_forgery_protection.rb#L322)
* [Learn more about Rails CSRF implementation here](https://github.com/rails/rails/issues/21948)

## TLS

* [Deploying Diffie-Hellman for TLS](https://weakdh.org/sysadmin.html)
* [HTTPS Performance Tuning](http://blog.httpwatch.com/2009/01/15/https-performance-tuning/)
* [Mozilla Server Side TLS](https://wiki.mozilla.org/Security/Server_Side_TLS#Recommended_configurations)

## JSON Hijacking

* [Re-Securing JSON](http://ejohn.org/blog/re-securing-json/)
* [JSON Hijacking](http://haacked.com/archive/2009/06/25/json-hijacking.aspx/)

## Tools

* [OpenVAS](http://www.openvas.org/)
* [Automated security testing of web applications using OWASP Zed Attack Proxy](https://blog.codecentric.de/en/2013/10/automated-security-testing-web-applications-using-owasp-zed-attack-proxy/)
* [List of testing tools](https://www.owasp.org/index.php/Appendix_A:_Testing_Tools)

OWASP

## Headers

Get rid of X-Powered-By headers or any sessionID common name.

```
X-Frame-Options: DENY
```

## Injection

* [Damn Vulnerable Web Application](http://www.dvwa.co.uk/)
* OS injection
* DO NOT trust user input
* DO NOT run code provided by the user
* DO NOT use blacklists for validation
* DO use SQL query parameters
* DO use whitelists and regexes for validation
* Do fuzz your code with invalid input

## Broken auth and session management

* DO NOT embed session id in URLs
* DO NOT trust cookie contents
* DO NOT trust URL query string contents
* DO NOT use predictable session ids
* DO use a Secure, HttpOnly cookie for session id
* DO use long, random session ids
* DO consider using OAuth
* DO reject weak passwords during signup
* DO hash and salt passwords
* Or use token and store in `localStorage`. No CSRF attack?

## Security misconfiguration

## Sensitive data exposure

## Unvalidated redirects and forwards

## Content-Security Policy

Real world security is usually provided in layers and CSP intends to be only one layer. It is nothing by a declarative policy operating on browsers that whitelists content sources. CSP is a mitigation or defence-in-depth, not a solution.

CSRF is not the primary focus of CSP, but XSS is!

Will fall back to Same Origin Policy if browsers don't support CSP.

Note: Best to set `default-src` to `none`!

* [**CSP 2015: CSP bypass in a Twitter bug**](https://blog.innerht.ml/csp-2015/)
* [**CSP The Reality**](https://embedthis.com/blog/posts/content-security-policy/)
* [CSP Level 2: July 2015](http://www.w3.org/TR/CSP11/)
* [**Check the headers**](https://securityheaders.io)
* [**HPKP: HTTP Public Key Pinning**](https://scotthelme.co.uk/hpkp-http-public-key-pinning/)
* [**Twitter: CSP to the Rescue**](https://blog.twitter.com/2013/csp-to-the-rescue-leveraging-the-browser-for-security)
* [**Dropbox experience on CSP**](https://blogs.dropbox.com/tech/2015/09/on-csp-reporting-and-filtering/)
* [An Intro to CSP](https://websec.io/2012/10/02/Intro-to-Content-Security-Policy.html)
* [The Promises of CSP](http://www.novogeek.com/post/The-promises-of-Content-Security-Policy-to-secure-the-web.aspx)
* [Using CSP to Prevent XSS](http://blog.sendsafely.com/post/42277333593/using-content-security-policy-to-prevent)
* [CSP Reference](http://content-security-policy.com/)
* [CSP proposal by Mozilla](https://wiki.mozilla.org/Security/CSP)
* [ember-cli-content-security-policy](https://github.com/rwjblue/ember-cli-content-security-policy)
* [Neil Matatall's blog](https://oreoshake.github.io/)
* [Twitter's CSP Report Collector](https://oreoshake.github.io/csp/twitter/2014/07/25/twitters-csp-report-collector-design.html)
* [CSP Reporting](https://report-uri.io/)

Enforced by the browser.

```
X-Content-Security-Policy: default-src 'self' *.jobline.com.sg
```

What Response Headers you will generally see:

```
Content-Encoding: gzip

X-CSRF-Token: K7lk3JRbv9gP/JDx

X-Content-Type-Options: nosniff
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block

Strict-Transport-Security: max-age=31536000
Content-Security-Policy: default-src https:
X-Content-Security-Policy: 

X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none

Public-Key-Pins
```

Twitter's CSP example

```
content-security-policy: default-src https: data:; report-uri https://twitter.com/i/csp_report?a=M5QXUZLCN4%3D%3D%3D%3D%3D%3D&ro=false; img-src https: data: ; script-src https://*.twitter.com https://*.twimg.com https://*.vine.co https://ssl.google-analytics.com https://bat.bing.com 'unsafe-eval' ; font-src https: data: ; frame-src https://* chrome-extension: about: javascript: ; connect-src https: ; media-src https: ; object-src https: ; style-src https:

content-security-policy: default-src https: data:; report-uri https://twitter.com/i/csp_report?a=M5QXUZLCN4%3D%3D%3D%3D%3D%3D&ro=false; img-src https: data: ; script-src https://*.twitter.com https://*.twimg.com https://*.vine.co https://ssl.google-analytics.com https://bat.bing.com 'unsafe-eval' ; font-src https: data: ; frame-src https://* chrome-extension: about: javascript: ; connect-src https: ; media-src https: ; object-src https: ; style-src 'unsafe-inline' https:
```

## Subresource Integrity

## Entry Point Regulation

## UI Redressing Attack, Clickjacking, IFRAME Overlay



## Blog

* [blog.innerht.ml](https://blog.innerht.ml)
* [Patrick Toomey](http://biasedcoin.com/)
* [Egor Homakov](http://homakov.blogspot.sg/)