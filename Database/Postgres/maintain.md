# Maintenance

If your database is within 100GB, it can still be served comfortably on a single instance.

* [Uber's switch to MySQL](https://eng.uber.com/mysql-migration/)
* [On Uber's Choice of Databases](http://use-the-index-luke.com/blog/2016-07-29/on-ubers-choice-of-databases)

## Tools

* [pglogical - Next-gen replication system](https://2ndquadrant.com/en/resources/pglogical/)

## Logging

* [Analyzing PostgreSQL logs using pgBadger](https://blog.garage-coding.com/2016/07/16/analyzing-postgres-logs-with-pgbadger.html)

## Sharding

> In order to determine the ideal sharding key you need to examine the query load and types of operations you’re looking to perform. If you are storing aggregated data and all of your queries are per customer then a shard key such as customer_id or tenant_id can be a great choice. Even if you have minutely rollups and then need to report on a daily basis this can work well. This allows you to easily route queries to shards just for that customer. As a result of routing queries to a single shard this can allow you a higher concurrency.

## Vacuum

* [It is very important to vacuum](https://engineering.semantics3.com/2016/07/27/return-of-the-vacuum/)
* [PostgreSQL Concurrency with MVCC](https://devcenter.heroku.com/articles/postgresql-concurrency)

```
autovacuum_max_workers
maintenance_work_mem
autovacuum_naptime
autovacuum_cost_limit
autovacuum_cost_delay

autovacuum_vacuum_threshold
autovacuum_freeze_max_age
autovacuum_vacuum_scale_factor
```