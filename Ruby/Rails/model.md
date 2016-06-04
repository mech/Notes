# Model

* [When we model (structural modeling, operational modeling, deep modeling)](http://therealadam.com/2015/06/30/when-we-model/)
* [Strip whitespace best practices](http://stackoverflow.com/questions/3268053/rails-before-validation-strip-whitespace-best-practices)
* [Normalize whitespace using PSQL](https://wiki.postgresql.org/wiki/Normalize_whitespace)
* [ActiveModel form objects](https://robots.thoughtbot.com/activemodel-form-objects)
* [attribute_assignment.rb](https://github.com/rails/rails/blob/master/activemodel/lib/active_model/attribute_assignment.rb)
* [Making ActiveRecord models thin](http://solnic.eu/2011/08/01/making-activerecord-models-thin.html)

## Repository

* [Working with Repositories](http://hawkins.io/2014/04/working_with_repositories/)

## Service Object

* [Improving Large Rails Apps with Service Objects](http://aaronlasseigne.com/2016/04/27/improving-large-rails-apps-with-service-objects/)
* [Service objects in Rails will help you design clean and maintainable code](https://www.netguru.co/blog/service-objects-in-rails-will-help)
* [Gourmet Service Objects](http://brewhouse.io/blog/2014/04/30/gourmet-service-objects.html)

Service object defines an application boundary that establishes a set of available operations.

Service object encapsulate cross-cutting operations.

Service object is standalone operation. Typically only one instance of each service type within the execution context.

In Rails, is everything that happens in the controller without all the HTTP-related stuff (`params`, `render`, `redirect`).

Service object encapsulates a single process of the business logic.

Service object is also not RESTful API, SOA, or even microservices.

## Presenter

You can think of presenter as a display/screen data structure with no HTML.

Or you can think of presenter as a convenient place to aggregate several different models for reporting or summarising feature.

Rather than have the controller fetch each model individually, it instead ask a presenter object to aggregate for him.

You can also think of presenter as a wrapper to wrap a difficult model instances to adapt the model for presentation. These wrappers are proper Decorators most of the time.

Class versions of your views.

```ruby
ReportPresenter
OrderCompletionPresenter
```

## Decorator

## Exhibit

```ruby
class Exhibit < SimpleDelegator
  def initialize(model, context)
    @context = context
    super(model)
  end
  
  def to_model
    __getobj__
  end
  
  def class
    __getobj__.class
  end
end
```

## Enum

* [Ruby on Enums, Queries and Rails 4.1](https://hackhands.com/ruby-on-enums-queries-and-rails-4-1/)