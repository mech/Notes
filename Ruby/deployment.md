# Deployment

* [DNS-level to prevent DDoS](https://www.cloudflare.com/plans)
* [things every `.htaccess` file should have](http://www.rrpowered.com/2014/05/things-every-htaccess-file-should-have.html)
* [Enable Gzip](http://www.feedthebot.com/pagespeed/enable-compression.html)
* https://gist.github.com/dennisreimann/3656874
* [Rails migrations with no downtime](http://pedro.herokuapp.com/past/2011/7/13/rails_migrations_with_no_downtime/)

```
rake quality
rake test
git push heroku-staging master
rake smoke:staging
git push heroku master
rake smoke:production
```

## Capistrano

* [Capistrano Version 3](https://medium.com/p/ba896a142ac)

## Videos

* [Guide to continuous deployment - RailsConf 2014](http://www.youtube.com/watch?v=DazHGyb7Gqg)
* [Monitoring and metrics for web scale applications](https://vimeo.com/94466544)