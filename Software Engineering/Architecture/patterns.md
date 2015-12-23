# Architecture Patterns

Software development is a creative tasks full of false starts, dead ends, backtracking and experimenting. Constraint by Law of Complexity.

Make decisions in the face of incomplete and uncertain knowledge.

> Structural engineering is the science and art of designing and making, with economy and elegance,... structures so that they can safely resist the forces to which may be subjected - Structural Engineer's Association

> Aware of the consequences and Live with the consequences

* **Traditional layered architecture** - Presentation layer, business layer, persistence layer, database layer, etc. Have separation of concerns. Layer isolation. Service layer is an "open" layer and the rest is "close". Good general purpose architecture. Easy to implement, test and govern. Not very performant like finance or trading applications.
* **Event-driven architecture (EDA)** - Event and process. Broker and broker-less (no mediator) topology. Highly de-couple and distributed. You can add and remove processes and great for business that change often! High degree of complexity!
* **Service-oriented architecture** - Business services (BS). Enterprise services (ES). BS - Message bus - ES. ProcessClaim, ExecuteTrade are all examples of BS. CreateCustomer, CheckCompliance, CalculateQuote is ES, not BS. You don't create customer as a business. addDriver, getInventoryCount are AS (Application services). writeAuditLog, checkUserAccess, writeErrorLog, singleSignOn are all Infrastructure services (IS)
* **Pipeline architecture** - Pipe and filter. Pipe is one-way, uni-directional only. Point-to-point for high performance. Filter is self-contained and independent and perform one single, very specific task. "producer", "transformer", "tester", and "consumer" filter. Not the same as event-driven architecture! EDA is asynchronous, but pipe is synchronous.
* **Microkernel architecture** - Plug-in module added to the core system. Eclipse IDE is the perfect example. Another example is the Claims Processing as the core system and plug-in country module.
* **Space-based architecture** - Database cannot scale out linearly like web-server or app-server. Really really expensive using cloud-based infrastructure.


https://dl.dropboxusercontent.com/u/6815194/Notes/SOA.png

Semantic interface, anti-corruption in DDD. Mostly at persistence layer.

2 common viewpoints of architectural styles are:

1. Component interaction style - Layered, pipes-and-filters, etc.
2. Control style - Distributed or centralized

---

* Software patterns - OOP and Design
* Software framework - Rails and Ember.js
* Software architecture - Brain ++

## Microservices

> ...surprising effect subtle changes in wording on the Facebook photo violations page eventually encouraged people to admit that they just didn’t like the photo. One of the key findings was the difference between "embarrassing" and "it's embarrassing" - the implication being that the photo is embarrassing, not you. The key enabler for this research? The ability to easily put out subtle changes and measure results, to create multiple versions of behaviors that differ in measurable ways. Facebook eventually saved untold amounts of money in manpower to sort through pictures because their architecture supported incremental, controlled change.

Single "job to be done" that are exposed via an API!

Disruptor: Continuous Delivery with Containerized Microservices.

Built for replacement (not reuse). You should not be afraid to throw away your implementation if it suck. Make it micro.

Microservices - Loosely coupled service oriented architecture with bounded contexts.

Monoliths try to share resources as much as possible. Monoliths can't scale read and write. No CQRS. No replacing of parts. See the case study of Iceland volcano where one airline couple their reservation and boarding into one system which lead them to delay their flight take off. The models may make sense to be together, but we must think about the Lifecycle instead.

Conway's law - separate into domain rather than departmental. Products, not projects. Amazon build products, not projects. You build it, you own it! Invert Conway's Law - teams own service groups and backend stores. Stateless business logic. Cattle, not pets.

Organized around capabilities - Conway's Law

Products, not projects. Amazon's "You build it, you run it!"

Smart endpoints, dump pipes.

ACID vs BASE.

Bounded Context - Decentralized Governance.

Application routing.

Asynchronous vs Synchronous - Temporal coupling. Send out request, but don't wait for response. Gun for eventual consistency. Event-driven architecture == Reactive == Choreography == Messaging.

Duplicate data is bad. DRY in data is not necessarily good.

Agile + DevOps + Microservices

No shared persistence. Each services use their own mini database.

* [Microservice - 72 resources](http://blog.arkency.com/2014/07/microservices-72-resources/)
* [Good resources on Microservices](http://microservices.io/)
* [Cloud trends - Adrian Cockcroft](https://www.youtube.com/watch?v=VaFktjlLp5M)
* [State of the Art in Microservices by Adrian Cockcroft](https://www.youtube.com/watch?v=nMTaS07i3jk)
* [Adopting Microservices at Netflix: Lessons for Architectural Design](http://nginx.com/blog/microservices-at-netflix-architectural-best-practices/)
* [Docker and related services enable a future of microservices for everyone](http://blog.giantswarm.io/docker-and-related-services-enable-a-future-of-microservices-for-everyone)
* [Simulating service discovery with Docker and etcd](http://talwai.github.io/#/blog/post/discovery)
* [Architecture without Architects](https://www.youtube.com/watch?v=qVyt3qQ_7TA)
* [Practical considerations for microservice architectures - Sam Newman](https://vimeo.com/105751281)
* [Pattern: Backends For Frontends](http://samnewman.io/patterns/architectural/bff/)

Gene Kim, Andrew Phillips, Gary Gruver, Randy Shoup

## Design Patterns

* [Design patterns to avoid](http://stackoverflow.com/questions/449731/design-patterns-to-avoid)
* [Reused Abstraction Principle](http://codemanship.co.uk/parlezuml/blog/?postid=934)

Good and bad of patterns. GoF is a terrible implementation guide. It is not a cookbook.

OO framework tends to be large and coarse-grained.
Functional is more tiny.

```
// Java to Clojure
indexOfAny(str, searchChars) {
  when (searchChars)
    for (i=0; i<str.length(); i++) {
      ch = str.charAt(i);
      when searchChars(ch) i;
    }
}

indexOfAny(str, searchChars) {
  when (searchChars)
    for ([i, ch] in indexed(str)) { // List comprehension?
      when searchChars(ch) i;
    }
}

(defn index-filter [pred coll]
  (when pred
    (for [[idx elt] (indexed coll) :when (pred elt)] idx)))
```

* **Strategy** - Define a family of algorithms, encapsulate each one, and make them interchangeable.
* **Command** - Encapsulate a request as an object, thereby letting you parameterise clients with different requests, queue or log requests, and support undoable operations. No reason to use command as a transport in higher-order function language.
* ??

## Repository

The Repository pattern is extremely useful when you have complex storage requirements or complicated access rules. It's especially useful in separating persistence and domain objects.

However only do it for complicated object. Do not use Repository for simple data objects.

## Business Driven. Industry Trends

## Anti-Patterns

* Architecture by implication - Be careful of over-confidence. Agile is not a substitute.
* Cover your assets
* Witches brew - Design by committee
* Gold plating - It just hide the real details.
* Vendor king - Product-dependent architectures or lock-in
* Big bang architecture - BDUF
* Armchair architecture - Whiteboard sketches without proving the design. Also known as Paper Architecture.
* Playing with new toy - Is it feasible?
* Spider Web Architecture
* Infinity Architecture - Too flexible. Instead do a Domain-specific architecture.
* Groundhog day - Email driven architecture
* Stovepipe Architecture - Lack of proper abstraction. Lack of an integration solution.








