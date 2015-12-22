# Swift Protocol

> Don't start with a class. Start with a Protocol.

* [Mixins and Traits in Swift 2](http://matthijshollemans.com/2015/07/22/mixins-and-traits-in-swift-2/)

Called interfaces in other languages.

The majority of the Swift Standard Library is largely implemented through protocols.

Almost every single aspect of the Swift language comes from this philosophy of protocols defining the behavior of objects, rather than their inheritance trees.

Duck typing.

```
protocol Drivable {
  func drive()
}
```

That's the power of protocols: they let you hide the actual type of your object. The code only cares that this object does what the protocol demands of it, but it does not need to know anything else about the object's internal structure.

This allows you to program against the interface, not the implementation, and that's considered to be a good thing.

## Extensions

Called "categories" in Obj-C.

Easy to mis-use and dangerous. Just like extending a class in Ruby.