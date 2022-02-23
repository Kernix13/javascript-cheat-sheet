# Notes: Basic JavaScript & ES6

Notes on specifics in README and other important notes and definitions

## Table of Contents

1. [Tips and Tricks](#tips-and-tricks)
1. [Terms]{#terms}
1. [Variables](#variables)
1. [Arrays and Strings](#arrays-and-strings)
   1. [Common Methods unique to Strings](#common-methods-unique-to-strings)
   1. [Common Methods unique to Arrays](#common-methods-unique-to-arrays)
   1. [High Order Array Methods](#high-order-array-methods)
   1. [Array Methods Notes](#array-methods-notes)
   1. [String Methods Notes](#string-methods-notes)
1. [Numbers](#numbers)
1. [Dates](#dates)
1. [Objects](#objects)
1. [Functions and Return](#functions-and-return)
1. [Conditional Logic](#conditional-logic)
1. If, Else, Else If, Switch
1. Loops
1. ES6
1. RegEx

## Tips and Tricks

- '=== better than ==
- filter falsy values out of an array
- constructors
- IIFE
- math.floor(math.random
- trim()
- push.apply()
- splice instead of delete
- num.toFixed(#)
- setTimeout() 
- setInterval()
- Avoid using try-catch-finally inside a loop
- Set timeouts to XMLHttpRequests
- Declare and Initialize Arrays
- reduce!
- Sorting Array of String, Numbers or Objects
- destructuring assignment syntax
- check performance with `performance.now()`
- template literals with variables
- ways to shorten if statements: ternary, &&, 
- comma operator
- spread operator to merge 2 objects
- undefined vs null
- arr.slice(-1) to get last item
- use `array.slice(0, #);` to truncate an array
- Destructuring Assignment for objects and arrays
- short circuit operators
- primitive types: number, string, boolean, symbol, null, and undefined
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
- https://github.com/wilfredinni/javascript-cheatsheet
- https://github.com/alhassy/JavaScriptCheatSheet 

## Terms

- arguments: 
- parameters: 
- arity: 
- arrow function: ( ) =>
- callback function: 
- currentTarget: 
- currying: 
- error:
- event bubbling: 
- event delegation: 
- exponential operator: 
- falsy = [false, 0, "", NaN, undefined, null]
- function statement vs var function: 
- hoisting: 
- if, else, else if, switch() case break default:
- IIFE: 
- inheritance:
- JSON.parse()
- JSON.stringify()
- Loops: for, while, do while, for in, for of
- new Date(): 
- parse: 
- parseInt:
- rest parameter
- spread operator
- recursion: 
- remainder %
- Rest Parameter: (...theArgs)
- scope: 
- Spread Operator: 
- target: 
- "use strict": 
- `${variable}`: 

## Variables

- It is common to initialize a var to an initial value in the same line as it is declared, e.g. `let a = 0;`
- When JS variables are declared, they have an initial value of `undefined`. If you do a mathematical operation on an `undefined` variable your result will be `NaN`
- `+`, `-`, `*`, `/`, `i++`, `i--`, 
- Remainder operator `%` - gives the remainder of the division of two numbers
- Escaping: use a backslash (`\`) in front of the quote in a string: `\'` or `\"`
- Bracket notation is a way to get a character at a specific index within a string: `string[index]`
- Bracket notation to find the Nth-to-last character: `string.length - n`, where `n` is a # from end
- String immutability: they cannot be altered once created

## Arrays and Strings

- Bracket notation to access & modify array data: `[0]`
- Unlike strings, the entries of arrays are mutable and can be changed
- Access multi-dimensional arrays  with indexes:

`var arr = [ [1, 2], [2, 3], [ [3, 4], 5] ] arr[2][0][1] = 4`

- Manipulate arrays with `push()` = append / add, takes one or more parameters and "pushes" them onto the **end** of the array|
- Manipulate arrays with `unshift()` = add elements in front of the array, takes one or more parameters and adds them onto the **beginning** of the array
- Manipulate arrays with `pop()` = remove a value off of the **end** (last item) of an array |
- Manipulate arrays with `shift()` = removes the **first** item

There are methods in common to both arrays and strings so I am combining them for more easily visualixe them. Check out the following MDN links:

- [MDN String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)
- [MDN Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)


Strings and Arrays: Same Methods, Same Effect n detail:
- `slice()`, str | Extracts a section of a string and returns a new string
- `slice()`, arr | Extracts a section of the calling array and returns a new array
- `concat()`, str | Joins two or more strings and returns the new string
  - Alternate: `str1 + str2`
- `concat()`, arr | Joins two or more arrays and returns a copy of the joined arrays
- `includes()`, str | Check if an string contains the specified string 
  - Alternate: `includes(searchVal, beginIndex)`
- `includes()`, arr | Check if an array contains the specified element
  - Alternate: includes(searchVal, beginIndex)` 
- `endsWith()`, str | Checks whether a string ends with the characters of a given string 
  - Alternate: `endsWith(searchString, length)`
- `indexOf()`, str | returns the index of the first occurrence of the specified substring
  - Alternate: indexOf(searchString, pos)
- `indexOf()`, arr | returns the first index at which a given element can be found
  - Alternate: `indexOf(searchVal, pos)`
- `lastIndexOf()`, str | returns the index of the last occurrence of the specified substring: 
  - Alternate: lastIndexOf(searchStr, fromIndex)
- `lastIndexOf()`, arr | returns the index of the last occurrence of the specified value
  - Alternate: `lastIndexOf(searchVal, fromIndex)`

Code examples:

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

Strings and Arrays: Different Methods, Same Effect (Additional notes):
- `arr.at()`: Accepts negative #’s, which counts from back
- `str.substring()`: returns the part of the string between the start and end indexes, or to the end of the string
  - Alernate: `substring(indexStart, indexEnd)`
- `arr.splice()`: changes the contents of an array by removing or replacing existing elements and/or adding new elements
  - Alternate: `splice(start, deleteCount)`

| join()  | Joins all elements of an array into a string | arr.join() | 

Strings and Arrays: Different Methods, Opposite Effect (Additional notes):
- `str.split()` alternate code: `split(separator)`, `split(separator, limit)`
- `arr.join()` alternate code: `join(separator)`
- These two are used in unison, first to split a string, then to join


### Common Methods unique to Strings

- `toLowerCase()`: Converts string to lowercase
- `toUpperCase()`: Converts string to uppercase
- `trim()`: removes whitespace from both ends of a string and returns a new string, without modifying the original string
- `test()`:	Though, not a string method, it executes a search for a match between a regular expression and a specified string. Returns true or false: `test(str)`
- `match()`: Used to match regular expression against a string; retrieves the result of matching a string against a regular expression: `match(RegEx)`
- `replace()`: returns a new string with some or all matches of a pattern replaced by a replacement. The pattern can be a string or a RegExp, and the replacement can be a string or a function to be called for each match. If pattern is a string, only the first occurrence will be replaced: `replace(regexp, newSubstr)`, `replace(regexp, replacerFunction)`, `replace(substr, newSubstr)`, or `replace(substr, replacerFunction)`

### Common Methods unique to Arrays

- `every()`: Checks if **every** element in an array pass a test, returns boolean. This have a number of variations for the syntax. Check the MDN doc [Array.prototype.every](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every).
- `some()`: tests whether at least one element in the array passes the test implemented by the provided function. It returns true if, in the array, it finds an element for which the provided function returns true; otherwise it returns false. It doesn't modify the array. This have a number of variations for the syntax. Check the MDN doc [Array.prototype.some](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some).
- `push()`: adds one or more elements to the end of an array and returns the new length of the array: 'push(elem1, elem2, ...)`
- `unshift()`: adds one or more elements to the beginning of an array and returns the new length of the array: `unshift(elem1, elem2, ...)`
- `shift()`: removes the first element from an array and returns that removed element. This method changes the length of the array (no arguments)
- `pop()`: removes the last element from an array and returns that element. This method changes the length of the array (no arguments)

### High Order Array Methods

- `filter()`: ?
- `map()`: ?
- `forEach()`: function to run on each item of an array, common in `for` loops
- `reduce()`: ?
- `sort()`: self-explanatory
- `reverse()`: reverse sort (why use?)
- `find()`: ?
- `every()`: Above
- `some()`: Above
- `includes()`: Above
- 

### Array Methods Notes

- `.length`: used often in `for` loops
- arr.[index]: to return a value at a specific index

Returns Boolean: `every()`, `includes()`, `some()`

Returns String: `join()`, `toString()`

Anything: `forEach()`

Returns Array: `filter()`, `map()`, `concat()`

Return Value/Position: `find()`, `indexOf()` (compare with `lastIndexOf()`, `reduce()`

Add, remove, sort: pop()`, shift()`, `push()`, `unshift()`, `slice(start, end)`, `splice()`, `reverse()`, `sort()`


## String Methods Notes

There are many different ways to work with strings:

- `charCodeAt(index)` — Gives you the Unicode of a character at that position
- `fromCharCode(num1, num2, ...)` — Returns a string created from the specified sequence of UTF-16 code units
- `valueOf()` — Returns the primitive value (that has no properties or methods) of a string object

## Numbers

Number Methods

toExponential() — Returns the string with a rounded number written as exponential notation
toFixed() — Returns the string of a number with a specified number of decimals
toPrecision() — String of a number written with a specified length
toString() — Returns a number as a string
valueOf() — Returns a number as a number

## Dates

Pulling Date and Time Values
getDate() — Get the day of the month as a number (1-31)
getDay() —  The weekday as a number (0-6)
getFullYear() — Year as a four-digit number (yyyy)
getHours() — Get the hour (0-23)
getMilliseconds() — The millisecond (0-999)
getMinutes() — Get the minute (0-59)
getMonth() —  Month as a number (0-11)
getSeconds() — Get the second (0-59)
getTime() — Get the milliseconds since January 1, 1970
getUTCDate() — The day (date) of the month in the specified date according to universal time (also available for day, month, full year, hours, minutes etc.)
parse — Parses a string representation of a date and returns the number of milliseconds since January 1, 1970

Set Part of a Date
setDate() — Set the day as a number (1-31)
setFullYear() — Sets the year (optionally month and day)
setHours() — Set the hour (0-23)
setMilliseconds() — Set milliseconds (0-999)
setMinutes() — Sets the minutes (0-59)
setMonth() — Set the month (0-11)
setSeconds() — Sets the seconds (0-59)
setTime() — Set the time (milliseconds since January 1, 1970)
setUTCDate() — Sets the day of the month for a specified date according to universal time (also available for day, month, full year, hours, minutes etc.)

## Objects

- instead of using indexes to access and modify their data, you access the data in objects through what are called `properties`
- Properties are often `strings` - you can omit the quotes for single-word string properties; property names with spaces in them must be in quotes
- Objects can be thought of as a `key`/`value` storage, like a dictionary `{word: definition}`
- There are two ways to access the properties of an object: dot notation (`.`) and bracket notation (`[]`), similar to an array. 
- Dot notation is what you use when you know the name of the property you're trying to access
- If the property of the object you are trying to access has a space in its name, you will need to use bracket notation
- USe dot or bracket notation to update a property
- Testing objects for properties: use the `.hasOwnProperty(propname)` method of objects to determine if that object has the given property name
- The sub-properties of objects can be accessed by chaining together the dot or bracket notation

Defining getters and setters
A getter is a method that gets the value of a specific property. A setter is a method that sets the value of a specific property. You can define getters and setters on any predefined core object or user-defined object that supports the addition of new properties.

`Object.prototype.toString()`:	Returns a string representation of the object.
Object.prototype.valueOf():	Returns the primitive value of the specified object.
Object.prototype.hasOwnProperty():	Returns a boolean indicating whether an object contains the specified property as a direct property of that object and not inherited through the prototype chain.

There are three native ways to list/traverse object properties:

for...in loops. This method traverses all enumerable properties of an object and its prototype chain.
Object.keys(o). This method returns an array with all the own (not in the prototype chain) enumerable properties' names ("keys") of an object o.
Object.getOwnPropertyNames(o). This method returns an array containing all own properties' names (enumerable or not) of an object o.

`Object.keys()`:	Returns an array containing the names of all of the given object's own enumerable string properties.
`Object.values()`:	Returns an array containing the values that correspond to all of a given object's own enumerable string properties

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects

## Functions and Return

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

## Conditional Logic

- `Boolean` and `if` statements: 

`if (boolean condition) { code if true}`

- if no `<` or `>` or other comparison symbol is used, the statement is considered `true` if the value is anything other than 0
- Comparison operators: `<`, `>`, `<=`, `>=`, `!=`, `==`, `!==`, `===`
- Equality operator (`==`) vs. strict equality operator (`===`): the strict equality operator compares both the data type and value
- The same is true for the inequality operators: `!=` and `!==`
- You can determine the type of a variable or a value with the typeof operator
- And operator:  to test more than one thing at a time. The logical and operator (`&&`) returns `true` if and only if the operands to the left and right of it are true
- Or operator: The logical or operator (`||`) returns `true` if either of the operands is true
- Ternary

## If, Else, Else If, Switch

- `else` statements: used when the condition in an `if` statement is not met and an alternate block of code is executed
- `else if` statements:  If you have multiple conditions that need to be addressed, you can chain `if` statements together with `else if` statements; be careful of what statement comes first
- `switch` statements: tests a value and can have many `case` statements which define various possible values. Statements are executed from the first matched `case` value until a `break` is encountered
- `case` statements are tested with strick equality (`===`): `switch(check value(s)) {case value: varname = something; break; next case check…}`
- `default` means `else` in a `switch` statement – you can also have multiple cases before a `break`

## Loops 

- `while` loop: runs while a specified condition is true and stops once that condition is no longer true
- `for` loop: The most common type of JavaScript loop is called a `for` loop because it runs for a specific number of times
  - `for (a; b; c) { }`, where a is the intialization statement, b is the condition statement, and c is the final expression
  - A common task in JavaScript is to iterate through the contents of an array. One way to do that is with a `for` loop
  - Accumulators: The expression += is an just abreviation of x = x + i
- Nested `for` loops: arrays inside another array
- `do...while` loops: it will first `do` one pass of the code inside the loop no matter what, and then continue to run the loop `while` the specified condition evaluates to `true`
- Conditional (ternary) operator: 	a ? b : c	
- Recursion: ???

## ES6

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
- `let` vs `var`: `var` can be overwritten, `let` cannot
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
- prevent object mutation: To ensure your data doesn't change, use the function `Object.freeze` to prevent data mutation. Once frozen, you can no longer add, update, or delete properties from it


**Arrow functions, Rest parameter, Spread operator, Template literals**:

- inline functions - When there is no function body, and only a return value, arrow function syntax allows you to omit the keyword `return` as well as the brackets surrounding the code 
- If an arrow function has a single parameter, the parentheses enclosing the parameter may be omitted
- Default parameters?
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

## RegEx

CAPTURE GROUPS, LOOKAHEADS
- 

## DEBUGGING - skip

`console.log()`, `typeof`, ONE OFF ERRORS, INDEXING, INFINITE LOOPS
- JavaScript recognizes six primitive (immutable) data types: Boolean, Null, Undefined, Number, String, and Symbol (new with ES6) and one type for mutable items: Object. Note that in JavaScript, arrays are technically a type of object
- Almost every value on its own in JavaScript evaluates to true, except what are known as the "falsy" values: `false`, `0`, `""`, `NaN`, `undefined`, and `null`
- Use of assignment operator (`=`) instead of equality operator (`==` and `===`)
- Thins *VS Code* catches: 1) typos of function and ariables names, 2) unclosed parentheses, bracket, braces, and quotes, 3) mixed usage of single and double quotes, 4) 
- Things VS Code does not catch: 1) open and closing parentheses after a Function call, 2) argumants passed in the wrong order. 3) Off by one errors

## DATA STRUCTURES

- 

## BASIC ALGORITHMS

### PRACTICE

## OOP

### THIS, PROTOTYPE, CONSTRUCTOR, INHERITANCE

## FUNCTIONAL PROGRAMMING

### MAP, FILTER, REDUCE, SORT, SPLIT

REMEMBER LWC 10 DAYS OF JS

## Strings


## Numbers


## DOM Nodes

Node Properties


Node Methods


## DOM Elements

Element Methods

## Errors

## Events

# DOM Events

## JavaScript Events
Events are things that can happen to HTML elements and are performed by the user. The programming language can listen for these events and trigger actions in the code. No JavaScript cheat sheet would be complete without them.

Mouse
onclick — The event occurs when the user clicks on an element
oncontextmenu — User right-clicks on an element to open a context menu
ondblclick — The user double-clicks on an element
onmousedown — User presses a mouse button over an element
onmouseenter — The pointer moves onto an element
onmouseleave — Pointer moves out of an element
onmousemove — The pointer is moving while it is over an element
onmouseover — When the pointer is moved onto an element or one of its children
onmouseout — User moves the mouse pointer out of an element or one of its children
onmouseup — The user releases a mouse button while over an element
Keyboard
onkeydown — When the user is pressing a key down
onkeypress — The moment the user starts pressing a key
onkeyup — The user releases a key

Frame
onabort — The loading of a media is aborted
onbeforeunload — Event occurs before the document is about to be unloaded
onerror — An error occurs while loading an external file
onhashchange — There have been changes to the anchor part of a URL
onload — When an object has loaded
onpagehide — The user navigates away from a webpage
onpageshow — When the user navigates to a webpage
onresize — The document view is resized
onscroll — An element’s scrollbar is being scrolled
onunload — Event occurs when a page has unloaded

Form
onblur — When an element loses focus
onchange — The content of a form element changes (for <input>, <select> and <textarea>)
onfocus — An element gets focus
onfocusin — When an element is about to get focus
onfocusout — The element is about to lose focus
oninput — User input on an element
oninvalid — An element is invalid
onreset — A form is reset
onsearch — The user writes something in a search field (for <input="search">)
onselect — The user selects some text (for <input> and <textarea>)
onsubmit — A form is submitted

Drag
ondrag — An element is dragged
ondragend — The user has finished dragging the element
ondragenter — The dragged element enters a drop target
ondragleave — A dragged element leaves the drop target
ondragover — The dragged element is on top of the drop target
ondragstart — User starts to drag an element
ondrop — Dragged element is dropped on the drop target
Clipboard
oncopy — User copies the content of an element
oncut — The user cuts an element’s content
onpaste — A user pastes the content in an element

Media
onabort — Media loading is aborted
oncanplay — The browser can start playing media (e.g. a file has buffered enough)
oncanplaythrough — The browser can play through media without stopping
ondurationchange — The duration of the media changes
onended — The media has reached its end
onerror — Happens when an error occurs while loading an external file
onloadeddata — Media data is loaded
onloadedmetadata — Metadata (like dimensions and duration) are loaded
onloadstart —  The browser starts looking for specified media
onpause — Media is paused either by the user or automatically
onplay — The media has been started or is no longer paused
onplaying — Media is playing after having been paused or stopped for buffering
onprogress — The browser is in the process of downloading the media
onratechange — The playing speed of the media changes
onseeked — User is finished moving/skipping to a new position in the media
onseeking — The user starts moving/skipping
onstalled — The browser is trying to load the media but it is not available
onsuspend — The browser is intentionally not loading media
ontimeupdate — The playing position has changed (e.g. because of fast forward)
onvolumechange — Media volume has changed (including mute)
onwaiting — Media paused but expected to resume (for example, buffering)
Animation
animationend — A CSS animation is complete
animationiteration — CSS animation is repeated
animationstart — CSS animation has started

Other
transitionend — Fired when a CSS transition has completed
onmessage — A message is received through the event source
onoffline — The browser starts to work offline
ononline — The browser starts to work online
onpopstate — When the window’s history changes
onshow — A <menu> element is shown as a context menu
onstorage — A Web Storage area is updated
ontoggle — The user opens or closes the <details> element
onwheel — Mouse wheel rolls up or down over an element
ontouchcancel — Screen-touch is interrupted
ontouchend — User’s finger is removed from a touch-screen
ontouchmove — A finger is dragged across the screen
ontouchstart — A finger is placed on the touch-screen

# Errors

Errors
When working with JavaScript, different errors can occur. There are several ways of handling them:

try — Lets you define a block of code to test for errors
catch — Set up a block of code to execute in case of an error
throw — Create custom error messages instead of the standard JavaScript errors
finally — Lets you execute code, after try and catch, regardless of the result

Error Name Values
JavaScript also has a built-in error object. It has two properties:

name — Sets or returns the error name
message — Sets or returns an error message in a string from
The error property can return six different values as its name:

EvalError — An error has occurred in the eval() function
RangeError — A number is “out of range”
ReferenceError — An illegal reference has occurred
SyntaxError — A syntax error has occurred
TypeError — A type error has occurred
URIError — An encodeURI() error has occurred

# DOM

## DOM Node Properties

attributes — Returns a live collection of all attributes registered to an element
baseURI — Provides the absolute base URL of an HTML element
childNodes — Gives a collection of an element’s child nodes
firstChild — Returns the first child node of an element
lastChild — The last child node of an element
nextSibling — Gives you the next node at the same node tree level
nodeName —Returns the name of a node
nodeType —  Returns the type of a node
nodeValue — Sets or returns the value of a node
ownerDocument — The top-level document object for this node
parentNode — Returns the parent node of an element
previousSibling — Returns the node immediately preceding the current one
textContent — Sets or returns the textual content of a node and its descendants

## DOM Node Methods

appendChild() — Adds a new child node to an element as the last child node
cloneNode() — Clones an HTML element
compareDocumentPosition() — Compares the document position of two elements
getFeature() — Returns an object which implements the APIs of a specified feature
hasAttributes() — Returns true if an element has any attributes, otherwise false
hasChildNodes() — Returns true if an element has any child nodes, otherwise false
insertBefore() — Inserts a new child node before a specified, existing child node
isEqualNode() — Checks if two elements are equal
isSameNode() — Checks if two elements are the same node
isSupported() — Returns true if a specified feature is supported on the element
removeChild() — Removes a child node from an element
replaceChild() — Replaces a child node in an element

## DOM Element Methods

getAttribute() — Returns the specified attribute value of an element node
getAttributeNode() — Gets the specified attribute node
getElementsByTagName() — Provides a collection of all child elements with the specified tag name
hasAttribute() — Returns true if an element has any attributes, otherwise false
removeAttribute() — Removes a specified attribute from an element
setAttribute() — Sets or changes the specified attribute to a specified value