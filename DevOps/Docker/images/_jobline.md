# _jobline

## Amazon S3

* [Bucket policy?](https://forums.aws.amazon.com/thread.jspa?messageID=188183)
* [How do I display protected S3 images](http://stackoverflow.com/questions/5172630/how-do-i-display-protected-amazon-s3-images-on-my-secure-site-using-php)

## MySQL

Step 1 is to bring up an empty MySQL database with `MYSQL_ROOT_PASSWORD`. Subsequently, we will not provide the password variable anymore as it is not needed.

```
▶ docker create --name mysql-data -v /var/lib/mysql mysql:5.6

▶ docker run -d \
    -v /docker/host/mysql_conf:/etc/mysql/conf.d \
    --volumes-from mysql-data \
    -e MYSQL_ROOT_PASSWORD=??? \
    --name jobline-mysql \
    --log-driver=syslog \
    --restart \
    mysql:5.6
```

After creating data container and initialising MySQL, it's time to import.

```
▶ docker cp /tmp/bak.sql jobline-mysql:/bak.sql
▶ docker exec -it jobline-mysql bash
▶ mysql -uroot -p jobline_pro < bak.sql
```

To perform daily hourly backup.

```
// We launch a brand new container just to backup one time and remove the container.
▶ docker run --rm -it \
    -v $(pwd)/mysql:/backup \
    --link jobline-mysql:mysql \
    mysql:5.6 \
    sh -c 'exec mysqldump \
      -h"$MYSQL_PORT_3306_TCP_ADDR" \
      -P"$MYSQL_PORT_3306_TCP_PORT" \
      -uroot \
      -p"$MYSQL_ENV_MYSQL_ROOT_PASSWORD" \
      jobline_pro > /backup/dump.sql'
      
▶ docker run --rm -it -v $(pwd)/mysql:/backup --link jobline-mysql:mysql mysql:5.6 sh -c 'exec mysqldump -h"$MYSQL_PORT_3306_TCP_ADDR" -P"$MYSQL_PORT_3306_TCP_PORT" -uroot -p"$MYSQL_ENV_MYSQL_ROOT_PASSWORD" jobline_pro > /backup/dump.sql'

▶ docker run --rm -it --link jobline-mysql:mysql mysql:5.6 sh -c 'exec mysql -h"$MYSQL_PORT_3306_TCP_ADDR" -P"$MYSQL_PORT_3306_TCP_PORT" -uroot -p"$MYSQL_ENV_MYSQL_ROOT_PASSWORD"'
```

## MongoDB

```
▶ docker create --name mongo-data -v /data/db mongo:2.6

▶ docker run -d \
    --volumes-from mongo-data \
    --name jobline-mongo \
    --log-driver=syslog \
    --restart \
    mongo:2.6
```

## Redis

```
▶ docker run -d \
    -v /docker/host/dir:/data \
    -v /docker/host/redis.conf:/usr/local/etc/redis/redis.conf \
    --name jobline-redis \
    --log-driver=syslog \
    --restart \
    redis redis-server --appendonly yes
```

## Memcached