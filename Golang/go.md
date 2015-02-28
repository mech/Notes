# Go Programming

```
package main

import "fmt"

const (
  version = 1.0
)

var (
  answer = 42
)

func main() {
  var message string
  message = "Hello, World!\n"
  
  // Or this
  message := "Hello, World!\n" 
  fmt.Printf(message)
  
  // i = index
  // r = each character of the variable `message`
  for i, r := range message {  }}
```