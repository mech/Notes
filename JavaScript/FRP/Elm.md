# Elm

Immutable and stateless function is the only game in town.

Functional HTML. You don't manipulate DOM directly.

```elm
import Html exposing (..)
import Html.Attributes exposing (src)

yogi =
  img [ src "http://a.b.c.jpg" ] []

main = 
  div [] [ yogi ]
```

Don't have statement so no curly braces.

* No NullPointer exception.

## Examples

* [take-home](https://github.com/NoRedInk/take-home)

## Videos

* [Functional Frontend Frontier](https://www.youtube.com/watch?v=06M0jdYYSis)