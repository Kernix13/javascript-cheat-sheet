# Important Function Code Examples

Below is a list of specific function code snippets that are not simple function code snippets.

- [MDN functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions)
- [MDN IIFE](https://developer.mozilla.org/en-US/docs/Glossary/IIFE)
- [MDN Async await](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)
- [MDN Arrow functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)
- [MDN methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Method_definitions)
- [MDN callback functions](https://developer.mozilla.org/en-US/docs/Glossary/Callback_function)

<div id="back-to-top"></div>

## Table of contents

1. [General](#general)
1. [IIFE](#iife)
1. [Async await](#async-await)
1. [Arrow functions](#arrow-functions)
1. [Methods](#methods)
1. [ES6 export import](#es6-export-import)
1. [Callback functions](#callback-functions)
1. [Local storage](#local-storage)
1. [Event delegation](#event-delegation)
1. [Miscellaneous](#miscellaneous)
   1. [ES6 Promises](#es6-promises)
   1. [Dynamic functions](#dynamic-functions)

## General

typeof:
```js
let typeOfTest;
typeOfTest = function() {
  return "Hello";
}                 
console.log(typeof typeOfTest) // function
```

<br />

Syntax:
```js
// no parameter
function lowerCase() {
  if() {
    // do something
    // return something
  }
}

// with parameter
function square(number) {
  return number * number;
}

function lowerCase(str) {
  return str.toLowerCase();
}
```

<br />

Declaration vs. expression
```js
// function declaration:
function myFunction() {
  code here
}

// function expression:
let myFunction = function() {
  code here
}
```

<br />

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

<br />

set default parameters for your Fx’s:
```js
const greeting = (name = "Anonymous") => "Hello " + name;
```

<br />

Default parameters 2:
```js
function greet(first = "John", last = "Doe") {
  console.log(`Hello ${first} ${last}`)
}
greet("Jim", "Kernix");
```

<br />

use the rest parameter w\ Fx parms:
```js
function howMany(...args) {
  return "You have passed " + args.length + " arguments.";
}
console.log(howMany(0, 1, 2, -1, -2));
```

<br />

Recursive example (computes factorials):
```js
function factorial(n) {
  if ((n === 0) || (n === 1))
    return 1;
  else
    return (n * factorial(n - 1));
}

var a, b, c, d, e;
a = factorial(1); // a gets the value 1
b = factorial(2); // b gets the value 2
c = factorial(3); // c gets the value 6
d = factorial(4); // d gets the value 24
e = factorial(5); // e gets the value 120
```

<br />

Nested functions:
```js
function addSquares(a, b) {
  function square(x) {
    return x * x;
  }
  return square(a) + square(b);
}
a = addSquares(2, 3); // returns 13
b = addSquares(3, 4); // returns 25
c = addSquares(4, 5); // returns 41

// example 2
function outside(x) {
  function inside(y) {
    return x + y;
  }
  return inside;
}
fn_inside = outside(3); // Think of it like: give me a function that adds 3 to whatever you give it
result = fn_inside(5); // returns 8
result1 = outside(3)(5); // returns 8
```

Other concepts from [MDN Functions doc](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions): Scope and the function stack, Recursion, Preservation of variables, Closures, Using the arguments object, Default parameters, Rest parameters, No separate this, Predefined functions

**Predefined functions**: `eval()`, `uneval()`, `isFinite()`, `isNaN()`, `parseFloat()`, `parseInt()`, `decodeURI()`, `decodeURIComponent()`, `encodeURI()`, `encodeURIComponent()`, `escape()`, and `unescape()`.

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

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

<br />

Execute an async function:
```js
const getFileStream = async (url) => { /* implementation */ };

(async () => {
  const stream = await getFileStream('https://domain.name/path/file.ext');
  for await (const chunk of stream) {
    console.log({ chunk });
  }
})();
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Async await

Syntax:
```js
async function name(parameters) {
   statements
}
```

<br />

Example 1:
```js
function resolveAfter2Seconds() {
  return new Promise(resolve => {
    setTimeout(() => {
      resolve('resolved');
    }, 2000);
  });
}

async function asyncCall() {
  console.log('calling');
  const result = await resolveAfter2Seconds();
  console.log(result);
  // expected output: "resolved"
}

asyncCall();

// example 2:
async function foo() {
   const result1 = await new Promise((resolve) => setTimeout(() => resolve('1')))
   const result2 = await new Promise((resolve) => setTimeout(() => resolve('2')))
}
foo()

// example 3:
async function foo() {
   const p1 = new Promise((resolve) => setTimeout(() => resolve('1'), 1000))
   const p2 = new Promise((_,reject) => setTimeout(() => reject('2'), 500))
   const results = [await p1, await p2] // Do not do this! Use Promise.all or Promise.allSettled instead.
}
foo().catch(() => {}) // Attempt to swallow all errors...
```

<br />

Async functions and execution order:
```js
function resolveAfter2Seconds() {
  console.log("starting slow promise")
  return new Promise(resolve => {
    setTimeout(function() {
      resolve("slow")
      console.log("slow promise is done")
    }, 2000)
  })
}

function resolveAfter1Second() {
  console.log("starting fast promise")
  return new Promise(resolve => {
    setTimeout(function() {
      resolve("fast")
      console.log("fast promise is done")
    }, 1000)
  })
}

async function sequentialStart() {
  console.log('==SEQUENTIAL START==')

  // 1. Execution gets here almost instantly
  const slow = await resolveAfter2Seconds()
  console.log(slow) // 2. this runs 2 seconds after 1.

  const fast = await resolveAfter1Second()
  console.log(fast) // 3. this runs 3 seconds after 1.
}

async function concurrentStart() {
  console.log('==CONCURRENT START with await==');
  const slow = resolveAfter2Seconds() // starts timer immediately
  const fast = resolveAfter1Second() // starts timer immediately

  // 1. Execution gets here almost instantly
  console.log(await slow) // 2. this runs 2 seconds after 1.
  console.log(await fast) // 3. this runs 2 seconds after 1., immediately after 2., since fast is already resolved
}

function concurrentPromise() {
  console.log('==CONCURRENT START with Promise.all==')
  return Promise.all([resolveAfter2Seconds(), resolveAfter1Second()]).then((messages) => {
    console.log(messages[0]) // slow
    console.log(messages[1]) // fast
  })
}

async function parallel() {
  console.log('==PARALLEL with await Promise.all==')

  // Start 2 "jobs" in parallel and wait for both of them to complete
  await Promise.all([
      (async()=>console.log(await resolveAfter2Seconds()))(),
      (async()=>console.log(await resolveAfter1Second()))()
  ])
}

sequentialStart() // after 2 seconds, logs "slow", then after 1 more second, "fast"

// wait above to finish
setTimeout(concurrentStart, 4000) // after 2 seconds, logs "slow" and then "fast"

// wait again
setTimeout(concurrentPromise, 7000) // same as concurrentStart

// wait again
setTimeout(parallel, 10000) // truly parallel: after 1 second, logs "fast", then after 1 more second, "slow"
```

<br />

Rewriting a Promise chain with an async function
```js
function getProcessedData(url) {
  return downloadData(url) // returns a promise
    .catch(e => {
      return downloadFallbackData(url)  // returns a promise
    })
    .then(v => {
      return processDataInWorker(v)  // returns a promise
    })
}

// rewritten as:
async function getProcessedData(url) {
  let v
  try {
    v = await downloadData(url)
  } catch(e) {
    v = await downloadFallbackData(url)
  }
  return processDataInWorker(v)
}

// or 
async function getProcessedData(url) {
  const v = await downloadData(url).catch(e => { 
    return downloadFallbackData(url)
  })
  return processDataInWorker(v)
}
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Arrow functions

Syntax and examples:
```js
param => expression
(param1, paramN) => expression

// examples
param => {
  let a = 1;
  return a + param;
}

(param1, paramN) => {
   let a = 1;
   return a + param1 + paramN;
}

// To return an object literal expression requires parentheses around expression
params => ({foo: "a"}) // returning the object {foo: "a"}
// Rest parameters are supported:
(a, b, ...r) => expression
// Default parameters are supported:
(a=400, b=20, c) => expression
// Destructuring within params supported:
([a, b] = [10, 20]) => a + b;  // result is 30
({ a, b } = { a: 10, b: 20 }) => a + b; // result is 30
```

<br />

Arrow functions used as methods:
```js
'use strict';

var obj = { // does not create a new scope
  i: 10,
  b: () => console.log(this.i, this),
  c: function() {
    console.log(this.i, this);
  }
}

obj.b(); // prints undefined, Window {...} (or the global object)
obj.c(); // prints 10, Object {...}
```

<br />

Another example involving `Object.defineProperty()`:
```js

'use strict';

var obj = {
  a: 10
};

Object.defineProperty(obj, 'b', {
  get: () => {
    console.log(this.a, typeof this.a, this); // undefined 'undefined' Window {...} (or the global object)
    return this.a + 10; // represents global object 'Window', therefore 'this.a' returns 'undefined'
  }
});
```

<br /> 

More examples:
```js
// Traditional Anonymous Function
function (a, b){
  return a + b + 100;
}

// Arrow Function
(a, b) => a + b + 100;

// Traditional Anonymous Function (no arguments)
let a = 4;
let b = 2;
function (){
  return a + b + 100;
}

// Arrow Function (no arguments)
let a = 4;
let b = 2;
() => a + b + 100;

// Traditional Anonymous Function
function (a, b){
  let chuck = 42;
  return a + b + chuck;
}

// Arrow Function
(a, b) => {
  let chuck = 42;
  return a + b + chuck;
}

// Traditional Function
function bob (a){
  return a + 100;
}

// Arrow Function
let bob = a => a + 100;
```

<br />

More examples: Check [MDN Arrow functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions):

```js
// An empty arrow function returns undefined
let empty = () => {};

(() => 'foobar')();
// Returns "foobar"
// (this is an Immediately Invoked Function Expression)

var simple = a => a > 15 ? 15 : a;
simple(16); // 15
simple(10); // 10

let max = (a, b) => a > b ? a : b;

// Easy array filtering, mapping, ...

var arr = [5, 6, 13, 0, 1, 18, 23];

var sum = arr.reduce((a, b) => a + b);
// 66

var even = arr.filter(v => v % 2 == 0);
// [6, 0, 18]

var double = arr.map(v => v * 2);
// [10, 12, 26, 0, 2, 36, 46]

// More concise promise chains
promise.then(a => {
  // ...
}).then(b => {
  // ...
});

// Parameterless arrow functions that are visually easier to parse
setTimeout( () => {
  console.log('I happen sooner');
  setTimeout( () => {
    // deeper code
    console.log('I happen later');
  }, 1);
}, 1);
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Methods

Syntax:
```js
const obj = {
  get property() {},
  set property(value) {},
  property( parameters… ) {},
  *generator( parameters… ) {},
  async property( parameters… ) {},
  async* generator( parameters… ) {},

  //  with computed keys
  get [property]() {},
  set [property](value) {},
  [property]( parameters… ) {},
  *[generator]( parameters… ) {},
  async [property]( parameters… ) {},
  async* [generator]( parameters… ) {},
};

// Given the following code:
const obj = {
  foo: function() {
    // ...
  },
  bar: function() {
    // ...
  }
}
// You are now able to shorten this to:
const obj = {
  foo() {
    // ...
  },
  bar() {
    // ...
  }
}
```

Also look into:
- Generator methods
- Async methods
- Async generator methods

<br />

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

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## ES6 export import

```js
// Strict mode: a restricted variant of JavaScript, intentionally has different semantics
"use strict";

// script tag if you intend to use import and export with defer attribute:
<script type="module" src="filename.js" defer></script>
```

<br />

Export:
```js
// export a code block
export const add = (x, y) => {
  return x + y;
}

// export a variable
const add = (x, y) => {
  return x + y;
}
export { add };

// export multiple objects:
export { add, subtract };

// create an export fallback with export default
export default function add(x, y) {
  return x + y;
}
// or
export default function(x, y) {
  return x + y;
}
```

<br />

Import:
```js
// single object:
import { add } from './math_functions.js'; 

// import multiple
import { add, subtract } from './math_functions.js';

// import all
import * as myMathModule from "./math_functions.js";

// use the imported module:
myMathModule.add(2,3);
myMathModule.subtract(5,3);

// import a default export
import add from "./math_functions.js"; 
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Callback functions

Example:
```js
function greeting(name) {
  alert('Hello ' + name);
}

function processUserInput(callback) {
  var name = prompt('Please enter your name.');
  callback(name);
}
processUserInput(greeting);
```

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

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

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

<br />

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

<br />

Then to get and use the local storage items, still inside the event listener:
```js
const tasks = JSON.parse(localStorage.getItem('tasks'));
tasks.forEach(function(task){
  console.log(tasks);
});
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

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

<br />

But the structure is ul > li > a > i and to delete the entire list item, which is the parent of the `<a>` tag, in the if statement:
```js
  if(e.target.patentElement.classList.contains("delete-item")) {
    // target is the icon
    e.target.parentElement.parentElement.remove();
  }
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Miscellaneous

Promises, ...

### ES6 Promises

```js
// lesson 29 freeCodeCamp
const myPromise = new Promise((resolve, reject) => {
  if (conditionhere) {
    resolve("Promise was fulfilled");
  } else {
    reject("Promise was rejected");
  }
});
// or this 
const makeServerRequest = new Promise((resolve, reject) => {
  let responseFromServer;

  if (responseFromServer) {
    resolve("We got the data");
  } else {
    reject("Data not received")
  }
});

// lesson 30 & 31 freeCodeCamp (confusing)
const makeServerRequest = new Promise((resolve, reject) => {
  // responseFromServer is set to false to represent an unsuccessful response from a server
  let responseFromServer = true;

  if (responseFromServer) {
    resolve("We got the data");
  } else {
    reject("Data not received");
  }
});

makeServerRequest.then(result => {
  console.log(result);
});

makeServerRequest.catch((error) => {
  console.log(error);
});
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Dynamic functions

```js
let foods = {
  apples: 25,
  oranges: 32,
  plums: 28,
  bananas: 13,
  grapes: 35,
  strawberries: 27
};

function checkInventory(scannedItem) {
  return foods[scannedItem];
}
// console.log(checkInventory("apples"));
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>