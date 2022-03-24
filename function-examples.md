# Important Function Code Examples

**Functional programming**: One of the core principles of functional programming is to not change things. Functional programming is all about creating and using non-mutating functions.

- Another principle of functional programming is to always declare your dependencies explicitly. 
- This means if a function depends on a variable or object being present, then pass that variable or object directly into the function as an argument. 
- The function is easier to test, you know exactly what input it takes, and it won't depend on anything else in your program.
- The function would always produce the same output for the same set of inputs

Distinct principles for functional programming:

- Don't alter a variable or object - create new variables and objects and return them if need be from a function. It's easier to prevent bugs knowing that your functions don't change anything, including the function arguments or any global variable
- Declare function parameters - any computation inside a function depends only on the arguments passed to the function, and not on any global object or variable

Here are docs from MDN:

- [MDN functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions)
- [MDN IIFE](https://developer.mozilla.org/en-US/docs/Glossary/IIFE)
- [MDN Async await](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)
- [MDN Arrow functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)
- [MDN methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Method_definitions)
- [MDN callback functions](https://developer.mozilla.org/en-US/docs/Glossary/Callback_function)
- [MDN Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- [MDN recursion](https://developer.mozilla.org/en-US/docs/Glossary/Recursion)

<div id="back-to-top"></div>

## Table of contents

1. [General](#general)
   1. [Definitions](#definitions)
   1. [Syntax](#syntax)
   1. [Declaration vs expression](#declaration-vs-expression)
   1. [Rest and spread syntax](#rest-and-spread-syntax)
   1. [Default parameters](#default-parameters)
   1. [Arguments object](#arguments-object)
   1. [Miscellaneous](#miscellaneous)
1. [Function methods](#function-methods)
   1. [apply](#apply)
   1. [bind](#bind)
   1. [call](#call)
   1. [toString](#tostring)
1. [Nested functions](#nested-functions)
   1. [Multiple nested functions](#multiple-nested-functions)
   1. [Closures](#closures)
1. [IIFE](#iife)
1. [Async await](#async-await)
1. [Arrow functions](#arrow-functions)
1. [Methods](#methods)
1. [ES6 export import](#es6-export-import)
1. [Callback functions](#callback-functions)
1. [Local storage](#local-storage)
1. [Event delegation](#event-delegation)
1. [Recursion](#recursion)
   1. [freeCodeCamp examples](#freecodecamp-examples)
   1. [MDN examples](#mdn-examples)
   1. [Recursion notes](#recursion-notes)
1. [Miscellaneous](#miscellaneous)
   1. [ES6 Promises](#es6-promises)
   1. [Dynamic functions](#dynamic-functions)
   1. [Randon stuff](#randon-stuff)

## General

Look into the function properties: `.length`, and maybe `.name`. Also check out the function methods: `apply()`, `bind()`, `call()`, and `toString()`.

### Definitions

<dl>
  <dt>Callback function</dt>
  <dd>is a function passed into another function as an argument, which is then invoked inside the outer function to complete some kind of routine or action. An example is the function in `addEventListener()`.</dd>
</dl>
<dl>
  <dt>First class functions</dt>
  <dd>Functions that can be assigned to a variable, passed into another function, or returned from another function just like any other normal value, are called first class functions. In JavaScript, all functions are first class functions.</dd>
</dl>
<dl>
  <dt>Higher order functions</dt>
  <dd>Functions that take a function as an argument, or return a function as a return value.</dd>
</dl>
<dl>
  <dt>Lambda functions</dt>
  <dd>When functions are passed in to or returned from another function, then those functions which were passed in or returned can be called a lambda. Lambda expression is an anonymous function that provides a very concise and functional syntax which is further used for writing anonymous methods...a simple, short, throwaway function which is designed to be created inline in code. They're also known as lambda expressions, anonymous functions, lambda abstractions, lambda form, or function literals</dd>
</dl>
<dl>
  <dt>Arity</dt>
  <dd>The arity of a function is the number of arguments it requires.</dd>
</dl>
<dl>
  <dt>Currying</dt>
  <dd>Currying a function means to convert a function of N arity into N functions of arity 1. In other words, it restructures a function so it takes one argument, then returns another function that takes the next argument, and so on.</dd>
</dl>

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div> 

### Syntax

```js
// typeof:
let typeOfTest;
typeOfTest = function() {
  return "Hello";
}                 
console.log(typeof typeOfTest) // function


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

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Declaration vs expression

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

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Rest and spread syntax

With rest parameter and spread operator in argument list:
```js
let someVar = [some other array]
let mainArray = [1, 2, ...someVar, 10, 11]

function someFx(...arr) {
  code here
}
someFx(mainArray);
```

<br />

use the rest parameter with function parameters:
```js
function howMany(...args) {
  return "You have passed " + args.length + " arguments.";
}
console.log(howMany(0, 1, 2, -1, -2));
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Default parameters

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

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Arguments object

MDN: `arguments` is an Array-like object accessible inside functions that contains the values of the arguments passed to that function. 

freeCodeCamp: The arguments object is an object that stores all of the values passed to the function. The arguments object takes on the structure of a JSON Object. 


```js
console.log(typeof arguments); // 'object' 
console.log(typeof arguments[0]); // returns the type of the first argument

// if a function is passed 3 arguments, you can access them as follows
arguments[0] // first argument
arguments[1] // second argument
arguments[2] // third argument


function func1(a, b, c) {
  console.log(arguments[0]); // expected output: 1
  console.log(arguments[1]); // expected output: 2
  console.log(arguments[2]); // expected output: 3
}
func1(1, 2, 3);

// Each argument can also be set or reassigned:
arguments[1] = 'new value';

// freeCodeCamp:
 function viewArgs() {
    return arguments;
}
console.log(viewArgs([3, 5, 1, 2, 2], 2, 3, 5));
// { '0': [ 3, 5, 1, 2, 2 ], '1': 2, '2': 3, '3': 5 }
console.log(viewArgs([2, 3, 2, 3, 2, 3]));
// { '0': [ 2, 3, 2, 3, 2, 3 ] }
console.log(viewArgs(3,2,1,"life the universe and all"));
// { '0': 3, '1': 2, '2': 1, '3': 'life the universe and all' }
console.log(viewArgs("Douglas","Adams"));
// { '0': 'Douglas', '1': 'Adams' }
```

The arguments object is not an Array. It is similar, but lacks all Array properties except length. As you can do with any Array-like object, you can use ES2015's `Array.from()` method or `spread syntax` to convert arguments to a real Array:

```js
let args = Array.from(arguments);
// or
let args = [...arguments];
```

The arguments object is useful for functions called with more arguments than they are formally declared to accept. This technique is useful for functions that can be passed a variable number of arguments, such as `Math.min()`.

If you were to pass 3 arguments to a function, say `storeNames()`, those 3 arguments would be stored inside an object called **arguments** and it would look like this when we pass the arguments storeNames("Springfield", "Clayton", "Smithville") to our function. When you execute that function with n arguments, 3 in this case, it will return the object to us and it will look like an array:

```js
function storeNames() { return arguments; } 
// ["Springfield", "Clayton", "Smithville"]
arguments.length // 3
```

The arguments object can be used in conjunction with _rest_, _default_, and _destructured parameters_. 

#### Treat it as an array

You should not slice on arguments because it prevents optimizations in JavaScript engines. Instead, try constructing a new array by iterating through the arguments object - try a `for loop`: 

```js
let args = []; // Empty array, at first.
for (let i = 0; i < arguments.length; i++) {
    args.push(arguments[i])
} // Now 'args' is an array that holds your arguments.

// also try the rest parameter or Array.from() method:
function func(...args) {
    console.log(args); // or 
    console.log(Array.from(arguments));
}
function func() {
    console.log(Array.from(arguments)); // or 
    return Array.from(arguments).sort((a, b) => a - b);
}
func(1,2,3); // [ 1, 2, 3 ]
```




<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Miscellaneous

returning boolean values from functions and `typeof`:
```js
function checkEqual(a, b) {
  return a === b;
}

// or 

function boolReturn(test) {
  // return typeof test === "number";
  // return typeof test === "string";
  return typeof test === "object";
  // return typeof test === "boolean";
}
console.log(boolReturn([1,2,3]));
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div> 

## Function methods

Also look into 

- [get and getter](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/get): The `get` syntax binds an object property to a function that will be called when that property is looked up.
- [set and setter](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/set): The `set` syntax binds an object property to a function to be called when there is an attempt to set that property. 

### apply

The [apply()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/apply) method **<ins>calls a function</ins>** with a given `this` value, and `arguments` provided as an array (or an array-like object).

```js
// syntax:
apply(thisArg)
apply(thisArg, argsArray)
```

<br />

### bind

The [bind()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) method creates a new function that, when called, has its `this` keyword set to the provided value, with a given sequence of arguments preceding any provided when the new function is called.

I've seen Brad Traversy use this one in some of his lessons. 

```js
// syntax:
bind(thisArg)
bind(thisArg, arg1)
bind(thisArg, arg1, arg2)
bind(thisArg, arg1, ... , argN)
```

<br />

### call

The [call()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/call) method calls a function with a given `this` value and arguments provided individually.

```js
// syntax:
call()
call(thisArg)
call(thisArg, arg1)
call(thisArg, arg1, arg2)
call(thisArg, arg1, ... , argN)
```

<br />

### toString

The [toString()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/toString) method returns a string representing the source code of the function. 

```js
// syntax:
toString()
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div> 

## Nested functions

**Nested functions**: The nested (inner) function is private to its containing (outer) function. The inner function forms a closure: the inner function can use the arguments and variables of the outer function, while the outer function cannot use the arguments and variables of the inner function.

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

// Since the inner function forms a closure, you can call the outer function and specify arguments for both the outer and inner function:
function outside(x) {
  function inside(y) {
    return x + y;
  }
  return inside;
}
fn_inside = outside(3);
result = fn_inside(5); // returns 8
result1 = outside(3)(5); // returns 8
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div> 

### Multiple nested functions

Functions can be multiple-nested:
- A function (`A`) contains a function (`B`), which itself contains a function (`C`).
- Both functions `B` and `C` form closures here. So, `B` can access `A`, and `C` can access `B`.
- In addition, since `C` can access `B` which can access `A`, `C` can also access `A`.

Thus, the closures can contain multiple scopes; they recursively contain the scope of the functions containing it. This is called _scope chaining_. 

```js
// In this example, C accesses B's y and A's x
function A(x) {
  function B(y) {
    function C(z) {
      console.log(x + y + z);
    }
    C(3);
  }
  B(2);
}
A(1); // logs 6 (1 + 2 + 3)
```

1. `B` forms a closure including `A`
1. `C` forms a closure including `B`
1. Because `B`'s closure includes `A`, `C`'s closure includes `A`, `C` can access both `B` and `A`'s arguments and variables. In other words, `C` chains the scopes of `B` and `A`, in that order
1. The reverse, however, is not true. `A` cannot access `C`

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div> 

### Closures

JavaScript allows for the nesting of functions and grants the inner function full access to all the variables and functions defined inside the outer function (and all other variables and functions that the outer function has access to).

However, the outer function does not have access to the variables and functions defined inside the inner function. This provides a sort of encapsulation for the variables of the inner function.

Also, since the inner function has access to the scope of the outer function, the variables and functions defined in the outer function will live longer than the duration of the outer function execution, if the inner function manages to survive beyond the life of the outer function. A closure is created when the inner function is somehow made available to any scope outside the outer function.

```js
let createPet = function(name) {
  let sex;

  return {
    setName: function(newName) {
      name = newName;
    },

    getName: function() {
      return name;
    },

    getSex: function() {
      return sex;
    },

    setSex: function(newSex) {
      if(typeof newSex === 'string' && (newSex.toLowerCase() === 'male' ||
        newSex.toLowerCase() === 'female')) {
        sex = newSex;
      }
    }
  }
}

let pet = createPet('Vivie');
pet.getName();                  // Vivie

pet.setName('Oliver');
pet.setSex('male');
pet.getSex();                   // male
pet.getName();                  // Oliver


// The functions do not even have to be assigned to a variable, or have a name:
let getCode = (function() {
  let apiCode = '0]Eal(eh&2';    // A code we do not want outsiders to be able to modify...

  return function() {
    return apiCode;
  };
})();

getCode();    // Returns the apiCode
```

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

Examples:
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

And more examples: Check [MDN Arrow functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions):

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
// syntax (HUH?)
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

Examples:
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

// script tag if you intend to use import and export (defer attribute added):
<script type="module" src="filename.js" defer></script>
```

<br />

Export:
```js
// export a code block:
export const add = (x, y) => {
  return x + y;
}

// export a variable:
const add = (x, y) => {
  return x + y;
}
export { add };

// export multiple objects:
export { add, subtract };

// create an export fallback with export default:
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
// import a single object:
import { add } from './math_functions.js'; 

// import multiple object:
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

<br />

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

Then to get and use the local storage items (still inside the event listener):
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

## Recursion

The act of a function calling itself, recursion is used to solve problems that contain smaller sub-problems. A recursive function can receive two inputs: a base case (ends recursion) or a recursive case (resumes recursion)

- Recursive function calls itself until condition met
- Recursion is limited by stack size

Syntax:
```js
function recurse() {
    if(condition) {
        // stop calling itself
    } else {
        recurse();
    }
}

// syntax 2:
function fxName() {
  return fxName();
  // executes forever resulting in a "stack overflow" - ran out of memory
  // so you need a base case
}

// syntax 3:
function recursion(parm) {
  if (parm cond) {   // base case, when hit stop recursion
    return;
  }
  return recursion(parm + 1); // here is the recursion
}

// 
```

<br />

Example:
```js
// recursive function, sum(arr, n), that returns the sum of the first n elements of an array arr
function sum(arr, n) {
  if(n <= 0) {
    return 0;
  } else {
    return sum(arr, n - 1) + arr[n - 1];
  }
}


// countdown
function countDown(fromNumber) {
    console.log(fromNumber);       // 3 2 1
    let nextNumber = fromNumber - 1;
    if (nextNumber > 0) {
        countDown(nextNumber);
    }
}
countDown(3);
// If you add the condition to stop calling itself, you will get this error:
Uncaught RangeError: Maximum call stack size exceeded.

// countdown2
function countdown(n) {
  if (n < 1) {
    return [];
  } else {
    const arr = countdown(n - 1);
    arr.unshift(n);
    return arr;
  }
}
// or 
// Solution 1 
function countdown(n) {
  if (n < 1) {
    return [];
  } else {
    const arr = countdown(n - 1);
    arr.unshift(n);
    return arr;
  }
}
// Solution 2 (Click to Show/Hide)
function countdown(n) {
  if (n < 1) {
    return [];
  } else {
    const arr = countdown(n - 1);
    arr.splice(0, 0, n);
    return arr;
  }
}

// countdown 3
function countdown(n){
   return n < 1 ? [] : [n].concat(countdown(n - 1));
}
// or 
function countdown(n){
   return n < 1 ? [] : [n, ...countdown(n - 1)];
}

// reverse a string: (use for palindrome?)
function string_reversal(string) {
  if (string == "") {
    return ""
  }

  return string_reversal(string.slice(1)) + string[0]
}

// Recursion to Create a Range of Numbers
function rangeOfNumbers(startNum, endNum) {
  if (endNum - startNum === 0) {
    return [startNum];
  } else {
    var numbers = rangeOfNumbers(startNum, endNum - 1);
    numbers.push(endNum);
    return numbers;
  }
}

// solution 2
function rangeOfNumbers(startNum, endNum) {
  return startNum === endNum
    ? [startNum]
    : rangeOfNumbers(startNum, endNum - 1).concat(endNum);
}
// or 
function rangeOfNumbers(startNum, endNum) {
  return startNum === endNum
    ? [startNum]
    : [...rangeOfNumbers(startNum, endNum - 1), endNum ];
}

```

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

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### freeCodeCamp examples

From the video 
```js
// factorial example with recursion
function factorial(num){
    if(num === 1){
        return num;
    }
    return num * factorial(num - 1) 
}
console.log(factorial(4)); // 24 = 4 * 3 * 2 * 1
console.log(factorial(5)); // 120

// for loop solution for factorials
function factorialize(num) {
  let product = 1;
  // let i = 1 also works
  for (let i = 2; i <= num; i++) {
    product *= i;
  }
  return product;
}
console.log(factorialize(5)); // 120


// count down example
function countDownFrom(number) {
	if (number === 0) {
		return;
	}
    console.log(number);    
    countDownFrom(number - 1);
}
countDownFrom(5); // 5 4 3 2 1

// Essay to revise until accepted:
function revise(essay) {
  read(essay);
  get_feedback_on(essay);
  apply_changes_to(essay);
  revise(essay) unless essay.complete;
}
// you do a little bit of work on ecah invocation of your method call until you hit the stopping condition
```

<br />

Recursion with strings:
```js
// STRING REVERSAL
// input str: "the simple engineer"
// output str: "reenigne elpmis eht" - string in reverse

function revString(str) {
// what are the steps? last char becomes 1st
  let len = str.length;
  return str[len - 1];
}
console.log(revString("the simple engineer")); // "reenigne elpmis eht"
// Uncaught RangeError: Maximum call stack size exceeded
// Uncaught RangeError: Maximum call stack size exceeded at String.substring 

// 
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### MDN examples

Recursion is limited by stack size:
```js
// The following code defines a function that returns the maximum size of the call stack available in the JavaScript runtime in which the code is run.
const getMaxCallStackSize = (i) => {
  try {
    return getMaxCallStackSize(++i);
  } catch {
    return i;
  }
};

console.log(getMaxCallStackSize(0));
```

<br />

Common usage examples:
```js
// factorial with recursion
const factorial = (n) => {
  if (n === 0) return 1;
  else return n * factorial(n - 1);
};
console.log(factorial(10)); // 3628800

// fibonacci
const fibonacci = (n) => (n <= 2 ? 1 : fibonacci(n - 1) + fibonacci(n - 2));
console.log(fibonacci(10)); // 55
console.log(fibonacci(6)); // 8

// reduce method example
const reduce = (fn, acc, [cur, ...rest]) => (
  cur === undefined ? acc : reduce(fn, fn(acc, cur), rest)
);
console.log(reduce((a, b) => a + b, 0, [1, 2, 3, 4, 5, 6, 7, 8, 9])); // 45
```

Look into the _call stack_ mentioned in [A Quick Intro to Recursion in Javascript](https://www.freecodecamp.org/news/quick-intro-to-recursion/) by freeCodeCamp.

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Recursion notes

Notes on Video [Recursion in Programming - Full Course](https://youtu.be/IJDJ0kBx2LM) from freeCodeCamp:

- 1) What is the least amount of work that I can do? What are the sub-problems? How do you tke a large problem and break it into sub problems?
- 2) What is my stopping condition? When would the process complete? What is the stopping condition?
- **Call Stack**: stack frame -> A depends on B, B depends on C, then C 

**PROS**:
- bridges the gap between elegance and complexity. His examples will be complex traversals of data structures of trees and graphs. 
- Also, reduces the need for complex loops and auxiliary data structures. Simplies your code.
- can reduce time complexity (memoization)
- works really well with data structures like **_JSON Objects_**, **_trees_** and **_graphs_** - things that allow you to focus on one tiny unit of the data structure at a time

**CONS**: 
- slowness because of CPU overhead. Can get messy with recursive data structures. 
- can lead to out of memory errors / stack overflow exceptions
- can be complex if poorly constructed. Always ask, "_Is this a good use case for recursion?_"

> _Uncaught RangeError: Maximum call stack size exceeded_

NOTE: For string recursion, very often you can make it easier by evaluating the input length - so try a str of length 0 and of 1 - 

NUMBER RECURSION
- 1st problem - base 10 to binary conversion - 
- 

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Miscellaneous

- arguments vs parameters
- scope
- `return`: 
- `undefined`: 

Other concepts from [MDN Functions doc](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions): Scope and the function stack, Recursion, Preservation of variables, No separate `this`, and Predefined functions.

**Predefined functions**: 
- DO NOT USE: `eval()`, `uneval()`, `escape()`, and `unescape()`.
- OK TO USE: `isFinite()`, `isNaN()`, `parseFloat()`, `parseInt()` with `radix`, `decodeURI()`, `decodeURIComponent()`, `encodeURI()`, and `encodeURIComponent()`

<br />

### ES6 Promises

The `Promise` object represents the eventual completion (or failure) of an asynchronous operation and its resulting value.

A `Promise` is a proxy for a value not necessarily known when the promise is created. It allows you to associate handlers with an asynchronous action's eventual success value or failure reason. This lets asynchronous methods return values like synchronous methods: instead of immediately returning the final value, the asynchronous method returns a promise to supply the value at some point in the future.

A Promise is in one of these states:

- _pending_: initial state, neither fulfilled nor rejected.
- _fulfilled_: meaning that the operation was completed successfully.
- _rejected_: meaning that the operation failed.

A pending promise can either be fulfilled with a value or rejected with a reason (error). When either of these options happens, the associated handlers queued up by a promise's `then` method are called. If the promise has already been fulfilled or rejected when a corresponding handler is attached, the handler will be called, so there is no race condition between an asynchronous operation completing and its handlers being attached.

As the `Promise.prototype.then()` and `Promise.prototype.catch()` methods return promises, they can be chained.

See also: [MDN Chained Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise#chained_promises), [MDN Incumbent settings object tracking](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise#incumbent_settings_object_tracking), [MDN Constructor](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise#constructor), [MDN Static methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise#static_methods), and [MDN Instance methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise#instance_methods)

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
``

- Promise, new, resolve, reject
- pending, fulfilled, rejected
- then, result, catch, try, error 
- refactor

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

### Randon stuff

- **freeCodeCamp**: Functions are considered first class objects in JavaScript, which means they can be used like any other object. They can be saved in variables, stored in an object, or passed as function arguments.

Web Dev Simplied: Once You Realize This You Will Never Struggle With Callbacks Again
- Functions are variables just like everything else:

```js
function test() {
  console.log("Hello")
}

const test2 = test;
console.log(test2 === test); // true
test.prop = "Hi";
console.dir(test) // prop: "Hi" prototype, name, length,...
```

Function.prototype.bind(): 

[MDN bind](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_objects/Function/bind): creates a new function that, when called, has its this keyword set to the provided value, with a given sequence of arguments preceding any provided when the new function is called (???)

```js
// syntax
bind(thisArg)
bind(thisArg, arg1)
bind(thisArg, arg1, arg2)
bind(thisArg, arg1, ... , argN)
```
Other terms:

- imperative approach
- declarative programming
- mutation, side effect, pure function
- first class objects
- 10. Implement the filter Method on a Prototype

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

