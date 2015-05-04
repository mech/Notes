# MySQL

* [docker-mysql](https://github.com/sameersbn/docker-mysql)
* [Official repo for MySQL](https://github.com/docker-library/mysql)
* [Docker-persistence](http://www.alexecollins.com/docker-persistence/)
* [**Tutum Docker MySQL**](https://github.com/tutumcloud/tutum-docker-mysql)
* [Securing MySQL Server](http://howtolamp.com/lamp/mysql/5.6/securing)
* [Why default character_set_server is latin1](http://dba.stackexchange.com/questions/29649/why-default-character-set-server-is-latin1)
* `sudo apt-get install mysqltuner`
* [Logrotate and the MySQL log](http://www.percona.com/blog/2014/11/12/log-rotate-and-the-deleted-mysql-log-file-mystery/)
* [Make uid & gid configurable for shared volumes](https://github.com/docker/docker/issues/7198)
* [Best way to manage permissions for Docker shared volumes](http://stackoverflow.com/questions/23544282/what-is-the-best-way-to-manage-permissions-for-docker-shared-volumes)
* [**Learn to stop using shiny new things and love MySQL**](http://engineering.pinterest.com/post/116038532184/learn-to-stop-using-shiny-new-things-and-love)

```
/var/lib/mysql
/etc/mysql
/var/log/mysql
/var/run/mysqld

/etc/mysql/my.cnf
datadir=/var/lib/mysql

// Where you data is stored?
▶ select @@datadir;

// Access a running container
▶ docker exec -it mysql bash
```

To find out if `/var/lib/mysql` has been initialised by `mysql_install_db`, we can check:

```
if [ ! -f /var/lib/mysql/ibdata1 ]; then
  mysql_install_db
fi

# OR...

VOLUME_HOME="/var/lib/mysql"

if [[ ! -d $VOLUME_HOME/mysql ]]; then
  echo "=> An empty or uninitialised MySQL volume is detected in $VOLUME_HOME"
  echo "=> Installing MySQL..."
  mysql_install_db > /dev/null 2>&1
  echo "=> Done!"
  echo "=> Creating admin user..."
  CreateMySQLUser
else
  echo "=> Using an existing volume of MySQL"
fi
```

## Backup and Restore

* [`mysqldump --single-transaction`](http://dba.stackexchange.com/questions/71961/mysqldump-single-transaction-yet-update-queries-are-waiting-for-the-backup)
* [Can I backup mysql while mysqld is running?](http://serverfault.com/questions/195125/can-i-backup-mysql-while-mysql-is-running)
* [How to pipe a mysql dump to s3cmd](http://serverfault.com/questions/605796/how-to-pipe-a-mysql-dump-to-s3cmd)
* [Backup MySQL to Amazon S3](https://gist.github.com/oodavid/2206527)
* [Backup MySQL to S3 in 30 seconds](https://fogstack.wordpress.com/2013/05/25/backup-mysql-to-s3-in-30-seconds/)
* [s3cmd options](http://s3tools.org/usage)

```
mysqldump -h localhost -u root -p --databases jobline_pro > /tmp/backup.sql
```

**Note**: After a dump, please do a restore in order to know the Docker MySQL is capable of restoring what you have dumped.

## my.cnf

`/etc/mysql/my.cnf` to set global options. `~/.my.cnf` to set user-specific options.

From the `/etc/mysql/my.cnf`:

```
#
# * IMPORTANT: Additional settings that can override those from this file!
#   The files must end with '.cnf', otherwise they'll be ignored.
#
!includedir /etc/mysql/conf.d/
```