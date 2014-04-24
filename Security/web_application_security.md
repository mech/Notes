# Web Application Security

* Exposure of user information (email, password, identity theft)
* Direct financial gain
* Creating a botnet
* Denial of service
* Mobile and embedded system all over HTTP!

Might be a kid, might be after your server (botnet), might be after your users. Or found you randomly.

* [Pineapple WiFi](https://hakshop.myshopify.com/products/wifi-pineapple)
* [DroidSheep]
* [zANTI]
* [Hash cracker for password](http://www.hash-cracker.com/)
* [Have I been pwned](https://haveibeenpwned.com/)

OWASP

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

Injecting JavaScript into pages viewed by other users. DDOS, bitcoin mining.

* [Using CSP with Rails](https://github.com/blog/1477-content-security-policy)

## Security misconfiguration

## Sensitive data exposure

## Cross-site request forgery

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