# MySQL

* [docker-mysql](https://github.com/sameersbn/docker-mysql)
* [Official repo for MySQL](https://github.com/docker-library/mysql)
* [Docker-persistence](http://www.alexecollins.com/docker-persistence/)
* [**Tutum Docker MySQL**](https://github.com/tutumcloud/tutum-docker-mysql)

```
/var/lib/mysql
/etc/mysql

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