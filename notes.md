# Notes: Basic JavaScript & ES6

Notes on specifics in README and other important notes, definitions, concepts, tips, tricks, etc. Currently, this file is a mess...

The code block below is a quick note for myself for a project I am stuck on (ignore):

**use `every()` to compare one array to other arrays and to return a match:**

```js
const hasSameElements = (a, b) => {
    return a.length === b.length && a.every((v,i) => v===b[i])
}
// But do the elements need to be in the same order?
```

## Table of Contents

1. [Tips and Tricks](#tips-and-tricks)
1. [Terms](#terms)
   1. [Code Specific](#code-specific)
   1. [Concepts](#concepts)
1. [Dates](#dates)
1. [Functions and Return](#functions-and-return)
1. [Conditional Logic](#conditional-logic)
1. [Conditional Statements](#conditional-statements)
1. [Loops](#loops)
1. [ES6](#es6)
1. [RegEx](#regex)
1. [Debugging](#debugging)
1. [Data Structures](#data-structures)
1. [Basic Algorithms](#basic-algorithms)
1. [OOP](#oop)
1. [Functional Programming](#functional-programming)
1. [The DOM](#the-dom)
1. [DOM Elements](#dom-elements)
   1. [DOM Node Properties](#dom-node-properties)
   1. [DOM Element Methods](#dom-element-methods)
1. [JavaScript Events](#javaScript-events)
   1. [Mouse](#mouse)
   1. [Keyboard](#keyboard)
   1. [Frame](#frame)
   1. [Form](#form)
   1. [Drag](#drag)
   1. [Clipboard](#clipboard)
   1. [Media](#media)
   1. [Animation](#animation)
   1. [Other Events](#other-events)
1. [Errors](#errors)

<h2 id="tips-and-tricks" align="center">Tips and Tricks</h2>

- === better than ==
- constructors
- IIFE
- trim()
- push.apply()
- splice instead of delete
- num.toFixed(#)
- setTimeout(), setInterval()
- Set timeouts to XMLHttpRequests
- Avoid using try-catch-finally inside a loop
- Declare and Initialize Arrays
- reduce!
- Sorting Array of String, Numbers or Objects
- destructuring assignment syntax
- check performance with `performance.now()`
- template literals with variables
- ways to shorten if statements: ternary, &&, 
- comma operator
- spread operator to merge 2 objects
- undefined (a variable that has not been assigned a value) vs null (intentional empty value)
- arr.slice(-1) to get last item
- use `array.slice(0, #);` to truncate an array
- Destructuring Assignment for objects and arrays
- short circuit operators
- Dealing With Empty and Non-Empty Values: 

```js
   const arr = [0,1,2,null,undefined,"",false];
   const nonEmptyValues = arr.filter(Boolean);
   console.log("nonEmptyValues: ", nonEmptyValues); //[1, 2]
```

- **Excellent**: https://www.freecodecamp.org/news/how-to-learn-javascript-a-little-faster/
- **Great**: https://www.codemotion.com/magazine/frontend/javascript/javascript-speed-up-tips/
- **Great**: https://samwalpole.com/my-top-5-javascript-tips-and-tricks-for-writing-cleaner-code
- Good: https://blog.yogeshchavan.dev/super-useful-tips-and-tricks-for-javascript-developers
- Good: https://www.jesssica.tech/post/Javascript-Tips-and-Tricks
- Good: https://pratapsharma.in/javascript-tips-and-tricks
- Good: https://github.com/wilfredinni/javascript-cheatsheet
- Maybe: https://github.com/alhassy/JavaScriptCheatSheet 

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<h2 id="terms" align="center">Terms</h2>

Concepts, specific code syntax, ...

### Code Specific

<dl>
  <dt>Callback function</dt>
  <dd>is a function passed into another function as an argument, which is then invoked inside the outer function to complete some kind of routine or action. An example is the function in `addEventListener`.</dd>
</dl>
<dl>
  <dt>currentTarget</dt>
  <dd>The read-only property of the Event interface identifies the current target for the event, as the event traverses the DOM. It always refers to the element to which the event handler has been attached, as opposed to Event.target</dd>
</dl>
<dl>
  <dt>Error</dt>
  <dd>Error objects are thrown when runtime errors occur. The Error object can also be used as a base object for user-defined exceptions. Runtime errors result in new Error objects being created and thrown.</dd>
</dl>
<dl>
  <dt>IIFE</dt>
  <dd>A function that runs as soon as it is defined.</dd>
</dl>
<dl>
  <dt>parsing</dt>
  <dd>Data parsing is a process in which a string of data is converted from one format to another. Parsing means analyzing and converting a program into an internal format that a runtime environment can actually run</dd>
</dl>
<dl>
  <dt>JSON.parse()</dt>
  <dd>A method that parses a JSON string, constructing the JavaScript value or object described by the string.</dd>
</dl>
<dl>
  <dt>JSON.stringify()</dt>
  <dd>A method that converts a JavaScript object or value to a JSON string.</dd>
</dl>
<dl>
  <dt>Parameters</dt>
  <dd>Parameters are variables that act as placeholders for the values that are to be input to a function when it is called.</dd>
</dl>
<dl>
  <dt>Arguments</dt>
  <dd>Are the actual values passed into a function that are represented by the parameters in the function declaration.</dd>
</dl>
<dl>
  <dt>parseInt</dt>
  <dd>A function that parses a string argument and returns an integer.</dd>
</dl>
<dl>
  <dt>Rest Parameter</dt>
  <dd>A syntax that allows a function to accept an indefinite number of arguments as an array.</dd>
</dl>
<dl>
  <dt>Spread Operator</dt>
  <dd>A syntax that can be used when all elements from an object or array need to be included in a list of some kind. he spread operator is commonly used to make shallow copies of JS objects. Using this operator makes the code concise and enhances its readability</dd>
</dl>
<dl>
  <dt>Event.target</dt>
  <dd>The read-only target property of the Event interface is a reference to the object onto which the event was dispatched.</dd>
</dl>
<dl>
  <dt>"use strict"</dt>
  <dd>Strict mode: a way to opt in to a restricted variant of JavaScript. </dd>
</dl>

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Concepts

<dl>
  <dt>Abstraction</dt>
  <dd>in OOP, refers to only showing essential details and keeping everything else hidden. Users of you classes should not worry about the inner details of those classes. Split up your code into small chunks. It’s best if the section you are working on is able to function without knowledge of the inner workings of a different section. Think in terms of interface and implementation. Interface refers to the way sections of code can communicate with one another (done thru methods that each class can access). The implementation of the methods (how they are coded) should be hidden.</dd>
</dl>
<dl>
  <dt>Arity</dt>
  <dd>Is the term used to refer to the number of arguments or operands in a function or operation; is the number of functions you can pass into an object; is the number of parameters the function contains; ...</dd>
</dl>
<dl>
  <dt>Currying</dt>
  <dd>currying is when a function — instead of taking all arguments at one time — takes the first one and returns a new function, which takes the second one and returns a new function, which takes the third one, etc. until all arguments are completed. It is a process in functional programming in which we can transform a function with multiple arguments into a sequence of nested functions. It returns a new function that expects the next argument inline</dd>
</dl>
<dl>
  <dt>Encapsulation</dt>
  <dd>in OOP, refers to bundling data with methods that can operate on that data within a class. It is the idea of hiding data within a class, preventing anything outside that class from directly interacting with it. Members of other classes can interact with the attributes of another object through its methods: `get` and `set` methods. Also, you may want some attributes to be read-only from outside the class, which means you only have a `getter` emthod, no `setter`. Don't allow external classes to directly edit an object's attributes. Each piece should not have access to or rely on the inner workings of other sections of code (Information hiding)!</dd>
</dl>
<dl>
  <dt>Event bubbling</dt>
  <dd>the bubbling up of events thru the DOM – so when an event happens it will bubble up thru its parents -  all the way to the body tag</dd>
</dl>
<dl>
  <dt>Event delegation</dt>
  <dd>The opposite of event bubbling – it's when we put the listener on one of the parents elements, then we use logic inside of the event handler to target the element we actually want</dd>
</dl>
<dl>
  <dt>Hoisting</dt>
  <dd>Refers to the process whereby the interpreter appears to move the declaration of functions, variables or classes to the top of their scope, prior to execution of the code. JavaScript's default behavior of moving declarations to the top</dd>
</dl>
<dl>
  <dt>Inheritance</dt>
  <dd>in OOP, is the principle that allows classes to erive from other classes – methods and attributes. A SuperClass with Subclasses. Subclasses inherit methods and attributes from their Superclass. </dd>
</dl>
<dl>
  <dt>Access modifiers</dt>
  <dd>A part of inheritance in OOP which change which classes have access to other classes, methods, or attributes. There are 3 main access modifiers: Public, Private, and Protected. Public modifiers can be accessed from anywhere in your program. Private modifier can only be accessed from within the same class that the member is defined. Protected modifiers can be access within the class it is defined, as well as subclasses of that class.</dd>
</dl>
<dl>
  <dt>"**_In place_**"</dt>
  <dd>In-place means that you should update the original string rather than creating a new one. You should change the content of the original string to the reverse without using a temporary storage variable to hold the string.</dd>
</dl>
<dl>
  <dt>Polymorphism</dt>
  <dd>in OOP, describes methods that are able to take on many forms. There are 2 types: Dynamic and Static. </dd>
</dl>
<dl>
  <dt>Dynamic polymorphism</dt>
  <dd>occurs during the runtime of the program. It describes when a method signature is in both a subclass and a superclass. They have the same name but different implementation, but the subclass overrides the superclass. This is because the form of the method is decided based on where in the class hierarchy it is called. This reduces the need for multiple if/else if statements</dd>
</dl>
<dl>
  <dt>Static polymorphism</dt>
  <dd>occurs during complie time and refers to when multiple methods with the same name but different arguments are defined in the same class: either a different # of parameters, or or different typss, or in a different order. That is known as method overloading. Despite the methods having the same name, their signatures are different due to their arguments.</dd>
</dl>
<dl>
  <dt>Recursion</dt>
  <dd>Is a process of calling itself. A function that calls itself is called a recursive function. The act of a function calling itself, recursion is used to solve problems that contain smaller sub-problems. A recursive function can receive two inputs: a base case (ends recursion) or a recursive case (resumes recursion).</dd>
</dl>
<dl>
  <dt>Scope</dt>
  <dd>Scope determines the accessibility (visibility) of variables. There are 3 types: 1) Block scope, 2) Function scope, 3) Global scope.</dd>
</dl>
<dl>
  <dt>Type coercion</dt>
  <dd>is the automatic or implicit conversion of values from one data type to another (such as strings to numbers).</dd>
</dl>

# Sloppy notes

Everything below here is a sloppy notebook: unordered notes, unclear notes, a true **_scratch-pad_**. 

Important things I need to memorize and incorporate:
- function statement vs var function: 
- arrow function: ( ) =>
- new Date(): 
- `${variable}`: 
- the use of +=, -=, *=, /= with numbers
- Escaping single and double quotes (`\'\"`), new line and tab (`\n\t`)
- Working with multi-dimensional arrays 
- Great data structures article: https://www.educative.io/blog/javascript-data-structures
  - my chord-intervals.json file is maybe a hash table or maybe a tre of some sort - 
- Memorize and fully understand `JSON.stringify()` vs `JSON.parse()` - why would you use them with arrays?
- Since ==, <, >, <=, >= do type coercion, you may need to include `&& typeof` == "type you want"
- Remember not to use `=` in an if condition but use `==` or `===`
- switch(), case, break, default - freeCodeCamp basic JS section, lessons: Golf Code and Counting Cards!
- Learn shorthand for if statements: if (a, b) return a === b;
- `freeCodeCamp`: 
   - 25 escape sequences in strings, 
   - 42 manipulate arrays with push ...45. manipulate arrays with unshift, 
   - 73 golf code, 
   - 74 selecting from many options with switch statements...77. replacing if else chains with switch, 
   - 78 returning boolean values from functions
   - 80 counting cards, 
   - 84 accessing object properties with variables is really good and the reference to lookup tables => link https://dev.to/k_penguin_sato/use-lookup-tables-for-cleaning-up-your-js-ts-code-9gk - similar to setting city = "Philadelphia" then using city in weather app, 
   - 86 add new properties to a js object - obj, newProp = "value"
   - 87 delete properties from a js object: delete obj.propname
   - 88 using objects for lookups - why does `lookup[val]` work but `lookup.val` does NOT? 
   - 89 hasOwnProperty, 92. accessing nested arrays for nice []. notation, 93. record collection WOW,
   - 96 iterate w\ js while loops 

**Notes on Record Collection**:
- 

78) returning boolean values from functions:
```js
function isEqual(a, b) {
  if (a === b) {
    return true;
  } else {
    return false;
  }
}
// reduced to
function isEqual(a, b) {
  return a === b;
}
```
> Therefore, `return a === b` shorthand for entire if statement

<div id="back-to-top"></div>

The best of my notes from Traversy Modern JS course:

- 8 - primitive data types: string, number, boolean, null, undefined - stored directly in the location that the variables accesses - stored on the stack
- reference types: arrays, object literals, functions, dates - accessed by reference, so the data isn’t actually stored in the variable – objects that are stored on the heap, the heap being dynalically alocated memory
- typeof operator – used with the reference data types will return ‘object’ for all of them 
- 9 - type conversion is where you change the datatype of a variable – e.g., data from a form will be a string by default but you may want to parse it
- `length - 1`
- 12 - template literals / template strings: ${ variables names or expressions/math or a function call or use conditionals / ternary op  }
- 13 - arr.sort() - great for strings but not the right result for a numbers based array
- `find()` method which takes in a testing Fx: arr.find(functionName) where functionName does a simple comparison and it gets an argument which s\b your array items I think – it returns the first number that neets the criteria
- the `this` keyword – trying to access another key in an object inside a Fx
- 15 – dates & times: new Date() - defaults to the present day if you don’t pass it anything
- new Date(year, monthIndex, day, hours, minutes, seconds)
- 16 - if (typeof thing !== 'undefined') – now you won’t get an error
- 18 - FUNCTION EXPRESSIONS: it’s when a Fx is the value of a variable, usually they are anonymous
- OBJECT ORIENTED PROGRAMMING: Functions inside of objects as opposed to in the global scope - in this case they are called METHODS – a Fx in an object `todo` called `add` or `edit` and you call it by `todo.add()` - or `todo.edit(id)`
- 19 - array specific iteration with forEach and map 
- BREAK and CONTINUE are really important things to know for loops
- forEach: takes in a callback function, an anonymous Fx – the anon Fx can take in 3 parameters, but you only need one – whatever you want to use as the current iteration, or the iterator -
- the first of the 3 things the Fx takes in is the iterator – the next is the index which is the index for each item in the array – and you can also pass in array for the actual array 
- map: map can work in a few diff ways – it’s used to return something diff – to return a diff array
- `for in` loop: often used for objects – create a user object > then for (let x in user) returns the names of the keys – user[x]) returns the values
- 24 - DOM selectors (methods) for single elements: getElementById, querySelector, getElementsByClassName, getElementsByTagName, querySelectorAll
- creating elements: className, setAttribute, appendChild, createTextNode, createElement, replaceChild, getAttribute, hasAttribute, removeAttribute, 
- 29 - NOTE: some elements have default behaviors – to stop the default behavior, pass a parm into the cb Fx and do e.preventDefault()
- Event Target Element: can get `e.taget.className` or to get a collection change className to classList - TARGET is really important especially for event delegation 
- 33 - localStorage: JSON.stringify, JSON.parse, clear, getItem, removeItem, setItem
- SKIP 4) DOM Projects 
- 44 - OOP: constructors & the _this_ Keyword: the most important things in OOP is the Constructor and the `this` keyword: if you want to create multiple instances of a certain type of object then you want to create a constructor
- the `this` keyword refers to the current instance of the object, the function scope
- NOTE: constructors are really powerful when they have functions w\in them known as methods
- 46 - each object in JS has a prototype – a prototype is an object itself – all objects inherit their properties and methods from their prototypes = Object.prototype vs Client.prototype 
- Object.prototype – you can see its methods like hasOwnProperty, toString, valueOf
- 47 - prototype inheritance: to have one object or one object type inherit from another 
- use .call(a, b, c, ...) - `call()` is a fx that allows us to call another Fx from somewhere else in the current context 
- 49 – ES6 classes: Any method you add inside the class gets added to the prototype and you still have Object.prototype 
- Static Methods – ones you can use without instantiating a new object or instance
- 50 inheritance and extending classes – or known as sub-classes 
- when you instantiate a sub-class you want to call the class constructor and you do that with a Fx called super() - that calls the parent class constructor – you have to pass in the parameters in common

7) Async JS, AJAX & Fetch API
- ajax and the fetch api to make http requests to files, apis, and services whether they are your own or not - 
- asynchronous Fx’s – you pass in a callback Fx which is one method for handling asynchronous code
- most async code you work with will come from an API or a library s\a AJAX and the XHR object – also jquery, libs like Axios, the fetch api, the Node.js filesystem (fs) module, XMLHttpRequest – these are all async technologies 
- the ways to work w\ Async code: 1. Callbacks, 2. Promises, 3. Async/Await 
- 58 Ajax – a set of web technologies to send and receeive data from the client & server asynchronously – done behind the scenes w\o having to relaod the page 
- updating a section of the page is faster w\ AJAX than having to reload the page - this happens by making an asynchronous AJAX or JS call – it goes thru an AJAX engine and uses the XmlHttpRequest object 
- the server returns the data usually in JSON format - then we parse and use that data in our application - 
- when we send and receive requests it can be from something on out local machine or from a public API - these APIS must have permissions granted for us to be able to use them - they usually have CORS enabled which allows for cross domain communication meaning we can make requests to their API even though we are on a different domain name 
- 59 - use new kw to instantiate a new instance of XMLHttpRequest which has properties like open()
- SUMMARY: 1. an event listener that 2. calls a Fx which 3. creates a new instance of the xhr object, 4. .open() is called and we pass in 4a. the type of request and the 4b. url/filename and 4c. true for asynchronous, when ready, 5. onload is called where we 6. check for staus = 200, 7. we do something w\ the response text, 8. .send to make it work
- there are also something called readyState values
- 61 - if you built a full-stack app it can be from your own api or from an external api - .open(), .send(), .onload() - 
- 62 - REST stands for REpresentational State Transfer – it’s a architecture style for designing networked applications – it works by relying on a stateless client-server communication protocol and is almost always HTTP 
- REST was made to treat objects on the server side as resources that can be created, updated, read and deleted (CRUD)
- what makes REST awesome is that since it operates using just HTTP requests and usually a standard like JSON 
- an API is the messenger and REST lets us use HTTP requests to format the message
- a REST API takes in multiple types of HTTP requests → GET, POST, PUT, DELETE, HEAD, CONNECT, TRACE, OPTIONS, PATCH 
- ENDPOINTS: the url’s that you access to do certain things
- with POST, PUT and DELETE you will send data long w\ your rquest – the API needs to know what data to add, update or delete 
- 63 – callback Fxs: function that is passed in as a parameter to another function and is then ran inside the Fx body - the one in forEach is synchronous – setTimeout uses an asynchronous cb
- 64, 65 - confusing 
- 66 – ES6 promises: 
- 67 – Fetch API: 
- 68 – Error handling w\ Fetch: 
- 69 – arrow Fxs: 
- 71 – async & await: 

The best of my notes from Traversy 20 web projects with vanilla javascript course:

- for a number input fied, using `typeof` shows it as a string - add a + symbol to turn it into a number
- `console.log(e.target);` - gives you the exact element that is clicked on
- the spread operator converts the nodes list into an array - then to map thru that use the high order array method called map() 
- Fetch is built into the browser so you don’t need to use a CDN or install it
- fetch runs asynchronously which means in the background and it returns a promise – when it’s done fetching it will return a promise – you catch that promise with .then() - .then() takes a function; res.json(); 

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>


Strings and Arrays: Same Methods, Same Effect in detail, Code examples:

```js
// slice string
const str = 'The quick brown fox jumps over the lazy dog.';
console.log(str.slice(4, 19)); // output: "quick brown fox"

// slice array
const clothes = ["shoes", "hat", "shirt", "pants", "socks", "belt"]
console.log(animals.slice(2, 4)); // output: Array ["shirt", "pants"]

// concat string
str1 = "Hey";
str2 = "there.";
str1.concat(' ', str2) // output "Hey there."

// concat array


// includes string


// includes array


// endsWith string


// indexOf string


// indexOf array


// lastIndexOf string


// lastIndexOf array

```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>





## Dates

**DATE CHEAT SHEET TO GET REAL DATES AND TIMES**:
- code examples from leafpickup.js:

```js
// Get day of week for November 1st for the current year
const d = new Date();
const year = d.getFullYear();
let currentNovFirst = '11/01/' + year;
let novFirstDay = new Date(currentNovFirst).getDay();
```
```js
// check the current year and update the startYr variable. 
if (year < 2032) {
  let startYr = 2021;
} else if (year >= 2032 && year <= 2042) {
  let startYr = 2032;
```

```js
/* CALCULATING AND FORMATTING THE MONDAY DATES FOR THE 6 WEEKS */
let week1 = new Date(), week2 = new Date(), week3 = new Date(), 
week4 = new Date(), week5 = new Date(), week6 = new Date();

const format = { year: "numeric", month: "short", day: "numeric" };

week1.setTime(weekOne.getTime());
week1Format = week1.toLocaleDateString('en-us', format);
// weekOne is the output from a switch() statement which finds the day of the 
// week for the 1st of Nov then return the date for the first Monday in November
```

<h2 id="functions-and-return" align="center">Functions and Return</h2>

- Parameters are variables that act as placeholders for the values that are to be input to a function when it is called
- When a function is defined, it is typically defined along with one or more parameters
- The actual values that are input (or "passed") into a function when it is called are known as arguments
- *Parameters* are <ins>variables</ins>, *Arguments* are <ins>values</ins>
- Scope:  refers to the visibility of variables
  - **Global scope** = defined outside of a function and are globally available
  - Variables which are declared without the let or const keywords are automatically created in the global scope. 
  - This can create unintended consequences elsewhere in your code or when running a function again. You should always declare your variables with let or const
  - **Local scope** = variables are declared within a function, they are only visible within that function
- **Return**: We can pass values into a function with arguments. You can use a `return` statement to send a value back out of a function
- When a `return` statement is used in a function body, the execution of the function is stopped and control returns to the calling location
- If specified, a given value is returned to the function caller
- In the case that the function doesn't have a `return` statement, when you call it, the function processes the inner code but the returned value is `undefined`

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<h2 id="conditional-logic" align="center">Conditional Logic</h2>

- `Boolean` and `if` statements: `if (boolean condition) { code if true}`
- if no `<` or `>` or other comparison symbol is used, the statement is considered `true` if the value is anything other than 0
- Comparison operators: `<`, `>`, `<=`, `>=`, `!=`, `==`, `!==`, `===`
- Like the `equality operator` (& `inequality operator`), the `greater than` operator **will convert data types of values while comparing** - same for `<`, `>=`, `<=`.
- Equality operator (`==`) vs. strict equality operator (`===`): the strict equality operator compares both the data type and value
- The same is true for the inequality operators: `!=` and `!==`
- You can determine the type of a variable or a value with the typeof operator
- And operator:  to test more than one thing at a time. The logical and operator (`&&`) returns `true` if and only if the operands to the left and right of it are true
- Or operator: The logical or operator (`||`) returns `true` if either of the operands is true
- Ternary

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<h2 id="conditional-statements" align="center">Conditional Statements</h2>

If, Else, Else If, Switch:
- `else` statements: used when the condition in an `if` statement is not met and an alternate block of code is executed
- `else if` statements:  If you have multiple conditions that need to be addressed, you can chain `if` statements together with `else if` statements; be careful of what statement comes first
- `switch` statements: tests a value and can have many `case` statements which define various possible values. Statements are executed from the first matched `case` value until a `break` is encountered
- `case` statements are tested with strick equality (`===`): `switch(check value(s)) {case value: varname = something; break; next case check…}`
- `default` means `else` in a `switch` statement – you can also have multiple cases before a `break`

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<h2 id="loops" align="center">Loops</h2>

- `while` loop: runs while a specified condition is true and stops once that condition is no longer true
- `for` loop: The most common type of JavaScript loop is called a `for` loop because it runs for a specific number of times
  - `for (a; b; c) { }`, where a is the intialization statement, b is the condition statement, and c is the final expression
  - A common task in JavaScript is to iterate through the contents of an array. One way to do that is with a `for` loop
  - Accumulators: The expression += is an just abreviation of x = x + i
- Nested `for` loops: arrays inside another array
- `do...while` loops: it will first `do` one pass of the code inside the loop no matter what, and then continue to run the loop `while` the specified condition evaluates to `true`
- Conditional (ternary) operator: 	a ? b : c	
- Recursion: ???

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<h2 id="es6" align="center">ES6</h2>

- Random numbers: 
  - Random whole numbers: `Math.floor(Math.random() * 20); `
  - Random whole numbers within a range: `Math.floor(Math.random() * (max - min + 1)) + min`
- The `parseInt()` function parses a string and returns an integer: `var a = parseInt("007");`
- Conditional (ternary) operator: `a ? b : c`, where `a` is the condition, `b` is the code to run when the condition returns `true`, and `c` is the code to run when the condition returns `false`

**Variables: var, let, const**:
- **Hoisting** refers to the process whereby the interpreter appears to move the declaration of functions, variables or classes to the top of their scope, prior to execution of the code.
- Hoisting allows functions to be safely used in code before they are declared - variables and function declarations are moved to the top of their scope before code execution
- When you declare a variable without a statement it is automatically declared as `var` 
- The scope is global when a `var` variable is declared outside a function
- `let` vs `var`: `var` can be overwritten, `CONST` cannot
- `let` is block scoped - A block is a chunk of code bounded by `{ }` - So a variable declared in a block with let is only available for use within that block
- `let` can be updated but not re-declared
- a variable declared with `let` can be updated within its scope
- a `let` variable cannot be re-declared within its scope
- Just like `var`, `let` declarations are hoisted to the top
- The `let` keyword is not initialized - if you try to use a `let` variable before declaration, you'll get a `Reference Error`
- `"use strict"`: declared at the top of your file or in a function: you can not use <ins>undeclared variables</ins> - It helps you to write cleaner code
- Scope: When you declare a variable with the `let` keyword inside a block, statement, or expression, its scope is limited to that block, statement, or expression
  - This behavior will cause problems if you were to create a function and store it for later use inside a `for` loop that uses the `i` variable. This is because the stored function will always refer to the value of the updated global `i` variable???
- Declare a read-only variable with the `const` keyword: `const` has all the awesome features that let has, with the added bonus that variables declared using `const` are read-only
- `const` variables are block scoped and must be initialized during declaration
- You should always name variables you don't want to reassign using the `const` keyword
- Use `let` when you want the variable to change, use `const` when you want it to be constant
- This behavior is somehow different when it comes to objects declared with `const`. While a `const` object cannot be updated, the properties of this objects can be updated
- Use `let` when you know their values will be changing
- Mutate an array declared with `const`: Objects assigned to a variable using `const` are still mutable
- prevent object mutation: To ensure your data doesn't change, use the function `Object.freeze` to prevent data mutation. Once frozen, you can no longer add, update, or delete properties from it: `Object.freeze(objName);`


**Arrow functions, Rest parameter, Spread operator, Template literals**:
- inline functions - When there is no function body, and only a return value, arrow function syntax allows you to omit the keyword `return` as well as the brackets surrounding the code 
- If an arrow function has a single parameter, the parentheses enclosing the parameter may be omitted
- Default parameters: allow named parameters to be initialized with default values if no value or undefined is passed: `function fnName(parm1 = val1) {```}` or `function fnName(parm1, parm2 = val, ...) {...}`
- **Rest parameter**: you can create functions that take a variable number of arguments. These arguments are stored in an array that can be accessed later from inside the function: `(...args)`
- The rest parameter eliminates the need to check the args array and allows us to apply `map()`, `filter()` and `reduce()` on the parameters array
- Only the last parameter in a function definition can be a rest parameter
- **Spread operator**: allows you to expand arrays and other expressions in places where multiple parameters or elements are expected

```
const arr = [6, 89, 3, 45];
const maximus = Math.max(...arr);
```

- `...arr` returns an unpacked array
- the spread operator only works in-place, like in an argument to a function or in an array literal
- **Template literals** allow you to create multi-line strings 
- The `${variable}` syntax is a placeholder
- **Object Literal**: ???
- Class, constructor, new, setter, getter???
- **Module** script: exporting parts of a file for use in one or more other files, and importing the parts you need, where you need them 
- You need to create a script in your HTML document with a type of module: `<script type="module" src="filename.js"></script>`
- Use the keywords `export` and `import` - 
- When you export a variable or function, you can import it in another file and use it without having to rewrite the code 
- Export multiple things: `export { thing1, thing2 };`
- `import` allows you to choose which parts of a file or module to load: `import { add } from './math_functions.js'; `
- Use `import *` to import everything from a file - 
- Create an export fallback with `export default` - omit the curly brackets when you import a default export
- SKIPPED PROMISES - DO NOT GET REST AND SPREAD

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<h2 id="regex" align="center">RegEx</h2>

Capture Groups, Lookaheads
- 

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<h2 id="debugging" align="center">Debugging</h2>

`console.log()`, `typeof`, ONE OFF ERRORS, INDEXING, INFINITE LOOPS
- JavaScript recognizes six primitive (immutable) data types: Boolean, Null, Undefined, Number, String, and Symbol (new with ES6) and one type for mutable items: Object. Note that in JavaScript, arrays are technically a type of object
- Almost every value on its own in JavaScript evaluates to true, except what are known as the "falsy" values: `false`, `0`, `""`, `NaN`, `undefined`, and `null`
- Use of assignment operator (`=`) instead of equality operator (`==` and `===`)
- Thins *VS Code* catches: 1) typos of function and Variables names, 2) unclosed parentheses, bracket, braces, and quotes, 3) mixed usage of single and double quotes, 4) 
- Things VS Code does not catch: 1) open and closing parentheses after a Function call, 2) argumants passed in the wrong order. 3) Off by one errors

<h2 id="data-structures" align="center">Data Structures</h2>

Window object:
- close, window.outerheight, window.outerwidth, innerHeight and innerWidth, window.scrollY, window.scrollX, window.location, window.location.search, window.location.href, window.location.reload(), window.history.go(-2), window.history.length, window.navigator, window.navigator.geolocation.getCurrentPosition, navigator.language

<h2 id="basic-algorithms" align="center">Basic Algorithms</h2>



<h2 id="oop" align="center">OOP</h2>

THIS, PROTOTYPE, CONSTRUCTOR, INHERITANCE

<h2 id="functional-programming" align="center">Functional Programming</h2>

MAP, FILTER, REDUCE, SORT, SPLIT

REMEMBER LWC 10 DAYS OF JS


# The DOM 

something here...

<h2 id="dom-elements" align="center">DOM Elements</h2>

something here...

### DOM Node Properties

- attributes — Returns a live collection of all attributes registered to an element
- baseURI — Provides the absolute base URL of an HTML element
- childNodes — Gives a collection of an element’s child nodes
- firstChild — Returns the first child node of an element
- lastChild — The last child node of an element
- nextSibling — Gives you the next node at the same node tree level
- nodeName —Returns the name of a node
- nodeType —  Returns the type of a node
- nodeValue — Sets or returns the value of a node
- ownerDocument — The top-level document object for this node
- parentNode — Returns the parent node of an element
- previousSibling — Returns the node immediately preceding the current one
- textContent — Sets or returns the textual content of a node and its descendants

### DOM Node Methods

- appendChild() — Adds a new child node to an element as the last child node
- cloneNode() — Clones an HTML element
- compareDocumentPosition() — Compares the document position of two elements
- getFeature() — Returns an object which implements the APIs of a specified feature
- hasAttributes() — Returns true if an element has any attributes, otherwise false
- hasChildNodes() — Returns true if an element has any child nodes, otherwise false
- insertBefore() — Inserts a new child node before a specified, existing child node
- isEqualNode() — Checks if two elements are equal
- isSameNode() — Checks if two elements are the same node
- isSupported() — Returns true if a specified feature is supported on the element
- removeChild() — Removes a child node from an element
- replaceChild() — Replaces a child node in an element

### DOM Element Methods

- getAttribute() — Returns the specified attribute value of an element node
- getAttributeNode() — Gets the specified attribute node
- getElementsByTagName() — Provides a collection of all child elements with the specified tag name
- hasAttribute() — Returns true if an element has any attributes, otherwise false
- removeAttribute() — Removes a specified attribute from an element
- setAttribute() — Sets or changes the specified attribute to a specified value

<h2 id="javaScript-events" align="center">JavaScript Events</h2>

Events are things that can happen to HTML elements and are performed by the user. The programming language can listen for these events and trigger actions in the code. No JavaScript cheat sheet would be complete without them.

### Mouse
- onclick — The event occurs when the user clicks on an element
- oncontextmenu — User right-clicks on an element to open a context menu
- ondblclick — The user double-clicks on an element
- onmousedown — User presses a mouse button over an element
- onmouseenter — The pointer moves onto an element
- onmouseleave — Pointer moves out of an element
- onmousemove — The pointer is moving while it is over an element
- onmouseover — When the pointer is moved onto an element or one of its children
- onmouseout — User moves the mouse pointer out of an element or one of its children
- onmouseup — The user releases a mouse button while over an element

### Keyboard

- onkeydown — When the user is pressing a key down
- onkeypress — The moment the user starts pressing a key
- onkeyup — The user releases a key

### Frame

- onabort — The loading of a media is aborted
- onbeforeunload — Event occurs before the document is about to be unloaded
- onerror — An error occurs while loading an external file
- onhashchange — There have been changes to the anchor part of a URL
- onload — When an object has loaded
- onpagehide — The user navigates away from a webpage
- onpageshow — When the user navigates to a webpage
- onresize — The document view is resized
- onscroll — An element’s scrollbar is being scrolled
- onunload — Event occurs when a page has unloaded

### Form 

- onblur — When an element loses focus
- onchange — The content of a form element changes (for <input>, <select> and <textarea>)
- onfocus — An element gets focus
- onfocusin — When an element is about to get focus
- onfocusout — The element is about to lose focus
- oninput — User input on an element
- oninvalid — An element is invalid
- onreset — A form is reset
- onsearch — The user writes something in a search field (for <input="search">)
- onselect — The user selects some text (for <input> and <textarea>)
- onsubmit — A form is submitted

### Drag

- ondrag — An element is dragged
- ondragend — The user has finished dragging the element
- ondragenter — The dragged element enters a drop target
- ondragleave — A dragged element leaves the drop target
- ondragover — The dragged element is on top of the drop target
- ondragstart — User starts to drag an element
- ondrop — Dragged element is dropped on the drop target

### Clipboard

- oncopy — User copies the content of an element
- oncut — The user cuts an element’s content
- onpaste — A user pastes the content in an element

### Media

- onabort — Media loading is aborted
- oncanplay — The browser can start playing media (e.g. a file has buffered enough)
- oncanplaythrough — The browser can play through media without stopping
- ondurationchange — The duration of the media changes
- onended — The media has reached its end
- onerror — Happens when an error occurs while loading an external file
- onloadeddata — Media data is loaded
- onloadedmetadata — Metadata (like dimensions and duration) are loaded
- onloadstart —  The browser starts looking for specified media
- onpause — Media is paused either by the user or automatically
- onplay — The media has been started or is no longer paused
- onplaying — Media is playing after having been paused or stopped for buffering
- onprogress — The browser is in the process of downloading the media
- onratechange — The playing speed of the media changes
- onseeked — User is finished moving/skipping to a new position in the media
- onseeking — The user starts moving/skipping
- onstalled — The browser is trying to load the media but it is not available
- onsuspend — The browser is intentionally not loading media
- ontimeupdate — The playing position has changed (e.g. because of fast forward)
- onvolumechange — Media volume has changed (including mute)
- onwaiting — Media paused but expected to resume (for example, buffering)

### Animation

- animationend — A CSS animation is complete
- animationiteration — CSS animation is repeated
- animationstart — CSS animation has started

### Other Events

- transitionend — Fired when a CSS transition has completed
- onmessage — A message is received through the event source
- onoffline — The browser starts to work offline
- ononline — The browser starts to work online
- onpopstate — When the window’s history changes
- onshow — A <menu> element is shown as a context menu
- onstorage — A Web Storage area is updated
- ontoggle — The user opens or closes the <details> element
- onwheel — Mouse wheel rolls up or down over an element
- ontouchcancel — Screen-touch is interrupted
- ontouchend — User’s finger is removed from a touch-screen
- ontouchmove — A finger is dragged across the screen
- ontouchstart — A finger is placed on the touch-screen

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<h2 id="errors" align="center">Errors</h2>

When working with JavaScript, different errors can occur. There are several ways of handling them:
- try — Lets you define a block of code to test for errors
- catch — Set up a block of code to execute in case of an error
- throw — Create custom error messages instead of the standard JavaScript errors
- finally — Lets you execute code, after try and catch, regardless of the result

Error Name Values
- JavaScript also has a built-in error object. It has two properties:
- name — Sets or returns the error name
- message — Sets or returns an error message in a string from

The error property can return six different values as its name:
- EvalError — An error has occurred in the eval() function
- RangeError — A number is “out of range”
- ReferenceError — An illegal reference has occurred
- SyntaxError — A syntax error has occurred
- TypeError — A type error has occurred
- URIError — An encodeURI() error has occurred

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

Code examples showing results with `console.log()` for `var`, `let`, and `const`:

```js
// Global scope:
var test1; // Declared, NOT assigned a value: undefined (Ok, not recommended)
test1 = 1; // Assigned a value: 1 (Ok)
test1 = 10; // Reassigned value: 10 (Ok)
var test1 = 1; // Declared with a value: 1 (Ok)
var test1 = 10; // Redeclared and reassigned value: 10 (MAJOR ISSUE!)

let test2; // Declared, NOT assigned a value: undefined (Ok, not recommended)
test2 = 2; // Assigned a value: 2 (Ok)
test2 = 20; // Reassigned value: 20 (Ok)
let test2 = 2; // Uncaught SyntaxError
let test2 = 20; // Uncaught SyntaxError
```