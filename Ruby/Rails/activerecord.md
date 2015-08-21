# ActiveRecord

* [**Ode to Sequel**](http://twin.github.io/ode-to-sequel/)
* [20,000 Leagues under ActiveRecord](http://patshaughnessy.net/2014/9/17/20000-leagues-under-activerecord)
* [How Arel converts Ruby queries into SQL statements](http://patshaughnessy.net/2014/9/23/how-arel-converts-ruby-queries-into-sql-statements)
* [Advanced ARel - When ActiveRecord just isn't enough](https://www.youtube.com/watch?v=ShPAxNcLm3o)
* [Scuttle](http://www.scuttle.io/)
* [Don't let your data out of the database](http://patshaughnessy.net/2015/6/18/dont-let-your-data-out-of-the-database)
* [Referential integrity with foreign keys](https://robots.thoughtbot.com/referential-integrity-with-foreign-keys)

## Role-based Authorization

* [Rails authorization](http://railsapps.github.io/rails-authorization.html)
* [Advanced Rails 4 authorization with Pundit](http://through-voidness.blogspot.sg/2013/10/advanced-rails-4-authorization-with.html)

## ActiveRecord::Querying

```ruby
module ActiveRecord::Querying
  def where
    all
  end
  
  def all
    ActiveRecord::Relation::where
  end
end
```

## ActiveRecord::Relation

```ruby
module ActiveRecord
  class Relation
    include FinderMethods
    include QueryMethods
  end
end
```

`Relation` includes `QueryMethods` which implement the real `where` method. It includes the `FinderMethods` which has the real `find` implementation.

Each chaining will create a brand new instance of `Relation` where the `where`, `order`, `limit`, `offset` being filled up.

Each call to a scoping method saves a new piece of information about our query, and returns a new instance of the `Relation` class. This is what allows us to easily chain together different method calls. We can add on as many different scopes as we wish; because each new object is also an `Relation`, it implements all of the same methods.

## Arel

```ruby
def arel_table
  @arel_table ||= Arel::Table.new(table_name, type_caster: type_caster)
end
```

```ruby
User.where(name: 'Nemo').first

users = Arel::Table.new(:users)
users.project(*)
     .where(users[:name].eq('Nemo))
     .order(users[:id], 'ASC')
     .take(1)
```

```ruby
Post
  .joins(:comments)
  .joins(Comment.joins(:author).join_sources)
  .where(
    Author[:name].eq("mech").and(Post[:active].eq(true))
  )

Post.select(
  Arel::Nodes::NamedFunction.new(
    "LENGTH", [Post[:text]]
  ).as("length")
).to_sql

# => SELECT LENGTH(`posts`.`text`) AS length FROM `posts`
```
