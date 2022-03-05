# Important Function Code Examples

Below is a list of specific function code snippets that are not simple function code snippets.

### General


Declaration vs. expression
```js
function myFunction() {
  code here
}

// expression:
let myFunction = function() {
  code here
}
```

With rest parameter and spread operator in argument list:
```js
let someVar = [some other array]
let mainArray = [1, 2, ...someVar, 10, 11]

function someFx(...arr) {
  code here
}
someFx(mainArray);
```

### IIFE

```js
// IIFE:
(function () {
  console.log("I rule because I am an IIFE!");
})();

// IIFE with parameter:
(function (name) {
  console.log(`Hello, my name is ${name}`);
})("Jim");

// Arrow IIFE:
(() => {
  console.log("I am an arrow function IIFE!");
})();

// Async IIFE:
(async () => {
  console.log("I am an async IIFE!")
})();
```

## Async await


## Arrow functions

No parameters:

Single parameter:

Multiple parameters:

## Methods

```js
const toDo = {
  add: function() {
    console.log("This is a method.");
  }
}
toDo.add();

// define a method outside of the object:
toDo.delete =  function() {
  console.log("Delete something");
}
toDo.delete();
```