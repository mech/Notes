# Elm

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