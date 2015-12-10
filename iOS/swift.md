# Swift

Swift makes your code SAFE, MODERN, and POWER.

* [A better way to learn Swift](https://thinkster.io/a-better-way-to-learn-swift)
* [**15 Open Source Swift projects**](https://medium.com/swift-programming/15-swift-ios-open-source-projects-you-cannot-ignore-6bd4ac37d7dd)
* [Official Apple's Swift blog](https://developer.apple.com/swift/blog/)
* [All the Swift things](http://thechangelog.com/all-the-swift-things/)
* [Learn Swift](http://www.learnswift.tips/)
* [Learn-Swift](http://learn-swift.co/)
* [Inside Swift](http://www.eswick.com/2014/06/inside-swift/)
* [Developing iOS apps using Swift - Part 1](http://ios-blog.co.uk/tutorials/developing-ios-apps-using-swift-part-1/)
* [Cheat Sheet](http://grant.github.io/swift-cheat-sheet/)
* [How to build a nice hamburger button transition in Swift](http://robb.is/working-on/a-hamburger-button-transition/)
* [Swift Yeti](http://swiftyeti.com/)
* [UIKitDynamics](http://omarfouad.com/blog/2014/08/02/getting-started-uikitdynamics-swift/)
* [An analysis of sorts between Objective-C and Swift](http://www.jessesquires.com/apples-to-apples-part-two/)
* [That thing in Swift](http://thatthinginswift.com/)
* [Scala for Android](http://blog.madhukaraphatak.com/scala-for-android/)
* [SCLAlertView](https://github.com/vikmeup/SCLAlertView-Swift)
* [Adaptive Tab Bar](https://github.com/Ramotion/adaptive-tab-bar/)
* [**Frameless**](https://github.com/stakes/Frameless)
* [Swift is like Scala](https://leverich.github.io/swiftislikescala/)

`String`, `Array` and `Dictionary` types are **value types**, a major difference from other programming languages where they are reference types.

## Swift Libraries

* Swift Standard Library
* Cocoa/Cocoa Touch Frameworks
* Xcode 6 exposes Objective-C APIs in Swift format


## Animation in Swift

* [Prototyping iOS animations in Swift](http://mathewsanders.com/prototyping-iOS-iPhone-iPad-animations-in-swift/)
* [Animation in Swift](http://mathewsanders.com/animations-in-swift-part-two/)
* [Twitter bird zoom animation in Swift](http://iosdevtips.co/post/88481653818/twitter-ios-app-bird-zoom-animation)
* [Spinning](http://blog.matthewcheok.com/design-teardown-spinning-tips/)

## Variables

Control + Command + Space to bring up the Emoji box.

```
var languageName: String = "Swift"
var weight: Float = 43

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

### String Interpolation



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

Only certain variables are allowed to be nil and they are called optional. A better "Weak pointer".

```
// I have a variable called firstName that may or may not have value
var firstName: String?

if firstName != nil {
	firstName! // ! is for unwrapping, but it is troublesome} else {
	println("There is no value")}

if let name = firstName {
	println("A value is set")} else {
	println("A value is not set")}
```

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

## Implicitly Unwrapped Options

```
// Option string that is guarantee to exist, unlike String?, which may or may not exist.
// More dangerous
var firstName: String!
```

## Tuples

Can be used as a stupid lightweight data structure?

```
let richard = ("Richard", "Branson", 50)
richard.0
richard.1

let (firstName, lastName, age) = richard
firstName
```

## Nil Coalescing Operator - ??

## Functions

```
// Default parameter
func buildGreeting(name: String = "World") -> String {
  return "Hello " + name
}

// To return multiple values, use a tuple
func refreshWebPage() -> (code: Int, #message: String) {
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

// Variadic
func addManyNumbers(numbers: Int ...) -> Int {
  return numbers[0];}

// inout???
func swapVariables(inout first: Int, inout second: Int) {
  var temp = second
  second = first
  first = temp}
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

// A function that return a function that return an Int
func createAdder(numberToAdd: Int) -> Int -> Int {
  func theAdder(number: Int) -> Int {
    return number + numberToAdd  }
  
  return theAdder}

let addTwo = createAdder(2)
addTwo(5)
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

## Extensions



