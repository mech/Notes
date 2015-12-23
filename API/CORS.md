# Cross-Origin Resource Sharing

JSON-P is just a hack to bypass same-origin as the `<script>` tag does not respect the same-origin policy. Can only do GET request. Has security issues.

* [**MDN for CORS**](https://developer.mozilla.org/en-US/docs/Web/HTTP/Access_control_CORS)
* [Browser supports for CORS](http://caniuse.com/#feat=cors)
* [The Same-Origin Saga](https://vimeo.com/54121245)
* [Origin policy enforcement in modern browser](https://www.youtube.com/watch?v=PbvxtMCUG8U)
* [HTTP Strict Transport Security](https://www.owasp.org/index.php/HTTP_Strict_Transport_Security)
* [Enable CORS](http://enable-cors.org/)
* [rack-cors](https://github.com/cyu/rack-cors)
* [RubyConf 12 - Building modular, scalable web apps? Of CORS!](https://www.youtube.com/watch?v=VQA2yrpI7Xk)
* [Example](https://github.com/mbleigh/cors-talk-example)
* [Cross-domain Ajax with CORS - Nicholas C. Zakas](http://www.nczonline.net/blog/2010/05/25/cross-domain-ajax-with-cross-origin-resource-sharing/)
* [Rails 4, CORS, JWT and Devise](https://www.youtube.com/watch?v=_CAq-F2icp4)
* [That's so fetch - Some CORS issues](http://jakearchibald.com/2015/thats-so-fetch/)
* [Same-Origin Policy](https://annevankesteren.nl/2015/02/same-origin-policy)

CORS let JavaScript XHR to securely communicate with cross-domain resources.

Organizations can publish read/write(R/W GET/POST) JSON APIs or make their entire data sets accessible to the world of JavaScript.

**It is not as simple as adding an HTTP header to your server and calling it a day**

While other programming languages have no restrictions on HTTP requests, JavaScript in a browser has the same-origin policy issue that prevent requests from different sites.

CORS is unique in that it has both a server-side and client-side component.

## The Problem

The browser's same-origin policy limit client code (i.e. JavaScript) from making HTTP requests to different origins.

## The CORS Request

```
('withCredentials' in (new XMLHttpRequest()));
```

The XHR underwent a revision around 2010 that enable CORS.

By setting `xhr.withCredentials = true;` you include cookie. Your server also must be setup to accept such setting.

IE8 and IE9 support a limited set of cross-origin requests using `XDomainRequest` object.

jQuery's `dataType` indicates that the response should be parsed as JSON. This saves the developer the additional step of using `JSON.parse` to parse the  response text into a JSON object.

```
$.ajax(url, {
	dataType: "json",
	xhrFields: { withCredentials: true },
	headers: { 'X-Requested-With': 'XMLHttpRequest' }});
```

POST request include:

```
Origin: https://www.jobline.com.sg
Access-Control-Request-Method: POST
Access-Control-Request-Headers: ???
```

Server response will be:

```
Access-Control-Allow-Origin: https://www.jobline.com.sg
Access-Control-Allow-Method: POST, GET
Access-Control-Allow-Headers: ???
Access-Control-Allow-Credentials: true
Access-Control-Max-Age: 1728000
```

## Server-Side

CORS gives servers the flexibility to configure cross-origin access in a variety of ways:

* Which domains are allowed to make requests
* Which HTTP methods are allowed
* Which headers are allowed on the HTTP request
* Whether or not requests may include cookie data
* Which response headers the client can read

Any custom headers must be sanctioned by the server. Client cannot anyhow set custom headers like `X-Requested-With`

The server has many reasons to reject a CORS request. It may allow cross-origin `GET` and `POST` requests, but not `PUT` or `DELETE` requests.

```
gem 'rack-cors', require: 'rack/cors'

# In application or config.ru
use Rack::Cors do
  allow do
    origins '*'
    resource '/public/*'
  end
  
  allow do
    origins 'localhost:3000', 'jobline.com.sg'
    resource '/private/*',
      methods: [:get, :post, :put, :delete, :options, :patch],
      headers: 'x-special-header',
      expose: ['X-Special-Response-Header']
  end
end
```

```
▶ curl -H "Origin: http://localhost:8000" --verbose http://localhost:3000/employments/S6414
```

## Headers

Only the following **simple headers** are allowed to to cross domain:

* Accept
* Accept-Language
* Content-Language
* Last-Event-ID
* Content-Type

### Pre-flight Checks

Debug with `chrome://net-internals/#events`

```
Preflight Headers:
  Content-Type: text/plain
  Access-Control-Allow-Origin: http://localhost:8000
  Access-Control-Allow-Methods: GET, POST, DELETE, PUT, PATCH, OPTIONS, HEAD
  Access-Control-Expose-Headers:
  Access-Control-Max-Age: 1728000
  Access-Control-Allow-Credentials: true
  Access-Control-Allow-Headers: accept, authorization, x-user-email
Incoming Headers:
  Origin: http://localhost:8000
  Access-Control-Request-Method:
  Access-Control-Request-Headers:
```

### Authorization

You can use per request tokens, e.g. OAuth.

## Vulnerability and Incidents

* Rosetta Flash