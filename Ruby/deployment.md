# Deployment

* [DNS-level to prevent DDoS](https://www.cloudflare.com/plans)
* [things every `.htaccess` file should have](http://www.rrpowered.com/2014/05/things-every-htaccess-file-should-have.html)
* [Enable Gzip](http://www.feedthebot.com/pagespeed/enable-compression.html)
* https://gist.github.com/dennisreimann/3656874
* [Rails migrations with no downtime](http://pedro.herokuapp.com/past/2011/7/13/rails_migrations_with_no_downtime/)
* [Server sandbox??](http://kikobeats.gitbooks.io/server-sandbox/)

```
rake quality
rake test
git push heroku-staging master
rake smoke:staging
git push heroku master
rake smoke:production
```

## Web Server

```
wget -S -O - www.jobline.com.sg
```

```
Server: jobline_web
X-XSS-Protection: 1; mode=block
X-Frame-Options: SAMEORIGIN
```

* [SPDY on Rails](https://bugsnag.com/blog/spdy-on-rails/)

## Capistrano

* [Capistrano Version 3](https://medium.com/p/ba896a142ac)

## Videos

* [Guide to continuous deployment - RailsConf 2014](http://www.youtube.com/watch?v=DazHGyb7Gqg)
* [Monitoring and metrics for web scale applications](https://vimeo.com/94466544)