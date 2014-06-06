# TDD

The reason to test is a new behaviour or new use-case, not because of a new method on a class.

* Override `Net::HTTP#start` to make sure it's never called by any test, because testing through network is slow and wrong.
* [Rails testing anti-patterns: Models](https://semaphoreapp.com/blog/2014/01/21/rails-testing-antipatterns-models.html)
* [Rails testing anti-patterns: Controllers](https://semaphoreapp.com/blog/2014/02/11/rails-testing-antipatterns-controllers.html)
* [Managing externals in Ruby tests](https://semaphoreapp.com/blog/2014/03/18/managing-externals-in-ruby-tests.html)

## Is TDD Dead?

* [Martin Fowler's Is TDD Dead links](http://martinfowler.com/articles/is-tdd-dead/)
* [Test isolation is about avoiding mocks](https://www.destroyallsoftware.com/blog/2014/test-isolation-is-about-avoiding-mocks)
* [Hexagonal Rails and the ludicrous terminal application](http://pivotallabs.com/hexagonal-rails-and-the-ludicrous-terminal-application/)

## Case Studies

* When a staff has resigned and took leaves, the "who-is-on-leave" email still include that staff. No test or edge case study was done on that. If we've written the test, we would have slow down and think of edge cases.

## Minitest

* [Shared example in Minitest is just Ruby](https://canaryup.com/blog/shared-examples-with-minitest)

## RSpec

* [Mixing and matching RSpec and Minitest](http://myronmars.to/n/dev-blog/2012/07/mixing-and-matching-parts-of-rspec)
* [New `expect` syntax since 2012](http://myronmars.to/n/dev-blog/2012/06/rspecs-new-expectation-syntax)

## Factories

* [Rails testing anti-patterns: fixtures and factories](https://semaphoreapp.com/blog/2014/01/14/rails-testing-antipatterns-fixtures-and-factories.html)

Factories are slow! They're slow by design.

## Videos

* [Jim Weirich on Decoupling from Rails](https://www.youtube.com/watch?v=tg5RFeSfBM4)
* [Sandi Metz The Magic Tricks of Testing](http://www.youtube.com/watch?v=URSWYvyc42M)