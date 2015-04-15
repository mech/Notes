# UI Component

* [Decomplexifying Code with React](https://www.youtube.com/watch?list=PLYRxaDweTODWcfe6V7XMPn40pE6iNd9ij&v=rI0GQc__0SM)

> Human has limit. Working memory is finite.

Cyclomatic complexity can be used to look at your UI code.

> Keep complexity down. Push simplicity up.
> Simple make easy - Closure

White-boarding a user experience - Moving from state to state from UI. As the number of interface states increase, what happen?

Your rendering target is the DOM. DOM is a way to get stuffs into your face. The DOM is a scene graph. Retained mode rendering.

Modelling the transition between states. Don't use imperative code.

```
if (count > 99) {
  if (!hasFire()) {
    addFire();  }} else {
  if (hasFire()) {
    removeFire();  }}
if (count == 0) {
  if (hasBadge()) {
    removeBadge();  }
  return;}
if (!hasBadge()) {
  addBadge();}
var countText = count > 99 ? '99+' : count.toString();
getBadge().setText(countText);
```

Imperative UI coding is very hard to maintain and extend.

Declarative UI coding like React make you model the states as it is. Given the input, what the final state will look like.

> Model states, not transitions!

Let React be your "immediate mode" to tell what the scene will look like over and over again.

React allow you to write your own DSL, your own components, your own HR lexicon!

```
<Pipeline>

</Pipeline
```

> Think of React as a platform

## Root Component

Your render tree.