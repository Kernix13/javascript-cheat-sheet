# Important Function Code Examples

Below is a list of specific function code snippets that are not simple function code snippets.

### General

typeof:
```js
let typeOfTest;
typeOfTest = function() {
  return "Hello";
}                 // function
```

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

returning boolean values from functions:
```js
function checkEqual(a, b) {
  return a === b;
}
```

set default parameters for your Fx’s:
```js
const greeting = (name = "Anonymous") => "Hello " + name;
```

Default parameters 2:
```js
function greet(first = "John", last = "Doe") {
  console.log(`Hello ${first} ${last}`)
}
greet("Jim", "Kernix");
```

use the rest parameter w\ Fx parms:
```js
function howMany(...args) {
  return "You have passed " + args.length + " arguments.";
}
console.log(howMany(0, 1, 2, -1, -2));
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

// another example:
const doSomething = {
  add: function() {
    console.log("This is a method.");
  }
}

doSomething.add();
```



## Callback functions

`addEventListener`:

```js
myvar.addEventListener("click", function(e) {
  console.log("Hello);

  e.preventDefault();
});
```

1. The parameter `e` is the event object. You want to prevent the default behavior associated with things like forms and links. 

To take a look at the event object:
```js
myVar.addEventListener("click", onClick);

function onClick(e) {
  let val;
  val = e;
  val = e.target;
  console.log(val); // look for target
}
```
The most important thing you will see is the `target` which represents the element that the event happened on. 

## Local storage

This would be the code inside of a function:
```js
// set local storage item (syntax first)
localStorage.setItem('key', 'value');
localStorage.setItem('name', 'Jim'); // check on Application tab

// get from storage:
const name = localStorage.getItem('name');

// remove from storage:
localStorage.removeItem('name');

// to clear everything from local storag:
localStorage.clear();
```

to have a form add an item to local storage amd store multiple items in an array as a string:
```js
document.querySelector('form').addEventListener('submit', function(e) {
  const task = document.getElementById('task').value;

  let tasks;

  // check local storage 
  if (localStorage.getItem('tasks') === null) {
    tasks = [];
  } else {
    tasks = JSON.parse(localStorage.getItem('tasks'));
  }

  tasks.push(task);

  localStorage.setItem('tasks', JSON.stringify(tasks);
  e.preventDefault();
});
```

Then to get and use the local storage items, still inside the event listener:
```js
const tasks = JSON.parse(localStorage.getItem('tasks'));
tasks.forEach(function(task){
  console.log(tasks);
});
```

## Event delegation

```js
// list items with delete link on the items but 
// fa fa-remove icon inside:
function deleteItem(e) {
  if(e.target.patentElement.className === "delete-item secondary-content") {
    console.log("delete item");
  }

  // or better...
  if(e.target.patentElement.classList.contains("delete-item")) {
    console.log("delete item");
  }
}
```

But the structure is ul > li > a > i and to delete the entire list item, which is the parent of the `<a>` tag, in the if statement:
```js
  if(e.target.patentElement.classList.contains("delete-item")) {
    // target is the icon
    e.target.parentElement.parentElement.remove();
  }
```