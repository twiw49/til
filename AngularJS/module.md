# AngularJS Modules

* An AngularJS module defines an application.
* The module is a container for the different parts of an application.
* The module is a container for the application controllers.
* Controllers always belong to a module.



## angular.module

* The "myApp" parameter refers to an HTML element in which the application will run.

```html
<div ng-app="myApp">...</div>

<script>
  var app = angular.module("myApp", []); 
</script>
```



## ng-controller

* Add a controller to the application.
* Refer to the controller with the `ng-controller` directive

```html
<div ng-app="myApp" ng-controller="myCtrl">
  {{ myCtrl.firstName + " " + myCtrl.lastName }}
</div>

<script>

var app = angular.module("myApp", []);

app.controller("myCtrl", function() {
  this.firstName = "John";
  this.lastName = "Doe";
});

</script>
```

