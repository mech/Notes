# Angular

* [Angular Gap](http://angulargap.github.io/)
* [Angular vs Ember](http://eviltrout.com/2013/06/15/ember-vs-angular.html)
* [Build your own Angular.js book](http://teropa.info/build-your-own-angular)

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

Use `$rootScope` as a event bus to broadcast event.

```
$rootScope.$broadcast(EVENT_NAME, {data: 'Some data'});
$scope.$on(EVENT_NAME, fn);
```

Or use promises instead of `$rootScope`. Use interceptors for global-level events.

## ngRoute

## ngResource

## Controllers

Don't use `ng-init` if you can. Better to use true controller.

```
PipelineApp.controller('KanbanController', function($scope, $http, $routeParams) {
});
```

## Templates

How do we connect template to controller. We do it through `$scope`. `$scope` will be the observable and notifier.

## Scope

## Directives

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
    }
  };
});
```


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