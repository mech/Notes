# Cross-Origin Resource Sharing

JSON-P is just a hack to bypass same-origin. Can only do GET request. Has security issues.

* [Browser supports for CORS](http://caniuse.com/#feat=cors)
* [The Same-Origin Saga](https://vimeo.com/54121245)
* [Origin policy enforcement in modern browser](https://www.youtube.com/watch?v=PbvxtMCUG8U)
* [HTTP Strict Transport Security](https://www.owasp.org/index.php/HTTP_Strict_Transport_Security)
* [Enable CORS](http://enable-cors.org/)
* [rack-cors](https://github.com/cyu/rack-cors)

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

## Server-Side

CORS gives servers the flexibility to configure cross-origin access in a variety of ways:

* Which domains are allowed to make requests
* Which HTTP methods are allowed
* Which headers are allowed on the HTTP request
* Whether or not requests may include cookie data
* Which response headers the client can read

Any custom headers must be sanctioned by the server. Client cannot anyhow set custom headers like `X-Requested-With`

The server has many reasons to reject a CORS request. It may allow cross-origin `GET` and `POST` requests, but not `PUT` or `DELETE` requests.

### Pre-flight Checks

Debug with `chrome://net-internals/#events`

### Authorization

You can use per request tokens, e.g. OAuth.