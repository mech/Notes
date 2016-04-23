# MySQL

* [Tuning MySQL](http://blog.codesherpas.com/on_the_path/2011/03/tuning-mysql.html)
* [Don't use virtualization for your database](https://signalvnoise.com/posts/1819-basecamp-now-with-more-vroom)
* [Native JSON data type and binary format](http://mysqlserverteam.com/json-labs-release-native-json-data-type-and-binary-format/)
* [WebScaleSQL](http://webscalesql.org/)
* [MySQL vs Postgres](https://news.ycombinator.com/item?id=9586504)
* [Growing with MySQL](https://nylas.com/blog/growing-up-with-mysql/)

## Backup

Logical vs Physical backups. Full vs Incremental backups.

* Physical - Raw copy of whole data directory. Faster methods without conversion. Suitable for large, important databases that need to be recovered quickly. Good for busy and important databases. Only portable to other machines with similar hardware characteristics. MySQL server must be locked during backup so as not to change the database contents during backup. Use `mysqlbackup`, `cp`, `scp`, `tar`, `rsync`, or `mysqlhotcopy`
* Logical - Done by querying the MySQL server to obtain database structure and content information. Slower. Output is larger for text format. Machine independent and highly portable. Server is not taken offline. Use `mysqldump`

