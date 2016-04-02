# Go Programming

* [Why Go?](http://nathany.com/why-go/)
* [Why Go is not good](http://yager.io/programming/go.html)
* [Go Object Oriented Design](http://nathany.com/good/)
* [Is Go OO?](http://spf13.com/post/is-go-object-oriented/)
* [Golang for Network Ops](http://networkstatic.net/golang-network-ops/)
* [Effective Go](http://golang.org/doc/effective_go.html)
* [Getting started with Go](http://spf13.com/presentation/first-go-app/)
* [Interfaces](http://research.swtch.com/interfaces)
* [Go at Google](https://talks.golang.org/2012/splash.article)
* [Less is more - Or why C++ programmers don't care about Go](http://commandcenter.blogspot.sg/2012/06/less-is-exponentially-more.html)
* [Vim as Go IDE](http://farazdagi.com/blog/2015/vim-as-golang-ide/)
* [Flame Graphs](https://medium.com/@calavera/docker-flame-graphs-f9523e98d57d?mkt_tok=3RkMMJWWfF9wsRonuqTMZKXonjHpfsX57uUtWqC%2BlMI%2F0ER3fOvrPUfGjI4DTMJgI%2BSLDwEYGJlv6SgFQ7LMMaZq1rgMXBk%3D#.gtiftw5ee)
* [**Go Training**](https://github.com/ardanlabs/gotraining)
* [The way of the Gopher - Making the switch from Node.js](https://medium.com/@theflapjack103/the-way-of-the-gopher-6693db15ae1f#.z0p5r3du8)
* [Handling 1 Million Requests per Minute with Go](http://marcio.io/2015/07/handling-1-million-requests-per-minute-with-golang/)

**Parametric Polymorphism**

Pass by value, rather than by reference.

## Variables and Constants

```
var name string // declare + zero value
name = "mech"

// Same as above, declare + initialize
name := "mech"

// Notice the `name` is in lowercase, which mean they cannot be used outside the
// main package. If it is `Name`, then it can be used.
var (
  name = "mech"
  answer = 42
)

var (
  name, course string
  module float64
)

const speedOfLightMph = 186000
```

## String

```
atoz[0:9]
atoz[:9]
len(atoz)
```

## Arrays and Slices

Arrays are passed by copying. So modifying an array in a function will not change it. This can be quite expensive. Instead use Slices. Slices are passed by reference.

```
words := [...]string{"the", "quick"}
words := [4]string{"the", "quick"}

// Make 4 items array
words := make([]string, 4)
words[0] = "The"

words := make([]string, 0, 4)
words = append(words, "The") // Must use append!
```

## Map

```
dayMonths := make(map[string]int)
dayMonths["Jan"] = 31
dayMonths["Feb"] = 28

days, ok := dayMonths["January"]

if !ok {}

for month, days := range dayMonths {
  fmt.Printf("%s has %d days\n", month, days)}
```

## Read from file

```
import (
  "fmt"
  "os"
)

func main() {
  f, err := os.Open("test.txt")
  if err != nil {
    fmt.Printf("%s\n", err)
    os.Exit(1)  }
  
  defer f.Close()
  
  b := make([]byte, 100)
  
  n, err := f.Read(b)
  
  fmt.Printf("%d: % x\n", n, b)}
```

## Error

Error are returned from function and handle in caller.

```
fmt.Errorf()

errors.New("Custom error")
```

## Pointers

Do you share or copy. Go is by default pass by copy. They don't share. If you want to share, you need to use pointer. You "share" the memory address via `&`.

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

## for Loop

```
// while loop
for counter < 10 {}

for i := 0; i < 10; i++ {}

for i, j := 0, 1; i < 10; i, j = i+1, j*2 {}
```

## Function

Functions are first-class citizen.

```
// If you have 2 parameters of same type
func printer(msg1 string, msg2 string) {}

// You can combine and do
func printer(msg1, msg2 string) {}
```

**Return multiple values**

```go
// Return string and an error in case there are any
func printer(msg, string) (string, error) {
	}

func printer(msgs ...string) {
  for _, msg := range msgs {
    fmt.Printf("%s\n", msg)  }}

printer("Hey", "How are you?")
```

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

## User-defined Types

Go does not have object-orientation. No sub-classes, but only duck-typing. Throughout Go library, they are all using interfaces.

Go has no classes. But they are types. They can be structures and method for those type, but there are strictly no classes.

```
type webPage struct {
  url string
  body []byte
  err error}

func (w *webPage) get() { // (w *webPage) is a pointer receiver
  resp, err := http.Get(w.url)
  if err != nil {
    w.err = err
    return  }
  defer resp.Body.Close()
  
  w.body, err = ioutil.ReadAll(resp.Body)
  if err != nil {
    w.err = err  }}

func (w *webPage) isOk() bool {
  return w.err == nil}

func main() {
  w := &webPage{url: "http://oreilly.com"}
  w.get()
  if w.isOk() {  }}
```

**Duck typing**

```
type shuffler interface {
	Len() int
	Swap(i, j int)}
```