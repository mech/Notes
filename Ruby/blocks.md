# Block

Why do we need block? We need block when we have unknown logic that is supposed to be provided by the user.

Blocks are a powerful tool for controlling scope (closure), meaning which variables and methods can be seen by which lines of code.

Blocks are just one member of a larger family of "callable objects", which includes procs and lambdas.

* [Why Ruby blocks exist Part 1](http://programming.oreilly.com/2014/02/why-ruby-blocks-exist.html), [Part 2](http://programming.oreilly.com/2014/03/why-ruby-blocks-exist-part-ii.html), [Part 3](http://programming.oreilly.com/2014/05/why-ruby-blocks-exist-part-iii.html)
* [Callbacks and Ruby](http://janjiss.github.io/blog/2014/05/14/callbacks-and-ruby/)

## `yield` - the "callback"

`yield` is how method perform "callback" to your supplied block.

## Blocks are closures

When code runs, it needs an environment: local variables, instance variables, `self`, etc. These are the bindings which you can think of as names bound to objects.

## Bindings

Bindings are the environment entities like local variables, instance variables, `self` that are bound to the object in question.

Binding is the execution context. It establishes an environment for evaluation.

As soon as you enter a new scope, the previous bindings are replacing by a new set of bindings.

```ruby
# Here instance_eval has a block that will see it's
# surrounding environment context which is the variable v.
# The block can still see the bindings fro the place where
# it's defined.
v = 2
obj.instance_eval { @v = v }
```

## Callable Objects - Procs and Lambdas

**Verdict:** Use lambdas as it is more strict on arity and return and behave more traditional methods.

Most things in Ruby are objects, but blocks are not! Why do you need to turn blocks into objects? So that you can pass it around and execute it later.

You can convert blocks into callable objets that you can set aside and call later.

```ruby
# Deferred Evaluation
inc = Proc.new { |x| x + 1 }
inc.call(2)

# Same
inc = lambda { |x| x + 1 }
inc = ->(x) { x + 1 } # Stabby lambda operator
```

You can convert any Ruby methods to a `Proc` by `Method#to_proc` and you can convert a block to a method with `define_method`.

Lambda is evaluated in the scope it's defined in (it's a closure, remember?), while a `Method` is evaluated in the scope of its object.

## `UnboundMethod`

