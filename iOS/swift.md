# Swift

Swift makes your code SAFE, MODERN, and POWER.

* [All the Swift things](http://thechangelog.com/all-the-swift-things/)
* [Learn Swift](http://www.learnswift.tips/)

## Variables

```
var languageName: String = "Swift"

// Constant if your variable does not vary!
// SAFE: Prefer immutability by default and only opt
// into variable if things need to change
let emptyArray = String[]()
let emptyDictionary = Dictionary<String, Float>()

var optionalString: String? = "Hello, \(name)"

if let name = optionalName {
  greeting = "Hello, \(name)"
}

println("The current user is \(currentUser)")
```

Basic types are `Int`, `Double`, `Float`, `Bool`, `String`, `Array` and `Dictionary`.

## String

Entire `NSString` API for you to use.

```
for character in "mouse" {
}

let dog: Character = ""
```

## Array

```
// SAFE: Typed collections
var names: String[] = ["A", "B", "C"]
```

## Loop

```
for i in 0..3 {
}

for number in 1...5 {
}

for name in ["A", "B", "C"] {
}

// Tuple
for (key, value) in dictionary {
}
```

## Optional

This value wasn't found.

```
// Optional integer
let possibleLegCount: Int? = numberOfLegs["aardvark"]

if possibleLegCount == nil {
  println("Aardvark wasn't found")
} else {
  let legCount = possibleLegCount! // Unwrap operator to force the value out
  println("Aardvark has \(legCount) legs")
}

// Or use this
if let legCount = possibleLegCount {
  println("Aardvark has \(legCount) legs")
}
```

## Functions

```
// Default parameter
func buildGreeting(name: String = "World") -> String {
  return "Hello " + name
}

// To return multiple values, use a tuple
func refreshWebPage() -> (code: Int, message: String) {
  // ...try to refresh...
  return (200, "Success")
}

let status = refreshWebPage()
status.code
status.message

// Function returning a function
func makeIncrementer() -> (Int -> Int) {
  func addOne(number: Int) -> Int {
    return 1 + number;
  }
  
  return addOne
}
```

## Closures

In Swift, functions are just named closure.

```
let greetingPrinter = {
  println("Hello")
}

// Same
let greetingPrinter: () -> () = {
  println("Hello")
}

// Closures as parameters
func repeat(count: Int, task: () -> ()) {
  for i in 0..count {
    task()
  }
}

repeat(2, {
  println("Hello!")
})

// Or more modern way, a trailing closure
repeat(2) {
  println("Hello!")
}
```

## Classes

No header file. No universal base class like `NSObject`. No distinction with instance variables and properties. Swift provide the backing store for us.

```
class Shape: ParentShape {
  // Stored properties
  var name: String
  
  // Computed properties - don't have a backing store
  var description: String {
    // Read-only
    get {
      return "\(numberOfWheels) wheels"
    }
  }
  
  // Swift initializer don't return a value, it's job is to
  // merely ensure properties' initial values
  init(name: String) {
    super.init()
    self.name = name
  }
  
  // Method - no need to use self inside unless setting it!
  func area() -> Double {
    return sideLength * sideLength
  }
  
  // SAFE
  override var parentDesc: String {
  }
  
  // Property observer
  override var speed: Double {
    willSet {
      // newValue
    }
    
    didSet {
      // oldValue
    }
  }
}

// No alloc()
var shape = Shape(name: "Demo")
```

## Beyond Classes

Structure cannot inherit from other structure. Structures are passed by value also. Classes are passed by reference.

```
// Structure
struct Point {
  var x, y: Double
}

var point = Point(x: 0.0, y: 0.0)
```



