# Swift

Swift is:

* Extremely modern language
* Extremely fast due to LLVM
* Strong safety
* Interesting features like optionals, cool error-handling, protocol-oriented architecture
* System-level language that feel like scripting language

No more `@` like `@interface`, `@property`, `@end`, `@implementation`, `@synthesize`.

**This is a very ugly class model**

```objective-c
@interface Player : NSObject

@property (nonatomic, copy) NSString *name;
@property (nonatomic, assign) int rating;

@end
```

```objective-c
#import "Player.h"

@implementation Player

@synthesize name;
@synthesize rating;

@end
```

```objective-c
NSMutableArray *players = [NSMutableArray arrayWithCapacity: 20];

Player *player = [[Player alloc] init];
player.name = @"mech";
player.rating = 4;

[players addObject: player];
```

## Data Types

`Int`, `Double`, `Float`, `Bool`, `String`, `Array`, `Dictionary`

* `Int8` from -128 to 127
* `UInt8` from 0 to 255

## Tuples

Temporary groups of related values. Useful as a return values of functions. Not suited for complex data structures.

```
let http404Error = (404, "Not Found")
let (code, message) = http404Error
let (justCode, _) = http404Error
```


## Optional Type

* Conditionally unwrapped with optional binding
* Use `!` to access it

In Swift, values are not allowed to be `nil`. To allow `nil`, you have to be very explicit about it and use optional type.

In Obj-C, if you try to call a method with a pointer variable that is nil, it is a no-op. This may sound nice, but is unpredictable. In Swift, optional type make the possibility of a nil optional value very clear.

Concept of optionals doesn't exist in C or Objective-C.

* Not Set (nil)
* Set to "something"

```objective-c
// Optional string - It's Optional that "can" be a String. Not a String that can be optional.
String?

var name: String
name = nil // Error!

var name: String?
name = nil // Allowed
```

To unwrap an optional, use `!`. It will crash if the value is `nil`. Sometime crashing is good as it is predictable and you can fix it before you ship it.

```objective-c
// "x" is passed as an optional Int
func foo(x: Int?) {
  guard var x = x where x > 0 else {
    print("Bad Params.")
    return  }
  
  x = x + 4}
```

If the value before the `?` is `nil`, everything after the `?` is ignored and the value of the whole expression is `nil`. Otherwise, the optional value is unwrapped. In both cases, the value of the whole expression is an optional value:

```objective-c
let optionalSquare: Square? = Square(sideLength: 2.4)

// You no need to check for nil and can invoke method call
// if optionalSquare is nil, the sideLength will not bother to be called
let sideLength = optionalSquare?.sideLength
```

Optionals are safer and more expressive than `nil` pointers in Objective-C and are at the heart of many of Swift's most powerful features. Can you imagine that?

Swift's `nil` is not the same as Obj-C. In Obj-C, `nil` is a pointer to a nonexistent object. In Swift, `nil` is not a pointer - it is merely the absence of a value of a certain type.

Once you are sure the optional has value, you can force-unwrap it using `!` like `sideLength!`

**Optional Binding**

No need to unwrap, just use the temporary constant or variable to access the optional value.

```objective-c
var optionalName: String? = “mech”
if let name = optionalName {
  greeting = “Hi, \(name)”
}
```

## Guard

* [Guard is like Assert](http://ericcerney.com/swift-guard-statement/)

## String Interpolation

No more string token replacement `%s, %d, %@`.

## Namespaces

No more `NSArray`, `NSString`, just normal `Array` and `String`. Obj-C lack namespaces but not in Swift!