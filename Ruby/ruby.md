# Ruby

```
ASCII = ('!'..'~')
UPPER = ASCII.grep(/[[:upper:]]/)
LOWER = ASCII.grep(/[[:lower:]]/)
ALPHA = ASCII.grep(/[[:alpha:]]/)
DIGIT = ASCII.grep(/[[:digit:]]/)
PUNCT = ASCII.grep(/[[:punct:]]/)
```

* [The Bastards Book of Ruby](http://ruby.bastardsbook.com/)
* [**All Ruby Books**](http://www.allrubybooks.com/)
* Don't mutate state unnecessarily. It will lead to bugs.
* [Polymorphism and Ruby](http://robots.thoughtbot.com/back-to-basics-polymorphism-and-ruby)
* [Scrape data](http://www.youtube.com/watch?v=eumekfP4IKQ)
* [**Nice resources**](https://github.com/dreikanter/ruby-bookmarks)
* [Practicing Ruby](http://blog.rubybestpractices.com/posts/gregory/063-practicing-ruby-v2.html)
* [Double dispatch](http://blog.rubybestpractices.com/posts/aaronp/001_double_dispatch_dance.html)
* [Implementing Repository pattern](http://hawkins.io/2013/10/implementing_the_repository_pattern/)
* [Basic tools for sniffing out errors](http://6ftdan.com/allyourdev/2015/02/20/some-basic-ruby-tools-for-sniffing-out-errors/#J7YH)
* [Replace rake with thor?](http://codecrate.com/2014/01/replace-rake-with-thor.html)
* [Build your own code climate analysis engine](http://blog.codeclimate.com/blog/2015/07/07/build-your-own-codeclimate-engine/)
* [Hound rubocop yml](https://github.com/thoughtbot/hound/blob/master/config/style_guides/ruby.yml)
* [Default rubocop yml](https://github.com/bbatsov/rubocop/blob/master/config/default.yml)
* [Ruby - #tap that!](http://seejohncode.com/2012/01/02/ruby-tap-that/)
* [Tempfile](https://viget.com/extend/make-remote-files-local-with-ruby-tempfile)

## String

```ruby
AVATAR_URL = 'http://www.gravatar.com/avatar/%{hash}'

def gravatar_url
  AVATAR_URL % {
    hash: hashed_email(email.downcase)  }
end
```

## Duck typing, parametric polymorphism

* [What is the difference between dynamic typing, duck typing and parametric polymorphism?](http://stackoverflow.com/questions/14625654/what-is-the-difference-between-dynamic-typing-duck-typing-and-parametric-polym)

## Service Object

> Service object defines an application boundary that establishes a set of available operations.
> 
> Service object encapsulate cross-cutting operations.
> 
> Service object is standalone operation. Typically only one instance of each service type within the execution context.
> 
> In Rails, is everything that happens in the controller without all the HTTP-related stuff (`params`, `render`, `redirect`).
> 
> Service object encapsulates a single process of the business logic.
> 
> Service object is also not RESTful API, SOA, or even microservices.

## Gem Authoring

Short story: `bundle gem gem_name`

## `require` and `autoload` and `const_missing`

`require_relative` is faster O(1) than `require` O(N).

* [Matz announced `autoload` is dead](https://www.ruby-forum.com/topic/3036681)

So for new gem, how do you `require` things? Every gem you installed gets its `lib` directory appended onto your `$LOAD_PATH`. This means any file on the top level of the `lib` directory could get required. See [RubyGems Guide](http://guides.rubygems.org/patterns/#loading-code).

* `$LOAD_PATH << '.'`
* `$LOAD_PATH << File.dirname(__FILE__)`
* `require './path/to/filename'`
* `$: << File.dirname(__FILE__)`
* `require Pathname.new(__FILE__).dirname + 'filename'`
* `require File.expand_path(File.join(File.dirname(__FILE__), 'filename'))`
* See [aws](https://github.com/appoxy/aws/blob/master/lib/awsbase/require_relative.rb)
* 

## Block

* [Why Ruby blocks exist Part 1](http://programming.oreilly.com/2014/02/why-ruby-blocks-exist.html)
* [Why Ruby blocks exist Part 2](http://programming.oreilly.com/2014/03/why-ruby-blocks-exist-part-ii.html)
* [Why Ruby blocks exist Part 3](http://programming.oreilly.com/2014/05/why-ruby-blocks-exist-part-iii.html)
* [Callbacks and Ruby](http://janjiss.github.io/blog/2014/05/14/callbacks-and-ruby/)

## Symbol

The `&` operator turn Symbol into proc.

```ruby
class Symbol
  def to_proc
    proc { |obj, *args| obj.send(self, *args) }
  end
end
```

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

```
module Faraday
  # These are all utility class methods
  class << self
    attr_accessor :root_path
    
    def new(url = nil, options = nil)
    end
  end
end
```

Prefer `module_function` over `extend self`.

### `module_eval and module_exec`

```
class Thing; end
Thing.module_exec do
  def hi; "Hi"; end
end

Thing.new.hi()
```


## Service

* [Gourmet Service Objects](http://brewhouse.io/blog/2014/04/30/gourmet-service-objects.html)

## Optimize Memory

1. Tune GC. `GC.stat[:minor_gc_count]`, `RUBY_GC_HEAP_GROWTH_FACTOR`, `RUBY_GC_MALLOC_LIMIT`
2. OobGC for unicorn
3. valgrind.org

## Performance

* Benchmark/ips
* stackprof
* GC.stat() - how many objects do we allocate.
* allocation_tracer
* '<tr></tr>'.freeze
* Profiling - ruby-prof (deterministic profiler), perftools.rb, stackprof, rblineprof (sampling profilers)
* GCTracer, AllocationTracer
* NewRelic
* Debugging - ruby-debug, byebug (2.0~) and tracer (stdlib)
* [Dive into Ruby VM Stats with New Relic](http://blog.newrelic.com/2014/04/23/ruby-vm-stats/)
* [Ruby VM measurements](http://docs.newrelic.com/docs/agents/ruby-agent/features/ruby-vm-measurements)
* [debug_inspector](https://github.com/banister/debug_inspector)

## CSV

* [Parsing CSV with Ruby](http://technicalpickles.com/posts/parsing-csv-with-ruby/)

## PDF

* [Developing with PDF Book](http://shop.oreilly.com/product/0636920025269.do)
* [pdf-reader](https://github.com/yob/pdf-reader)

## Enumerator

* [Creating enumerators on the fly](http://blog.honeybadger.io/creating-ruby-enumerators-on-the-fly/)

## Strange looking code

```
article = Article.new.tap(&:save!)
```

```
def built_in_formatter(key)
  case key.to_s
  when 'd', 'doc', 'documentation'
    DocumentationFormatter
  when 'h', 'html'
    HtmlFormatter
  when 'p', 'progress'
    ProgressFormatter
  when 'j', 'json'
    JsonFormatter
  end
end
```

```
raise ArgumentError, <<-EOS.gsub(/^\s+\|/, '')
  |The message here is inside EOS but its whitespace will
  |be removed to make the code easier to read!
EOS
```

```
require 'etc'

Etc.getlogin
```

```
SleepTimer = Struct.new(:minutes, :notifier) do
  def start
    sleep minutes * 60
    notifier.call("Tea is ready!")
  end
end
```

```
("[%1.3f] %s\n" % [duration, message])
```

```
RUBY_VERSION =~ /([\d]+)\.([\d]+)\.([\d]+)/
major, minor, revision = $1.to_i, $2.to_i, $3.to_i
```

## People

* [BIGBinary](http://blog.bigbinary.com/archive.html)
* [Josh Haberman - Ruby Protocol Buffer](http://blog.reverberate.org/)
* [Schneems](http://www.schneems.com/)