# Elm

* [Starting with Elm](http://www.romanzolotarev.com/elm/)
* [functional-frontend-architecture](https://github.com/paldepind/functional-frontend-architecture)
* [Learn You an Elm](http://learnyouanelm.github.io/)
* [Building a Live-Validated Signup Form in Elm](http://tech.noredink.com/post/129641182738/building-a-live-validated-signup-form-in-elm)
* [Scalable frontend, with Elm or Redux](https://github.com/slorber/scalable-frontend-with-elm-or-redux)
* [Automatically curried and memoized](https://medium.com/@matthiasak/on-elm-currying-memoization-pragmatism-and-learning-other-languages-1825d6673766#.2l31ybcu0)

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

## Modules

In Elm, the basic building blocks are a set of modules. Think of it as component in React. Each component has 2 basic functions: update and view.

Think of it as `setState/reducer` for update and `render` for view.

You have to be discipline enough to not mutate state during `setState`.

## Effects

Tasks is like composable promises

## Examples

* [take-home](https://github.com/NoRedInk/take-home)

## Videos

* [Functional Frontend Frontier](https://www.youtube.com/watch?v=06M0jdYYSis)