# MySQL

* [docker-mysql](https://github.com/sameersbn/docker-mysql)
* [Official repo for MySQL](https://github.com/docker-library/mysql)

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