# Angular

* [Angular Gap](http://angulargap.github.io/)
* [Angular vs Ember](http://eviltrout.com/2013/06/15/ember-vs-angular.html)
* [John Lindquist](http://johnlindquist.com/)
* [AngularJS is too humble to say you're doing it wrong](http://thesmithfam.org/blog/2012/12/02/angularjs-is-too-humble-to-say-youre-doing-it-wrong/)
* [Introduction to Angular in 50 examples](https://github.com/curran/screencasts/tree/gh-pages/introToAngular)

List of books

* [Build your own Angular.js book](http://teropa.info/build-your-own-angular)
* [D3 on Angular](https://leanpub.com/d3angularjs)
* [ng-book](https://www.ng-book.com/)
* [Recipes with Angular](https://leanpub.com/recipes-with-angular-js)


Features of Angular:

* Plain JavaScript. Not extending and not inheriting. Make testing easy.
* Data binding
* Routing/PushState
* Testing
* Templates/Directives/Controllers
* Modular
* Dependency injection
* jqLite? jQuery built in?
* jQuery plugins require custom directives (cons)
* Large apps requiring self-imposed structure (cons)

## Leveling Up

Services and modules. Promises and directives.

## Module

```
angular.module('app', []);
```

Break module by feature. As Angular will add dynamic loading of module. So base on feature is better.

## Services

Services is where most of your code are.

* Factory
* Provider

## Asynchronous Events

Use `$rootScope` as a event bus to broadcast event. Avoid `$rootScope` for sharing data, use Services. Use custom crazy event systems at your own risk. Rely on binding!

```
$rootScope.$broadcast(EVENT_NAME, {data: 'Some data'});
$scope.$on(EVENT_NAME, fn);
```

Or use promises instead of `$rootScope`. Use interceptors for global-level events.


## ngRoute (Very limited)

1 route to 1 controller to 1 view. Or use AngularUI Router to have master-detail case.

http://joelhooks.com/blog/2013/07/22/the-basics-of-using-ui-router-with-angularjs/

## ngResource

* [Restangular](https://github.com/mgonto/restangular)

## Controllers

Don't use `ng-init` if you can. Better to use true controller.

```
PipelineApp.controller('KanbanController', function($scope, $http, $routeParams) {
});
```

Controller don't know about the view.

## Templates

How do we connect template to controller. We do it through `$scope`. `$scope` will be the observable and notifier.

## Scope

## Directives

Don't use jQuery, but rather just use directive.

```
// jQuery
$('truck');

// Angular
<truck></truck>
```

Don't manipulate DOM in controller, do that in directives.

We have 3 directives here:

```
<body ng-app>
  <ng-view></ng-view> <!-- like yield? -->
  <ul>
    <li ng-repeat="comment in comments">
      {{comment.body}}
    </li>
  </ul>
</body>
```

```
App.directive("upCaser", function() {
  return {
    link: function(scope, el, attrs) {
      $(el).find('p').each(function(i, p) {
        p = $(p);
        p.text(p.text().toUpperCase());
      });
      
      // Can watch also
      scope.$watch('pressed', function() {
        $(el).text('I am pressed!');
      });
    }
  };
});

<div up-caser>
  <p>some text</p>
</div>
```

Why write custom directives?
* Reusable component
* Manipulate the DOM

```
angular.module('ats.pipeline').directive('ats:stage', function() {
  return {
    template: '',
    replace: true,
    restrict: 'E',
    scope: {
      type: '@stageType',      // interpolated
      currentStage: '=active', // data bind
      onNextStage: '&'         // pass a function (callback)
    },
    link: function() {
      // Do DOM manipulation here
    }
  };
});
```

The `link` function is where DOM manipulation happens. Linker can know about controller, but controller better don't know about linker for testability.

* [ng-infinite-scroll](http://binarymuse.github.io/ngInfiniteScroll/)

Isolated scope is important in directive. Prevent you to modify your parent scope's data.
You probably do not need compile in directive.

## Filters

Like Unix's pipe. Output of one expression and pipe it into another.

```
 <li ng-repeat='c in comments | orderBy: "date"'>
   {{c.author | uppercase}}
 </li>
```

```
window.App = angular.module('app', []);

App.filter("salaryRange", function() {
  return function(input) {
    return input.min + " - " + input.max
  };
});
```

## ng-min

* html2js
* transpilers

## Libraries

* Ionic
* ng-upload
* Restangular
* angular-ui
* angular-ui-utils
* angular-bootstrap (learn the testing of directives?)


## Video Resources

* [AngularJS + REST Made Simple](https://www.youtube.com/watch?v=aGHzqwQU06g)
* [Introduction to Angular in 50 examples](http://www.youtube.com/watch?v=TRrL5j3MIvo)

## People

* [Lukas Ruebbelke](http://onehungrymind.com/)
* [Joel Hooks](http://joelhooks.com/)
* [John Lindquist](http://johnlindquist.com/)