# Ruby

* Don't mutate state unnecessarily. It will lead to bugs.
* [Polymorphism and Ruby](http://robots.thoughtbot.com/back-to-basics-polymorphism-and-ruby)
* [Scrape data](http://www.youtube.com/watch?v=eumekfP4IKQ)

## Gem Authoring

Short story: `bundle gem gem_name`

## `require` and `autoload` and `const_missing`

* [Matz announced `autoload` is dead](https://www.ruby-forum.com/topic/3036681)

## Block

* [Why Ruby blocks exist Part 1](http://programming.oreilly.com/2014/02/why-ruby-blocks-exist.html)
* [Why Ruby blocks exist Part 2](http://programming.oreilly.com/2014/03/why-ruby-blocks-exist-part-ii.html)
* [Why Ruby blocks exist Part 3](http://programming.oreilly.com/2014/05/why-ruby-blocks-exist-part-iii.html)
* [Callbacks and Ruby](http://janjiss.github.io/blog/2014/05/14/callbacks-and-ruby/)

## Hash

```
def method_missing(name, *args, &block)
  profile.fetch(name.to_s) { super }
  
  # Don't write like this
  if profile.has_key?(name.to_s)
    profile[name.to_s]
  else
    super
  end
end

def respond_to_missing?(name, include_priv)
  profile.has_key?(name.to_s)
end
```

## Module

```
module FmStore
  module Configurable
    attr_accessor :hostname, :account_name, :password
  end
end

module FmStore
  extend Configurable
end

FmStore.hostname # Because we extend, hostname is class method

module FmStore
  class << self
    include Configurable
  end
end

FmStore.hostname # Notice the use of include in this way is equivalent to extend
```

See http://stackoverflow.com/questions/10039039/why-self-method-of-module-cannot-become-a-singleton-method-of-class

## Service

* [Gourmet Service Objects](http://brewhouse.io/blog/2014/04/30/gourmet-service-objects.html)

## Optimize Memory

1. Tune GC. `GC.stat[:minor_gc_count]`, `RUBY_GC_HEAP_GROWTH_FACTOR`, `RUBY_GC_MALLOC_LIMIT`
2. OobGC for unicorn
3. valgrind.org

## CSV

* [Parsing CSV with Ruby](http://technicalpickles.com/posts/parsing-csv-with-ruby/)