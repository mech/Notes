# Controller

* [Overuse of global state and class methods. With ActiveRecord, it is very hard not to use class methods.](http://googletesting.blogspot.sg/2008/11/clean-code-talks-global-state-and.html)
* [MVC: How to write controllers](http://andrzejonsoftware.blogspot.sg/2008/07/mvc-how-to-write-controllers.html)
* [A defence of @ivars in Rails controllers](http://naildrivin5.com/blog/2014/02/09/a-defense-of-ivars-in-rails-controllers.html)
* [See the `Dashboard` facade pattern](https://robots.thoughtbot.com/sandi-metz-rules-for-developers)
* [H**ow DHH Organizes His Rails Controllers**](http://jeromedalbert.com/how-dhh-organizes-his-rails-controllers/)

## Composite Pattern (Delegation)

Why we don't use composition so often. The reason is Ruby mixins are more popular. Look at DHH's `concerns`.

The result of mixins is you end up with a class which has lots of responsibilities. It leads to object/self schizophrenia which is a complication arising from delegation (having a split identity).

Use mixins for Roles in the DCI sense.

> In an e-commerce app you would have User class but the buying/cart logic would be in the Buyer module. The User class knows nothing about cart, buying.

## Filters

Do not have dependencies between filters.

## Action

One controller action is a specific Use Case. It is the Context in DCI. A single HTTP request is some kind of a Use Case!

Just like Flux's *action* is a single Use Case.

## DCI and the use of `extend`

* [DCI and MVC](http://rebo.ruhoh.com/dci-and-mvc/)
* [Why DCI Contexts?](http://rebo.ruhoh.com/why-dci-contexts/)

Already defined method calls will always be faster than `extend` method calls.