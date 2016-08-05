# Interesting Queries

```sql
SELECT c.key, c.x_key, c.tags
       x.name
FROM context c
JOIN x ON c.x_key = x.key
WHERE c.key = ANY (ARRAY[145545, 223444, 3344443, -- 11,000 other keys --])
  AND c.x_key = 1
  AND c.tags @> ARRAY[E'blah'];
```

## SELECT *

* [The real reason SELECT star queries are bad: index coverage](https://weblogs.asp.net/jongalloway/the-real-reason-select-queries-are-bad-index-coverage)

Using `*` would likely not make use of a covering index unless you index the entire table (which is unlikely) and keep it up-to-date with added columns.

## Date

```sql
WHERE visited_at > now() - '7 days'::interval

WHERE visited_at > date_trunc('date', now())
```

## DISTINCT

Doing DISTINCT is slow for very large records in Postgres. Unlike MySQL which is fast using index. If you have large number of distinct values, it is even worse.

* [Optimizing DISTINCT](https://explainextended.com/2009/05/03/postgresql-optimizing-distinct/)
* [Optimizing Postgres query for DISTINCT values](http://zogovic.com/post/44856908222/optimizing-postgresql-query-for-distinct-values)

## Aggregation and Recursive Queries

* [Our journey from Graph Databases to PostgreSQL](http://engineering.hipolabs.com/graphdb-to-postgresql/)

## Prepared Statement

* [Since Rails 3.1, we have prepared statements](http://patshaughnessy.net/2011/10/22/show-some-love-for-prepared-statements-in-rails-3-1)