# Compose

Docker 1.2 allow rewriting `/etc/hosts` during run-time, so when DB instance IP changed, the web can be updated. Does that mean we do not need to re-run compose?

```
export COMPOSE_FILE=docker-compose-old.yml
```

* [libcompose](http://rancher.com/our-journey-with-docker-compose-and-the-introduction-of-libcompose/)
* [Orchestrate containers for development with compose](http://blog.codeship.com/orchestrate-containers-for-development-with-docker-compose/)
* [Don't stop containers when fig up exits](https://github.com/docker/compose/issues/741)
* [Data only containers / No run containers](https://github.com/docker/compose/issues/942)
* [centurion from NewRelic](https://github.com/newrelic/centurion)
* [maestro-ng](https://github.com/signalfuse/maestro-ng)
* [How we used Docker to deploy](http://www.schibsted.pl/2015/05/how-we-used-docker-when-developing-schibstedpl/)
* [With the `extends` keyword](http://bfischer.blogspot.com/2015/05/first-experiences-with-docker-compose.html)

Multi-container apps are a hassle.

* Build images from Dockerfiles
* Pull images from the Hub
* Configure and create containers
* Start and stop containers
* Stream their logs

```
mysql:
  image: tutum/mysql
  environment:
    MYSQL_USER: root
    MYSQL_PASSWORD: ???
  volumes:
    - /mnt/sda1/var/lib/mysql_data:/var/lib/mysql
  ports:
    - "3306:3306"
web:
  build: .
  links:
    - mysql
    - mongodb
    - redis:redis
    - memcached
  volumes:
    - .:/var/www/webapp
  ports:
    - "80:80"
```