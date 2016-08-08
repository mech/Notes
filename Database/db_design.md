# Design

Row-store for no good reason.

Ingres, System R, Sybase?

* [**SciDB**](http://www.paradigm4.com/resources/videos/)
* [5 simple database design errors you should avoid](https://www.simple-talk.com/sql/database-administration/five-simple--database-design-errors-you-should-avoid/)
* [Learning about DB design errors](http://www.vertabelo.com/blog/notes-from-the-lab/19-online-resources-for-learning-about-database-design-errors)
* [HN: How to handle 50GB of transaction data each day?](https://news.ycombinator.com/item?id=11157829)

## Relational vs Document

> If the data in your application has a document-like structure (i.e. a tree of one-to- many relationships, where typically the entire tree is loaded at once), then it's probably a good idea to use a document model. The relational technique of shredding - splitting a document-like structure into multiple tables (like positions, education and contact_info) - can lead to cumbersome schemas and unnecessarily complicated application code.

The poor support for joins in document databases may or may not be a problem, depending on the application. For example, many-to-many relationships may never be needed in an analytics application that uses a document database to record which events occurred at which time.

It's not possible to say in general which data model leads to simpler application code; it depends on the kinds of relationships that exist between data items. For highly interconnected data, the document model is very awkward, the relational model is acceptable, and graph models are the most natural.

## Locality

Good at document databases.

## Constraints

## Normal Forms

* [What's the actual definition of 1NF?](http://www.vertabelo.com/blog/technical-articles/what-is-the-actual-definition-of-first-normal-form-1nf)

## People

Michael Stonebraker