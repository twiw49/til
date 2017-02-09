# Function in Javascript

## 함수의 기본형태
```javascript
function a() {
	...
}
```



## 함수는 `변수(variable)의 값`이 될 수 있다!

```javascript
var a = function() {
	...
}
```



## 함수는 `배열(array)의 값`이 될 수 있다!

```javascript
var process = [
  function(input) {
    return input + 10;
  },
  function(input) {
    return input * input;
  },
  function(input) {
    return input / 2;
  }
];

var input = 1;

for (var i = 0; i < process.length; i++) {
  input = process[i](input);
}

alert(input);
```



## 함수는 `객체(object)의 값`이 될 수 있다!

```javascript
a = {
  b: function() {
    ...
  }
};
```



## 함수는 `다른 함수의 매개변수`가 될 수 있다!

```javascript
function cal(func, num) {
  return func(num);
};

function increase(num) {
  return num + 1;
};

function decrease(num) {
  return num - 1;
};

alert(cal(increase, 1));
alert(cal(decrease, 1));
```



## 함수는 `다른 함수의 리턴 값`이 될 수 있다!

```javascript
function cal(mode) {
  var funcs = {
    'plus': function(left, right) {
      return left + right;
    },
    'minus': function(left, right) {
      return left - right;
    }
  };
  return funcs[mode];
};

alert(cal('plus')(2, 1));
alert(cal('minus')(2, 1));
```



## 콜백(callback) 함수

* 값으로 사용될 수 있는 특성을 이용하면 함수는 다른 함수의 인자로 전달될 수 있다.
* 값으로 전달된 함수를 콜백함수라고 한다.
* 콜백함수는 특정 시점에 호출될 수 있기 때문에, 이를 이용하여 다른 함수의 동작을 바꿀 수 있다.

```javascript
var numbers = [20, 10, 9, 8, 7, 6, 5, 4, 3, 2, 1];

function sortNumber_desc(a, b) {
  return a - b;
};

alert(numbers.sort(sortNumber_desc)); // [1,2,3,4,5,6,7,8,9,10,20]

function sortNumber_asc(a, b) {
  return b - a;
};

alert(numbers.sort(sortNumber_asc)); // [20,10,9,8,7,6,5,4,3,2,1]
```



## AJAX 에서의 callback 함수

* get method의 매개변수로 함수가 이용됨 (callback 함수)

```javascript
$.get("data/data.html", function(data) {
  $("#content").html(data);
});
```