# SQL

* [Good guide on SQL generally](https://community.modeanalytics.com/sql/tutorial/sql-aggregate-functions/)
* [**SQL Style Guide**](http://www.sqlstyle.guide/)
* [4 ways to join only the first row in SQL](https://www.periscope.io/blog/4-ways-to-join-only-the-first-row-in-sql.html)
* [Correlated subquery](https://en.wikipedia.org/wiki/Correlated_subquery)

Database is not a place to store your data. Database is a platform to enforce your business rules. It is a ethnological problem.

| -------- | ------ |
| Relation | Table  |
| Tuple    | Row    |
| Domain   | Schema |

* Restrictions pick up tuples - `WHERE`
* Projections pick up attributes - `SELECT`

## Indexing

If your table have large number of rows and it makes good use of an index, then the lookup will take place in the index instead of sequentially scan (Seq Scan) your table for the matching rows.

* [Using additional indexes](https://tomafro.net/2009/08/using-indexes-in-rails-choosing-additional-indexes)
* [Postgres indexing in Rails](http://rny.io/rails/postgresql/2013/08/20/postgresql-indexing-in-rails.html)

## Transaction Phenomena

|           Mode           |                                                                                      Description                                                                                      |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| P0 (Dirty Write)         | T1 modifies data and T2 also modifies same data before T1 COMMIT/ROLLBACK. Violate consistency. ACID database don't even allow Dirty Write                                            |
| P1 (Dirty Read)          | T1 modifies data and T2 then read the data before T1 COMMIT. If T1 instead ROLLBACK, T2 will have a Dirty Read. (Uncommitted dependency)                                              |
| P2 (Non-repeatable Read) | T1 read a row, then T2 delete that row. T1 no longer can repeat that same read. Same as Dirty Read just that row was committed. (Inconsistent analysis)                               |
| P3 (Phantom)             | Same as non-repeatable read. T1 read a row using same SELECT, T2 insert/delete row that affect that same SELECT result.                                                               |
| P4 (Lost Update)         | T1 read a row, then T2 read the same row. T1 update the row and T2 update it also. T2 won but result in lost update that T1 made. (Lost or buried updates). Solved by 2-phase locking |

* [Editor example](https://technet.microsoft.com/en-us/library/aa213029(v=sql.80).aspx)

To combat these concurrency problem we need **concurrency control** through some **isolation level**.

* [A gentle introduction to isolation levels](https://blog.engineyard.com/2010/a-gentle-introduction-to-isolation-levels)


`DELETE` is a row-level action. `DROP TABLE` is a schema-level action.

## Constraints

* [Postgres 9.4.4 Constraints](http://www.postgresql.org/docs/9.4/static/ddl-constraints.html)

```sql
ALTER TABLE users ADD CONSTRAINT email_uniqueness UNIQUE (email);
ALTER TABLE users ADD CONSTRAINT email_uniqueness UNIQUE (email, account_id);

ALTER TABLE users ADD CONSTRAINT email_presence CHECK (char_length(email) > 0);
ALTER TABLE users DROP CONSTRAINT email_presence

ALTER TABLE user ADD CONSTRAINT adult_age CHECK (age >= 18);
ALTER TABLE user ADD CONSTRAINT age_inclusion CHECK (age IN generate_sequence(18, 65));
ALTER TABLE user ADD CONSTRAINT password_length CHECK (char_length(password) BETWEEN 6 AND 32)

-- If someone remove company, we remove positions also
-- ON DELETE/UPDATE sub-clause always refer to the referenced table
ALTER TABLE positions ADD CONSTRAINT positions_fk_company
FOREIGN KEY (company_id) REFERENCES companies(id)
ON DELETE CASCADE

-- If someone remove job_type, we disallow it if there are still positions referencing it
ALTER TABLE positions ADD CONSTRAINT positions_fk_job_type
FOREIGN KEY (job_type_id) REFERENCES job_types(id)
ON DELETE RESTRICT
```

When the referenced table is changed, one of the referential actions is set in motion by the SQL engine:

* CASCADE - Changes are propagated automatically. If referenced row is deleted, referencing rows should be automatically deleted as well.
* RESTRICT - Prevent deletion of referenced rows.
* SET NULL - Referencing table need to be `NULL`-able.
* SET DEFAULT
* NO ACTION - The default. An error is usually raised.

## Functional Dependency

Functional dependency is better enforce at the database level than trying to use procedural code.

For example, teaching: you want to make sure a teacher is in only one room each period, teaches only one class each period and a room has only one class each period and a room has only one teacher in each period.

```
{StudentID, Lecture} → TA
```

## Common Table Expression (CTE)

It is just one query after another after another

```sql
WITH vendors AS (
  SELECT DISTINCT(body -> 'vendor' -> 'id') AS id,
  (body -> 'vendor' ->> 'name') AS vendor
  FROM products
), rollups AS (
  SELECT vendors.vendor AS artist,
  1 AS count,
  ((body ->> 'price')::int)/100 AS price,
  (body ->> 'name') AS title
  FROM products
  INNER JOIN vendors ON vendors.id = body -> 'vendor' -> 'id'
), avg_album_price AS (
  SELECT artist, AVG(price)::money AS avg_price
  FROM rollups
  GROUP BY artist
  ORDER BY avg_price DESC
)

SELECT * FROM avg_album_price;
```

## NULL

An EMPTY SET is still a set.

If SQL make empty set a NULL concept, maybe there will be error.

## EAV - Entity-Attribute-Value Model

* [Is EAV bad in all scenarios](http://programmers.stackexchange.com/questions/93124/eav-is-it-really-bad-in-all-scenarios)