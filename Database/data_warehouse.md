# Data Warehouse

* [Druid vs Redshift](http://druid.io/docs/latest/comparisons/druid-vs-redshift.html)

> BigQuery and/or Redshift are more targeted towards analytics workloads, but you could use them to saw the data into another system that you use for OLAP -- MySQL or Postgres probably.

Operational system users almost always deal with one record at a time. Data warehouse users almost never deal with on record at a time.

A database that is dedicated to data analysis and reporting.

Store denormalized data. Because user usually read data. No constraints. Rolling up data. Roll up and drill down.

Anticipating user queries.

Evolving warehouse - Agile's iterative and incremental.

3NF is efficient for transaction processing. 3NF is easy to get data in, but a huge disadvantage for BI and data warehousing: it makes it harder to get the data out.

**Not just simple denormalization of data**

The resulting dimensions and fact tables are not arbitrary collections of denormalized data but the 7Ws that describe the full details of each individual business event worth measuring.

## Column-Store

* [One Size Fits None](http://slideshot.epfl.ch/play/suri_stonebraker)

## Star Schema vs Snowflake

## Data Cube

> Most data warehouses therefore try to keep as much raw data as possible, and use aggregates such as data cubes only as a performance boost for certain queries.

## Think Dimensionally

Who, what, when, where, why and how question combinations that measure the business.

## Data Stories

Data modeling *by example* rather than by abstraction.

## Staging Tables

Serve as a buffer. Snapshot of the data. Often loaded daily.

Mirror operational data.

## Facts, Events

Fact is a measurement of the performance of a business. Examples are sales, budget, revenue, profit, inventory, etc.

## Dimension

* [OLAP concepts](http://druid.io/docs/latest/design/index.html)

Dimensions are attributes of an event, and the columns most commonly used in filtering the data

Dimension is a concept or thing with intrinsic meaning for a business. Examples are Date, customer, location, product, account, supplier, etc.

5-15 dimensions per fact.

* Date
* Time
* Customer

Who, what, when, where, why, and how represent dimension types.

How many, represents facts.

## Surrogate Keys

Surrogate key is a unique, meaningless ID. We use it for isolation from change. Good for warehouse integration. Support for data history.

Each dimension and fact should have a surrogate key.

