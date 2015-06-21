# Authentication

* [MailChimp API v3.0 OAuth2](http://kb.mailchimp.com/api/article/about-oauth2)
* [Gems you might not need! AdminController and Forbid pattern](https://vimeo.com/39498553)

Provider is at https://api.jobline.com.sg. Consumer will be:

* Jobline Web: https://www.jobline.com.sg
* Jobline Mobile (iOS and Android)
* Companies? Maybe some access
* Candidates? Maybe not!

The de-facto practice for API authentication is to provide an API Key/Secret combination to the consumer of your API and have them submit as the `Authorization` header on every request.

```
Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==
```

The header will be sent on every request. Assuming you use HTTPS, this is a secure way to authenticate users.

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
	
## Using `has_secure_password`

`has_secure_password` already checks for existence and confirmation on create.

* [How to safely store a password](http://codahale.com/how-to-safely-store-a-password/)
* [**Simple Authentication with BCrypt**](https://gist.github.com/thebucknerlife/10090014)
* [With Rails 4.1](http://robert-reiz.com/2014/04/12/has_secure_password-with-rails-4-1/)