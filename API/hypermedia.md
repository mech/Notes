# Hypermedia APIs

* [Richardson Maturity Model](http://martinfowler.com/articles/richardsonMaturityModel.html)
* [Haters gonna HATEOAS](http://timelessrepo.com/haters-gonna-hateoas)
* [HAL Primer](http://phlyrestfully.readthedocs.org/en/latest/halprimer.html)
* [On choosing a hypermedia format](http://sookocheff.com/post/api/on-choosing-a-hypermedia-format/)
* [Roar](https://github.com/apotonick/roar)

## Hypermedia Links

* [Link relation](http://blog.stateless.co/post/38378679843/hypermedia-apis-on-rails-why-dhh-should-give-a)


## Hypermedia Controls

HTML as a media type already has many controls. Should we abandon JSON and use HTML instead? [See Using HTML as the Media Type for your API](http://codeartisan.blogspot.de/2012/07/using-html-as-media-type-for-your-api.html)

Clients should not be dependent on a specific URL structure, rather, they should just use the URLs as they are provided by the server using hypermedia controls. This is URI opacity.

## Examples

* [HATEOAS and the PayPal REST Payment API](https://developer.paypal.com/docs/integration/direct/paypal-rest-payment-hateoas-links/)

```json
[
  {
    "href": "https://api.sandbox.paypal.com/v1/payments/payment/PAY-6RV70583SB702805EKEYSZ6Y",
    "rel": "self",
    "method": "GET"
  },
  {
    "href": "https://www.sandbox.paypal.com/webscr?cmd=_express-checkout&token=EC-60U79048BN7719609",
    "rel": "approval_url",
    "method": "REDIRECT"
  },
  {
    "href": "https://api.sandbox.paypal.com/v1/payments/payment/PAY-6RV70583SB702805EKEYSZ6Y/execute",
    "rel": "execute",
    "method": "POST"
  }
]
```

## Videos

* [Hypermedia APIs - Jon Moore](https://vimeo.com/20781278)