# Metaprogramming

* [Nice learning](http://ruby-metaprogramming.rubylearning.com/html/ruby_metaprogramming_1.html)

## Instance Variables

Instance variables just spring into existence when you assign them a value, so you can have objects of the same class that carry different instance variables.

Objects of the same class share methods but don't share instance variables.

## Instance Methods

```ruby
String.instance_methods == "abc".methods
```

## Object Model

**Open Class**

```ruby
class String
  def shout
    self.upcase
  end
end

# Open the scope of the class
String.class_eval do
  # Same?
  def shout
    self.upcase
  end
end
```

## Dynamic Dispatch

Typically with the help of `send()`.

## Dynamic Methods

```ruby
class MyClass
  define_method :my_method do |args|
  end
end
```

## `instance_eval`

Let you mix code and bindings at will. `instance_eval` is a **Context Probe** for you to dip inside an object to do something there.

```ruby
# Since 'everything' is an object, you can use
# instance_eval on class also. But you can't use
# class_eval on an instance like 'hello'
String.instance_eval { puts self } # => String
'hello'.instance_eval { puts self } # => 'hello'

'hello'.class_eval # => NoMethodError
```

## 