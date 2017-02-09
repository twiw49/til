# AngularJS Form

* Forms in AngularJS provides data-binding and validation of input controls.
* Input controls
  * input elements
  * select elements
  * button elements
  * textarea elements
* Data-Binding
  * Input controls provides data-binding by using the `ng-model` directive.

```HTML
<div ng-app="">
  <form>
    First Name: <input type="text" ng-model="firstname">
  </form>
  <h1>You entered: {{firstname}}</h1>
</div>
```

```HTML
<div ng-app="myApp" ng-controller="formCtrl">
  <form>
    First Name: <input type="text" ng-model="firstname">
  </form>
</div>

<script>
var app = angular.module('myApp', []);
app.controller('formCtrl', function($scope) {
    $scope.firstname = "";
});
</script>
```



## Checkbox

* A checkbox has the value `true` or `false`.
* `ng-model` : checkbox의 값 : `true` or `false`

```html
<div ng-app="">
  <form>
    Check to show a header:
    <input type="checkbox" ng-model="myVar">
  </form>
  <h1 ng-show="myVar">My Header</h1>
</div>
```



## Radiobutton

* Radiobuttons with the same `ng-model` can have different values, but only the selected one will be used.

```html
<body ng-app="">

<form>
  Pick a topic:
  <input type="radio" ng-model="myVar" value="dogs">Dogs
  <input type="radio" ng-model="myVar" value="tuts">Tutorials
  <input type="radio" ng-model="myVar" value="cars">Cars
</form>
  
<!-- The value of myVar will be either dogs, tuts or cars. -->

<div ng-switch="myVar">
  <div ng-switch-when="dogs">
     <h1>Dogs</h1>
     <p>Welcome to a world of dogs.</p>
  </div>
  <div ng-switch-when="tuts">
     <h1>Tutorials</h1>
     <p>Learn from examples.</p>
  </div>
  <div ng-switch-when="cars">
     <h1>Cars</h1>
     <p>Read about cars.</p>
  </div>
</div>
</body>
```



## Selectbox

* The property defined in the `ng-model` attribute will have the value of the selected option in the selecbox.

```html
<body ng-app="">

<form>
  Select a topic:
  <select ng-model="myVar">
    <option value="">
    <option value="dogs">Dogs
    <option value="tuts">Tutorials
    <option value="cars">Cars
  </select>
</form>

<div ng-switch="myVar">
  <div ng-switch-when="dogs">
     <h1>Dogs</h1>
     <p>Welcome to a world of dogs.</p>
  </div>
  <div ng-switch-when="tuts">
     <h1>Tutorials</h1>
     <p>Learn from examples.</p>
  </div>
  <div ng-switch-when="cars">
     <h1>Cars</h1>
     <p>Read about cars.</p>
  </div>
</div>
</body>
```



## Form validation

### required

```html
<body ng-app="">

<p>Try writing in the input field:</p>

<form name="myForm">
  <input name="myInput" ng-model="myInput" required>
</form>

<p>The input's valid state is:</p>
<h1>{{myForm.myInput.$valid}}</h1> <!-- true or false -->

</body>
```



### email

```html
<body ng-app="">

<p>Try writing an E-mail address in the input field:</p>

<form name="myForm">
  <input type="email" name="myInput" ng-model="myInput">
</form>

<p>The input's valid state is:</p>
<h1>{{myForm.myInput.$valid}}</h1>
</body>
```



### Input State

Input fields have the following states:

- `$untouched` : The field has not been touched yet
- `$touched` : The field has been touched
- `$pristine` : The field has not been modified yet
- `$dirty` : The field has been modified
- `$invalid` : The field content is not valid
- `$valid` : The field content is valid

They are all properties of the input field, and are either `true` or `false`.

```html
<body ng-app="">

<p>Try leaving the first input field blank:</p>

<form name="myForm">
  <p>Name:
    <input name="myName" ng-model="myName" required>
    <span ng-show="myForm.myName.$touched && myForm.myName.$invalid">
      The name is required.
    </span>
  </p>
  
  <p>Address:
    <input name="myAddress" ng-model="myAddress" required>
  </p>
</form>
</body>
```



### CSS Classes

The following classes are added to, or removed from, input fields:

- `ng-untouched` : The field has not been touched yet
- `ng-touched` : The field has been touched
- `ng-pristine` : The field has not been  modified yet
- `ng-dirty` : The field has been modified
- `ng-valid` : The field content is valid
- `ng-invalid` : The field content is not valid

```html
<style>
input.ng-invalid {
    background-color:pink;
}
input.ng-valid {
    background-color:lightgreen;
}
</style>

<body ng-app="">

<p>Try writing in the input field:</p>

<form name="myForm">
  <input name="myName" ng-model="myName" required>
</form>

</body>
```



The following classes are added to, or removed from, forms:

- `ng-pristine` : No fields has not been modified yet
- `ng-dirty` : One or more fields has been modified
- `ng-valid` : The form content is valid
- `ng-invalid` : The form content is not valid

The classes are removed if the value they represent is `false`.

```html
<style>
form.ng-valid {
    background-color:lightblue;
}
form.ng-invalid {
    background-color:pink;
}
</style>
<body ng-app="">

<p>Try writing in the input field:</p>
  
<form name="myForm">
  <input name="myName" ng-model="myName" required>
  <input name="myAge" ng-model="myAge" required>
</form>

</body>
```

