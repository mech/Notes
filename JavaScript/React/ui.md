# UI Component

Segmentation of the UI along these functional boundaries. Black-boxing. Predictable input and output. 

Create dependency graph for your UI! To help coder to visual hierarchy also.

* [AutoResponsive React](http://xudafeng.github.io/autoresponsive-react/)
* [RxJS at Modern Web UI for Netflix](https://www.youtube.com/watch?v=yk_6eU3Hcwo)
* [Nicolas Gallagher - Thinking beyond "Scalable CSS"](https://www.youtube.com/watch?v=L8w3v9m6G04)
* [**React-UI**](https://github.com/React-UI)

## UI Widget Names

## UI Libraries

* [Belle - Configurable React Components with great UX](http://nikgraf.github.io/belle/#/)
* [MediaMath's Strand - Using Web Components](http://mediamath.github.io/strand/)
* [Material Design Lite](http://www.getmdl.io/)
* [Learn from Web Component gallery](http://customelements.io/)
* [Khan Academy reusable components](http://khan.github.io/react-components/)
* [Touchstone](https://github.com/jedwatson/touchstonejs)
* [material-ui](http://material-ui.com/#/)
* [Reapp](http://reapp.io/)
* [React Bootstrap](https://react-bootstrap.github.io/components.html)
* [Elemental UI](http://elemental-ui.com/)
* [MUI](https://www.muicss.com/)
* [Grommet](http://grommet.io/docs/)
* [material-ui](https://github.com/firetix/material-ui)

## CSS

* [Beware of contextual styling](http://csswizardry.com/2015/06/contextual-styling-ui-components-nesting-and-implementation-detail/)
* [Styling React components in Sass](http://hugogiraudel.com/2015/06/18/styling-react-components-in-sass/)
* [Using Webpack to build React components and their assets](http://simonsmith.io/using-webpack-to-build-react-components-and-their-assets/)

## ?

> At any point in time, you describe how you want your UI to look like.

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