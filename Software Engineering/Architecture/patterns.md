# Architecture Patterns

* **Traditional layered architecture** - Presentation layer, business layer, persistence layer, database layer, etc. Have separation of concerns. Layer isolation. Service layer is an "open" layer and the rest is "close". Good general purpose architecture. Easy to implement, test and govern. Not very performant like finance or trading applications.
* **Event-driven architecture (EDA)** - Event and process. Broker and broker-less (no mediator) topology. Highly de-couple and distributed. You can add and remove processes and great for business that change often! High degree of complexity!
* **Service-oriented architecture** - Business services (BS). Enterprise services (ES). BS - Message bus - ES. ProcessClaim, ExecuteTrade are all examples of BS. CreateCustomer, CheckCompliance, CalculateQuote is ES, not BS. You don't create customer as a business. addDriver, getInventoryCount are AS (Application services). writeAuditLog, checkUserAccess, writeErrorLog, singleSignOn are all Infrastructure services (IS)
* **Pipeline architecture** - Pipe and filter. Pipe is one-way, uni-directional only. Point-to-point for high performance. Filter is self-contained and independent and perform one single, very specific task. "producer", "transformer", "tester", and "consumer" filter. Not the same as event-driven architecture! EDA is asynchronous, but pipe is synchronous.
* **Microkernel architecture** - Plug-in module added to the core system. Eclipse IDE is the perfect example. Another example is the Claims Processing as the core system and plug-in country module.
* **Space-based architecture** - Database cannot scale out linearly like web-server or app-server. Really really expensive using cloud-based infrastructure.
* [Microservice - 72 resources](http://blog.arkency.com/2014/07/microservices-72-resources/)

https://dl.dropboxusercontent.com/u/6815194/Notes/SOA.png

Semantic interface, anti-corruption in DDD. Mostly at persistence layer.

2 common viewpoints of architectural styles are:

1. Component interaction style - Layered, pipes-and-filters, etc.
2. Control style - Distributed or centralized

---

* Software patterns - OOP and Design
* Software framework - Rails and Ember.js
* Software architecture - Brain ++

## Design Patterns

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








