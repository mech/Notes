# Cross-Origin Resource Sharing

JSON-P is just a hack to bypass same-origin as the `<script>` tag does not respect the same-origin policy. Can only do GET request. Has security issues. Although JSON-P is useful, it is strictly limited to GET requests. CORS builds on top of XHR to allow developers to make cross-domain requests.

* [Cookies with CORS](https://quickleft.com/blog/cookies-with-my-cors/)
* [**Test for browser support**](https://test-cors.appspot.com/#technical)
* [CORS for JSON and Rails](http://www.tsheffler.com/blog/2011/02/22/cross-origin-resource-sharing-for-json-and-rails/)
* [**CORS on MDN**](https://developer.mozilla.org/en-US/docs/Web/HTTP/Access_control_CORS)
* [HTML5 Rocks: Using CORS](http://www.html5rocks.com/en/tutorials/cors/)
* [Nicholas C.Zakas's explanation of CORS](https://www.nczonline.net/blog/2010/05/25/cross-domain-ajax-with-cross-origin-resource-sharing/)
* [The Same-Origin Saga](https://vimeo.com/54121245)
* [Origin policy enforcement in modern browser](https://www.youtube.com/watch?v=PbvxtMCUG8U)
* [HTTP Strict Transport Security](https://www.owasp.org/index.php/HTTP_Strict_Transport_Security)
* [Enable CORS](http://enable-cors.org/)
* [RubyConf 12 - Building modular, scalable web apps? Of CORS!](https://www.youtube.com/watch?v=VQA2yrpI7Xk)
* [Example](https://github.com/mbleigh/cors-talk-example)
* [Cross-domain Ajax with CORS - Nicholas C. Zakas](http://www.nczonline.net/blog/2010/05/25/cross-domain-ajax-with-cross-origin-resource-sharing/)
* [Rails 4, CORS, JWT and Devise](https://www.youtube.com/watch?v=_CAq-F2icp4)
* [That's so fetch - Some CORS issues](http://jakearchibald.com/2015/thats-so-fetch/)
* [Same-Origin Policy](https://annevankesteren.nl/2015/02/same-origin-policy)

http://stackoverflow.com/questions/19770359/xmlhttprequest-cors-post-sent-without-cookies

CORS let JavaScript XHR to securely communicate with cross-domain resources.

Organizations can publish read/write(R/W GET/POST) JSON APIs or make their entire data sets accessible to the world of JavaScript.

**It is not as simple as adding an HTTP header to your server and calling it a day**

While other programming languages have no restrictions on HTTP requests, JavaScript in a browser has the same-origin policy issue that prevent requests from different sites.

CORS is unique in that it has both a server-side and client-side component.

## The Problem

The browser's same-origin policy limit client code (i.e. JavaScript) from making HTTP requests to different origins.

SOP is a Web Application Security Model. It is a policy by a web browser to permit script to access data that are within the same domain.

However, server-side code is not affected. That's why to overcome SAMEORIGIN, people traditionally use server-side proxying.

## Browsers Support

IE10 does support CORS withCredential but you have to be careful of user settings turning it off at Internet Options. A better way is to use P3P Policy:

* [A quick look at P3P](http://blogs.msdn.com/b/ieinternals/archive/2013/09/17/simple-introduction-to-p3p-cookie-blocking-frame.aspx)
* [Craft a P3P policy to make IE behave](http://www.techrepublic.com/blog/software-engineer/craft-a-p3p-policy-to-make-ie-behave/)

### IE9

* [XDomainRequest and CORS on IE9](http://perrymitchell.net/article/xdomainrequest-cors-ie9/)

## The CORS Request

Firefox 3.5+, Safari 4+, and Chrome all automatically send the `Origin` header when using XHR. When attempting to open a resource on a different origin, this behavior automatically gets triggered without any extra code.

```js
('withCredentials' in (new XMLHttpRequest()));
```

The XHR underwent a revision around 2010 that enable CORS.

By setting `xhr.withCredentials = true;` you include cookie. Your server also must be setup to accept such setting.

IE8 and IE9 support a limited set of cross-origin requests using `XDomainRequest` object.

```js
function createCORSRequest(method, url) {
  var xhr = new XMLHttpRequest();
  if ('withCredentials' in xhr) {
    xhr.open(method, url, true);
  } else if (typeof XDomainRequest != 'undefined') {
    xhr = new XDomainRequest();
    xhr.open(method, url);
  } else {
    xhr = null;
  }
}
```

jQuery's `dataType` indicates that the response should be parsed as JSON. This saves the developer the additional step of using `JSON.parse` to parse the  response text into a JSON object.

```js
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

* [Solving the OPTIONS performance issue](https://www.soasta.com/blog/options-web-performance-with-single-page-applications/)
* [Killing CORS Preflight Requests on a React SPA](https://m.alphasights.com/killing-cors-preflight-requests-on-a-react-spa-1f9b04aa5730#.9b7fbmlpx)
* [What is the motivation behind preflight requests?](https://stackoverflow.com/questions/15381105/cors-what-is-the-motivation-behind-introducing-preflight-requests)

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

Don't do the preflight dance with `X-Requested-With`. Avoid it!

### Authorization

You can use per request tokens, e.g. OAuth.

## Vulnerability and Incidents

* Rosetta Flash