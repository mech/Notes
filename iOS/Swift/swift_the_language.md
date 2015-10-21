# Swift

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

## Optional Type

In Obj-C, if you try to call a method with a pointer variable that is nil, it is a no-op. This may sound nice, but is unpredictable. In Swift, optional type make the possibility of a nil optional value very clear.

* Not Set (nil)
* Set to "something"

```
// Optional string - It's Optional that "can" be a String. Not a String that can be optional.
String?
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

## Guard

* [Guard is like Assert](http://ericcerney.com/swift-guard-statement/)

## String Interpolation

No more string token replacement `%s, %d, %@`.

## Namespaces

No more `NSArray`, `NSString`, just normal `Array` and `String`. Obj-C lack namespaces but not in Swift!