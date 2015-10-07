# _jobline

## Amazon S3

* [Bucket policy?](https://forums.aws.amazon.com/thread.jspa?messageID=188183)
* [How do I display protected S3 images](http://stackoverflow.com/questions/5172630/how-do-i-display-protected-amazon-s3-images-on-my-secure-site-using-php)
* [Restoring/Backing up Postgres in a Docker container](http://vinceyuan.blogspot.sg/2015/05/restoringbacking-up-postgres-database.html)

## Passenger

* [How we've made Passenger 5 up to 4x faster than Unicorn, up to 2x faster than Puma](http://www.rubyraptor.org/how-we-made-raptor-up-to-4x-faster-than-unicorn-and-up-to-2x-faster-than-puma-torquebox/)
* [Cache bundle install](http://ilikestuffblog.com/2014/01/06/how-to-skip-bundle-install-when-deploying-a-rails-app-to-docker/)

```
▶ docker run --rm -t -i phusion/passenger-ruby22 bash -l
▶ docker build -t jobline/eva .

▶ docker run --rm -t -i jobline/eva bash -l
▶ docker exec -it ?? bash -l

// Do not name it! Since you are going to deploy often!
▶ docker run -d \
  -p 80:80 \
  --log-driver=syslog \
  --link postgres-db \
  -e POSTMARK_API_KEY=? \
  -e FILEMAKER_HOST=? \
  -e FILEMAKER_ACCOUNT_NAME=? \
  -e FILEMAKER_PASSWORD=? \
  -e DATABASE_URL=postgres://postgres:@postgres-db/EVA_production \
  -e SECRET_KEY_BASE=? \
  jobline/eva
```

## Nginx

Nginx using links from web servers (multiples) and acts as load balancer. Web servers links from databases and other services.

Where do we put the nginx config file?

## Postgres

Config files:

* /var/lib/postgresql/data/pg_hba.conf
* /var/lib/postgresql/data/postgresql.conf

```
▶ docker create --name postgres-data -v /var/lib/postgresql/data postgres:9.4

▶ docker run -d --volumes-from postgres-data --name postgres postgres:9.4

▶ docker exec -it postgres bash -l
```

**To backup**

* [Backup Postgres to S3](http://rob.conery.io/2011/11/01/how-to-backup-your-postgres-db-to-amazon-nightly/)

```
▶ docker run --rm -it -v $(pwd)/psql:/backup --link postgres-db:db postgres:9.4  sh -c 'exec pg_dump -h db -U postgres EVA_production | gzip -c > /backup/1.sql.gz'
```

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