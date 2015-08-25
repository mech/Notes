# Redis

PORT: 6379

```
▶ docker run -d \
    -v /docker/host/dir:/data \
    -v /docker/host/redis.conf:/usr/local/etc/redis/redis.conf \
    --name jobline/redis \
    --log-driver=syslog \
    redis redis-server --appendonly yes
```

Compose

```
redis:
  image: redis:3
  volumes:
    - /db/redis:/data

web:
  build: .
  links:
    - redis:redis
```

* [Example of backup](https://gist.github.com/alister/ed664cb51c21bc801e9a)
* [bitnami-docker-redis](https://github.com/bitnami/bitnami-docker-redis)