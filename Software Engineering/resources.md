# Resources

* Architect for change. Make change less expensive. Able to evolve overtime.
* Software always becomes iterative. Architecture also becomes iterative.
* Architecture is a snapshot of a process.
* Architecture is coupled to process (esp. continuous delivery).
* [Sorting - Visualized](http://sorting.at/)

* [What is Software Design?](http://www.developerdotstar.com/mag/articles/reeves_design.html)
* [Imperative vs Declarative](http://latentflip.com/imperative-vs-declarative/)

## Architect (Feasibility)

1. **Leadership and communication** - Effective communication. Collaboration. Clarity. Listen to business and translate.
2. **Technical knowledge** - as a Ruby architect, everything you see is a Ruby solution :( Technical breadth is important.
3. **Business domain knowledge** - Trend in HR.
4. **Methodology and strategy** - Once you know, how do you get there?

Techniques for change:

1. **Reduce dependencies** - De-couple components. Faster to deploy due to decoupling. Components can evolve independently. Use messaging, service bus, adapter or even architectural patterns.
2. **Leverage standards** - allow to integrate easier.
3. **Create product-agnostic architectures** - No vendor lock-in. Surround it with message bus, adapters, etc. Anti-corruption layer in DDD.
4. **Create domain-specific architectures** - Don't make generic or too broad architecture. Focus on domain-specific. Limit the scope. Follow business direction and industry trends. Business requirements -> Business goals -> Business direction + Industry trends = Domain-specific architecture.


## From CI to CD

* **Continuous Integration** - Fast, automated feedback on the correctness of your application every time there is a change to code.
* **Continuous Deployment**
* **Continuous Delivery** - Fast, automated feedback on the production readiness of your application every time there is a change - to code, infrastructure, or configuration

Get your Continuous Delivery early and often. Do it first!

Releases occur according to business needs, not operational constraints.

1. Commit stage - Compile, unit test, build.
2. Acceptance stage - Puppet to configured environment. Deploy and smoke test. Again acceptance test one final time?

## Metrics

Don't let people "gain metric" through over-reaction.

* Kiviat metric
* Cyclomatic complexity
* Size and complexity pyramid
* Vuze - Quality pyramid
* Efferent coupling
* Afferent coupling

## API Design

* [API design principles](http://qt-project.org/wiki/API-Design-Principles)