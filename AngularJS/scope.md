# AngularJS Scope

* The scope is the binding part between the HTML (view) and the Javascript (controller).
* The scope is an object with the available properties and methods.
* The scope is available for both the view and the controller.
* When you make a controller in AngularJS, you pass the `$scope` object as an argument.
* When adding properties to the `$scope` object in the controller, the view (HTML) gets access to these properties.
* In the view, you do not use the prefix `$scope`, you just refer to a propertyname, like ``{{carname}}``.

```html
<div ng-app="myApp" ng-controller="myCtrl">
  <h1>{{carname}}</h1>
</div>

<script>
var app = angular.module('myApp', []);

app.controller('myCtrl', function($scope) {
    $scope.carname = "Volvo";
});
</script>
```

* without `$scope`

```html
<div ng-app="myApp" ng-controller="myCtrl as myCtrl">
  <h1>{{myCtrl.carname}}</h1>
</div>

<script>
var app = angular.module("myApp", []);

app.controller("myCtrl", function() {
  this.carName = "Volvo";
});
</script>
```



* If you make changes in the view, the model and the controller will be updated.

```html
<div ng-app="myApp" ng-controller="myCtrl">
  <input ng-model="name">
  <h1>My name is {{name}}</h1>
</div>

<script>
var app = angular.module('myApp', []);

app.controller('myCtrl', function($scope) {
    $scope.name = "John Doe";
});
</script>
```

* without `$scope`

```html
<div ng-app="myApp" ng-controller="myCtrl as myCtrl">
  <input ng-model="myCtrl.name">
  <h1>My name is {{myCtrl.name}}</h1>
</div>

<script>
var app = angular.module('myApp', []);

app.controller('myCtrl', function() {
    this.name = "John Doe";
});
</script>
```



* When dealing with the `ng-repeat` directive, each repetition has access to the current repetition object.

```html
<div ng-app="myApp" ng-controller="myCtrl">

<ul>
    <li ng-repeat="x in names">{{x}}</li>
</ul>

</div>

<script>
var app = angular.module('myApp', []);

app.controller('myCtrl', function($scope) {
    $scope.names = ["Emil", "Tobias", "Linus"];
});
</script>
```

* without `$scope`

```html
<div ng-app="myApp" ng-controller="myCtrl as myCtrl">

<ul>
    <li ng-repeat="x in myCtrl.names">{{x}}</li>
</ul>

</div>

<script>
var app = angular.module('myApp', []);

app.controller('myCtrl', function() {
    this.names = ["Emil", "Tobias", "Linus"];
});
</script>
```



## $rootScope

* All applications have a `$rootScope` which is the scope created on the HTML element that contains `ng-app` directive.
* The rootScope is available in the entire application.
* If a variable has the same name in both the current scope and in the rootScope, the application use the one in the current scope.

```html
<body ng-app="myApp">

<p>The rootScope's favorite color:</p>
<h1>{{color}}</h1> <!-- blue -->

<div ng-controller="myCtrl">
    <p>The scope of the controller's favorite color:</p>
    <h1>{{color}}</h1> <!-- red -->
</div>

<p>The rootScope's favorite color is still:</p>
<h1>{{color}}</h1> <!-- blue -->

<script>
var app = angular.module('myApp', []);
app.run(function($rootScope) {
    $rootScope.color = 'blue';
});
app.controller('myCtrl', function($scope) {
    $scope.color = "red";
});
</script>
</body>
```