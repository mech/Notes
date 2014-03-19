# Rails

## 4.0

Rails 4 is thread-safe by default (good for `thin` and `puma`). You need to ensure your application (and its dependencies) are thread-safe, which means avoiding global state. See [here](http://tenderlovemaking.com/2012/06/18/removing-config-threadsafe.html)

* [Digging into Rails 4](http://code.tutsplus.com/tutorials/digging-into-rails-4--net-31255)
* [What's new in ActiveRecord](http://blog.remarkablelabs.com/2012/12/what-s-new-in-active-record-rails-4-countdown-to-2013)

## 4.1

* [ActiveRecord enum vs PostgreSQL's enum](http://www.postgresql.org/docs/9.2/static/datatype-enum.html)


## ActiveRecord

* [7 patterns to refactor fat ActiveRecord models](http://blog.codeclimate.com/blog/2012/10/17/7-ways-to-decompose-fat-activerecord-models/)