# AngularJS Directives

* AngularJS lets you extend HTML with new attributes call **Directives**.
* AngularJS has a set of built-in directives which offers functionality to your applications.
* AngularJS also lets you define your own directives.
* AngularJS directives are extended HTML attributes with the prefix `ng-`.



## ng-app

* ng-app directive initializes an AngularJS application.
* ng-app directive defines the root element of an AngularJS application.



## ng-init

* ng-init directive is used to 
  * initialize a javascript variable
  * evaluate an expression



## ng-model

* The `ng-model` directive binds the value of HTML controls (input, select, textarea) to application data.
* Two-way data binding 
  * The binding goes both ways. 
  * If the user changes the value inside the input field, the AngularJS property will also change its value.

```html
<div ng-app="" ng-init="quantity=1;price=5">
Quantity: <input type="number" ng-model="quantity">
Costs:    <input type="number" ng-model="price">
Total in dollar: {{ quantity * price }}
</div>
```

```html
<div ng-app="myApp" ng-controller="myCtrl">
  Name: <input ng-model="name">
  <h1>You entered: {{name}}</h1>
</div>

<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
    $scope.name = "John Doe";
});
</script>
```



## ng-repeat

* `ng-repeat` directive is a looping construct
  * loops over items in a collection
  * instantiates a template for each item

```html
<div ng-app="" ng-init="names=['Jani','Hege','Kai']">
  <ul>
    <li ng-repeat="x in names">
      {{ x }}
    </li>
  </ul>
</div>
```

```html
<div ng-app="" ng-init="names=[
{name:'Jani',country:'Norway'},
{name:'Hege',country:'Sweden'},
{name:'Kai',country:'Denmark'}]">

<ul>
  <li ng-repeat="x in names">
    {{ x.name + ', ' + x.country }}
  </li>
</ul>

</div>
```



## ng-show

* `ng-show` directive shows the specified HTML element if the expression evaluates to true, otherwise the HTML element is hidden.
* `<element ng-show="expression">...</element>`
  * An expression will show the element only if the expression returns true.

```html
<body ng-app="">

Show HTML: <input type="checkbox" ng-model="myVar">
  
<div ng-show="myVar">
  <h1>Welcome</h1>
  <p>Welcome to my home.</p>
</div>

</body>
```

