# Ruby

## Gem Authoring

Short story: `bundle gem gem_name`

## `require` and `autoload` and `const_missing`

* [Matz announced `autoload` is dead](https://www.ruby-forum.com/topic/3036681)

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
