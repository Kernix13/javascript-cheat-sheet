# VANILLA JAVASCRIPT CHEAT SHEET

> This file is really good though the notes section is a little sloppy. The tables are the best part of it. Also, string-array-examples.md is also REALLY good! All the other files are work-in-progress (**as of 3/10/2022**).

This is not an all-inclusive list of every possible JavaScript method, property, etc. This file has tables of comparisons for quick reference. Notes on elements in the tables are at the bottom of the file.

- `conditionals-examples.md`: Mostly done
- `function-examples.md`: Good but need more notes and examples or Local storage, Event delegation,  Promises, and Recursion.
- `loop-examples.md`: still raw - need more examples
- `notes.md`: various important notes on anything and everything (REALLY MESSY!)
- `number-date-examples.md`: Good but need to learn how to format dates, unless my tests in CodePen are the problem. Try local file...
- `object-examples.md`: Mostly complete
- `practical-examples.md`: Work in process - not much here yet
- `regex-examples.md`: this is pretty good but not finished
- `string-array-examples.md`: The **_BEST_** file by far!

<div id="back-to-top"></div>

## Table of Contents

1. Table Comparisons
   1. [Data types](#data-types)
   1. [Math and variables](#math-and-variables)
   1. [Boolean methods](#boolean-methods)
   1. [Operators and conditionals](#operators-and-conditionals)
   1. [Loops](#loops)
   1. [String and array methods](#string-and-array-methods)
   1. [Other String and array methods](#other-string-and-array-methods)
   1. [Object methods](#object-methods)
   1. [Number Methods](#number-methods)
   1. [Date methods](#date-methods)
   1. [Functions and Rest Syntax](#functions-and-rest-syntax)
   1. [Regex](#regex)
   1. [ES6 Syntax](#es6-syntax)
   1. [Console Commands](#console-commands)
   1. [Local and session storage](#local-and-session-storage)


[Important Notes](#important-notes)
1. [JavaScript version of CRUD](#javascript-version-of-crud)
   1. [Create](#create)
   1. [Read and return index and length](#read-and-return-index-and-length)
   1. [Read and return values](#read-and-return-values)
   1. [Update and mutate](#update-and-mutate)
1. [Arrays and Strings](#arrays-and-strings)
   1. [Same Methods and Same Effect](#same-methods-and-same-effect)
   1. [Different Methods and Same Effect](#different-methods-and-same-effect)
   1. [Different Methods and Opposite Effect](#different-methods-and-opposite-effect)
   1. [Common Methods unique to Strings](#common-methods-unique-to-strings)
   1. [String Methods Notes](#string-methods-notes)
   1. [Other Methods unique to Arrays](#other-methods-unique-to-arrays)
   1. [High Order Array Methods](#high-order-array-methods)
   1. [Array Methods Notes](#array-methods-notes)
1. [Object Notes](#object-notes)
1. [Number notes](#number-notes)
1. [Date Notes](#date-notes)
1. [Loop Notes](#loop-notes)
1. [Miscellaneous](#miscellaneous)

## Table Comparisons

The following tables are for visual memorization. It is easy to see similarites and differences between different methods, as well as, for variabes, data types, operators, etc.

### Data types

JavaScript Primitive Data Types (data that is immutable, is not an object, and has no methods). Though most f them have object equivalents: 

|    Name   | Type              | Obj Equiv? |
| :-------- | :----:            | :----:  | 
| `null`      | nonexistent value | NO | 
| `undefined` | default variable value | NO | 
| Boolean   | `true` or `false` | YES | 
| Number    | numeric values    | YES | 
| String    | characters/text   | YES | 
| Bigint    | large numbers     | YES | 
| Symbol    | unique identifier | YES | 

Characterististics of primitive types:
- No methods
- Immutable

<br>

Object Types (multiple values):
|  Name    | Type   | 
| :-----   | :----: |
| Objects  | a collection of properties with values of any type in key-value pairs | 
| Array    | values are most commonly str, num, obj, and arr  | 
| Function | self-explanatory | 
| Date     | self-explanatory | 
| JSON     | an object type most often used for data retrieved from an API | 
| `keys`   | keys are strings and are the *name* of an object property |
| `value`  | the value that follows `"keyName": value`|

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Math and variables

Basic math operators:
|    Purpose      | Symbol | 
| :-----------    | :----: |
| Addition        | +      |
| Subtraction     | -      | 
| Multiplication  | *      |
| Division        | /      | 
| **Remainder**   | %      |
| Exponentiation  | a**b   | 

<br>

var, let, const:
| Topic                | var       | let                  | const                |
| :--------            | :----     | :---                 | :----                |
| Scope                | Global    | Block                | Block                |
| Declared (no value)  | undefined | undefined            | Uncaught SyntaxError |
| Redeclare?           | Yes       | Uncaught SyntaxError | Uncaught SyntaxError |
| Reassign?            | Yes       | Yes                  | Uncaught TypeError   |

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Boolean methods

JavaScript methods, conditionals, etc. that return `true` or `false`: 

| Type:              | Checks against:                      |
| :----------        | :--------------                      |
| <, >, <=, >=       | number, .length, typeof, ...         |
| ==, ===, !=, !==   | Anything                             |
| &&, \|\|           | Checking multiple and/or conditions  |
| hasOwnProperty(prop) | If an object has a property          | 
| obj.is(a, b)       | if 2 values are the same value       |
| isPrototypeOf(obj) | checks if an obj exists in another obj's prototype chain | 
| obj instanceof Class | if obj is an instance of a certain class | 
| Array.isArray(arr) | If item checked is an array          |
| isNaN()            | if a value is NaN or not             | 
| every()            | if ALL elements pass a test          |
| some()             | if at least ONE element passes a test |
| incudes()          | if arr or str contains the search value |
| endsWith()         | if str ends with the search value    |
| Number.isInteger(num) | if value is an integer            |
| isFinite()         | if a number is finite or infinite | 
| test()             | RegEx test if the string contains the match expression |
| in operator        | if prop is `in` the obj or prototype (prop in obj) | 
| true, false        | equals `true` and `false`            | 

> Common to see `typeof` with ==, ===, !=, !==

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Operators and conditionals

Operators:
| Type       | Ex. 1  | Ex. 2  | Ex. 3   | Ex. 4   | Ex. 5  | 
| :--------- | :----- | :----- | :------ | :------ | :------ | 
| Assigment  | =      | +=     | -=      | *=      | /=      |
| Comparison | <, >   | <=, >= | ==, === | !=, !== |         |
| Arithmetic | +, -, *, /      | %       | ++      | --      | **   |
| Logical    | &&     | \|\|   | !       | ,       |         |
| Type       | typeof | instanceof |     |         |         | 

<br>

Comparisons for conditionals:
|    Purpose                | Symbol | 
| :-----------              | :----: |
| Equality check            | ==     |
| Inequality check          | !=     |
| Strict equality           | ===    |
| Strict inequality         | !==    |
| Less than                 | <      |
| Greater than              | >      |
| Less than or equal to     | <=     |
| Less than or equal to     | >=     |
| **all** things true       | &&     |
| 2 **or** more things true | \|\|   |
| if `a` exists             | if (a) {...}      |
| if `a` doesn't exist      | if  (!a) {...}    |
| Ternary operator          | a ? b : c         |
| Nested Ternary            | a ? b : c ? d : e |
| Ternary syntax:           | if cond ? do : else do |

<br>

Conditional Statements 
| Type    | Syntax 1        | Syntax 2             | Syntax 3     | Syntax 4 | Syntax 5  |
| :-----  | :-------       | :------             | :--------   | :------ | :------- |
| if      | if (a) {run} |                      |              |          |           |   
| else    | if (a) {run} | else {run}           |              |          |           |
| else if | if (a) {run} | else if (a) {run} | *else {run}* |          |           |
| ternary | a ? b : c       |                      |              |          |           |
| switch  | switch(val)     |  case "a":           | {run}        | *break*  | *default* | 

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Loops

Types of Loops:

|    Type        | Syntax | Syntax 2          | Syntax 2 |
| :-----------   | :---- | :----            | :---- | 
| while    | let i = num  | while (i cond)    | {code with i; i++} | 
| do while | let i = num  | do {code with i; i++} | while (i cond) |
| for      | for (a; b; c) | {code with i}    |                  |
| for in   | let i `in` obj | {code with i}   |                 |
| for of   | let i `of` obj  | {code with i}  |                |

<br>

Loop assigment:
|    Purpose          | Symbol | 
| :-----------        | :----: |
| Loop addition       | +=     |
| Loop subtraction    | -=     |
| Loop multiplication | *=     |
| Loop division       | /=     |
| Loop increment      | ++     |
| Loop decrement      | --     |

<br>

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### String and array methods

String and Array methods/properties (Same Methods, Same Effect):
|    Method   | Purpose: | Returns:     | Arr basic code        | Str basic code | 
| :---------- | -------: | :------      | :------------         | :-----------   |
| slice()     | creates: | new arr/str  | arr.slice(start, end) | str.slice(start, end) | 
| concat()    | creates: | new arr/str  | arr1.concat(arr2)     | str1.concat(' ', str2)  | 
| indexOf()   | finds:   | index # or -1 | indexOf(searchVal)   | indexOf(searchStr) | 
| lastIndexOf() | finds: | index # or -1 | lastIndexOf(searchVal) | lastIndexOf(searchStr) |
| includes()  | checks:  | Boolean      | includes(searchVal)   | includes(searchStr) | 
| length      | counts:  | arr/str len  | arr.length            | str.length | 
| [index]     | value:   | specific value | arr[index]          | str[index] | 

<br>

Strings and Arrays (Different Method Name, Same Effect): 
|    Method        | Returns:               |  Syntax:          | 
| :-------------   | :--------------------  | :-----------  |
| str.charAt(i)    | Returns the character at the index  | str.charAt(index) | 
| arr.at(i)        | Returns the array item at the index | arr.at(index)     | 
| str.substring(i) | Returns part of a string            | str.substring(indexStart)|
| arr.slice(i)     | Returns part of an array            | arr.sllice(indexStart) |
| _arr.splice(i)_  | *_Returns part of an array (mutates)_ | arr.splice(indexStart) |

<br>

Strings and Arrays (Different Name, Opposite Effect):

|    Method       | Returns:               |  Syntax:     | 
| :-------------  | :-------------------- | :---------- |
| split() | Turns a string into an array of substrings | str.split() | 
| join()  | Turns all elements of an array into a string  | arr.join() | 

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Other String and array methods

Other common string methods:
|    Method         | Returns:                |  Syntax:     | 
| :-------------    | :--------------------  | :---------- |
| str.toLowerCase() | new string              | str.toLowerCase() |
| str.toUpperCase() | new string              | str.toUpperCase() |
| concat. operator       | new string              | str1 + str2    |
| str.trim()        | new string              | str.trim() |
| str.replace()     | new string              | let newStr = str.replace(regex, subStr) |
| str.match()       | new array               | let newArr = str.match(regex) |
| endsWith()        | Boolean                 | endsWith(searchStr) | 
| regex.test()      | Boolean                 | regex.test(str) |
| str.charCodeAt()  | Unicode #               | charCodeAt(index) |
| str.fromCharCode() | Character              | fromCharCode(n1, n2, ...) |

<div align="left">&#8675; <a href="#arrays-and-strings" title="Arrays and Strings">To notes section</a></div>

<br />

Other common array methods:
|    Method       | Returns:          |  Syntax:                | 
| :-------------  | :--------------  | :----------            |
| [x][y]          | sub-array values  | arr[x][y]               |
| arr.pop()       | item removed      | arr.pop()               |
| arr.shift()     | item removed      | arr.shift()             |
| arr.reverse()   | mutated array     | arr.reverse()           |
| arr.join()      | new string        | arr.join(separator)     |
| arr.push()      | new array length  | arr.push(item, item2, ...) |
| arr.unshift()   | new array length  | arr.unshift(item, item2, ...) |
| arr.splice()    | mutated array     | arr.splice(start, deleteCt, ...items)
| arr.find()      | 1st element found | arr.find(item, index, array) |
| arr.sort()      | mutated array     | arr.sort((a, b) => a - b) |
| arr.every()     | boolean           | arr.every((item) => {...}) |
| arr.some()      | boolean           | arr.some((item) => {...}) |
| arr.map()       | new array         | arr.map((item) => {...}) |
| arr.filter()    | new array         | arr.filter((item) => {...}) |
| arr.forEach()   | new array         | arr.forEach((item) => {...}) |
| arr.reduce()    | new array         | arr.reduce((a, b) => {...}, val) |



<div align="left">&#8675; <a href="#other-methods-unique-to-arrays" title="Other methods unique to arrays">To notes section</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Object methods

Common Object methods:
| Method, Class term   | Returns:  | Returns what?       |
| :------------------- | :-------  | :-------            |       
| Object.keys(obj)     | new array | obj property keys   |
| Object.values()      | new array | obj property values |
| Object.entries(obj)  | new array | obj key-value pairs  |
| Object.getOwnPropertyNames() | new array | all prop names except symbols |
| Object.freeze(obj)   | NA        | prevents mutation for entire object |  
| obj.toString()       | new string | obj as a string     |
| obj.hasOwnProperty() | boolean   | if obj has (prop)   |
| obj.prop or obj[prop] | value    | return value for `prop` |
| obj.prop[i] or obj.[prop][i] | value |  at pos [i] for array in object |
| obj.prop.length      | value     | length of array in an object |

<br>

Object class syntax and terms (Fx = 'function'):
| Class term  | Purpose:                                        |
| :---------- | :-------                                        | 
| class       | template for creating objects                   | 
| constructor | for creating and initializing an object created with a class | 
| this        | the value of this is determined by how a function is called | 
| new         | create a new instance of the class              |  
| get         | binds an obj prop to a Fx, called when that prop is looked up | 
| set         | binds an obj prop to a Fx, called when there is an attempt to set that prop | 
| extends     | used to create a class as a child of another class | 
| prototype   | the mechanism of how objects inherit features from one another |

Look into [MDN Method definitions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Method_definitions).

<div align="left">&#8675; <a href="#object-notes" title="Object Notes">To notes section</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Number methods

Common Number and Math methods (single argument):
| Method          | Result/Purpose: | 
| :---            | :----            |
| toExponential(n) | returns a string representing the Number object in exponential notation |
| toFixed(n)      | Returns number with a specified # of decimal places | 
| toPrecision(n)  | Returns a # to a specified # of significant digits |
| isFinite()      | Returns boolean for finite vs infinite number check | 
| Number.isInteger() | Returns boolean for number as integer or not | 
| parseFloat()    | Parses an argument and returns a floating point number |
| Math.abs(x)     | Returns the absolute value of x | 
| Math.ceil(x)    | Always rounds a number up to the next largest integer |
| Math.floor(x)   | Returns the largest integer less than or equal to x. |
| Math.random(x)  | Returns a pseudo-random number between 0 and 1. |
| Math.round(x)   | Returns the value of the number x rounded to the nearest integer. |
| Math.sign(x)    | Returns the sign of the x: positive, negativ or zero |
| Math.sqrt(x)    | Returns the positive square root of x. |
| Math.trunc(x)   | Returns the integer portion of `x`, removing any fractional digits. |

<br /> 

Common Math Methods (2 or more arguments):
| Method | Result/Purpose: | 
| :---   | :----           |
| Math.max(n1, n2, ...)   | Returns the largest of zero or more numbers |
| Math.min(n1, n2, ...))  | Returns the smallest of zero or more numbers. |
| Math.pow(x, y)          | Returns base x to the exponent power y (that is, x^y). |

<div align="left">&#8675; <a href="#number-notes" title="Number notes">To notes section</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Date methods

<br />

Common Date Methods: Pulling Date and Time Values

| Method            | Description:                                      | 
| :---              | :------                                           | 
| new Date()        | Defaults to present day if you don’t pass it anything |
| getDate()         | Returns the day of the month as a # (1-31)        | 
| getDay()          | Weekday as a number (local time, 0-6, 0 = Sunday) | 
| getFullYear()     | Year as a four-digit number (yyyy)                | 
| getHours()        | Get the hour (0-23)                               | 
| getMilliseconds() | The millisecond (0-999)                           | 
| getMinutes()      | Get the minute (0-59)                             | 
| getMonth()        | Month as a number (0-11)                          | 
| getSeconds()      | Get the second (0-59)                             | 
| getTime()         | Get the milliseconds since January 1, 1970                  | 
| getUTCDate()      | Date according to universal time                  | 

<br />

Set Part of a Date
| Method            | Description:                        | Syntax:               | 
| :---              | :------                             | :----                 |
| setDate()         | Set the day as a number (1-31)      | setDate(dayValue)     | 
| setFullYear()     | Sets the year (optional month & day) | setFullYear(yrValue) | 
| setHours()        | Set the hour (0-23)                 | setHours(hrsValue)    | 
| setMilliseconds() | Set milliseconds (0-999)            | setMilliseconds(msValue) | 
| setMinutes()      | Sets the minutes (0-59)             | setMinutes(minsValue) | 
| setMonth()        | Set the month (0-11)                | setMonth(moValue)     | 
| setSeconds()      | Sets the seconds (0-59)             | setSeconds(secsValue) | 
| setTime()         | Set the time (ms since Jan 1, 1970) | setTime(timeValue)    | 
| setUTCDate()      | Set day of the month for spec. UT   | setUTCDate(dayValue)  | 

<div align="left">&#8675; <a href="#date-notes" title="Date Notes">To notes section</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Functions and Rest Syntax

Basic function declaration & expressions:
| Type     | Declare                        | Call | 
| :---     | :-----                         | :----- |
| Declaration | function name() {...}       | name(); | 
| Expresson | const varName = function() {...} | varName(); | 
| Arrow    | () => {...}                    | -   
| Arrow2   | () => "value"                  | -   | 
| Arrow3   | item => {item...}              | -   | 
| Arrow4   | (arr1, arr2) => {arr1...arr2}  | -   | 
| IIFE     | (function() {...})             | (); |
| _Spread/Rest op._ | (...) | | 

<br>

Spread and Rest operator:
| Type         | Declare        | Used to/with | 
| :---         | :-----         | :----- |
| Spread oper. | (...arr)       | Unpack an array |
| Spread oper. | (...obj)       | Unpack an object |
| Rest oper.   | (...args)      | As Function parameters |
| Variation:   | (a, ...args)    | 1st element then rest | 
| Variation:   | (a, b, ...obj) | 1st two elements then rest | 

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### RegEx

General: 

| Char  | Example   | Description | 
| :---  | :----     | :---- |
| string | `/Some word/` | Match a literal string |
| \|    | `/dog\|cat/`| Either or, match dog or cat |
| i	    | `/The/ig `  | Flag to ignore case, find all occurences of `the`  | 
| g	    | see above | Global flag, match all occurrences | 
| .	    | `/.ing/`    | Wildcard character, match anything except new lines. | 
| \	    | `\. `      | Escapes special characters (`.`, `+`, `^`, `*`, `?`, `$`, etc.) | 
| [ ]	  | `/[aeiou]/` | Character set/class, matches vowels in this case | 
| [^]	  | `/[^aeiou]/` | Don't match what's inside, don't match lowercase vowels | 
| -     | `[a-zA-Z]`  | Match all upper and lower case alphabet letters | 
| [0-9]	| NA          | Match all the numbers between 1 and 9 | 
| [a-z0-9] | NA       | Combineation of the 2 above | 
| +	    | `/s+/gi `   | Match 1 or more occurrences of the previous character | 
| *	    | `/boo*/`    | Match 0 or more occurrences: both, booth, booooom, bot, ...  | 
| ?	    | `/docx?/`   | Lazy matching, optional match 0 or 1 times of the previous char | 
| ^	    | `/^The/`    | Search for patterns at the beginning of strings. | 
| $	    | `/end.$/`   | Search for patterns at the end of a string. | 
| {#}   | `a{5}`      | Quantity specifier, specify the exact number of matches (5 a's) | 
| {#,}  | `\s{2,}`    | Match at least the lower number or more, find 2 or more spaces | 
| {#,#} | `a{2,5}`    | Match the letter `a` between 2 and 5 times | 
| (?<=...) | NA       | Positive lookbehind, put inside a group, start with `?<=` | 
| (?<!...) | NA       | Negative lookbehind, put inside a group, start with `?<!` | 
| (?=...) | NA        | Positive lookahead |
| (?!...) | NA        | Negative lookahead |

<br>

Shorthand syntax: 

| Char  | Example   | Description | 
| :---  | :----     | :---- |
| \w	  | NA          | Equals [A-Za-z0-9_] | 
| \W	  | NA          | Equals [^a-za-z0-9_]. | 
| \d	  | NA          | Equals [0-9] | 
| \D	  | NA          | Equals [^0-9] | 
| \s	  | NA          | Match a whitespace, equals [\r\t\f\n\v] | 
| \S	  | NA          | Match everything except whitespace, equals [^\r\t\f\n\v] | 
| ( )	  | `(anything)` | Capture group, use for different blocks to match | 
|       | `$1`        | use `$1` to reference the 1st capture group, `$2` for 2nd, ... |
| <?name> | (?\<name\>regex) | Name your capture groups instead of `$1`, `$2`, etc. |

<br>

Regex Methods
| Method	| Description |
| :-----  | :---- |
| regEx.test(str)	| Returns true or false if the pattern match is found | 
| str.match(regEx)	| Extract the actual matches found | 
| str.replace(regEx, 'replacement')	| Search and replace text in a string | 

<br>

Escaping characters (common):
| Code | Character output |
| :--- | :----- |
| `\'` | Single quote `'` | 
| `\"` | Double quote `"` | 
| `\\` | Backslash `\`| 
| `\\|` | Pipe `\|` | 
| `\n` | New line | 
| `\r` | Carriage return | 
| `\t` | <kbd>TAB</kbd> | 

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### ES6 Syntax

Table of syntax for various ES6 topics:
| ES6 topic             | Code example                          | 
| -------:              | :-----------                          |
| Arrow functions:      | const varName = () => {code}          | 
| Default parameters:   | function fnName(parm1 = val1) {...}   |
| Rest parameter:       | const product = (...n) => {code}      | 
|                       | product(2, 4, 6, 2)                   |
| Spread operator:      | let numbers = [-12, 160, 0, -3, 51, -50]; | 
|                       | let minNum = Math.min(...numbers);    |
| Destructuring assigment.: | const user = { name: 'John Doe', age: 34 }; | 
| `// instead of:`      | const name = user.name;               | 
|                       | const age = user.age;                 | 
| `// use:`             | const { name, age } = user;           | 
| `// assign to var names:` | const { name: userName, age: userAge } = user; | 
| Destructuring  with Rest Parm: | const [a, b, ...arr] = [1, 2, 3, 4, 5, 7]; | 
| Template literals ${var}: | \`Hello, my name is ${name}.\`      | 
| Object literal:       | const person = (name, age, email) => ( {name, age, email} );|
| Declarative functions: | no colon or `function` keyword, name(parm) (code) | 
| Class syntax:         | class ConstrFunc { constructor(x) {this._x = x}} | 
| getter:          | get something() { return this.x; }      |
| setter:          | set something(updateX) this.x = updateX |
| `this._var`:          | private var, only accessible within the class | 
| Module script:        | <script type="module" src="script.js"></script> | 
| export1          | export const add = (x, y) => {...}      | 
| export2          | export { add };                         | 
| export default   | export default function(x, y) => {...}  | 
| import           | import { add } from './functions';   | 
| import default      | import add from './functions.js';       | 
| import multiple     | import { add, subtract } from './functions.js'; | 
| import all          | import * as codeObj from "./functions.js"; | 
| JavaScript Promise:   | new Promise((resolve, reject) => {...});  | 
| then                | myPromise.then(result => {...}); | 
| catch               | myPromise.catch(error => {...}); | 
| promise keywords: | then, result, catch, error             | 

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Console commands

Useful console commands:

| Command                  | Purpose |
| :------                  | :------- | 
| console.log( )           | Debugging |
| console.error( )         | Same as `.log` but wraps message is red error box | 
| console.table( )       | Dispay arrays and objects as a table |
| console.time("label")    | Displays how long the function took to run | 
| console.timeEnd("label") | Used in tandem with the .time() | 
| console.dir(obj)         | Prints everything about a JS object | 
| console.clear( )         | clears the console of all other results | 

> `console.time`: requires `timeEnd` as well to work. Put `time` before the function and `timeEnd` after the function.

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Local and session storage

| Command       | Example | 
| :---          | :----     |
| clear         | localStorage.clear(); | 
| getItem       | const a = localStorage.getItem('myVar'); | 
| setItem       | localStorage.setItem('myVar', 'Value'); | 
| removeItem    | localStorage.removeItem('myVar'); | 
| JSON.parse    | const user = JSON.parse(localStorage.getItem('Value')); | 
| JSON.stringify | localStorage.setItem('Value', JSON.stringify(myVar)); | 

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

# Important Notes

Notes on various tables for specific methods and syntax for everything listed above. For notes on other topics or code, check notes.md.

Miscellaneous:

- `typeof`: Returns the type of a variable
- `instanceof`: Returns true if the prototype property of a constructor appears anywhere in the prototype chain of an object

## JavaScript version of CRUD

There are 4 ways to work with data that are known collectively as CRUD:
  - C = _Create_: e.g., writing to the dom, creating a copy of an array or a new instance of an object.
  - R = _Read_: e.g., reading values from arrays or objects, getting user input values, etc.
  - U = _Update_: Changing a value for an existing record like client/customer contact information, user password, mutating an array, ...
  - D = _Delete_: Removing a record or item from an object or array, ...

Typically, CRUD involves ineracting with databases. However, you can apply that acronym to front-end JavaScript as well. This is just another way of visualizing and understanding JS. 

But before you can **Read**, **Update**, or **Delete**, you need to check if a piece of data exists. This is done with some kind of conditional statement:
  - Go back and view the [Boolean methods](#boolean-methods), [Operators and conditionals](#operators-and-conditionals), [Loops](#loops) and/or [Regex](#regex) sections.

If an element does not, then you can **Create** it. If `the thing` exists, then you can read, update and/or delete. In JavaScript you can **read** for the purpose of 1) returning the value, or 2) returning the length or the index # (arr, str) of an item. 

And whatever you can read, you can do so for the purpose of updating or deleting the values. 

Let's look at create, then read/return, and finally update/mutate and delete.
<!--  
Return position:
| Method | Does: | Data Type:
| :----  | :----  | :---- | 
| indexOf()     | returns position | str & arr |
| lastIndexOf() | returns position | str & arr |
| .length | returns the count of items | str & arr |
| [i] | returns the value at position | str & arr |
-->

### Create

Create new objects or variables:
| Method            | Creates: |
| :----             | :----  |
| =                 | assign values using `let` or `const` |
| user input        | create from `getElementById`, `querySelector`, etc. |
| obj.keys()        | new array of object keys | 
| obj.values()      | new array of object values | 
| Object.create()   | new object, using an existing object as the prototype |
| class syntax      | create objects from a class and the `new` keyword |
| Date methods, new Date() | create a date, year, month, hour, etc. |

<br>

Create from existing objects:
| Method            | Creates: |
| :----             | :----  |
| str.toLowerCase() | returns str as lowercase  |  
| str.toUpperCase() | returns str as uppercase  |
| +=, *=, -=, /=    | new object from object |
| str.trim()        | new str |
| str.substring()   | new str | 
| str.replace()     | new str | 
| arr.join()        | new string from array | 
| arr or str.concat() | new array or string | 
| arr.slice()       | new array | 
| str.split()       | new array | 
| arr.filter()      | new array |
| arr.map()         | new array |

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Read and return index and length

Read / Return index # and length: 
| Syntax          | Returns: |
| :----           | :----  |
| indexOf()       | index # |
| lastIndexOf()   | index # |
| arr.findIndex() | index # for first occurrence that passes test | 
| .length         | length of arr/str |
| arr.push()      | length of new arr after mutating arr | 
| arr.unshift()   | length of new arr after mutating arr | 

### Read and return values

Simple returns / read:
| Syntax        | Returns:            |
| :----         | :----               |
| str[i]        | str value at index position |
| str.charAt(i) | same as above       |
| arr[i]        | array value at index position |
| arr[x][y]     | sub-aaray value at index position |
| arr.at(i)     | same as above, try `arr.at(-1)` for last item |
| obj.prop      | obj value for prop  |
| obj[prop]     | variation of above  |
| obj.prop[i]   | value at index position for arr in obj prop |
| obj[prop][i]  | variation of above  |
| includes()    | boolean value, arr/str | 
| str.endsWith() | boolean value      | 
| obj.hasOwnProperty() | boolean value | 
| str.test()    | boolean value       | 
| arr.every()   | boolean value       |   
| arr.some()    | boolean value       | 

<br>

More involved returns / read:
| Syntax        | Returns: |
| :----         | :----  |
| arr.find()    | arr value for first occurrence that passes test |   
| arr.reduce()  | single value after function | 
| arr.shift()   | the item value removed from array | 
| arr.pop()     | the item value removed from array | 
| arr.slice     | new array with the imes sliced out (same for string?) |
| str.match()   | str value(s) that matches RegEx |
| Number methods | formatted number, e.g.: | 
| num.toFixed(2) | returns number with 2 decimal places |
| Math() methods | calculated number, e.g.: | 
| Math.abs(x)   | returns the absolute value of a number |

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Update and Delete

Update, Mutate, Delete:
| Syntax          | Returns:                    |
| :----           | :----                       |
| arr.splice(i)   | changes array contents      | 
| arr.push()      | changes array contents      | 
| arr.unshift()   | changes array contents      | 
| arr.shift()     | changes array contents      | 
| arr.pop()       | changes array contents      | 
| arr.sort()      | changes array order         | 
| arr.reverse()   | changes array order         | 
| obj[prop] = val | change property value, or set value if empty |
| obj.prop = val  | variation of above          |
| `delete` obj.prop | removes prop from an object, returns `true` |
| obj.prop = " "  | update obj.prop to empty value, also try `null`|
| arr.length = 0  | empties the array           |  
| delete obj[prop] | delete a property from an object |

> Look into `arr.entries()` in conjuction with `.next().value`. Also, `obj.entries()` is confusing as well.


<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Arrays and Strings 

Miscellaneous notes:
- Unlike strings, the entries of arrays are mutable and can be changed
- Access multi-dimensional arrays  with indexes: `var arr = [ [1, 2], [2, 3], [ [3, 4], 5] ] arr[2][0][1] = 4`

There are methods in common to both arrays and strings so I am combining them to more easily visualize them. Check out the following MDN links: [MDN String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String), [MDN Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array).

### Same Methods and Same Effect

- `slice()`, str | Extracts a section of a string and returns a new string, does not mutate original
- `slice()`, arr | Extracts a section of the calling array and returns a new array
- `concat()`, str | Joins two or more strings and returns the new string
- `concat()`, arr | Joins two or more arrays and returns a copy of the joined arrays
- `includes()`, str | Check if a string contains the specified string 
  - Alternate: `includes(searchVal, beginIndex)`
- `includes()`, arr | Check if an array contains the specified element
  - Alternate: `includes(searchVal, beginIndex)` 
- `endsWith()`, str | Checks whether a string ends with the characters of a given string 
  - Alternate: `endsWith(searchString, length)`
- `indexOf()`, str | returns the index of the first occurrence of the specified substring
  - Alternate: indexOf(searchString, pos)
- `indexOf()`, arr | returns the first index at which a given element can be found, similar to `includes()`; uses strict equality
  - Alternate: `indexOf(searchVal, pos)`
- `lastIndexOf()`, str | returns the index of the last occurrence of the specified substring: 
  - Alternate: lastIndexOf(searchStr, fromIndex)
- `lastIndexOf()`, arr | returns the index of the last occurrence of the specified value
  - Alternate: `lastIndexOf(searchVal, fromIndex)`

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Different Methods and Same Effect

- `arr.at()`: Accepts negative #’s, which counts from back
- `str.substring()`: returns the part of the string between the start and end indexes, or to the end of the string
  - Alernate: `substring(indexStart, indexEnd)` where `indexEnd` is the index of the first character to exclude from the returned substring.
- `arr.splice()`: changes the contents of an array (_mutates_) by removing or replacing existing elements and/or adding new elements
  - Alternate: `splice(start, deleteCount)`, `splice(start, deleteCount, item1, item2, ...)`, where itemN = equals the values to add to the array beginning from `start`.

### Different Methods and Opposite Effect

- `str.split()`: alternate code: `split(separator)`, `split(separator, limit)`
- `arr.join()`: alternate code: `join(separator)`
- These two are used in unison, first to split a string, then to join. 

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Common Methods unique to Strings

- `toLowerCase()`: Converts string to lowercase
- `toUpperCase()`: Converts string to uppercase
- `trim()`: Removes whitespace from both ends of a string and returns a new string, without modifying the original string
- `repeat(count)`: constructs and returns a new string which contains the specified number of copies of the string on which it was called, concatenated together
- `test()`:	Though, not a string method, it executes a search for a match between a regular expression and a specified string. Returns true or false: `test(str)`
- `match()`: Used to match regular expression against a string; retrieves the result of matching a string against a regular expression: `match(RegEx)`
- `replace()`: Returns a new string with some or all matches of a pattern replaced by a replacement. The pattern can be a string or a RegExp, and the replacement can be a string or a function to be called for each match. If pattern is a string, only the first occurrence will be replaced: `replace(regexp, newSubstr)`, `replace(regexp, replacerFunction)`, `replace(substr, newSubstr)`, or `replace(substr, replacerFunction)`

### String Methods Notes

- `charCodeAt(index)` — Gives you the Unicode number for the character at that position
- `fromCharCode(num1, num2, ...)` — Returns the character associated with a unicode number
- `charCodeAt` takes an index and returns a number, whereas `fromCharCode` does the opposite: returns a character given a number.
- `valueOf()` — Returns the primitive value (that has no properties or methods) of a string object
- 'toString()`: Every JavaScript object has a `toString()` method. You can convert a number, boolean or array to a string. However, you can not use this to convert an object to a string (See [MDN Object.toString](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/toString)).

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Other Methods unique to Arrays

- `push()`: Adds one or more elements to the end of an array and returns the new length of the array: 'push(elem1, elem2, ...)`
- `unshift()`: Adds one or more elements to the beginning of an array and returns the new length of the array: `unshift(elem1, elem2, ...)`
- `shift()`: Removes the first element from an array and returns that removed element. This method changes the length of the array (no arguments). To get the removed item make sure to set it to a var: `let removedItem = arr.shift();`
- `pop()`: Removes the last element from an array and returns that element. This method changes the length of the array (no arguments)
- `flat()`: creates a new array with all sub-array elements concatenated into it recursively up to the specified depth

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### High Order Array Methods

- `forEach()`: Function to run on each item of an array, common in `for` loops, performs a function on each item in your array, similar to using a "for" loop to apply a function to an array but with much less work to code. Unlike map(), forEach() does not create a new array automatically, you would have to code a specific function to do so
- `filter()`: Takes a function containing a test and returns a new array with all the elements that pass that test. The filtration is done using a function that returns a boolean value
- `map()`: Performs a function on every element in your array and places the result in a new array
- `reduce()`: Takes a _reducer_ function and executes it on each array element to output a single value while returning. It takes a `reducer` function with an `accumulator` variable and a `current` element variable as required parameters. The accumulator's value is remembered across all the iterations and is ultimately returned after the final iteration
- `every()`: Checks if **every** element in an array pass a test, returns boolean. This have a number of variations for the syntax. Check the MDN doc [Array.prototype.every](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every). The every method executes the provided callbackFn function once for each element present in the array until it finds the one where callbackFn returns a falsy value.
- `some()`: Tests whether at least one element in the array passes the test implemented by the provided function. It returns true if, in the array, it finds an element for which the provided function returns true; otherwise it returns false. It doesn't modify the array. This have a number of variations for the syntax. Check the MDN doc [Array.prototype.some](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some). The some() method executes the callbackFn function once for each element present in the array until it finds the one where callbackFn returns a truthy value.
- `sort()`: One of the most common operations performed on an array, used to sort an array of numbers or even strings with just a single line of code, returns original array but modified. Sorting a number based array may require a callback function.
- `reverse()`: Reverses the order of the array items, does NOT do a reverse sort
- `find(FxName)` and `findIndex()`: Returns the first element value (for `find`) or index (for `findIndex`) in the array that passes on the test provided by the callback. If there is no match, it returns `undefined` (for find) or `-1` (for findIndex).
- Link: [Mastering ES6 higher-order functions for Arrays](https://www.airpair.com/javascript/posts/mastering-es6-higher-order-functions-for-arrays).

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Array Methods Notes

- `.length`: used often in `for` loops to loop for each element
- `arr.[index]`: to return a value at a specific index, e.g. `arr[3]` to return value at the 4th position
- Returns boolean: `every()`, `includes()`, `some()`
- Returns string: `join()`, `toString()`
- Return New Array: `filter()`, `map()`, `concat()`
- Return Value/Position: `find()`, `indexOf()`, `lastIndexOf()`, 
- Add:  `push()`, `unshift()`,  
- Remove: `pop()`, `shift()`, `slice(start, end)` (does not mutate), `splice()`
- Index change: `reverse()`, `sort()`
- Various: `forEach()`, `reduce()` (although mosty for simple arithmetic)

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Object Notes

- Instead of using indexes to access and modify their data, you access the data in objects through what are called `properties`
- Properties are often `strings` - you can omit the quotes for single-word string properties and for numbers
- Objects can be thought of as a `key`/`value` storage, like a dictionary `{word: definition}`
- There are two ways to access the properties of an object: dot notation (`.`) and bracket notation (`[]`), similar to an array. 
- Dot notation is what you use when you know the name of the property you're trying to access
- If the property of the object you are trying to access has a space in its name, you will need to use bracket notation
- It's also best to use bracket notation when a variable name is substituted for a key name, especially if the name may contain multiple words
- Use dot or bracket notation to update a property
- Testing objects for properties: use the `.hasOwnProperty(propName)` method of objects to determine if that object has the given property
- Sub-properties of objects can be accessed by chaining together the dot or bracket notation
- `Object.prototype.toString()`:	Returns a string representation of the object.
- `Object.prototype.valueOf()`:	Returns the primitive value of the specified object.
- `Object.prototype.hasOwnProperty()`:	Returns a boolean indicating whether an object contains the specified property as a direct property of that object _and not inherited through the prototype chain_.
- `Object.keys(obj)`:	Returns an array containing the names of all of the given object's own enumerable string properties.
- `Object.values()`:	Returns an array containing the values that correspond to all of a given object's own enumerable string properties

Defining getters and setters
- A **getter** is a method that gets the value of a specific property. A **setter** is a method that sets the value of a specific property. You can define getters and setters on any predefined core object or user-defined object _that supports the addition of new properties_.

There are three native ways to list/traverse object properties:
- `for...in` loops: This method traverses all enumerable properties of an object _and its prototype chain_.
- `Object.keys(obj)`: This method returns an array with all the own (not in the prototype chain) enumerable properties names ("keys") of an object `o`.
- `Object.getOwnPropertyNames(o)`: This method returns an array containing all own properties names (enumerable or not) of an object `o`. I don't see the difference with `obj.keys()`.

Check out the [MDN Working with Objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects) page.

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Number notes

- `Math.max()`: returns the largest of the zero or more numbers given as input parameters, or NaN if any parameter isn't a number and can't be converted into one: `Math.max(value0, value1)`, `Math.max(value0, value1, /* ... ,*/ valueN)`
- `Math.min()`: returns the lowest-valued number passed into it, or NaN if any parameter isn't a number and can't be converted into one: `Math.min(value0, value1)`, `Math.min(value0, value1, ... , valueN)`
- `Math.pow()`: static method, given two arguments, base and exponent, returns baseexponent: `Math.pow(base, exponent)`
- `Math.random()`: returns a floating-point, pseudo-random number in the range 0 to less than 1 (inclusive of 0, but not 1) with approximately uniform distribution over that range — which you can then scale to your desired range
- `Math.sign()`: returns either a positive or negative +/- 1, indicating the sign of a number passed into the argument
- `Number.parseFloat()`: parses an argument and returns a floating point number. If a number cannot be parsed from the argument, it returns NaN: `Number.parseFloat(string)` where `string` is value to parse
- `Math.floor(Math.random())`: "Trick" to get a random number within a certain interger range, e.g. `* 100` returns whole numbers between 0 and 99.
- `toString()`: converts a number to a string

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Date Notes

Pulling Date and Time Values:
- `new Date()`: Formats are `2015-03-25`, `03/25/2015`, `Mar 25 2015`, or `25 Mar 2015`. Can also be written without specifying the day (YYYY-MM): `2015-03` (Time zones will vary the result above between February 28 and March 01); or year only `2015`. Can also be written with added hours, minutes, and seconds (YYYY-MM-DDTHH:MM:SSZ): `2015-03-25T11:59:47Z`. Date and time is separated with a capital T. UTC time is defined with a capital letter Z. Or do `9-10-87 11:59-42`.
- `getDate()`: Returns the day of the month for the specified date according to local time as a number (1-31)
- `getDay()`: Returns the day of the week as a number (0-6) for the specified date according to local time, where 0 represents Sunday 
- `getFullYear()`: Returns the year as a four-digit number (yyyy) of the specified date according to local time 
- `getHours()`: Get the hour (0-23), returns the hour for the specified date, according to local time
- `getMilliseconds()`: The millisecond (0-999), returns the milliseconds in the specified date according to local time
- `getMinutes()`: Get the minute (0-59), returns the minutes in the specified date according to local time
- `getMonth()`: Month as a number (0-11)m returns the month in the specified date according to local time, as a zero-based value (where zero indicates the first month of the year)
- `getSeconds()`: Get the second (0-59), returns the seconds in the specified date according to local time
- `getTime()`: Get the milliseconds since January 1, 1970, returns the number of milliseconds since the ECMAScript epoch
- `getUTCDate()`: The day (date) of the month in the specified date according to universal time (also available for day, month, full year, hours, minutes etc.)
- `parse`: Parses a string representation of a date and returns the number of milliseconds since January 1, 1970

<br />

Set Date Methods:
- `setDate(dayValue)`: Set the day as a number (1-31), changes the day of the month of a given Date instance, based on local time
- `setFullYear(yearValue)`: Sets the year (optionally month and day), sets the full year for a specified date according to local time. Returns new timestamp
  - **Additional syntax**: `setFullYear(yearValue, monthValue)`, `setFullYear(yearValue, monthValue, dateValue)`
- `setHours(hoursValue)`: Set the hour (0-23), sets the hours for a specified date according to local time, and returns the number of milliseconds since January 1, 1970
  - **Additional syntax**: `setHours(hoursValue, minutesValue)`, `setHours(hoursValue, minutesValue, secondsValue)`, `setHours(hoursValue, minutesValue, secondsValue, msValue)`
- `setMilliseconds(millisecondsValue)`: Set milliseconds (0-999), sets the milliseconds for a specified date according to local time
- `setMinutes(minutesValue)`: Sets the minutes (0-59), sets the minutes for a specified date according to local time
  - **Additional syntax**: `setMinutes(minutesValue, secondsValue)`, `setMinutes(minutesValue, secondsValue, msValue)`
- `setMonth(monthValue)`: Set the month (0-11), sets the month for a specified date according to the currently set year
  - **Additional syntax**: `setMonth(monthValue, dayValue)`
- `setSeconds(secondsValue)`: Sets the seconds (0-59), sets the seconds for a specified date according to local time
  - **Additional syntax**: `setSeconds(secondsValue, msValue)`
- `setTime(timeValue)`: Set the time (milliseconds since January 1, 1970), sets the Date object to the time represented by a number of milliseconds since January 1, 1970
- `setUTCDate(dayValue)`: Sets the day of the month for a specified date according to universal time (also available for day, month, full year, hours, minutes etc.)

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Loop Notes

- Loops run the same block of code but using different values each time. 
- *While loops*: runs while a specified condition is true and stops once that condition is no longer true. Make sure to initialize your variable outside of the loop and do your increment INSIDE the loop.
  - Be careful! It is very easy to create an infinite loop and have your computer lock up.
- *For loops*: The most common type of JavaScript loop, it runs **`for`** a specific number of times; are declared with three optional expressions separated by semicolons; it’s also common for a loop to iterate thru an array
  - `(a; b; c)`: stands for ( initialization; condition; final-expression ), or are declared with three optional expressions separated by semicolons
  - The initialization statement is executed one time only before the loop starts. It is typically used to define and setup your loop variable
  - The condition statement is evaluated at the beginning of every loop iteration and will continue as long as it evaluates to true. When the condition is false at the start of the iteration, the loop will stop executing. This means if the condition starts as false, your loop will never execute
  - The final expression is executed at the end of each loop iteration, prior to the next condition check and is usually used to increment or decrement your loop counter
  - Use a 'for` loop over a `while` loop when you know how many times the loop will run; otherwise, use a `while` loop.
- *Nested for loops*: If you have a multi-dimensional array, you can use the same logic as the prior waypoint to loop through both the array and any sub-arrays
- *Do...while loops*: it will first do one pass of the code inside the loop no matter what, and then continue to run the loop while the specified condition evaluates to true - a do...while loop ensures that the code inside the loop will run at least once
- `forEach loops`: An array method that runs a callback function for each element in an array, `var.forEach(a, b, c) {code}` where `a` is the iterator, `b` is the index, and `c` is the actual array 
- `map()`: used to return something different in a new array.
- `for in`: for objects
- `for of` loop: also for objects - 
- `break`: use to break out of the loop like in switch statements.
- `continue`: use to skip an iteration in a loop.
- ***Recursion***: ???

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Miscellaneous

Here are the best of my notes or tips and tricks:

General:
- Escaping: use a backslash (`\`) in front of the quote in a string: `\'` or `\"`
- An algorithm is a series of step-by-step instructions that describe how to do something 
- To write an effective algorithm, it helps to break a problem down into smaller parts and think carefully about how to solve each part with code
- BREAK and CONTINUE are really important things to know for loops
- if no `<` or `>` or other comparison symbol is used, the statement is considered `true` if the value is anything other than 0
- `switch` statements: tests a value and can have many `case` statements which define various possible values. Statements are executed from the first matched `case` value until a `break` is encountered
- `case` statements are tested with strick equality (`===`): `switch(check value(s)) {case value: varname = something; break; next case check…}`
- `default` means `else` in a `switch` statement – you can also have multiple cases before a `break`
- **Module** script: You need to create a script in your HTML document with a type of module: `<script type="module" src="filename.js"></script>`
- Use the keywords `export` and `import` - 
- When you export a variable or function, you can import it in another file and use it without having to rewrite the code 
- Export multiple things: `export { thing1, thing2 };`
- `import` allows you to choose which parts of a file or module to load: `import { add } from './math_functions.js'; `
- Use `import *` to import everything from a file - 
- Create an export fallback with `export default` - omit the curly brackets when you import a default export
- Almost every value on its own in JavaScript evaluates to true, except what are known as the "falsy" values: `false`, `0`, `""`, `NaN`, `undefined`, and `null`
- THIS IS HUGE: The **_comma operator_** (`, `) allows multiple expressions to be evaluated in a single statement and returns the result of the last expression: `function isLess(a, b) { return a <= b; }` AND `function isEqual(a, b) { return a === b; }`

<br />

Variables and values: 
- When JS variables are declared, they have an initial value of `undefined`. If you do a mathematical operation on an `undefined` variable your result will be `NaN`
- Variables which are declared without the `let` or `const` keywords are automatically created in the global scope
- **_Falsy_** = [`false`, `0`, `""` or `''`, `NaN`, `undefined`, and `null`]. Make sure to filter falsy values out of an array. 
- `let` is block scoped - A block is a chunk of code bounded by `{ }` - So a variable declared in a block with let is only available for use within that block
- you do not want to declare a variable 2 times in the same scope - 
- variables assigned using `const` should be uppercase: const WEATHER = "It's cold!";

<br />

Objects:
- Objects do not maintain an ordering to stored keys like arrays do; thus a key's position on an object, or the relative order in which it appears is irrelevant when referencing or accessing that key
- Constructors define properties and behaviors instead of returning a value as other functions might 
- OBJECT ORIENTED PROGRAMMING: Functions inside of objects as opposed to in the global scope - in this case they are called METHODS – a Fx in an object `todo` called `add` or `edit` and you call it by `todo.add()` - or `todo.edit(id)`
- `for in` loop: used for objects – create a user object > then for `(let x in user)` returns the names of the keys – user([x]) returns the values
- OOP: constructors & the _this_ Keyword: the most important things in OOP are the `constructor` and the `this` keyword. If you want to create multiple instances of a certain type of object then you want to create a constructor
- the `this` keyword refers to the **_current_** instance of the object, the function scope. To access a variable outside of the function nut in the same object, you have to use `this.varName`, where `this` is pertaining to the current object.
- NOTE: constructors are really powerful when they have functions w\in them known as `methods`
- each object in JS has a prototype – a prototype is an object itself – all objects inherit their properties and methods from their prototypes = Object.prototype vs Client.prototype 
- `Object.prototype` – you can see its methods like hasOwnProperty, toString, valueOf
- `Client.prototype` - when you are dealing with objects that were created thru a constructor
- prevent object mutation: To ensure your data doesn't change, use the function `Object.freeze` to prevent data mutation. Once frozen, you can no longer add, update, or delete properties from that object

<br />

Syntax:
- Bracket notation to find the Nth-to-last character: `string.length - n`, where `n` is a # from end
- Another use of bracket notation on objects is to access a property which is stored as the value of a variable (?)
- Use the spread operator to evaluate arrays, `Math.max(...arr);`
- Use destructuring assignment to extract values from objects (?)
- Use destructuring assignment w\ the rest parameter to reassign array elements

<br />

Functions:
- The function passed to High Order Array Methods will run as many times as the # of items in the array it is called on 
- FUNCTION EXPRESSIONS: it’s when a function is the value of a variable, usually they are anonymous: `let one = function() {...}`
- Function expressions require an ending semicolon because they are the value of a variable, whereas normal functions do not require that.
- There are times when there is no difference between a function declaration vs. expression, but there are times when expressions have benefits: hoisting closures, ...
- Function closure: is a function that references variables in the outer scope from its inner scope.
- inline functions - When there is no function body, and only a return value, arrow function syntax allows you to omit the keyword `return` as well as the brackets surrounding the code: `const magic = () => new Date();`
- WHENEVER YOU HAVE AN ANONYMOUS FUNCTION, YOU CAN CONVERT IT INTO AN ARROW FUNCTION
- arrow function with arguments: `let myConcat = (arr1, arr2) => arr1.concat(arr2);`
- arrow functions work great with higher order functions b\c they take functions as arguments (Arrow) - 
- **Default parameters**: allow named parameters to be initialized with default values if no value or undefined is passed: `function fnName(parm1 = val1) {...}` or `function fnName(parm1, parm2 = val, ...) {...}`
- **Rest parameter**: you can create functions that take a variable number of arguments. These arguments are stored in an array that can be accessed later from inside the function: `(...args)`
- The rest parameter eliminates the need to check the args array and allows us to apply `map()`, `filter()` and `reduce()` on the parameters array
- Only the last parameter in a function definition can be a rest parameter
- **Spread operator**: allows you to expand arrays and other expressions in places where multiple parameters or elements are expected. It expands an already existing array - it spreads it out intto its individual parts. You can only use it in an argument to a function or in an array literal 
- **Array Literal**: An array literal is a list of zero or more expressions, each of which represents an array element - aka, an array.
- Destructuring assignment - a special syntax for taking values from an object to a variable - it's a quicker way of assigning values from an object into variables - it's seems like the assignment is reversed with the var name to the right of `=` and the destructuring of the object to the left
- IIFE: is an anonymous function you declare and run at the same time. To do that you need it to be an expression, and you make it an expression by enclosing it in parentheses (). 
- IIFE's can also take in parameters. IIFE's are very useful with certain design patterns like the module pattern. 
- Methods: you can put functions inside objects as well. 

<br />

Conditionals:
- Most times you want to check the value and type so use `===` ans not `==`
- use `if(typeof varName !== 'undefined')` to check whether or not a variable exists or not. You will get an error if you just use `if (varName)` and it does NOT exist.
- Only `===` and `!==` don't do type conversion, all other comparisons do.
- **_NOTE_**: the curly brackets `{}` in an if statement are optional, though are recommended. Here is an example wiiihout them:
```js
if (id === 100)
  console.log("Equal");
// or 
if (id === 100) console.log("Equal");
```

<br />

Other:
- template literals / template strings: 
```js
${ "vars or expressions/math or a function call or use conditionals / ternary op"  }
```
- **Event bubbling**: when an event happens in the DOM it will bubble up through its parents. If you put an event listener for all the parents with a console.log of their class, they will all fire off even though you did not click them.
- <ins>**Event delegation**</ins>: The oppsite of event bubbling - you put the listener on a parent element, then you use logic inside of the event handler to target the element you want. If you have a list of items all with the same class,  your event listener will only fire for the first one, unless you use event delegation. Another situation where you need it is if you dynamiclly insert something into the DOM using JS.
- for for the multiple list items, put the event listener on the parent or higher then put a condition to find the target. 
- `localStorage`: an API that is part of the `window` object. You can set key-value pairs, but what you set as a value has to be a string. You can save objects and arrays but you have to turn them into a string using `JSON.stringify()`, then to use it use `JSON.parse().` 

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>
<!--  
Testing meta view of ALL syntax and keywords:

Assign, declare, define, set, reassign, initialize:
| Name / Desc        | Keyword, char:                               | Used with/for: | 
| :-------           | :------                                      | :-------  |
| Assignment         | =, +=, etc., set                             | variables |  
| Default parameters | (parm1 = val1)                               | Functions |
| Destructuring      | {key1: val1, key2: val2}                     | Obj       | 
| Template literals  | \`<p>Text ${var}</p>\`                       | variables | 
| Object literal     | (name, age, email) => ( {name, age, email} ) | Obj       |

<br>

Things:
| What              | Why            | 
| :-------          | :------        | 
| data types        | storing values | 
| Variables         | set to a datatype and assign value | 
| Operators         | assign values to variables | 
| data type methods | create, read, update, check, delete | 
| conditionals      | check, test in code blocks |
| comparisons       | same as abve |
| Loops             | working with groups of variables or values |
| functions         | combination of above |
| escaping          | format, output | 
| RegEx             | Check | 
| shorthand syntax  | variable input, alternate, DRY, dynamic | 
-->

<!-- Testing a change for my terminal WTF -->