# TDD

* Override `Net::HTTP#start` to make sure it's never called by any test, because testing through network is slow and wrong.
* [Rails testing anti-patterns: Models](https://semaphoreapp.com/blog/2014/01/21/rails-testing-antipatterns-models.html)
* [Rails testing anti-patterns: Controllers](https://semaphoreapp.com/blog/2014/02/11/rails-testing-antipatterns-controllers.html)
* [Managing externals in Ruby tests](https://semaphoreapp.com/blog/2014/03/18/managing-externals-in-ruby-tests.html)

## Minitest

## RSpec

* [Mixing and matching RSpec and Minitest](http://myronmars.to/n/dev-blog/2012/07/mixing-and-matching-parts-of-rspec)
* [New `expect` syntax since 2012](http://myronmars.to/n/dev-blog/2012/06/rspecs-new-expectation-syntax)

## Factories

* [Rails testing anti-patterns: fixtures and factories](https://semaphoreapp.com/blog/2014/01/14/rails-testing-antipatterns-fixtures-and-factories.html)

Factories are slow! They're slow by design.

## Videos

* [Jim Weirich on Decoupling from Rails](https://www.youtube.com/watch?v=tg5RFeSfBM4)
* [Sandi Metz The Magic Tricks of Testing](http://www.youtube.com/watch?v=URSWYvyc42M)