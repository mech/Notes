# PostgreSQL

* [**Use the Index, Luke**](http://use-the-index-luke.com/)
* [**Discovering indexes**](http://patshaughnessy.net/2014/11/11/discovering-the-computer-science-behind-postgres-indexes)
* [Aggregating NBA data, PostgreSQL vs MongoDB](http://tapoueh.org/blog/2014/02/17-aggregating-nba-data-PostgreSQL-vs-MongoDB)
* [Why you should never use MongoDB](http://www.sarahmei.com/blog/2013/11/11/why-you-should-never-use-mongodb/)
* [Sentiment analysis on GitHub commit messages](http://geeksta.net/geeklog/exploring-expressions-emotions-github-commit-messages/)
* [A love affair with PostgreSQL and Rails 4](http://blog.remarkablelabs.com/2012/12/a-love-affair-with-postgresql-rails-4-countdown-to-2013)
* [UPSERT (SQL MERGE) using Ruby](https://github.com/seamusabshere/upsert)
* [HperLogLog in Postgres](http://tapoueh.org/blog/2013/02/25-postgresql-hyperloglog.html)
* [Benchmarking](http://blog.bleything.net/articles/postgresql-benchmarking-background.html)
* [Inserting using new record](http://rob.conery.io/2015/02/09/inserting-using-new-record-postgres/)

Activity stream goes to MongoDB.
When you follow a candidate, use PubSub to get notify of all his activities!

Use Neo4j for candidate's relationship with each other.

## WITH

An implementation of UPSERT using Writable CTEs (Common Table Expressions)

```
WITH upsert as (
  update table1 m set sales=m.sales+d.sales, status=d.status from table2 d where m.pid=d.pid
  RETURNING m.*
)

insert into table2 select a.pid, a.sales, 'NEW' from table1 a where a.pid not in (select b.pid from upsert b)
```

## Timestamp TZ

Always use `timestamptz`!

```
CREATE TABLE events (
  when timestamps default now(),
  uuid uuid default uuid_generate_v4(),
  event hstore
);
```

## Indexing and Sargable

Don't use expression on your `WHERE` clause. Make sure you don't use function like `YEAR(date_column)`, `WHERE actor_id + 1 = 5`, `UPPER(name_column)`, `TRIM(name_column)`, etc.

Remember, whenever you apply functions on columns in the `WHERE` clause, the index no longer can be used.

> Inform the database whenever you don't need all rows.

* [Partial indexing with Rails](http://rny.io/rails/postgresql/2013/08/20/postgresql-indexing-in-rails.html)
* [! Results of the SQL performance quiz](http://use-the-index-luke.com/blog/2014-02/results-three-minutes-sql-performance-quiz)
* [Function-based indexes](http://use-the-index-luke.com/sql/where-clause/functions/case-insensitive-search)
* [What makes a SQL statement sargable](http://stackoverflow.com/questions/799584/what-makes-a-sql-statement-sargable)

In Postgres, you can index certain functions and maintain sargability.

### Multi-column Indexes

The column order of a composite index has great impact on its usability so it must be chosen carefully. If the order is not correct, a full table scan (`Seq Scan`) will result!

* [Concatenated indexes](http://use-the-index-luke.com/sql/where-clause/the-equals-operator/concatenated-keys)

### Expression Indexes

* [Virtual columns and expression indexes](http://momjian.us/main/blogs/pgblog/2013.html#April_6_2013)

## Range

See http://www.postgresql.org/docs/9.2/static/functions-range.html

```
daterange('["Jan 1 2013", "Jan 15 2013"]') @> 'Jan 10 2013'::date

// overlap (&&)
select numrange(3,7) && numrange(4,12);

// union (+)
numrange(5,15) + numrange(10,20);

// intersection (*)
numrange(5,15) * numrange(10,20);
```

## Aggregation

* [Aggregations with hstore](http://big-elephants.com/2012-10/aggregations-with-pg-hstore/)
* [Use subqueries to count distinct 50x faster](https://periscope.io/blog/use-subqueries-to-count-distinct-50x-faster.html)

## SQL Windowing Functions

* [SQL Window functions](http://hashrocket.com/blog/posts/sql-window-functions)
* [Understanding Window Functions](http://tapoueh.org/blog/2013/08/20-Window-Functions)
* [Month over month using Window Functions](http://www.craigkerstiens.com/2014/02/26/Tracking-MoM-growth-in-SQL/)

## Full-Text Search

* [pg_search Ruby gem](http://isotope11.com/blog/postgres-search-using-pg-search)
* [PostgreSQL's own FTS](http://www.postgresql.org/docs/current/static/textsearch.html)
* [FTS examples](http://citusdata.com/blog/57-postgresql-full-text-search)
* [Building faceted search](http://tech.pro/tutorial/1142/building-faceted-search-with-postgresql)
* [Why Solr is so much faster than Postgres](http://stackoverflow.com/questions/10053050/why-is-solr-so-much-faster-than-postgres/10054078)
* [Updating index with trigger](http://1fifty9.com/post/42878706283/auto-updating-full-text-search-with-postgres)

## Statistics

```
pg_stat_activity
pg_stat_statements
pg_locks
pg_cancel_backend()
```

* [Visibility using `pg_stat_statements` and `cubism` from Square](https://github.com/will/datascope)

## Performance

* [More on Postgres performance](http://www.craigkerstiens.com/2013/01/10/more-on-postgres-performance/)
* [Handling growth with Postgres from Instagram](http://instagram-engineering.tumblr.com/post/40781627982/handling-growth-with-postgres-5-tips-from-instagram)

## Batching

* [Batch update](http://tapoueh.org/blog/2013/03/15-batch-update.html) 

## Custom Type

```
CREATE TYPE squid AS (
  length float,
  tentacles integer,
  weight float
);
```

## Videos

* [Postgres - The bits you haven't found](https://vimeo.com/61044807)

## Stories

* [Scaling PostgreSQL at Braintree](https://www.braintreepayments.com/braintrust/scaling-postgresql-at-braintree-four-years-of-evolution)

## Scaling

* Sharding - Horizontally partition rows of a table across multiple databases

### Partitioning


### Sharding

* [Sharding & IDs at Instagram](http://instagram-engineering.tumblr.com/post/10853187575/sharding-ids-at-instagram)
* [Sharding at Disqus](http://mike-clarke.com/2013/03/sharding-with-the-django-orm/)

> A large part of how we've been able to scale Instagram with very few engineers is by choosing simple, easy-to-understand solutions that we trust.

## Tools

* [pg_activity](https://github.com/julmon/pg_activity)
* [pg_tail](https://github.com/aaparmeggiani/pg_tail)

## People

* Michael Stonebraker
* Peter van Hardenberg