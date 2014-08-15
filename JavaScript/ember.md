# Ember

STOP: http://emberjs.com/guides/components/

Use ember-cli instead of starter kit.

Ember is Cocoa and Angular is JSF? Ember in a page has many tiny group of MVC.

Don't operating on wrong assumption. Expose your ignorance.

* [Twitter search for Ember.js news](https://twitter.com/search?q=emberjs&src=typd)
* [Ember Weekly](http://emberweekly.com/issues.html)
* [Ghost using Ember.js](https://github.com/TryGhost/Ghost/issues/2144)
* [An in-depth introduction to Ember.js (Smashing Magazine)](http://www.smashingmagazine.com/2013/11/07/an-in-depth-introduction-to-ember-js/)
* [Want to learn Ember.js? Start here!](http://elweb.co/want-to-learn-ember-js-start-here/)
* [Robin Ward's AngularJS vs Ember](http://eviltrout.com/2013/06/15/ember-vs-angular.html)
* [Instructure](http://instructure.github.io/blog/)
* [Ember vs Angular - Templates](http://pivotallabs.com/ember-vs-angular-templates/)
* [ember-appkit-rails using ES6 module but testing is QUnit](https://github.com/dockyard/ember-appkit-rails)
* [A series to compare Angular with Ember](http://www.benlesh.com/2014/04/embular-part-2-whats-great-about-angular.html)
* [ic-ajax](https://github.com/instructure/ic-ajax)
* [EmberScript](http://emberscript.com/)
* [Ember ListView](http://emberjs.com/list-view/)
* [Build your own Ember app kit lite](http://toranbillups.com/blog/archive/2014/04/07/Building-your-own-ember-app-kit-lite-part-1/)
* [ES6 modules, build tools and browser app delivery](http://ryanflorence.com/2013/es6-modules-and-browser-app-delivery/)
* [Sketches from EmberConf 2014](http://chantastic.io/emberconf2014/)
* [Drag and drop image upload with Ember.js](https://medium.com/ember-js-framework/c19e99f9823c)
* [Ember and Web Components](https://gist.github.com/wycats/9144666b0c606d1838be)
* [Ember.js with Ruby on Rails](http://blog.abuiles.com/ember-js-with-ruby-on-rails/)
* [Shared terminology yet different concepts between Ember.js and Rails](http://robots.thoughtbot.com/shared-terminology-yet-different-concepts-between-emberjs-and-rails)
* [Ember and Polymer](https://news.ycombinator.com/item?id=7945084)
* [Tuts+ Let's Learn Ember](http://courses.tutsplus.com/courses/lets-learn-ember)
* [Some nice things to learn from iOS MVVM](https://medium.com/@ramshandilya/lets-discuss-mvvm-for-ios-a7960c2f04c7)
* [Ember Best Practices](https://github.com/chrisjlee/ember-best-practices)

```
Ember.run.once();

setProperties({});
```

Since there is no round-trip, just pass real object in parameters, and no need for String.

## Ember and Browserify?

* https://gist.github.com/simme/8931006

## ember-cli

* [Broccoli: First beta release](http://www.solitr.com/blog/2014/02/broccoli-first-release/)
* [From gulp.js to ember-cli](https://medium.com/ember-js-framework/450f1ffb1967)
* [ember-cli-plus-backend](https://github.com/dockyard/ember-cli-plus-backend)
* [Rails and ember-cli](https://devmynd.com/blog/2014-7-rails-ember-js-with-the-ember-cli-redux)


### ember-cli with Rails

* [Building an Ember app with Rails](http://reefpoints.dockyard.com/2014/05/07/building-an-ember-app-with-rails-part-1.html)
* [Building an Ember.js production application with ember-cli](http://edgycircle.com/blog/2014-building-an-emberjs-production-application-with-ember-cli/)
* [Deploying ember-cli and Rails to Heroku](http://blog.abuiles.com/blog/2014/05/21/deploying-ember-cli-and-rails-to-heroku/)
* [ember-cli-rails?](https://github.com/knomedia/ember-cli-rails)
* [Deploying ember-cli to Amazon S3 with Grunt](http://www.octolabs.com/blogs/octoblog/2014/05/24/deploying-ember-cli-to-amazon-s3-with-grunt/)
* [Rails and ember-cli](https://devmynd.com/blog/2014-7-rails-ember-js-with-the-ember-cli-redux)

## Broccoli

![Broccoli trees](https://dl.dropboxusercontent.com/u/6815194/Notes/broccoli.png)

Broccoli is all about trees. Take the 'lib' tree, concat it into a single `app.js`.

```
var concat = require('broccoli-concat');
var compileSass = require('broccoli-sass');
var autoprefixer = require('broccoli-autoprefixer');
var mergeTrees = require('broccoli-merge-trees');

var appJs = concat('lib', {
  inputFiles: ['jquery.js', '**/*.js'],
  outputFile: '/assets/app.js'
});

var appCss = compileSass(['styles'], 'app.scss', '/assets/app.css');

module.exports = mergeTrees([appJs, appCss, 'public']);
```

## Application

```
// See what object in memory is being created
App = Ember.Application.create({
  LOG_ACTIVE_GENERATION: true,
  LOG_TRANSITIONS: true,
  LOG_TRANSITIONS_INTERNAL: true,
  LOG_VIEW_LOOKUPS: true,
  
  modulePrefix: 'CP',
  
  ready: function() {
    // jQuery ready hook
  }
});
```

## Run Loop (backburner.js)

* [How does run loop work](http://stackoverflow.com/questions/13597869/what-is-ember-runloop-and-how-does-it-work)
* [Visualization of the run loop](https://machty.s3.amazonaws.com/ember-run-loop-visual/index.html)
* [backburner is a rewrite of the run loop](https://github.com/ebryn/backburner.js)

Not a loop like programmers might think. It is an "aggregate changes over time" mechanism. Used to batch, and order (or reorder) work in a way that is most efficient by scheduling work on specific queues. These queues have a priority, and are processed to completion in priority order.

The run loop is not constantly running!

Some things 'cost' more than others:

* DOM manipulation
* Layout calculation
* Your cool, but expensive algorithm

`Ember.run.queues` return an array of queue buckets like `["sync", "actions", "routerTransitions", "render", "afterRender", "destroy"]`. We throw jobs into these buckets and they are prioritise to run.

`autoRun` not in test environment.

```
// Asynchronous
Ember.run(function() {
  this.set();
  this.set();
});
```

* `Ember.run.join`
* `Ember.run.later` - Use this instead of `setTimeout`
* `Ember.run.next` - Next tick, consider `schedule`
* `Ember.run.schedule` - Push to queue
* `Ember.run.scheduleOnce`
* `Ember.run.debounce`
* `Ember.run.throttle`

Usually user events that will trigger run loop.

## Naming Convention

Every ember has a default top-level `ApplicationRoute` with a first nested `IndexRoute`. Think of it this way, at your `application.hbs` template, you will have an `{{outlet}}` where the `index.hbs` can reside when the `IndexRoute` is being visited.


|    Name    |                      Object                     |
| ---------- | ----------------------------------------------- |
| Router     | `this.resource('tables')` and `App.TablesRoute` |
| Controller | `App.TablesController`                          |
| Model      | `App.Table`                                     |
| View       | `App.TablesView`                                |
| Template   | `tables`                                        |

## URLs and Routing

* [What should my Rails routes look like to work with pushState](http://stackoverflow.com/questions/12116804/what-should-my-rails-routes-look-like-to-work-with-pushstate-ember-js-routes)

The shareable part. Ember router presents a DSL that helps bridge user-readable URLs with an *application-level state machine*. **As you enter or exit URLs, the router signals to routes that they should configure or cleanup.**

If you have `this.resource('tickets')`, you will have 2 routes automatically like `TicketsRoute` and `TicketsIndexRoute`. The route name will be `tickets.index`.

Index routes provide the default route where another may be nested.

```
// Detect the '/' path and render the todos template
this.resource('todos', { path: '/' });
```

Action routes (I like verb):

- /login/one-time-password/authenticate
- /recover-username

```
// If your developing and when to change index to other module
App.IndexRoute = Ember.Route.extend({
  redirect: function() {
    this.transitionTo('pipelines');
  }
});
```

### State

State is collection of active objects in memory.

Your route prepare state, fetch model data from API and setup controller state. The controller state is where all state change happen (long-living State). The view presents the state.

```
App.SearchRoute = Ember.Route.extend({
  model: function() { /* models for state */ },
  setupController: function(controller, model) {
    controller.set('content', model);
    // other initial state
  },
  renderTemplate: function() {
    this.render();
  }
});

<button {{ action 'search' }}>Search</button>
```

## Router

Only ever one instance.

Router has a map to find our route.

Besides generating route classes, router also generates controllers and templates. The router *wires* them together when entering a route.

## Route

* [Tom Dale: Building URL-driven apps with Ember.js](https://vimeo.com/68390483)

You'll spend most time on the route than any other Ember's parts. In Rails, you use Controller to load data, but in Ember, you do it at Route. Route loads data and assigns it to a controller using `setupController()`. Controller in Ember rarely has the job to load data!

When `/tables` is visited, Ember calls the `App.TablesRoute` object, which finds the list of tables and assigns it to the `App.TablesController`.

Routes manage state, including serialisation and de-serialisation.

```
// search-results makes a better class name than it does a URL
this.route('search-results', { path: 'search/:term' });
```

Route has a entrance or exit and the following are the lifecycle hooks (asynchronous or synchronous).

Route hooks:

* `beforeModel` - (Async) intended for rejecting entrance to a route or redirecting away to another route (permission maybe)
* `model` - (Async) is expected to return a promise that will be set as the model presented to the template
* `afterModel` - (Async) can reject proceeding into a route based on the content of the model or fetch additional data
* `activate` (Sync) is called when a route is first entered
* `setupController` - (Sync) set the model on the controller
* `renderTemplate` - (Sync)
* `serialize` - (Sync) formats an object or collection passed as the model into parameters for building the route's URL segment
* `deactivate` - (Sync) called when exiting a route
* `willTransition`
* `didTransition`

Can we have more than one model in a route?

```
App.IndexRoute = Ember.Route.extend({
  actions: {
    didTransition: function() {
      Ember.run.once(this, function() {
        trackAnalytics(this.get('router.url'));
      });
    }
  }
});
```

Asynchronous promises `getJSON`

```
App.IndexRoute = Ember.Route.extend({
  model: function() {
    return new Ember.RSVP.Promise(function(resolve, reject) {
      $.getJSON('/tickets.json').then(function(data) {
        Ember.run(null, resolve, data);
      }, function(error) {
        Ember.run(null, reject, error);
      });
    });
  }
});
```

## Controller

One Page != One Controller. This is almost always wrong in Ember.js. Don't give a controller too many responsibilities. Break it up into tiny pieces of UI functionalities. Just introduce more controllers. They are free on client-side :)

```
App.ListsController = Ember.ArrayController.extend({
  needs: ['snapshot'], // use more controllers
  
  selected: -> {
    this.get('model').findBy('selected')
  }.property('model.@each.selected'),
  
  hovering: -> {
    this.get('model').findBy('hovering')
  }.property('model.@each.hovering')
});
```

**Controller is not the place to LOAD data as in Rails. Instead make use of Route's hook and promises to load data.**

[Controller in Ember is just ViewModel](http://www.wekeroad.com/2014/05/28/the-frustratingly-lovable-crazy-making-huggable-ball-of-whack-that-is-ember-js/). In Cocoa iOS, every View is backed by a Controller, which may or may not have some data.

* Model - All sessions. Represent long-term state that persists from session to session.
* Controller - Just this session
* Template/View - What is currently visible. Are transient, responsible for little or no state.

> Ember's controllers are mediating controllers and route objects are coordinating controllers - [Tom Dale on services](http://discuss.emberjs.com/t/services-a-rumination-on-introducing-a-new-role-into-the-ember-programming-model/4947/56)

Controllers have 2 responsibilities in Ember:

* Manage transient state for sections of the running application. This involves setting properties on the controller, and having the controller handle some actions.
* Decorate models for presentation.

Delivers model data to views and templates.
Array and Object controllers manage a `model` property. They act as proxy to the model's attributes and methods, sending them along if asked.

In a single UI view, you will have many controllers at one go. They are all instantiated by Ember and stay on the screen for as long as the UI need it to. So 1 page does not mean you have only 1 controller.

3 types:

* `Controller`
* `ObjectController`
* `ArrayController`

Extend `Ember.Evented` for your controller if you want event bus.

How controller talk to view? `Ember.View.views.XX`

```
// Some validation example for controller. isValid state is available to you all the time
App.SearchController = Ember.Controller.extend({
  actions: {
    search: function() {
      if (this.get('isValid')) {
        this.transitionToRoute('search.index', keyword);
      }
    }
  },
  
  isValid: function() {
    return !Ember.isEmpty(this.get('keyword'));
  }.property('keyword'),
  
  isNotValid: Ember.computed.not('isValid')
});

<button {{ action='search' }} {{ bind-attr disabled=isNotValid }}>Search</button>
```

### ArrayController

Sortable mix-in.

An `ArrayController` could manage the knowledge about which item in an array is selected.

* [Sorting array using `Ember.computed.sort`](http://balinterdi.com/2014/03/05/sorting-arrays-in-ember-dot-js-by-various-criteria.html)

### Managing transient state

Controller is also the place where you hold UI temporary state like checkbox status, etc.

```
{{ view Ember.Checkbox checkedBinding="artistIsChecked" }}
```

The `artistIsChecked` resides at the controller and make the UI show or hide with ease.

Controllers can share their state with other controllers, and have parent-child relationships. Actions can bubble up through these relationships, making them a powerful and important part of how complex applications are structured.

### Decorating models

### Actions

To cause an action to keep bubbling even though it was handled, return `true` from the handler.

### Communicating between controllers

The `itemController` of an `{{#each` helper can access its parent via `parentController` to access maybe toggle, filter states, or search query etc.

You can also use `needs` which is good for placing `currentUser` information.

Always consider the tradeoffs inherent in coupling controllers to each other. Good alternatives to `needs` include use of `controllerFor` on routes to access controller instances and send messages, and the `register/inject` dependency injection of Ember containers.

[See how itemController come about](https://github.com/emberjs/ember.js/issues/1637#issuecomment-11785445)

## Partial and Render

    <script type="text/x-handlebars" data-template-name="_map">
      <div id="map"></div>
    </script>
    
    {{ partial 'map' }}

## Query Params (a new primitive)

* [Ember Query Parameters - Elte Hupkes](https://www.youtube.com/watch?v=nyD7CRuA-PU)

Why it took so long? Model (Route) vs Controller are two equally good place for Query Params? But now, it is the controller's job.

`/?query=params`

```
App.ArticlesController = Ember.ArrayController.extend({
  queryParams: ['page'],
  page: 1
});
```

> Model-dependent state! - Alex Matchneer

What's the job of a controller anyway?

* Manage application state
* Wrap the model with additional information to present to the template (also application state)

Query params will be on the controller state.

## Screens and Flows

Flows are just as important to good interfaces as individual screens are.

Directed graph, nodes, edges, etc

`replaceWith`
`transitionTo`

* [ember-flows](https://github.com/nathanhammond/ember-flows)
* [ember-flows slide?](https://github.com/alexdiliberto/emberconf-2014-demo)

See http://www.youtube.com/watch?v=iFBOYMxDl40

## Nested Routes means Nested UI

Nesting in Ember.js is visual (rendering views inside views). It is not like in Rails, which is nested resources for scoped access.

```
this.resource('project', { path: '/projects/:projectId' }, function() {
  this.route('story', { path: '/stories/:storyId' });
});
```

If you want to render into other named outlet, you can:

```
{{outlet toolbar}}
{{outlet inspector}}

export default Ember.Route.extend({
  renderTemplate: function() {
    this.render({outlet: 'inspector'});
  }
});
```

## Object Model, KVO and Computed Properties

* [KVO in Apple](https://developer.apple.com/library/mac/documentation/cocoa/conceptual/KeyValueObserving/KeyValueObserving.html)
* [Ember.js Object Model](http://emberjs.com/guides/object-model/classes-and-instances/)

CP

* Transforms an object property defined as a function into a value
* The function will only be called once and the returned value will be cached, so they are efficient
* Can specify properties that your computed property depends on
* The cached result will be recomputed if the dependencies are modified

Check out the source at `computed.js`

* Consider data as flowing in 2 different directions from a computed property
* A `.get()` flows down, while a `.set()` flows up

Element attributes in views can be bound to objects' properties.

```
<button {{ bind-attr disabled=isNotValid }}>Search</button>
```

## Array Computed Properties (reduce)

```
.property('names.[]') // bad?

.property('activeSquares.@each')

// Or use Ember.arrayComputed using Ember.computed.map
names: map('people.@each.name', function(person) {
  return person.get('name').toUpperCase();
})
```

```
@this!!!!!
```

[Array Computing Properties](http://www.youtube.com/watch?v=v6Q7vSwNNz4)

## Component

> For you Angular peeps, an Ember.js component is roughly equivalent to an E restricted, transcluded, isolate-scoped directive. - [https://twitter.com/tomdale/status/361288660240441344](Tom Dale)

Followed closely to Web Component standard.

If you just want some static HTML and pass in simple properties, you do not need to extend `Ember.Component`, but if you need to change the wrapped element, integrating with third-party library like D3, or handle actions, then you need to extend `Ember.Component` class to better manage things.

```
App.HeatMapComponent = Ember.Component.extend({
  width: 900,
  height: 280,
  margin: { top: 50, right: 0, bottom: 100, left: 30 },
  colors: [ '#2F0000', '#661201' ],
  
  draw: function(data) {
    // draw the heat map using D3
    this.set('data', data);
    var svg = d3.select('#' + this.get('elementId'));
  },
  
  didInsertElement: function() {
    var data = this.get('controller.data.content');
    // You can prepare the data here and do anything initial
    // data massaging here
    this.draw(data);
  }
});
```

## Ember.View

* [Difference between views and components](http://stackoverflow.com/questions/18593424/views-vs-components-in-ember-js)

One of the major reasons an Ember.View exists is to translate browser events into application events. That's why it captures all browser events in functions like `dragStart`, `click`, etc. It's also why Ember.View emits application events to Controllers. Browser events come in, application events go out.

The `Ember.View` is the Ember object responsible for pushing the HTML into the DOM, updating the DOM as the bound object's values are modified, and then responding to user interaction such as clicks.

Views only manage DOM and rendering concerns and you don't typically need to create them.

`Ember.View` manages DOM lifecycle and events, but is not responsible for decorating models or managing state. For that you need a controller.

Views are normally quite temporary instances, and ill suited for keeping track of application state. Once a view is no longer displayed its `Ember.View` instance is destroyed, losing any state. So if you want application state, do it are controller!

```
App.MyView = Ember.View.extend({
  didInsertElement: function() {
    this.get('controller').on('startAnimation', this.startAnimation, this);
  },

  startAnimation: function() {
    this.$().css(left: 200);
  }
});
```

```
// Possible future for Ember.View?
class View extends HTMLElement {
  hide() {
    this.isVisible = false;
  }
}
```

Separate row, cell into view.

```
App.RowView = Ember.View.extend({
  templateName: 'row',
  tagName: 'tr',
  classNames: ['board-row']
});

App.CellView = Ember.View.extend({
  templateName: 'cell',
  tagName: 'td',
  classNameBindings: ['color', 'piece'],
  attributeBindings: 'draggable',
  draggable: 'true',
  
  dragOver: function(e) {
    e.preventDefault();
  },
  
  dragLeave: function(e) {
    e.preventDefault();
  },
  
  dragStart: function(e) {
    e.dataTransfer.setData('text/text', 'data');
  },
  
  drop: function(e) {
    this.get('controller').send('gameChanged');
  }
});

// Create a new App.RowView for each row...
{{ #each rows }}
  {{ view App.RowView }}
{{ /each }}

// And the RowView itself will in turn create a new CellView for each cell...
<tr class="board-row">
  {{ #each this }}
    {{ view App.CellView }}
  {{ /each }}
</tr>

// If we use tagName and classNames, we can simplify it:
{{ #each this }}
  {{ view App.CellView colorBinding=color pieceBinding=piece }}
{{ /each }}
```

## HTMLBars

* HTML-aware
* Context-specific helpers/bindings
* No more `bind-attr`
* Validate HTML
* No more metamorphs
* No more DOM pollution
* Use DOM fragment and deep clone
* String manipulations increase the pressure on the GC

```
{{#link-to 'articles' (query-params sort='ASC')}}

// s-expressions
{{capitalize (reverse foo)}}
{{reverse (capitalize foo)}}
```

## Ember.Handlebars

If you use `Handlebars.SafeString`, be sure to escape any user input with `Handlebars.Utils.escapeExpression`

## Lifecycle Hooks

## Animations and Transitions

* [Liquid Fire: Animations and Transitions for Ember Apps](http://ef4.github.io/liquid-fire/#/)
* [ember-animation-demo](https://github.com/ef4/ember-animation-demo)
* [ember-animate](https://github.com/gigafied/ember-animate)

With `Ember.View`, we can use the hooks:

* Animate in using `willInsertElement/didInsertElement`
* Swap? Maybe `willClearRender`??
* Animate out using `willDestroyElement`
* `parentViewDidChange`?

No animation story in Ember, is it because need to wait for HTMLBars?

## Data

The places your data will go!

* Migration (From old MySQL CP to new Postgres CP)
* Search (ElasticSearch)
* Caching (Redis)
* Mobile (API endpoints)
* [Transition for ember-data?](https://github.com/emberjs/data/blob/master/TRANSITION.md)
* [wycats's app.js example](https://gist.github.com/wycats/8129945)
* [EPF - Ember.js Persistence Foundation by GroupTalent](http://epf.io/)
* [Model maker](http://andycrum.github.io/ember-data-model-maker/)
* [ember-cli + ic-ajax](https://www.youtube.com/watch?v=7twifrxOTQY)

All you need to do is implement the `find` and `findAll` methods.

## Model

Model can be used for transient data (data we don't plan to store to a database) as well as persistence data.

Models are good for defining structured data.

## Bootstrap

Pre-render data server-side rather than calling 50+ Ajax on boot-time. Use server-side rendering.

## Authentication and Session

* [Torii - Best one to use?](https://github.com/vestorly/torii)
* [Ember.SimpleAuth](https://github.com/simplabs/ember-simple-auth)
* [ember-devise-simple-auth](https://github.com/d-i/ember-devise-simple-auth)
* [End-to-end security](http://apigee.com/about/products/apis/edge-secure-enterprise-apis)
* [How Zendesk use ember-resource for authentication token? At the initializer?](https://github.com/zendesk/ember-resource)
* [Ember add-on to track of Rails CSRF](https://github.com/abuiles/rails-csrf)
* [AI auth using Angular](http://engineering.talis.com/articles/elegant-api-auth-angular-js/)
* [OAuth with Ember and Rails](http://www.youtube.com/watch?v=q_gy8EgN8FE)
* [SOA in Rails](http://www.youtube.com/watch?v=L1B_HpCW8bs)
* [OAuth for Rails](http://www.octolabs.com/blogs/octoblog/2014/04/22/service-oriented-authentication-railsconf/)
* [OAuth provider](https://github.com/doorkeeper-gem/doorkeeper)
* [Minimal API Authentication on Rails ](http://resistor.io/blog/2013/08/07/mimimal-api-authentication-on-rails/)
* [Authentication options in Rails](http://everydayrails.com/2011/09/21/rails-authentication.html)


```
App.SecretArticlesRoute = Ember.Route.extend({
  beforeModel: function() {
    if (!this.controllerFor('auth').get('isLoggedIn')) {
      this.transitionTo('login');
    }  
  }
});
```


`Access-Control-Allow-Origin` with CORS (Cross Origin Resource Sharing). Use `rack-cors` gem.

By default, jQuery does not send cookies with Ajax requests, so session-based authentication may not be working! `withCredentials` to the rescue!

```
$.ajaxPrefilter(function(options, originalOptions, jqXHR) {
  options.xhrFields = { withCredentials: true };
});
```

```
// OAuth?
App = Ember.Application.create({
  ready: function() {
    var store = App.__container__.lookup('store:main');
    var id = 'me?_=' + (new Date()).getTime();
    store.find('user', id).then(function(user) {
      App.currentUser = user;
    });
  }
});

// Custom 401 error handler
App.ApplicationAdapter = DS.RESTAdapter.extend({
  ajaxError: function(jqXHR) {
    var error = this._super(jqXHR);
    if (jqXHR && jqXHR.status === 401) {
      var newLocation = 'https://host.com/auth?return="xxx"';
      newLocation += encodeURIComponent(document.location.toString());
      document.location = newLocation;
    } else {
      return error;
    }
  }
});
```


```
// Vine's CurrentUserController
sessionChanged: (function() {
  if (this.get('session.isAuthenticated')) {
    this.userService.currentUser().then(function(user) {
      this.set('content', user);
    }.bind(this)).catch(function(err) {
      // handle session expiry, etc.
    });
  }
}).observes('session.userId').on('init');
```
```
TimelineIndexController = Ember.ArrayController.extend({
  itemController: 'post'
});
```

## Container and Resolver (Register and Inject)

* [Containers and Dependency Injection in Ember by Matthew Beale](http://www.youtube.com/watch?v=6FlWyOoo6hQ)
* [How to call A from B in Ember](http://www.youtube.com/watch?v=VdQfNIm2-g0)
* [Containers and DI by @mixonic](https://www.youtube.com/watch?v=iCZUKFNXA0k)
* [Dependency Injection in Ember.js - First Steps](http://balinterdi.com/2014/05/01/dependency-injection-in-ember-dot-js.html)

The entire Ember framework go through an object called the *resolver*. The resolver is the part of Ember's dependency injection system that is responsible for determining naming conventions.

The container organises new building blocks.

```
var container = new Ember.Container();
container.register('workerPool:main', workerPool);
container.lookup('workerPool:main'); // Instance of workerPool
```

Don't ever use `App.__container__`

## Each

* [Hidden features of the `#each` helper](http://ember.guru/2014/hidden-features-of-the-each-aka-loopedy-loop-helper) 
* [Ember Arrays and 'observable' state](https://docs.google.com/presentation/d/1dVPWiB7OvimNUSJv8JF0u87LlzIq9_JLz9P5H5vTJrM/edit#slide=id.p)
* [Observers and object initialization](http://emberjs.com/guides/object-model/observers/#toc_observers-and-object-initialization)
* [CP is lazy and do not trigger observers](http://emberjs.com/guides/object-model/observers/#toc_unconsumed-computed-properties-do-not-trigger-observers)

"What the hell" API driven design.

## Ember Components, Web Components, Angular Directives

In some places where you may imagine `{{render` is the best solution, a component could be a better and more re-usable tool.

[See Instructure's component examples](https://github.com/instructure)

MUST include hyphen in the component name!

* [Ember widgets](http://addepar.github.io/#/ember-widgets/overview)
* [ic-ember](http://instructure.github.io/ic-ember/)
* [Angular vs Ember star rating component comparison](http://wintellect.com/blogs/nstieglitz/angular.js-vs-ember.js-star-rating-component-comparison)

```
App.LeafletMapComponent = Ember.Component.extend({
  attributeBindings: ['style'],
  
  width: '600px',
  height: '400px',
  
  style: function() {
    return [
      'width:' + this.get('width'),
      'height:' + this.get('height')\
    ].join(';');
  }.property('width', 'height'),
  
  didInsertElement: function() {
    var map = L.map(this.get('element'));
    this.set('map', map);
    
    map.setView([0, 0], 1);
    
    L.tileLayer('http://{s}.title.osm.org/{z}/{x}/{y}.png', { attribution: '&copy' }).addTo(map);
    
    map.on('move', this.mapDidMove, this);
  },
  
  mapDidMove: function() {
    Ember.run(this, function() {
      var map = this.get('map'),
          centre = map.getCenter(),
          zoom = map.getZoom();
      
      this.setProperties({
        latitude: center.lat,
        longitude: center.lng,
        zoom: zoom
      });
    });
  },
  
  willRemoveElement: function() {
    var map = this.get('map');
    if (map) map.remove();
  }
});
```

`Components` differ from `View` in the way they isolate behavior and data.

### Component Actions

There is no bubbling to the route. Actions are sent only to the component itself.

## Ember-cli Add-on

* [The add-on story](http://reefpoints.dockyard.com/2014/06/24/introducing_ember_cli_addons.html)

## Ember with D3

* [Reusable D3 charts with Ember.js components](http://heyjinjs.us/post/57158250642/reusable-d3-charts-with-ember-js-components)
* [Ember charts](http://addepar.github.io/)

## Search

* [Searching on Ember.js](http://blog.balancedpayments.com/ember-building-search/)

## Testing

```
Ember.testing = true;
App.deferReadiness();
App.Router.reopen({location: 'none'});
```

* Understand how containers work and injections work.
* Lookup objects as needed from containers. You'll probably want to include some test helpers for this.
* Wire together objects based upon their "needs".

## Videos

* [SparkCasts](http://www.sparkcasts.net/)
* [EmpireJS Videos](http://2014.empirejs.org/#/videos)
* [Ember Watch: Screencasts](http://emberwatch.com/screencasts.html)
* [Hashrocket's Introduction to Ember.js](http://www.youtube.com/watch?v=_lubCRPw17s)
* [Bosten Ember - April 2014](https://www.youtube.com/watch?v=ceFNLdswFxs&t=1h8m20s)
* [Testing your Ember applications](https://www.youtube.com/watch?v=GRT5YcXmm7E)
* [Building an Ember application](https://www.youtube.com/watch?v=1QHrlFlaXdI)
* [Building web applications with Ember.js and Rails](https://vimeo.com/78847391)
* [How to call A from B in Ember?](http://www.youtube.com/watch?v=VdQfNIm2-g0)
* [The Promise Land by Stefan Penner](http://www.youtube.com/watch?v=eHomHs3PrP8)
* [Ember Sherpa YouTube channel](http://www.youtube.com/user/EmberSherpa)
* [Ember NYC YouTube channel](https://www.youtube.com/user/EmberNYC)
* [Modern build workflows with Broccoli](https://vimeo.com/96431267)
* [Modern build workflows with Broccoli @Scotland.js](https://vimeo.com/96508134)
* [Building URL-driven web-apps with Ember.js](http://www.infoq.com/presentations/emberjs-url)

### Watched

* Ember.js NYC - [Apr 14, Mar 14, Feb 14, Jan 14]

## People

* [Robin Ward](http://eviltrout.com/)
* [simplereach](http://www.simplereach.com/blog/)
* [Eric Berry](http://coderberry.me/)
* [Dan Gebhardt](http://www.cerebris.com/blog/)
* [Adam Hawkins](http://hawkins.io/)
* [Balint Erdi](http://balinterdi.com/)
* [Igor Terzic](http://terzicigor.com/)
* [Matthew Beale](http://madhatted.com/)

## Example Apps

* [phaserapp](http://phaserapp.com/)
* [GroupTalent](https://grouptalent.com/)

## Libraries

* ember-cloaking
* [ember-responsive](https://freshbooks.github.io/ember-responsive/)

## Tips and Tricks

* [Progress bar](http://emberjs.jsbin.com/keduxelu/1/edit)
* [Ember Table](https://github.com/Addepar/ember-table)

## Analytics

What to track?

* Page views: `link-to`, `this.transitionTo()`, `this.replaceWith()`, URL
* Actions: `{{action}}`, `this.send()`, `this.triggerAction()`, `this.sendAction()`

[Extending Ember with Analytics](http://www.youtube.com/watch?
v=G0de3zNEkC4)

```
App.ApplicationRoute = Ember.Route.extend({
  actions: {
    didTransition: function() {
      Ember.run.once(this, function() {
        ga('send', 'page view', this.router.get('url'));
      });
    }
  }
});
```

## Debugging

* Be aware promises swallowing your rejection. Router promises may swallow.
* jQuery throws exception on certain places, so be careful when doing TDD.

```
// Error sub-state
{{message}}

{{stack}}
```

## Deprecations and Changes

* `linkTo` is `link-to` now, see [here](http://stackoverflow.com/questions/20291475/ember-handlebars-link-to-vs-linkto)