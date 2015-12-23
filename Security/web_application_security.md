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

## SSL

* [Deploying Diffie-Hellman for TLS](https://weakdh.org/sysadmin.html)
* 

## XSS and Content Security Policy

XSS happen when you have comment box that accept input from others but you did not escape it properly, or it can happen if you are too CMS.

```html
<!-- XSS can happen here, even if you quote it -->
<div style="background-color: {userSpecifiedColor}"></div>

<!-- IE loves CSS to be executable -->
<div style="background-color: expression(alert(localStorage))"></div>
```

Fixing XSS once and for all - Using CSP

* [Towards a Post-XSS world](http://2013.jsconf.eu/speakers/mike-west-towards-a-postxss-world.html)
* [Making CSP work for you](https://www.youtube.com/watch?v=IIcYRiVyOlw)
* [We're struggling to keep up](https://www.youtube.com/watch?v=mj-U9FlbAl0)
* [An extensible approach to browser security policy](http://yehudakatz.com/2013/05/24/an-extensible-approach-to-browser-security-policy/)
* [ember-cli CSP](https://github.com/rwjblue/ember-cli-content-security-policy#options)

CSP - HTTP header that allows policies such as:

* No eval and friends
* No inline scripts for styles
* Load scripts only from https://trusted.com
* Enforced by browsers

Other client-side security mechanisms

* X-Frame-Options (clickjacking)
* HTTP Strict Transport Security (force SSL)
* X-Content-Type-Options: nosniff;

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

## Cross-site scripting (XSS)

Untrusted and unsanitized input.

```
<div>[Untrusted Data]</div>
```

OWASP ESAPI is on such encoding.

Input fuzzing?
ReDoS - Regular Expression Denial of Service
http://taylor.fausak.me/2013/02/10/redos-regular-expression-denial-of-service/

Injecting JavaScript into pages viewed by other users. DDOS, bitcoin mining.

* [Using CSP with Rails](https://github.com/blog/1477-content-security-policy)

## Security misconfiguration

## Sensitive data exposure

## Cross-site request forgery

* [CSRF Demystified](http://www.gnucitizen.org/blog/csrf-demystified/)
* [Do I need CSRF token for Ajax?](http://stackoverflow.com/questions/9089909/do-i-need-a-csrf-token-for-jquery-ajax)
* [CSRF Prevention Cheat Sheet](https://www.owasp.org/index.php/Cross-Site_Request_Forgery_%28CSRF%29_Prevention_Cheat_Sheet)

You won't have CSRF if you use localstorage for token authentication and refuse to use cookie. If you must use cookie, HTTPS it and use `HttpOnly` so that JavaScript cannot read it.

70 ways to encode `>` :( so you can't always filter out using blacklists.

* DO NOT trust user input
* DO NOT allow GETs to modify state
* DO NOT rely on blacklists
* DO escape and sanitise HTML
* DO use whitelists or a non-HTML format like Markdown
* Do generate anti-CSRF tokens and validate them
* DO validate Referer headers (but people can fake it)


## Unvalidated redirects and forwards

## Content-Security Policy

Enforced by the browser.