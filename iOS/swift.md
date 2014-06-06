# Swift

## Variables

```
let emptyArray = String[]()
let emptyDictionary = Dictionary<String, Float>()

var optionalString: String? = "Hello, \(name)"

if let name = optionalName {
  greeting = "Hello, \(name)"
}

println("The current user is \(currentUser)")
```

Basic types are `Int`, `Double`, `Float`, `Bool`, `String`, `Array` and `Dictionary`.

## Loop

```
for i in 0..3 {
}
```

## Functions

```
func makeIncrementer() -> (Int -> Int) {
  func addOne(number: Int) -> Int {
    return 1 + number;
  }
  
  return addOne
}
```

## Classes

```
class Shape: ParentShape {
  var name: String
  
  init(name: String) {
    self.name = name
  }
  
  func area() -> Double {
    return sideLength * sideLength
  }
}

var shape = Shape(name: "Demo")
```

