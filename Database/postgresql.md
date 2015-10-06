# PostgreSQL

https://vividcortex.com/pricing/

* [**Postgres Guide**](http://www.postgresguide.com/)
* [**Don't let your data out of the database**](http://patshaughnessy.net/2015/6/18/dont-let-your-data-out-of-the-database)
* [**Discovering the science behind Postgres indexes**](http://blog.codeship.com/discovering-computer-science-behind-postgres-indexes/)
* [**pgcli**](http://pgcli.com/)
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
* [Embracing SQL in Postgres](http://rob.conery.io/2015/02/24/embracing-sql-in-postgres/)
* [Simple continuous archiving for Postgres](https://github.com/wal-e/wal-e)
* [s3cmd](http://s3tools.org/s3cmd)
* [MADlib - For data science](https://github.com/madlib/madlib)
* [Why should you learn Postgres](http://www.brightball.com/postgresql/why-should-you-learn-postgresql)
* [**Rob Conery's node-db-project**](https://github.com/robconery/node-db-project)

Activity stream goes to MongoDB.
When you follow a candidate, use PubSub to get notify of all his activities!

Use Neo4j for candidate's relationship with each other.

## Config files

```
▶ echo $PGDATA

▶ SHOW hba_file;
  /usr/local/var/postgres/pg_hba.conf
  /var/lib/postgresql/data/pg_hba.conf
▶ SHOW config_file;
  /usr/local/var/postgres/postgresql.conf
  /var/lib/postgresql/data/postgresql.conf

▶ ps aux | grep postgres
```

* **shared_buffers = 2GB** - Default value is really small. Set it to 30% of total RAM. So 30% of 8GB is 2GB. High GB like 8GB is not worth it though. Real allocation of memory.
* **work_mem = 10MB** - A higher value improves query performance faster with in-memory sort.
* **maintenance_work_mem = 1GB** - Helps improve performance of maintenance operations like VACCUM, CREATE INDEX, etc. Set to 2GB for 64GB RAM is safe.
* **random_page_cost = 2.0** - ??
* **effective_cache_size = 8GB** - 50%  to 80% of your RAM. Promote index scans. Just an indicator, not real memory allocation.
* 

## CLI

```
▶ psql -l
▶ createdb demo

▶ \dx # List of installed extensions
▶ \dt # List of relations
▶ \d users
▶ \pset

▶ \c EVA_development # Switch database

▶ analyze verbose users;
▶ vacuum users; # Remove dead rows!

▶ \p # Access the buffer

▶ \e # Open VIM to type in query
▶ \i ~/sql_scripts/my_query.sql

▶ \! mkdir ~/reports
▶ psql demo 'select * from users' -H -o ~/reports/users.html

▶ \copy users to ~/reports/users.csv cvs

▶ select name,setting from pg_settings;

▶ select * from pg_stat_archiver;
```

## Rails

* [Porting ActiveRecord validations to Postgres](http://shuber.io/porting-activerecord-validations-to-postgres/)
* [Rails support for UUID](http://blog.nakonieczny.it/posts/rails-support-for-uuid/)
* [Rails Guides](http://edgeguides.rubyonrails.org/active_record_postgresql.html)
* [Postgres, the best tool you're already using](http://adamsanderson.github.io/railsconf_2013/)
* [Using arrays in Rails](http://blog.arkency.com/2014/10/how-to-start-using-arrays-in-rails-with-postgresql/)
* [Postgres arrays the right way](http://blog.heapanalytics.com/dont-iterate-over-a-postgres-array-with-a-loop/)

## Migration from MySQL

* [Things to note when migration from MySQL](https://wiki.postgresql.org/wiki/Things_to_find_out_about_when_moving_from_MySQL_to_PostgreSQL)
* [mysql2postgres](https://github.com/maxlapshin/mysql2postgres)

Postgres is case-sensitive for string comparison

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

Creating a foreign key does not automatically create an index for it. You still have to create an index separately.

```
▶ \di+

-- Check the size of the index
SELECT pg_size_pretty(pg_relation_size('index_name'::regales)) as big_index;
```

Don't use expression on your `WHERE` clause. Make sure you don't use function like `YEAR(date_column)`, `WHERE actor_id + 1 = 5`, `UPPER(name_column)`, `TRIM(name_column)`, etc.

Remember, whenever you apply functions on columns in the `WHERE` clause, the index no longer can be used.

> Inform the database whenever you don't need all rows.

* [**Discovering the science behind Postgres indexes**](http://blog.codeship.com/discovering-computer-science-behind-postgres-indexes/)
* [Partial indexing with Rails](http://rny.io/rails/postgresql/2013/08/20/postgresql-indexing-in-rails.html)
* [Results of the SQL performance quiz](http://use-the-index-luke.com/blog/2014-02/results-three-minutes-sql-performance-quiz)
* [Function-based indexes](http://use-the-index-luke.com/sql/where-clause/functions/case-insensitive-search)
* [What makes a SQL statement sargable](http://stackoverflow.com/questions/799584/what-makes-a-sql-statement-sargable)
* [pg_idx_advisor - Give indexing advise](https://github.com/cohenjo/pg_idx_advisor)
* [Should you index a boolean field?](http://stackoverflow.com/questions/12539772/adding-an-index-on-a-boolean-field)
* [**How to index concurrently in Rails**](https://robots.thoughtbot.com/how-to-create-postgres-indexes-concurrently-in)

In Postgres, you can index certain functions and maintain sargability.

```sql
CREATE UNIQUE INDEX posts_title ON posts (lower(title));

CREATE INDEX tags_index ON posts USING gin(to_tsvector('english'::regconfig, tags::text));
```

* btree - Good for equality, range, sorting
* rtree - Good for lines, spatial, volumetric
* gin - Good for full-text search

### Multi-column Indexes

The column order of a composite index has great impact on its usability so it must be chosen carefully. If the order is not correct, a full table scan (`Seq Scan`) will result!

* [Concatenated indexes](http://use-the-index-luke.com/sql/where-clause/the-equals-operator/concatenated-keys)

### Expression Indexes

* [Virtual columns and expression indexes](http://momjian.us/main/blogs/pgblog/2013.html#April_6_2013)

## GIN - Generalized Inverted Indexes

GIN is just a B-tree, with efficient storage of duplicates. If you have need for unique index, GIN may not be a good fit due to no duplicates. Use regular B-tree for unique index instead.

## JSONB

JSONB does not store duplicate keys. It also clear whitespace. JSONB is stored as binary.

**Note**: JSONB will always perform a Seq Scan if you use the `->>` operator on a path that have no expression index. So if you don't know beforehand which keys you'll query, or if you can query any path, make sure you define an GIN index and use the `@>` that benefits from that index.

**Note**: If you need to query arrays inside JSON, make sure you create an expression index.

```sql
CREATE INDEX preferences_interests_on_users ON users USING GIN ((preferences->'interests'))
```

* [Using Postgres and jsonb with Rails](http://nandovieira.com/using-postgresql-and-jsonb-with-ruby-on-rails)
* [An explanation of JSONB](http://stackoverflow.com/questions/22654170/explanation-of-jsonb-introduced-by-postgresql)
* [complex??](http://stackoverflow.com/questions/18404055/index-for-finding-an-element-in-a-json-array)
* [Some nice gist to follow](https://gist.github.com/fnando/f672c9243186933b3c8e)
* [What I think of jsonb](http://pgeoghegan.blogspot.in/2014/03/what-i-think-of-jsonb.html)
* [**Unleash the power of storing JSON in Postgres**](http://blog.codeship.com/unleash-the-power-of-storing-json-in-postgres/)
* [**Query array of objects in JSONB field**](http://stackoverflow.com/questions/28486192/postgresql-query-array-of-objects-in-jsonb-field)

```sql
-- Last array
SELECT '[{"a":"foo"},{"b":"bar"},{"c":"baz"}]'::json->2;

-- Find by key
SELECT '{"a": {"b":"bar"}}'::json->'a';

-- Double arrow return text only
SELECT '{"b":"bar"}'::json->>'b';

select json_build_array(json_build_object('foo', 1), json_build_object('bar', true));

[{"foo" : 1}, {"bar" : true}]

-- Full containment support
SELECT '{"a":1, "b":2}'::jsonb @> '{"b":2}'::jsonb;

-- Existence
SELECT '{"a":1, "b":2}'::jsonb ? 'b';

-- Any exist?
SELECT '{"a":1, "b":2}'::jsonb ?| ARRAY['b', 'd'];

-- First array item 
SELECT questions->0->>'text' AS text from templates;

-- Find all {text: '??'} inside the array [{text: '??'}, {text: '??'}, {text: '??'}]
SELECT jsonb_array_elements(questions)->>'text' FROM survey_responses WHERE id=1;

-- Will return unknown
SELECT pg_typeof('{"name": "mech"}');

-- x is the alias
SELECT row_to_json(x) FROM (SELECT id, name FROM artists) x;
SELECT json_agg(x) FROM (SELECT id, name FROM artists) x;

-- Here a is an alias for the entire bracket SQL statement
SELECT *,
(SELECT json_agg(a) FROM (SELECT * FROM albums WHERE artist_id == artists.artist_id) a) AS albums
FROM artists;

SELECT * FROM templates
WHERE (questions ->> 'id')::int > 100;
```

**Using PLV8**

```sql
CREATE FUNCTION save_user()
RETURNS jsonb
AS $$
  var newUser = {name: "mech", email: "mech@test.com"};
  plv8.execute("INSERT INTO user_docs(body) VALUES($1)", JSON.stringify(newUser));
  return newUser;
$$ LANGUAGE plv8;
```

## Date

```
// only check last year records
WHERE created_at > now() - '1 year'::interval;
```

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
* [Moving aggregates]()

## SQL Windowing Functions

* [SQL Window functions](http://hashrocket.com/blog/posts/sql-window-functions)
* [Understanding Window Functions](http://tapoueh.org/blog/2013/08/20-Window-Functions)
* [Month over month using Window Functions](http://www.craigkerstiens.com/2014/02/26/Tracking-MoM-growth-in-SQL/)

## Full-Text Search

In your `postgresql.conf`, the `default_text_search_config` is set to `pg_catalog.english`.

* [pg_search Ruby gem](http://isotope11.com/blog/postgres-search-using-pg-search)
* [PostgreSQL's own FTS](http://www.postgresql.org/docs/current/static/textsearch.html)
* [FTS examples](http://citusdata.com/blog/57-postgresql-full-text-search)
* [Building faceted search](http://tech.pro/tutorial/1142/building-faceted-search-with-postgresql)
* [**Why Solr is so much faster than Postgres?**](http://stackoverflow.com/questions/10053050/why-is-solr-so-much-faster-than-postgres/10054078)
* [Updating index with trigger](http://1fifty9.com/post/42878706283/auto-updating-full-text-search-with-postgres)
* [**FTS Part 1**](http://shisaa.jp/postset/postgresql-full-text-search-part-1.html)
* [FTS in ms](https://blog.lateral.io/2015/05/full-text-search-in-milliseconds-with-postgresql/)
* [**Search across multiple models**](https://robots.thoughtbot.com/implementing-multi-table-full-text-search-with-postgres)

Good things to have:

* Ignore diacritical marks (accents like ü)
* Searching for soundalikes (double metaphone)
* Searching for misspelled (trigrams)

2 data type: `tsvector` and `tsquery` and many functions and operators to work on them.

```
Full document (table, view, select) -> tsvector (document) -> tsquery (query)
```

`to_tsvector()` is the function to parse document into token.

```
SELECT to_tsvector('english', '!!!!....hello, 14');
```

```
▶ \dF+
▶ \dFp+
```


## Statistics

```
pg_stat_activity
pg_stat_statements
pg_locks
pg_cancel_backend()
```

* [Visibility using `pg_stat_statements` and `cubism` from Square](https://github.com/will/datascope)
* `percentile_cont()`
* `percentile_disc()`
* `rank()`
* `dense_rank()`
* `percent_rank()`
* `mode()`

```sql
SELECT COUNT(*), min(amount), max(amount),
percentile_cont(array[0.5, 0.9])
WITHIN GROUP (ORDER BY amount)
FROM payment;
```


## Performance

* [More on Postgres performance](http://www.craigkerstiens.com/2013/01/10/more-on-postgres-performance/)
* [Handling growth with Postgres from Instagram](http://instagram-engineering.tumblr.com/post/40781627982/handling-growth-with-postgres-5-tips-from-instagram)

## Batching

* [Batch update](http://tapoueh.org/blog/2013/03/15-batch-update.html) 

## Custom Type

```sql
CREATE TYPE squid AS (
  length float,
  tentacles integer,
  weight float
);
```

## Enum Type

```sql
CREATE TYPE question_type AS ENUM(
  'TextInstruction',
  'MultipleChoice',
  'OpenEnded'
);
```

## Videos

* [Postgres - The bits you haven't found](https://vimeo.com/61044807)
* [PGCon 2014](https://www.youtube.com/watch?v=oQ1LSW31Y1A&list=PLWW0CjV-Tafa2jvcjihXwSvZZKsLAsb9Y#t=2492)

## Stories

* [Scaling PostgreSQL at Braintree](https://www.braintreepayments.com/braintrust/scaling-postgresql-at-braintree-four-years-of-evolution)

## Scaling

* Sharding - Horizontally partition rows of a table across multiple databases

### Partitioning


### Sharding

* [Sharding & IDs at Instagram](http://instagram-engineering.tumblr.com/post/10853187575/sharding-ids-at-instagram)
* [Sharding at Disqus](http://mike-clarke.com/2013/03/sharding-with-the-django-orm/)

```
set search_path = membership;
create sequence id_sequence;
create or replace function id_generator(out new_id bigint)
as $$
DECLARE
  our_epoch bigint := 1072915200000; -- Pluralsight founding
  seq_id bigint;
  now_ms bigint;
  shard_id int := 1;
BEGIN
  SELECT nextval('id_sequence') %1024 INTO seq_id;
  SELECT FLOOR(EXTRACT(EPOCH FROM now()) * 1000) INTO now_ms;
  new_id := (now_ms - our_epoch) << 23;
  new_id := new_id | (shard_id << 10);
  new_id := new_id | (seq_id);
END;
$$
LANGUAGE PLPGSQL;

SELECT id_generator();
```

> A large part of how we've been able to scale Instagram with very few engineers is by choosing simple, easy-to-understand solutions that we trust.

## Functions

You have to know what is business logic (Ruby) and what is data logic (PLPGSQL).

```
create or replace function random_string(len int default 36)
returns text
as $$
select upper(substring(md5(random()::text), 0, len + 1));
$$
language sql;
```

## Tools

* [pg_activity](https://github.com/julmon/pg_activity)
* [pg_tail](https://github.com/aaparmeggiani/pg_tail)
* [pg_view]()
* [PGObserver]()
* [OPM]()
* [PoWA]()
* [pg_prewarm - Loading relation data into memory]()
* [Wagon - SQL Editor](http://www.wagonhq.com/)

## Backup

* [How to backup your Postgres to Amazon nightly](http://rob.conery.io/2011/11/01/how-to-backup-your-postgres-db-to-amazon-nightly/)

## People

* Michael Stonebraker
* Peter van Hardenberg
* Andrew Dunstan (jsonb)