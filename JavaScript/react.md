# React (by Facebook)

http://facebook.github.io/react/index.html

* Components rather than templates
* State is hard to manage
* DOM insertion is painful!

```
f(d) = v
f(d`) = v`
diff(v, v`) = changes
diff(v`, v) = undo # Go back in time, getting undo for free

d = data
v = virtual DOM
```
Flux is like a game engine.

`renderComponentToString() // Isomorphic applications`

The initial HTML can be generated on the server. React handles the "view" but not with templates in the usual sense. React views are not dumb, they are "virtual DOM".

Using a [difference algorithm](http://calendar.perfplanet.com/2013/diff/) to calculate the fewest number of steps required to render each state.

Render (and re-render) a view hierarchy to any sort of backend you want. It is DOM agnostic.

What makes UI so hard? State changing over time is evil.
Model your UI as pure function.

* [Pete Hunt: High performance functional programming with React and Meteor](http://www.youtube.com/watch?v=qqVbr_LaCIo)
* [Building robust web apps with React](http://maketea.co.uk/2014/03/05/building-robust-web-apps-with-react-part-1.html)
* [Using react with browserify](https://medium.com/publish-what-you-learn/a1ea2dd606b)
* [Example](https://github.com/aslansky/react-stack-playground)
* [Gulpfile example for reactify](https://github.com/callum/tool-test/blob/master/gulpfile.js)
* [Client side layout engines: React vs FruitMachine](http://labs.ft.com/2013/10/client-side-layout-engines-react-vs-fruitmachine/)
* [React vs Angular](http://stackoverflow.com/questions/21111217/react-vs-angular)
* [The question of having DOM in JavaScript](https://twitter.com/jo_liss/status/459101670656708608)
* [Faster AngularJS rendering with ReactJS](http://www.williambrownstreet.net/blog/2014/04/faster-angularjs-rendering-angularjs-and-reactjs/)
* [Quickcoin nice React programming](http://quickcoin.co/tech/responsive-design-and-multi-platform-live-coding/)
* [Why you might not need MVC with React.js](http://www.code-experience.com/why-you-might-not-need-mvc-with-reactjs/)
* [Introduction to React.js](https://vimeo.com/106261417)
* [Goya](https://github.com/jackschaedler/goya)
* [Relieving Backbone Pain with Flux and React](http://dev.hubspot.com/blog/moving-backbone-to-flux-react)

```
var gulp = require('gulp');
var browserify = require('gulp-browserify]');
var concat = require('gulp-concat');

gulp.task('scripts', function() {
  gulp.src(['./src/main.js'])
      .pipe(browserify({
        transform: ['reactify']
      }))
      .pipe(concat('main.js'))
      .pipe(gulp.dest('./build'));
});
```

## Composition

Combine *simple* functions to build more *complicated* ones. One way to manage complexity.

Just build simple interfaces. Makes it easier to predict what will happen.

## Idempotence

Certain operations that can be applied multiple times without changing the result beyond the initial application.

Easy to predict output for a given input. Immutability gets you idempotence for free.

## Virtual DOM

Dirty-checking model can be slow. Virtual DOM is using tree, as we all know, tree can be fast.

DOM operation is very expensive! Because modifying the DOM will also apply and calculate CSS styles, layouts, etc.

* [A Virtual DOM and diffing algorithm](https://github.com/Matt-Esch/virtual-dom)
* [Issues/3](https://github.com/Matt-Esch/virtual-dom/issues/3)

## Director

* [Router for React](https://github.com/flatiron/director)
* [Example of router](https://github.com/andreypopp/react-router-component)

## Mithril

* [Mithril - with Virtual DOM diff](http://lhorie.github.io/mithril/)

## Examples

* [React tutorial](https://github.com/phaedryx/react-tutorial)