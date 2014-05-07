# Ember

Ember is Cocoa and Angular is JSF?

* [Robin Ward's AngularJS vs Ember](http://eviltrout.com/2013/06/15/ember-vs-angular.html)
* [Instructure](http://instructure.github.io/blog/)
* [Ember vs Angular - Templates](http://pivotallabs.com/ember-vs-angular-templates/)
* [ember-appkit-rails using ES6 module but testing is QUnit](https://github.com/dockyard/ember-appkit-rails)
* [A series to compare Angular with Ember](http://www.benlesh.com/2014/04/embular-part-2-whats-great-about-angular.html)

```
Ember.run.once();

setProperties({});
```

## Run Loop (backburner.js)

* [How does run loop work](http://stackoverflow.com/questions/13597869/what-is-ember-runloop-and-how-does-it-work)
* [Visualization of the run loop](https://machty.s3.amazonaws.com/ember-run-loop-visual/index.html)
* [backburner is a rewrite of the run loop](https://github.com/ebryn/backburner.js)

Not a loop like programmers might think. It is an "aggregate changes over time" mechanism. Used to batch, and order (or reorder) work in a way that is most efficient by scheduling work on specific queues. These queues have a priority, and are processed to completion in priority order.

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
* `Ember.run.throttle`

Usually user events that will trigger run loop.

## Naming Convention

|    Name    |                     Object                    |
| ---------- | --------------------------------------------- |
| Router     | `this.resource('tables')` and App.TablesRoute |
| Controller | `App.TablesController`                        |
| Model      | `App.Table`                                   |
| View       | `App.TablesView`                              |
| Template   | `tables`                                      |

## URLs and Routing

The shareable part.

```
// Detect the '/' path and render the todos template
this.resource('todos', { path: '/' });
```

Action routes (I like verb):

- /login/one-time-password/authenticate
- /recover-username

## Route

You'll spend most time on the route than any other Ember's parts. In Rails, you use Controller to load data, but in Ember, you do it at Route. Route loads data and assigns it to a controller using `setupController()`. Controller in Ember rarely has the job to load data!

When `/tables` is visited, Ember calls the `App.TablesRoute` object, which finds the list of tables and assigns it to the `App.TablesController`.

Route hooks:

* `beforeModel`
* `model`
* `afterModel`
* `setupController`
* `deactivate`

Can we have more than one model in a route?

## Controller

3 types:

* `Controller`
* `ObjectController`
* `ArrayController`

Extend `Ember.Evented` for your controller if you want event bus.

How controller talk to view? `Ember.View.views.XX`

## Query Params

`/?query=params`

```
App.ArticlesController = Ember.ArrayController.extend({
  queryParams: ['page'],
  page: 1
});
```

What's the job of a controller anyway?

* Manage application state
* Wrap the model with additional information to present to the template (also application state)

## Screens and Flows

Flows are just as important to good interfaces as individual screens are.

Directed graph, nodes, edges, etc

`replaceWith`
`transitionTo`

* [ember-flows](https://github.com/nathanhammond/ember-flows)
* [ember-flows slide?](https://github.com/alexdiliberto/emberconf-2014-demo)

See http://www.youtube.com/watch?v=iFBOYMxDl40

## Nested Routes means Nested UI

```
this.resource('project', { path: '/projects/:projectId' }, function() {
  this.route('story', { path: '/stories/:storyId' });
});
```

## View

* [Difference between views and components](http://stackoverflow.com/questions/18593424/views-vs-components-in-ember-js)

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

## Ember Run Loop

## Lifecycle Hooks

## Register and Inject (Resolver)

## Animations and Transitions

* [ember-animation-demo](https://github.com/ef4/ember-animation-demo)

## Data

The places your data will go!

* Migration (From old MySQL CP to new Postgres CP)
* Search (ElasticSearch)
* Caching (Redis)
* Mobile (API endpoints)
* [Transition for ember-data?](https://github.com/emberjs/data/blob/master/TRANSITION.md)
* [wycats's app.js example](https://gist.github.com/wycats/8129945)

## Authentication and Session

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

## Container and Resolver


## Ember Components, Web Components, Angular Directives

* [Ember widgets](http://addepar.github.io/#/ember-widgets/overview)
* [ic-ember](http://instructure.github.io/ic-ember/)
* [Angular vs Ember star rating component comparison](http://wintellect.com/blogs/nstieglitz/angular.js-vs-ember.js-star-rating-component-comparison)

## Ember with D3

* [Reusable D3 charts with Ember.js components](http://heyjinjs.us/post/57158250642/reusable-d3-charts-with-ember-js-components)
* [Ember charts](http://addepar.github.io/)

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

* [Ember Watch: Screencasts](http://emberwatch.com/screencasts.html)
* [Hashrocket's Introduction to Ember.js](http://www.youtube.com/watch?v=_lubCRPw17s)

## People

* [Robin Ward](http://eviltrout.com/)
* [simplereach](http://www.simplereach.com/blog/)
* [Eric Berry](http://coderberry.me/)
* [Dan Gebhardt](http://www.cerebris.com/blog/)

## Example Apps

* [phaserapp](http://phaserapp.com/)


## Libraries

* ember-cloaking