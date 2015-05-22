# Event Sourcing

* [Event Aggregator](http://martinfowler.com/eaaDev/EventAggregator.html)
* [Event Sourcing](http://martinfowler.com/eaaDev/EventSourcing.html)
* [Observer Synchronization](http://martinfowler.com/eaaDev/MediatedSynchronization.html)
* [Storing aggregate](https://vaughnvernon.co/?p=942)

Example: Booking-keeping ledger

> State transitions are an important part of our problem space and should be modelled within our domain. Event sourcing says all state is transient and you only store facts. - Greg Young
>
> The model that a client needs for the data in a distributed system is screen-based and different than the domain model

Screen-based UI vs RESTful UI

Current State is a left fold of events.

```
# Ruby
[1, 2, 3].inject(0, :+)

# Scala
List(1, 2, 3).foldLeft(0)(_+_)
```

History replay? Never lost information (append-only log). Eventual consistency. No built-in querying of domain models. Lack of agreement on tools and infrastructure. Increase storage requirements.

With CRUD, you lose data all the time because you are only interested in the current state of the world.

## Pure Function

```
process(currentState, command) => e1, e2, e3
apply(currentState, event) => nextState
```

## Command

A command is a request for a state transition in the domain. A request for an event. Something happen.

## Query

## Projection

Read model. Projections eventually consistent!

Projection is to derive current state from the stream of events.