# Angular 2.0

Angular 2.0 favors class-based designs with annotations as metadata.

* [AtScript](https://docs.google.com/document/d/11YUzC-1d0V1-Q3V0fQ7KSit97HnZoKVygDxpWzEYW0U/mobilebasic?viewopt=127)
* [All about Angular 2.0](http://eisenbergeffect.bluespire.com/all-about-angular-2-0/)
* [Design doc for Angular 2.0](https://drive.google.com/drive/#folders/0B7Ovm8bUYiUDR29iSkEyMk5pVUk)
* [Preparing for the future of Angular.js](https://www.airpair.com/angularjs/posts/preparing-for-the-future-of-angularjs)

# Angular 1.0

Think of Angular as a Model View View Model.

* Model - The services (business logics and domain models)
* View - HTML template
* View Model - $scope + controller
* [Angular Gap](http://angulargap.github.io/)
* [Angular vs Ember](http://eviltrout.com/2013/06/15/ember-vs-angular.html)
* [John Lindquist](http://johnlindquist.com/)
* [AngularJS is too humble to say you're doing it wrong](http://thesmithfam.org/blog/2012/12/02/angularjs-is-too-humble-to-say-youre-doing-it-wrong/)
* [Introduction to Angular in 50 examples](https://github.com/curran/screencasts/tree/gh-pages/introToAngular)
* [AngularJS and D3](http://vicapow.github.io/angular-d3-talk/slides/#/1)
* [Make your own AngularJS](http://teropa.info/blog/2013/11/03/make-your-own-angular-part-1-scopes-and-digest.html)
* [Angular for beginner](https://news.layervault.com/stories/28546-angularjs--how-to-start-)

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

## Module Array Syntax


## Module.run

Executed when all modules have been loaded.

```
angular.module('MyApp', [])
  .constant('VERSION', '1.0')
  .run(['VERSION', '$rootScope', function(VERSION, $rootScope) {
  }]);
```

## Models

* [Universal Access Principle, Identity Map, Memoization](https://www.youtube.com/watch?v=JfykD-0tpjI)

Decorating function.

```
angular.module('myPlane.models')
  .factory('Proposal', function(Model) {
    return Model.extend({
      memoize: ['revenue', 'cost'],
      
      get profit() {
        return this.revenue.minus(this.cost);
      },
      
      get revenue() {
        return this.price.convertTo(this.internalCurrency);
      }
    });
  });
```


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
* Services carry out common tasks specific to the web application
* Services are consumed via Dependency Injection
* Services are application singletons. One service per application.
* Services are instantiated lazily

## Asynchronous Events

Use `$rootScope` as a event bus to broadcast event. Avoid `$rootScope` for sharing data, use Services. Use custom crazy event systems at your own risk. Rely on binding!

```
$rootScope.$broadcast(EVENT_NAME, {data: 'Some data'});
$scope.$on(EVENT_NAME, fn);
```

Or use promises instead of `$rootScope`. Use interceptors for global-level events.


## ngRoute (Very limited using ng-view)

1 route to 1 controller to 1 view. Or use AngularUI Router to have master-detail case.

http://joelhooks.com/blog/2013/07/22/the-basics-of-using-ui-router-with-angularjs/

```
angular.module('MyApp', [])
  .constant('VERSION', '1.0')
  
  .config(['$routeProvider', function($routeProvider) {
    $routeProvider.when('/', {
      controller: 'HomeController',
      templateUrl: './home.html'
    });
  }]);
```

## ngResource

* [Restangular](https://github.com/mgonto/restangular)

## Controllers

Don't use `ng-init` if you can. Better to use true controller.

```
PipelineApp.controller('KanbanController', ['$scope', '$http', '$routeParams', function($scope, $http, $routeParams) {
}]);
```
Controller don't know about the view.

Controllers should not talk to each other. But in rare cases where you need to, what can you do?

Use a service to facilitate communication. `$scope` has events built in after the compilation cycle complete.

- `$broadcast` - sends events downward from parent to children
- `$emit` sends events upwards
- `$on` listens for events

One of the few acceptable time where you can use `$rootScope` as an event bus.

## Templates

How do we connect template to controller. We do it through `$scope`. `$scope` will be the observable and notifier.

## Scope

`$scope` is the glue between the Controller and the View.
`$scope` also provide context.

`$rootScope` is the topmost Scope object with all other children `$scope`

## View

View = $compile(HTML, $scope)

## Directives (Extend HTML to do new thing)

When to use directives?

Domain Specific Languages.

* If you want a reusable HTML component like `<my-widget>`
* If you want reusable HTML behavior like `ng-click`
* If you want to wrap a jQuery plugin `<div ui-date>`
* Almost any time you need to interface with the DOM. Don't interact with the DOM in controller, service or anywhere except in directive.

```
angular.module('CpDirectives', []); // It's own directive module
angular.module('CpApp', ['CpDirectives']); // Load the directives in your app

// Code the directive
angular.module('CpDirectives')
  .directive();
```

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

### Link

The `link` function is where DOM manipulation happens.

* The `scope` is the same `$scope` in the controller function
* `element` is a jQuery instance of the DOM element where the directive is declared on
* `attrs` is a list of attributes (normalized array) declared on the element

```
.directive('myCircle', function() {
  return {
    templateUrl: './circle.html',
    link: function(scope, element) {
      element.on('click', function() {});
    }
  };
});
```


### Controller

The controller is constructed during the pre-linking phase. It receives `$scope` which is the current scope for the element.

The setup of the event is still best done at the `link` function, but any other logics can be inside this `controller` function.

```
.directive('myCircle', function() {
  return {
    templateUrl: './circle.html',
    
    controller: ['$scope', '$rootScope', function($scope, $rootScope) {
      $scope.afterClick = function() {
        $rootScope.$broadcast('clicked');
      };
    }],
    
    link: function(scope, element) {
      element.on('click', function() {
        scope.$apply(function() {
          scope.afterClick(); // ask the controller for help
        });
      });
    }
  };
});
```

### More directive examples

```
// Directive call one time, and link call multiple times depending on how many inputs you have.

<input type="text" form-select-all-on-focus />

angular.module('CpDirectives')
  .directive('formSelectAllOnFocus', function() {
    return {
      restrict: 'A',
      link: function(scope, element) {
        element.mouseup(function(event) {
          event.preventDefault();
        });
        
        element.focus(function() {
          element.select();
        });
      }
    };
  });
```

### Layout Directives

* ngIf
* ngShow / ngHide
* ngRepeat
* ngSwitch
* ngInclude

### Interaction Directives

Directives that call methods and provide data to controller.

* ngModel - attach properties to `$scope`
* ngBlur / ngFocus
* ngClick
* ngSubmit

### Styling Directives

* ngClass

```
ng-class="{'label-success':focus}"
```

## Filters

Like Unix's pipe. Output of one expression and pipe it into another.

```
 <li ng-repeat='c in comments | orderBy: "-date"'>
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

```
{{'1388123412323' | date:'MM/dd/yyyy @ H:mma'}}
{{'gem' | uppercase}}
{{'My Description' | limitTo:8}}
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

## Authentication / Bootstrapping

```
<html ng-app="myApp">
  <script>
  // The active profile is populated using server side rendering
  var myActiveProfile = { "id": 123, "name": "Ido", "language": "en" };
  </script>
</html>

// Later
angular.module('myApp', []).config(['$provide', function($provide) {
  var profile = angular.copy(window.myActiveProfile);
  
  profile.canEditAccount = function() {
    return profile.isAccountManager || profile.permissions.editAccount;
  };
  
  // Provide the active profile as an injectible constant.
  $provide.constant('activeProfile', profile);
}]);
```

## Testing

Testing filter

```
describe('filter', function() {
  beforeEach(module('phonecatFilter'));
  
  describe('checkmark', function() {
    
    it('should convert boolean value to unicode checkmark or cross', inject(function(checkmarkFilter) {
      expect(checkmarkFilter(true)).toBe('\u2713');
      expect(checkmarkFilter(false)).toBe('\u2718');
    }));
  });
});
```

## Video Resources

* [AngularJS + REST Made Simple](https://www.youtube.com/watch?v=aGHzqwQU06g)
* [Introduction to Angular in 50 examples](http://www.youtube.com/watch?v=TRrL5j3MIvo)

### Paid

* [egghead.io - Paid Angular.js, Node.js, D3.js resources](https://egghead.io/)


## People

* [Lukas Ruebbelke](http://onehungrymind.com/)
* [Joel Hooks](http://joelhooks.com/)
* [John Lindquist](http://johnlindquist.com/)