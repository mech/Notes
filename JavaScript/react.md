# React (by Facebook)

## People

* Christopher Chedeau
* Tom Occhino

> "Given the extremely tight coupling between the template and it's context (a controller/component), the concerns are the same, and splitting the DOM into a template is an arbitrary separation of technologies rather than a legit separation of concerns." - Hence in React, everything is a component. There is no template. Just define a `render` function.

---
> "The React alternative is programming like you are throwing away your entire component and re-rendering it every time because it is simpler and easier to reason about. Event-based and data binding approaches frequently run into timing problems keeping track of which callback gets called first as well as make it difficult to understand how a small change in state will affect performance."

http://facebook.github.io/react/index.html

**React replaces an imperative mutating API with a declarative one that favors immutability.**

Declarative -> Predictable -> Confidence -> Reliability

* Components rather than templates
* State is hard to manage
* DOM insertion is painful!
* No controller in React
* No template in React
* The single source of truth is all at the Component
* All the stuffs that live on the Ember controller live in React component

React don't like 2-way data binding and template. It like one-way data flow and no template.

```
f(d) = v
f(d`) = v`
diff(v, v`) = changes
diff(v`, v) = undo # Go back in time, getting undo for free

d = data
v = virtual DOM
```

`renderComponentToString() // Isomorphic applications`

The initial HTML can be generated on the server. React handles the "view" but not with templates in the usual sense. React views are not dumb, they are "virtual DOM".

Using a [difference algorithm](http://calendar.perfplanet.com/2013/diff/) to calculate the fewest number of steps required to render each state.

Render (and re-render) a view hierarchy to any sort of backend you want. It is DOM agnostic.

What makes UI so hard? State changing over time is evil.
Model your UI as pure function.

* [**React Future??**](https://github.com/reactjs/react-future)
* [**React Components - Searchable database**](http://react-components.com/)
* [**Presenting the most over-engineered blog ever - Pretty insightful**](http://jlongster.com/Presenting-The-Most-Over-Engineered-Blog-Ever)
* [**React.js UI framework for hybrid mobile apps**](http://touchstonejs.io/)
* [Pete Hunt: High performance functional programming with React and Meteor](http://www.youtube.com/watch?v=qqVbr_LaCIo)
* [**React: RESTful UI Rendering**](https://www.youtube.com/watch?v=IVvHPPcl2TM)
* [Building robust web apps with React](http://maketea.co.uk/2014/03/05/building-robust-web-apps-with-react-part-1.html)
* [Using react with browserify](https://medium.com/publish-what-you-learn/a1ea2dd606b)
* [Example](https://github.com/aslansky/react-stack-playground)
* [Gulpfile example for reactify](https://github.com/callum/tool-test/blob/master/gulpfile.js)
* [Client side layout engines: React vs FruitMachine](http://labs.ft.com/2013/10/client-side-layout-engines-react-vs-fruitmachine/)
* [React vs Angular](http://stackoverflow.com/questions/21111217/react-vs-angular)
* [The question of having DOM in JavaScript](https://twitter.com/jo_liss/status/459101670656708608)
* [Faster AngularJS rendering with ReactJS](http://www.williambrownstreet.net/blog/2014/04/faster-angularjs-rendering-angularjs-and-reactjs/)
* [Improving AngularJS long list rendering performance using ReactJS](http://mono.software/posts/Improving-AngularJS-long-list-rendering-performance-using-ReactJS/)
* [Quickcoin nice React programming](http://quickcoin.co/tech/responsive-design-and-multi-platform-live-coding/)
* [Why you might not need MVC with React.js](http://www.code-experience.com/why-you-might-not-need-mvc-with-reactjs/)
* [Introduction to React.js](https://vimeo.com/106261417)
* [Goya](https://github.com/jackschaedler/goya)
* [Rendering React Components on the server](http://www.crmarsh.com/react-ssr/)
* [Om - too mind blow!](https://github.com/swannodette/om)
* [Facebook's Immutable.js](https://github.com/facebook/immutable-js)
* [React.js and how does it fit in with everything else?](http://www.funnyant.com/reactjs-what-is-it/)
* [Pete Hunt response to side-by-side AngularJS comparison](http://www.quora.com/Pete-Hunt/Posts/Facebooks-React-vs-AngularJS-A-Closer-Look)
* [Isomorphic React app with Rails](https://medium.com/@olance/isomorphic-reactjs-app-with-ruby-on-rails-part-1-server-side-rendering-8438bbb1ea1c)
* [React for stupid people](http://blog.andrewray.me/reactjs-for-stupid-people/)
* [Creating a workflow with WebPack](http://christianalfoni.github.io/javascript/2014/12/13/did-you-know-webpack-and-react-is-awesome.html)

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

## JSX

Solved cross-site scripting?

Allow to create composite component. Component is the proper separation of concern for us. Not the 3-legged stool of HTML, CSS and JavaScript. But a single JavaScript all the way. More composable?

* [JSX: E4X The Good Parts](http://blog.vjeux.com/2013/javascript/jsx-e4x-the-good-parts.html)

## React Router

* [Ryan Florence's and Michael Jackson's brainchild](https://github.com/rackt/react-router)

## Flux

Flux is like a game engine.

* [Flocks.js](https://github.com/StoneCypher/flocks.js)
* [Relieving Backbone Pain with Flux and React](http://dev.hubspot.com/blog/moving-backbone-to-flux-react)
* [Flux for stupid people](http://blog.andrewray.me/flux-for-stupid-people/)
* [Reflux data flow model?](http://blog.krawaller.se/posts/the-reflux-data-flow-model/)
* [Getting to know flux](https://scotch.io/tutorials/getting-to-know-flux-the-react-js-architecture)
* [Simple data flow in React apps using Flux and Backbone](http://www.toptal.com/front-end/simple-data-flow-in-react-applications-using-flux-and-backbone)

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

## Videos

* [Pete Hunt - Rethinking Best Practices](https://www.youtube.com/watch?v=x7cQ3mrcKaY)
* [Pete Hunt - Rethinking Best Practices (updated) 2013](https://www.youtube.com/watch?v=DgVS-zXgMTk)
* [Functional Web Development](https://www.youtube.com/watch?v=Elr_RNt2R5Q)
* [Secret of the Virtual DOM](https://www.youtube.com/watch?v=1h2G20A-AvY)
* [Alt.Net Jan 2015](http://youtu.be/kNVatRjnU7U)