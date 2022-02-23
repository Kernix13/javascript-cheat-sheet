# Notes: Basic JavaScript & ES6

## VARIABLES

- It is common to initialize a var to an initial value in the same line as it is declared, e.g. `let a = 0;`
- When JS variables are declared, they have an initial value of `undefined`. If you do a mathematical operation on an `undefined` variable your result will be `NaN`
- `+`, `-`, `*`, `/`, `i++`, `i--`, 
- Remainder operator `%` - gives the remainder of the division of two numbers
- Escaping: use a backslash (`\`) in front of the quote in a string: `\'` or `\"`
- Bracket notation is a way to get a character at a specific index within a string: `string[index]`
- Bracket notation to find the Nth-to-last character: `string.length - n`, where `n` is a # from end
- String immutability: they cannot be altered once created

## ARRAYS

- Bracket notation to access & modify array data: `[0]`
- Unlike strings, the entries of arrays are mutable and can be changed
- Access multi-dimensional arrays  with indexes:

`var arr = [ [1, 2], [2, 3], [ [3, 4], 5] ] arr[2][0][1] = 4`

- Manipulate arrays with `push()` = append / add, takes one or more parameters and "pushes" them onto the **end** of the array|
- Manipulate arrays with `unshift()` = add elements in front of the array, takes one or more parameters and adds them onto the **beginning** of the array
- Manipulate arrays with `pop()` = remove a value off of the **end** (last item) of an array |
- Manipulate arrays with `shift()` = removes the **first** item

## FUNCTIONS AND RETURN

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

## CONDITIONAL LOGIC AND COMPARISON

- `Boolean` and `if` statements: 

`if (boolean condition) { code if true}`

- if no `<` or `>` or other comparison symbol is used, the statement is considered `true` if the value is anything other than 0
- Comparison operators: `<`, `>`, `<=`, `>=`, `!=`, `==`, `!==`, `===`
- Equality operator (`==`) vs. strict equality operator (`===`): the strict equality operator compares both the data type and value
- The same is true for the inequality operators: `!=` and `!==`
- You can determine the type of a variable or a value with the typeof operator
- And operator:  to test more than one thing at a time. The logical and operator (`&&`) returns `true` if and only if the operands to the left and right of it are true
- Or operator: The logical or operator (`||`) returns `true` if either of the operands is true

### IF, ELSE, ELSE IF, SWITCH

- `else` statements: used when the condition in an `if` statement is not met and an alternate block of code is executed
- `else if` statements:  If you have multiple conditions that need to be addressed, you can chain `if` statements together with `else if` statements; be careful of what statement comes first
- `switch` statements: tests a value and can have many `case` statements which define various possible values. Statements are executed from the first matched `case` value until a `break` is encountered
- `case` statements are tested with strick equality (`===`): `switch(check value(s)) {case value: varname = something; break; next case check…}`
- `default` means `else` in a `switch` statement – you can also have multiple cases before a `break`

### OBJECTS

- instead of using indexes to access and modify their data, you access the data in objects through what are called `properties`
- Properties are often `strings` - you can omit the quotes for single-word string properties; property names with spaces in them must be in quotes
- Objects can be thought of as a `key`/`value` storage, like a dictionary `{word: definition}`
- There are two ways to access the properties of an object: dot notation (`.`) and bracket notation (`[]`), similar to an array. 
- Dot notation is what you use when you know the name of the property you're trying to access
- If the property of the object you are trying to access has a space in its name, you will need to use bracket notation
- USe dot or bracket notation to update a property
- Testing objects for properties: use the `.hasOwnProperty(propname)` method of objects to determine if that object has the given property name
- The sub-properties of objects can be accessed by chaining together the dot or bracket notation

### LOOPS 

- `while` loop: runs while a specified condition is true and stops once that condition is no longer true
- `for` loop: The most common type of JavaScript loop is called a `for` loop because it runs for a specific number of times
  - `for (a; b; c) { }`, where a is the intialization statement, b is the condition statement, and c is the final expression
  - A common task in JavaScript is to iterate through the contents of an array. One way to do that is with a `for` loop
  - Accumulators: The expression += is an just abreviation of x = x + i
- Nested `for` loops: arrays inside another array
- `do...while` loops: it will first `do` one pass of the code inside the loop no matter what, and then continue to run the loop `while` the specified condition evaluates to `true`
- Recursion: ???

### ES6

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

| something  | var  | let     | const  |
| :--------  | :----: | :---: | :----: |
| Scope      | Global | Block | Block |
| Overwrite? | Yes    | No    | No    |
| Updated?   | Yes    | Yes   | No    |
| Redeclared? | Yes  | No    | No    |
| Hoisted?   | Yes    | Yes   | Yes   | 
| initialized? | undefined | No | No  |

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

### REGEX

CAPTURE GROUPS, LOOKAHEADS
- 

# Notes: 

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



## Tips & Tricks

Tips & tricks
'=== better than ==
falsy
constructors
IIFE
math.floor(math.random
trim()
push.apply()
splice instead of delete
num.toFixed(#)
setTimeout() 
setInterval()
Avoid using try-catch-finally inside a loop
Set timeouts to XMLHttpRequests

https://dev.to/techygeeky/top-20-javascript-tips-and-tricks-to-increase-your-speed-and-efficiency-283g
Declare and Initialize Arrays
reduce!
Sorting Array of String, Numbers or Objects
filter falsy values out of an array





https://dev.to/worldindev/8-javascript-tips-tricks-that-no-one-teaches-24g1
https://levelup.gitconnected.com/15-magical-javascript-tips-for-every-web-developer-3301feb0b70c
https://www.codelivly.com/8-javascript-tips-tricks-that-no-one-teaches/
https://blog.greenroots.info/my-favorite-javascript-tips-and-tricks
https://www.lflus.com/useful-javascript-tips-and-tricks-for-your-browser/
https://www.microverse.org/blog/10-javascript-tips-make-you-a-better-developer
https://www.codemotion.com/magazine/frontend/javascript/javascript-speed-up-tips/
https://samwalpole.com/my-top-5-javascript-tips-and-tricks-for-writing-cleaner-code
https://blog.yogeshchavan.dev/super-useful-tips-and-tricks-for-javascript-developers
https://www.jesssica.tech/post/Javascript-Tips-and-Tricks
https://www.bytesized.xyz/three-es6-javascript-tricks-you-should-know/
https://www.freecodecamp.org/news/how-to-learn-javascript-a-little-faster/
https://pratapsharma.in/javascript-tips-and-tricks
