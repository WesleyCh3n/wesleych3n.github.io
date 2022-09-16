---
title: "JavaScript Learning Note"
date: 2021-10-12
categories:
  - note
tags:
  - javascript
toc: true
toc_label: "Outline"
toc_icon: "box-open"
header:
  teaser: ./assets/teasers/code-bg.png
---

## JavaScript Note
## 5 type

- Undefined
- Null
- String
- Boolen
- Number
Others r `Object`

## 3 way create `Object`

- Object literal
```javascript
var a = { name:'Wesley', score: 100 };
```
- new operator
```javascript
var a = new Date
```
- Constructor function
```javascript
function Student(name, score){
  this.name = name
  this.score = score
}
var a = new Student('Wesley', 100);
```

- Primitive variable assignment makes a "copy"
- Object variable assignment pass the "reference"
- Function can be anonymous // recommended
```javascript
var add = function(a, b) { return a + b; };
```
- Return a function
```javascript
var f = function(s) {
  return s?
    function(a,b) { return a+b; }:
    function(a,b) { return a-b; }
};
var f1 = f(true); f1(3,5);
var f2 = f(false); f2(3,5);
```

- When a function is used only once, we can
declare it anonymously and evoke it
immediately
```javascript
(function() {
... some statements
})()
```
- function hoist:
    - function declaration will elevate to top
        ```javascript
        sum(3,5); // This is OK!
        function sum(a, b) { return a + b; };
        ```
    - expression function declaration won't
        ```javascript
        sum(3,5); // Error
        var sum = function(a, b) { return a + b; }
        ```
## Variable Scope

- if no `var`, global variable
- if `var`, function scope.
- if same variable name use var multiple time, later ones will be assignment

- `let` use block scope, can't re-declare in one scope, no elevate
- `const` => `read-only` variable

## DOM Manipulations
- select DOM node/element. If DOM contain:
    ```html
    <div id="target"></div>
    <div class="a-class"></div>
    ```
    - unique DOM node
        - `document.getElementByID('target')`
    - array of DOM node
        - `document.getElementByClassName('a-class')`
    - CSS selector
        - `document.querySelector()`: With a querySelector statement, you can select an element based on a CSS selector. This means you can select elements by ID, class, or any other type of selector.
            - `document.querySelector(#myid);`: select by ID
            - `document.querySelector(.myclass);`: select by CSS class name
            - `document.querySelector("p.example");`: Get the first <p> element in the document with class="example"
        - `document.querySelectorAll()`: a list of the document's elements that match the specified group of selectors.
- Browse node
    - `parentNode.children`
    - `parentNode.firstElementChild`
    - `parentNode.lastElementChild`
    - `parentNode.childElementCount`
- Add/Remove node
    - `document.createElement(“div”);`
    - `newText = document.createTextNode(“Hello!”);`
    - `parentNode.appendChild(childNode);`
    - `parentNode.removeChild(childNode);`
    - `parentNode.removeChild(childNode);`
    - `parentNode.replaceChild(newNode, oldNode)`
- Modify node
    - `thisElement.style.color = “red”;` // Modify CSS style
    - `thisElement.className = “new-class1 new-class2”;` // Modify properties
    - `thisElement.classList.add(className);`
    - `thisElement.classList.remove(className)`
- **Bind Event**
    - `addEventListener()`. eventType:
        - click
        - focus: start to input
        - blur: leave the input
        - change: value change
        - keydown
        - keyup
        - mouseenter
        - mouseleave
    - e.g.
        ```html
        <!-- in .html -->
        <button id=“target">This is a button</button>
        ```
        ```javascript
        var targetElement = document.getElementById("target");
        targetElement.addEventListener( "click", function() {
           // Do something you wnat
            alert('what do you wnat to do?');
        });
        ```
    - `GlobalEventHandlers()` [Ref](https://developer.mozilla.org/en-US/docs/Web/API/GlobalEventHandlers)
        ```javascript
        let log = document.getElementById('log');
        log.onclick = inputChange;
        function inputChange(e) {
            //.. some something here
        }
        ```
    - As a tag attribute [Ref](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes)
        ```javascript
         <div class="myClass" onclick="clickHandler()">
        ```

## Closer Look at Constructor Function

```javascript
// #1 Function call to a ref to an anonymous function
var Car = function(make) { this.make=make; }
var car = Car("BMW");
console.log(car); // undefined
console.log(car.make); // ERROR
// #2 Constructor call to a ref to an anonymous function
var Car = function(make) { this.make=make; }
var car = new Car("BMW");
console.log(car); // { make: "BMW" }
console.log(car.make); // "BMW"
// #3 Ref to a ref to an anonymous function
var Car = function(make) { this.make=make; }
var car = Car;
console.log(car); // is a function
console.log(car.make); // undefined
// #4 Constructor call to a ref to an anonymous function
var Car = function(make) { this.make=make; }
var car = new Car; // missing parameter
console.log(car); // is an object
console.log(car.make); // undefine
// #5 Create an object from another object as a prototype
var Car = function(make) { this.make=make; }
var car = new Car("BMW");
console.log(car); // { make: "BMW" }
console.log(car.make); // "BMW"
var myCar = Object.create(car);
console.log(myCar); // { } <- no own property
console.log(myCar.make);// "BMW" <- inherited property
```
Each object has a *private property* which holds a link to another object called its **prototype**.

- `Object.keys(obj)` vs. `for (var i in obj)`
    - `Object.keys(obj)` returns an array with all the own (not in the prototype chain) enumerable properties’ names (“keys”) of the object obj.
    - `for (var i in obj)` traverses all enumerable properties of an object and its prototype chain.

## More on function

- Arrow function (=>): is like `lambda` in python
    - Syntax:
    ```javascript
    (arg1, arg2) => {
      // function body
    }
    ```
    - if no function body:
    ```javascript
    (arg1, arg2) => expression
    // but if expression is obj definition, () is required
    arg => ({property: value})
    ```
    - if arg only 1
    ```javascript
    arg1 => expression
    ```
    - call it on spot
    ```javascript
    (() => console.log("hello world!"))()
    ```
## More on Variable

"const" defines “read-only” variables.  However, the properties inside a const object are NOT constrain

Iterate through an Array
```javascript
var array = ['1', '2', '3']
for (var i=0; i< array.length; i++)
  console.log(array(i));
```
or

```javascript
array.forEach(i => console.log(i))
```

## Usefule concept
```javascript
var arr = [3, 5, 7];
arr.foo = 'hello';
for (var i in arr) {
  console.log(i); // "0", "1", "2", "foo"
}
for (var i of arr) {
  console.log(i); // 3, 5, 7; NO "hello"
}
```
- The `in` operator returns true if the specified property is in the specified object

- Template literal
    ```javascript
    `string text ${expression} string text`
    ```
- `instanceof`
