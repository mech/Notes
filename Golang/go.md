# Go Programming

* [Why Go?](http://nathany.com/why-go/)
* [Go Object Oriented Design](http://nathany.com/good/)
* [Golang for Network Ops](http://networkstatic.net/golang-network-ops/)
* [Effective Go](http://golang.org/doc/effective_go.html)
* [Getting started with Go](http://spf13.com/presentation/first-go-app/)

Pass by value, rather than by reference.

## Variables and Constants

```
var (
  name, course string
  module float64
)

const speedOfLightMph = 186000
```

## Pointers

Go passes arguments by value. It has pros and cons.

Use pointers if you want to get around that.

* `&` - References a pointer
* `*` - De-references a pointer

```
module := 3.2
ptr := &module

fmt.Println("Memory address of *module* variable is", ptr, "and the value of *module* is", *ptr)
```

```
// Pass by reference
changeCourse(&course)

// Working with de-reference
func changeCourse(course *string) string {
  *course = "First look"
  return *course}
```

## Function

Functions are first-class citizen.

```
package main

import (
  "fmt"
  "reflect"
  "os"
)

const (
  version = 1.0
)

// These variables are global in scope
var (
  answer = 42
)

func main() {
  for _, env := range os.Environ() {
    fmt.Println(env)  }
  
  name := os.Getenv("USERNAME")

  var message string
  message = "Hello, World!\n"
  
  // := only work inside func
  a := 10.0000
  b := 3
  c := int(a) + b // convert float to int
  fmt.Println("A is type", reflect.TypeOf(a))
  
  // Or this
  message := "Hello, World!\n" 
  fmt.Printf(message)
  
  // i = index
  // r = each character of the variable `message`
  for i, r := range message {  }}

func bestFinishes(finishes ...int) int {
  // Slice of int
  for _, i := range finishes {  }}
```