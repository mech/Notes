# UI Component

Big ideas:

* Purely functional UIs
* Single atom app states
* Immutability
* State container

Segmentation of the UI along these functional boundaries. Black-boxing. Predictable input and output. 

Create dependency graph for your UI! To help coder to visual hierarchy also.

* [AutoResponsive React](http://xudafeng.github.io/autoresponsive-react/)
* [RxJS at Modern Web UI for Netflix](https://www.youtube.com/watch?v=yk_6eU3Hcwo)
* [Nicolas Gallagher - Thinking beyond "Scalable CSS"](https://www.youtube.com/watch?v=L8w3v9m6G04)
* [**React-UI**](https://github.com/React-UI)
* [**Pure UI**](http://rauchg.com/2015/pure-ui/)
* [Managing UI complexity with React - Part 1](http://alanbsmith.io/managing-ui-complexity-with-react-part-1/)
* [Managing UI complexity with React - Part 2](http://alanbsmith.io/managing-ui-complexity-with-react-part-ii/)

## Button

```js
class Button extends React.Component {
  render() {
    var className = cx('btn', this.props.primary && 'btn-primary');
    return <button type="button" className={className} onClick={this.props.onClick}>{this.props.children}</button>;  }}
```

## Showcase

* [FatFileFinder](https://github.com/pwambach/fat-file-finder)

## UI Widget Names

## UI Libraries

* [**react-container**](https://github.com/JedWatson/react-container)
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
* [Modals in React](http://www.mybridge.co/view/1943)
* [React components with Material Design Lite](http://quaintous.com/2015/07/09/react-components-with-mdl/)
* [react-look](https://github.com/rofrischmann/react-look)

## CSS

* [Beware of contextual styling](http://csswizardry.com/2015/06/contextual-styling-ui-components-nesting-and-implementation-detail/)
* [Styling React components in Sass](http://hugogiraudel.com/2015/06/18/styling-react-components-in-sass/)
* [Using Webpack to build React components and their assets](http://simonsmith.io/using-webpack-to-build-react-components-and-their-assets/)
* [**Atomic Components**](https://medium.com/@yejodido/atomic-components-managing-dynamic-react-components-using-atomic-design-part-1-5f07451f261f#.rl6hul3o5)
* [**Modularise CSS the React Way**](https://medium.com/@jviereck/modularise-css-the-react-way-1e817b317b04#.q40t5faup)
* [**CSS in JS - techniques comparison**](https://github.com/MicheleBertoli/css-in-js)
* [Responsive breakpoints in JavaScript](https://github.com/nygardk/BreakJS)
* [**Radium - inline styles on React elements**](http://projects.formidablelabs.com/radium/)
* [Applying CSS transitions on initial render](https://web-design-weekly.com/2015/02/05/applying-react-js-css-transitions-initial-render/)
* [**Interoperable CSS**](http://glenmaddern.com/articles/interoperable-css)
* [The debate around 'Do we even need CSS anymore?'](https://css-tricks.com/the-debate-around-do-we-even-need-css-anymore/)
* [The end of global CSS](https://medium.com/seek-ui-engineering/the-end-of-global-css-90d2a4a06284)
* [The future of CSS](http://keithjgrant.com/posts/into-the-future-of-css.html)
* [**Styling React components in Sass**](http://hugogiraudel.com/2015/06/18/styling-react-components-in-sass/)
* [ReactCSS???](http://reactcss.com/)
* [Contextual styling](http://csswizardry.com/2015/06/contextual-styling-ui-components-nesting-and-implementation-detail/)
* [A system for structuring your React application's styles](http://jamesknelson.com/a-system-for-structuring-your-react-applications-styles/)

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

**Don't feed any data as props to your ROOT component (if you can help it) Have your root component manage state.**

A root component is a very good place to manage overall application shell's state. It is also a good place to do data caching!

Container-displayer relationship.

