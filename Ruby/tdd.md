# TDD

* Override `Net::HTTP#start` to make sure it's never called by any test, because testing through network is slow and wrong.

## Minitest

## RSpec

* [Mixing and matching RSpec and Minitest](http://myronmars.to/n/dev-blog/2012/07/mixing-and-matching-parts-of-rspec)
* [New `expect` syntax since 2012](http://myronmars.to/n/dev-blog/2012/06/rspecs-new-expectation-syntax)

## Factories

Factories are slow! They're slow by design.