# JAVASCRIPT CHEAT SHEET

This is not an all-inclusive list of every possible JavaScript method, property, etc. This file has tables of comparisons or for quick reference. 

<div id="back-to-top"></div>

## Table of Contents

1. Table Comparisons
   1. [Data types](#data-types)
   1. [Math and variables](#math-and-variables)
   1. [Boolean methods](#boolean-methods)
   1. [Operators and conditionals](#operators-and-conditionals)
   1. [Loops](#loops)
   1. [String and array methods](#string-and-array-methods)
   1. [Object methods](#object-methods)
   1. [Number Methods](#number-methods)
   1. [Date methods](#date-methods)
   1. [Functions and Escaping](#functions-and-escaping)
   1. [Regex](#regex)
   1. [Console Commands](#console-commands)
1. Important Notes
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
1. [Loop Notes](#loo-notes)
1. [Miscellaneous](#miscellaneous)
1. [Basics](#basics)

## Table Comparisons

The following tables are for visual memorization. It is easy to see similarites and differences between different methods for the various data types.

### Data types

JavaScript Primitive Data Types:

|    Name   | Type              | 
| :-------- | :----:            |
| Boolean   | `true` or `false` | 
| Null      | `null`            | 
| Undefined | `undefined`       | 
| Number    | self-explanatory  | 
| String    | text              | 
| Object*   | See below |

SKIPPED: `Bigint` (huge numbers) and `Symbol` (can be used an object keys).

<br>

Object Types (everything in JS is consdered an object):
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
| :--------            | :----:    | :---:                | :----:               |
| Scope                | Global    | Block                | Block                |
| Declared (no value)  | undefined | undefined            | Uncaught SyntaxError |
| Redeclare?           | Yes       | Uncaught SyntaxError | Uncaught SyntaxError |
| Reassign?            | Yes       | Yes                  | Uncaught TypeError   |

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Boolean methods

Js methods that return true or false: 

| Type:              | Checks against:                      |
| :----------        | :--------------                      |
| <, >, <=, >=       | number, .length, typeof, ...         |
| !=, !==            | Anything                             |
| &&, \|\|           | Checking multiple and/or conditions  |
| hasOwnProperty()   | If an object has a property          | 
| obj.is(a, b)       | if 2 values are the same value       |
| isArray()          | If item checked is an array          |
| every()            | if ALL elements pass a test          |
| some()             | if at least ONE element passes a test |
| incudes(val)       | if arr or str contains the search value |
| endsWith(val)      | if str ends with the search value    |
| isInteger()        | if value is an integer               |
| test()             | RegEx test if the string contains the match expression |
| in operator        | if prop is `in` the obj or prototype (prop in obj) | 

> Common to see `typeof` with ==, ===, !=, !==

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Operators and conditionals

Operators:
| Type       | Ex. 1  | Ex. 2  | Ex. 3   | Ex. 4   | Ex. 5  | 
| :--------- | :----- | :----- | :------ | :------ | :------ | 
| Assigment  | =      | +=     | -=      | *=      | /=      |
| Comparison | <, >   | <=, >= | ==, === | !=, !== |         |
| Arithmetic | +, -, *, /      | %      | ++      | --      | **   |
| Logical    | &&     | \|\|   | !       |         |         |

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
| if `a` exists             | if (a) {...} |
| if `a` doesn't exist      |if  (!a) {...} |
| **all** things true      | &&     |
| 2 **or** more things true | \|\|   |
| Ternary operator          | a ? b : c |

<br>

Conditional Statements 
| Type    | Syntax 1        | Syntax 2             | Syntax 3     | Syntax 4 | Syntax 5  |
| :-----  | :-------:       | :------:             | :--------:   | :------: | :-------: |
| if      | if (a) {run} |                      |              |          |           |   
| else    | if (a) {run} | else {run}           |              |          |           |
| else if | if (a) {run} | else if (a) {run} | *else {run}* |          |           |
| ternary | a ? b : c       |                      |              |          |           |
| switch  | switch(val)     |  case "a":           | {run}        | *break*  | *default* | 

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Loops

Types of Loops:

|    Type        | Syntax | Syntax 2          | Syntax 2 |
| :-----------   | :----: | :----:            | :----: | 
| while    | let i = num  | while (i cond)    | {code with i; i++} | 
| for      | for (a; b; c) | {code with i}    |                  |
| for in   | let i `in` obj | {code with i}   |                 |
| for of   | let i `of` obj  | {code with i}  |                |
| do while | let i = num  | do {code with i; i++} | while (i cond) |
| forEach  | forEach(el)  | =>                | {code with el} | 

<br>

Loop specific arithmetic:
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

Strings and Arrays: Same Methods, Same Effect:
|    Method   | Purpose: | Returns:   | Arr basic code | Str basic code | 
| :---------- | -------: | :------:   | :------------: | :-----------:  |
| slice()     | creates: | new arr/str | arr.slice(start, end) | str.slice(start, end) | 
| concat()    | creates: | new arr/str | arr1.concat(arr2) | str1.concat(' ', str2)  | 
| concat. op. | creates: | new str    | -              | str1 + str2    |
| includes()  | checks:  | Boolean    | includes(searchVal) | includes(searchStr) | 
| endsWith(() | checks:  | Boolean    | -                   | endsWith(searchStr) | 
| indexOf()   | returns: | index #    | indexOf(searchVal)  | indexOf(searchStr) | 
| lastIndexOf() | returns: | index #  | lastIndexOf(searchVal) | lastIndexOf(searchStr) |
| [index]     | returns: | specific value | arr[index]     | str[index] | 
| length      | returns: | arr/str len | arr.length         | str.length | 

<br>

Strings and Arrays: Different Methods, Same Effect: 
|    Method       | Returns:               |  Code         | 
| :-------------  | :--------------------: | :-----------: |
| str.charAt(i) | Returns the character at the specified index | str.charAt(index) | 
| arr.at(i)     | Returns the array item at the given index    | arr.at(index)     | 
| str.substring(i) | Returns part of a string                  | str.substring(indexStart)|
| arr.splice(i) | Adds/Removes elements from an array          | arr.splice(start) |

<br>

Strings and Arrays: Different Methods, Opposite Effect

|    Method       | Returns:               |  Code         | 
| :-------------  | :--------------------: | :-----------: |
| split()  | divides str into substrings   | str.split() | 
| join()  | Joins all elements of an array into a string | arr.join() | 

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Object methods

Common Object methods:
| Method, Class term   | Returns: | Returns what?       |
| :------------------- | :------- | :-------            |       
| obj.keys()           | array    | obj property keys   |
| obj.values()         | array    | obj property values |
| obj.entries()        | array    | obj key-value pairs  |
| obj.getOwnPropertyNames() | array | all prop names except symbols |
| obj.toString()       | string   | obj as a string     |
| obj.hasOwnProperty() | boolean  | if obj has (prop)   |
| obj.prop or obj[prop] | value   | return value for `prop` |
| obj.prop[i] or obj.[prop][i] | value |  at pos [i] for array in object |
| obj.prop.length      | value    | length of array in object |

<br>

Object class syntax and terms (Fx = 'function'):
| Class term  | Purpose:                                        | Other?       |
| :---------- | :-------                                        | :-------            |    
| class       | template for creating objects                   | - |
| constructor | for creating and initializing an object created with a class | - |
| this        | the value of this is determined by how a function is called | - |
| new         | create a new instance of the class              | - | 
| get         | binds an obj prop to a Fx, called when that prop is looked up | - |
| set         | binds an obj prop to a Fx, called when there is an attempt to set that prop | - |
| extends     | used to create a class as a child of another class | - |

Look into [MDN Method definitions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Method_definitions).

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Number methods

Common Number Methods (single argument):
| Method          | Result/Purpose: | 
| :---            | :----            |
| toExponential(n) | returns a string representing the Number object in exponential notation |
| toFixed(n)       | Returns number with a specified # of decimal places | 
| toPrecision(n)   | Returns a # to a specified # of significant digits |
| pasreFloat()    | Parses an argument and returns a floating point number |
| Math.abs(x)     | Returns the absolute value of x | 
| Math.ceil(x)    | Always rounds a number up to the next largest integer |
| Math.floor(x)   | Returns the largest integer less than or equal to x. |
| Math.random(x)  | Returns a pseudo-random number between 0 and 1. |
| Math.round(x)   | Returns the value of the number x rounded to the nearest integer. |
| Math.sign(x)    | Returns the sign of the x, indicating whether x is positive, negative, or zero. |
| Math.sqrt(x)    | Returns the positive square root of x. |
| Math.trunc(x)   | Returns the integer portion of `x`, removing any fractional digits. |

Common Number Methods (2 or more arguments):
| Method | Result/Purpose: | 
| :---   | :----           |
| Math.max(n1, n2, ...)   | Returns the largest of zero or more numbers |
| Math.min(n1, n2, ...))  | Returns the smallest of zero or more numbers. |
| Math.pow(x, y)          | Returns base x to the exponent power y (that is, x^y). |


<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Date methods

Common Date Methods: Pulling Date and Time Values

| Method            | Description:                                      | 
| :---              | :------                                           | 
| getDate()         | Returns the day of the month as a # (1-31)        | 
| getDay()          | Weekday as a number (local time, 0-6, 0 = Sunday) | 
| getFullYear()     | Year as a four-digit number (yyyy)                | 
| getHours()        | Get the hour (0-23)                               | 
| getMilliseconds() | The millisecond (0-999)                           | 
| getMinutes()      | Get the minute (0-59)                             | 
| getMonth()        | Month as a number (0-11)                          | 
| getSeconds()      | Get the second (0-59)                             | 
| getTime()         | Get the ms since January 1, 1970                  | 
| getUTCDate()      | Date according to universal time                  | 

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

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Functions and Escaping

Basic function expressions:
| Type     | Declare            | Call | 
| :---     | :-----            | :----- |
| Standard | function() {...}   | function(); | 
| Arrow    | () => {...}        | - | 
| Arrow2   | () => "value"      | - | 
| Arrow3   | (item) => {item...} | - | 
| IIFE     | (function() {...}) | (); |


Escaping characters:
| Code | Character output |
| :--- | :----- |
| `\'` | Single quote `'` | 
| `\"` | Double quote `"` | 
| `\\` | Backslash `\`| 
| `\\|` | Pipe `\|` | 
| `\n` | New line | 
| `\r` | Carriage return | 
| `\t` | <kbd>TAB</kbd> | 

### RegEx

General: 

| Char | Description | 
| :--- | :---- |
| \	| Escapes a special character. | 
| i	| This flag is used to ignore upper and lowercase. /ignorecase/i. | 
| g	|  or extract a pattern more than once. | 
| .	| The wildcard character . will match any character except new lines. | 
| [ ]	| Allow you to define the characters to match. /b[au]g/ will match "bag", "bug" but not "bog". | 
| [a-z]	| Match all the characters between a and z. | 
| [1-9]	| Match all the numbers between 1 and 9. | 
| [a-z1-9] | Match all the character between a and z, and the numbers between 1 and 9. | 
| [^]	| Match the characters not in the set. [^a-e] match all other characters except A, B, C, D, and E. | 
| +	| Match 1 or more occurrences of the previous character in a row. | 
| *	| Match 0 or more occurrences of the previous character. | 
| ?	| Match 0 or 1 occurrence of the previous character. Useful for Lazy matching. | 
| ^	| Search for patterns at the beginning of strings. | 
| $	| Search for patterns at the end of a string. | 
| \w	| Equal to [A-Za-z0-9_]. Matches upper, lowercase, numbers the and underscore character (-). | 
| \W	| Matches any nonword character. Equivalent to [^a-za-z0-9_]. | 
| \d	| Equal to [0-9]. Match one digit. | 
| \D	| Equal to [^0-9]. Match one non digit. | 
| \s	| Match a whitespace. | 
| \S	| Match everything except whitespace. | 
| a{2,5}	| Match the letter a between 3 and 5 times | 
| a{2,}	| Specify only the lower number of matches | 
| a{5}	| Specify the exact number of matches | 
| (...)	| Specify a group that can be acceded with number (from 1) | 

Regex Methods
| Method	| Description |
| :-----  | :---- |
| test()	| Returns true or false if the pattern match a string or not | 
| match()	| Extract the actual matches found | 
| replace()	| Search and replace text in a string | 

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

# Important Notes

Notes on various tables for specific methods and syntax.

## Arrays and Strings 

Miscellaneous notes:
- Unlike strings, the entries of arrays are mutable and can be changed
- Access multi-dimensional arrays  with indexes: `var arr = [ [1, 2], [2, 3], [ [3, 4], 5] ] arr[2][0][1] = 4`

There are methods in common to both arrays and strings so I am combining them for more easily visualixe them. Check out the following MDN links: [MDN String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String), [MDN Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array).

### Same Methods and Same Effect

- `slice()`, str | Extracts a section of a string and returns a new string
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
  - Alernate: `substring(indexStart, indexEnd)`
- `arr.splice()`: changes the contents of an array by removing or replacing existing elements and/or adding new elements
  - Alternate: `splice(start, deleteCount)`

### Different Methods and Opposite Effect

- `str.split()`: alternate code: `split(separator)`, `split(separator, limit)`
- `arr.join()`: alternate code: `join(separator)`
- These two are used in unison, first to split a string, then to join. 

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Common Methods unique to Strings

- `toLowerCase()`: Converts string to lowercase
- `toUpperCase()`: Converts string to uppercase
- `trim()`: Removes whitespace from both ends of a string and returns a new string, without modifying the original string
- `test()`:	Though, not a string method, it executes a search for a match between a regular expression and a specified string. Returns true or false: `test(str)`
- `match()`: Used to match regular expression against a string; retrieves the result of matching a string against a regular expression: `match(RegEx)`
- `replace()`: Returns a new string with some or all matches of a pattern replaced by a replacement. The pattern can be a string or a RegExp, and the replacement can be a string or a function to be called for each match. If pattern is a string, only the first occurrence will be replaced: `replace(regexp, newSubstr)`, `replace(regexp, replacerFunction)`, `replace(substr, newSubstr)`, or `replace(substr, replacerFunction)`

### String Methods Notes

- `charCodeAt(index)` — Gives you the Unicode of a character at that position
- `fromCharCode(num1, num2, ...)` — Returns a string created from the specified sequence of UTF-16 code units
- `valueOf()` — Returns the primitive value (that has no properties or methods) of a string object

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Other Methods unique to Arrays

- `push()`: Adds one or more elements to the end of an array and returns the new length of the array: 'push(elem1, elem2, ...)`
- `unshift()`: Adds one or more elements to the beginning of an array and returns the new length of the array: `unshift(elem1, elem2, ...)`
- `shift()`: Removes the first element from an array and returns that removed element. This method changes the length of the array (no arguments). To get the removed item make sure to set it to a var: `let removedItem = arr.shift();`
- `pop()`: Removes the last element from an array and returns that element. This method changes the length of the array (no arguments)

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### High Order Array Methods

- `forEach()`: Function to run on each item of an array, common in `for` loops, performs a function on each item in your array, similar to using a "for" loop to apply a function to an array but with much less work to code. Unlike map(), forEach() does not create a new array automatically, you would have to code a specific function to do so
- `filter()`: Takes a function containing a test and returns a new array with all the elements that pass that test. The filtration is done using a function that returns a boolean value
- `map()`: Performs a function on every element in your array and places the result in a new array
- `reduce()`: Takes a _reducer_ function and executes it on each array element to output a single value while returning. It takes a `reducer` function with an `accumulator` variable and a `current` element variable as required parameters. The accumulator's value is remembered across all the iterations and is ultimately returned after the final iteration
- `every()`: Checks if **every** element in an array pass a test, returns boolean. This have a number of variations for the syntax. Check the MDN doc [Array.prototype.every](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every).
- `some()`: Tests whether at least one element in the array passes the test implemented by the provided function. It returns true if, in the array, it finds an element for which the provided function returns true; otherwise it returns false. It doesn't modify the array. This have a number of variations for the syntax. Check the MDN doc [Array.prototype.some](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some).
- `sort()`: One of the most common operations performed on an array, used to sort an array of numbers or even strings with just a single line of code, returns original array but modified
- `reverse()`: Reverses the order of the array items, does NOT do a reverse sort
- `find()` and `findIndex()`: Returns the first element value (for `find`) or index (for `findIndex`) in the array that passes on the test provided by callback. If there is no match, it returns `undefined` (for find) or `-1` (for findIndex).
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
- Remove: `pop()`, `shift()`, `slice(start, end)`, `splice()`
- Index change: `reverse()`, `sort()`
- Various: `forEach()`, `reduce()`

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Object Notes

- Instead of using indexes to access and modify their data, you access the data in objects through what are called `properties`
- Properties are often `strings` - you can omit the quotes for single-word string properties and for numbers; property names with spaces in them must be in quotes
- Objects can be thought of as a `key`/`value` storage, like a dictionary `{word: definition}`
- There are two ways to access the properties of an object: dot notation (`.`) and bracket notation (`[]`), similar to an array. 
- Dot notation is what you use when you know the name of the property you're trying to access
- If the property of the object you are trying to access has a space in its name, you will need to use bracket notation
- It's also best to use bracket notation when a variable name is substituted for a key name, especially if the name may contain multiple words
- Use dot or bracket notation to update a property
- Testing objects for properties: use the `.hasOwnProperty(propName)` method of objects to determine if that object has the given property
- The sub-properties of objects can be accessed by chaining together the dot or bracket notation
- `Object.prototype.toString()`:	Returns a string representation of the object.
- `Object.prototype.valueOf()`:	Returns the primitive value of the specified object.
- `Object.prototype.hasOwnProperty()`:	Returns a boolean indicating whether an object contains the specified property as a direct property of that object _and not inherited through the prototype chain_.
- `Object.keys()`:	Returns an array containing the names of all of the given object's own enumerable string properties.
- `Object.values()`:	Returns an array containing the values that correspond to all of a given object's own enumerable string properties

Defining getters and setters
- A **getter** is a method that gets the value of a specific property. A **setter** is a method that sets the value of a specific property. You can define getters and setters on any predefined core object or user-defined object _that supports the addition of new properties_.

There are three native ways to list/traverse object properties:
- `for...in` loops: This method traverses all enumerable properties of an object _and its prototype chain_.
- `Object.keys(o)`: This method returns an array with all the own (not in the prototype chain) enumerable properties names ("keys") of an object `o`.
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

## Date Notes

Pulling Date and Time Values:
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

- *While loops*: runs while a specified condition is true and stops once that condition is no longer true. 
  - Be careful! It is very easy to create an infinite loop and have your computer lock up.
- *For loops*: The most common type of JavaScript loop, it runs **`for`** a specific number of times; are declared with three optional expressions separated by semicolons; it’s also common for a loop to iterate thru an array
  - `(a; b; c)`: stands for ( initialization; condition; final-expression ), or are declared with three optional expressions separated by semicolons
  - The initialization statement is executed one time only before the loop starts. It is typically used to define and setup your loop variable
  - The condition statement is evaluated at the beginning of every loop iteration and will continue as long as it evaluates to true. When the condition is false at the start of the iteration, the loop will stop executing. This means if the condition starts as false, your loop will never execute
  - The final expression is executed at the end of each loop iteration, prior to the next condition check and is usually used to increment or decrement your loop counter
- *Nested for loops*: If you have a multi-dimensional array, you can use the same logic as the prior waypoint to loop through both the array and any sub-arrays
- *Do...while loops*: it will first do one pass of the code inside the loop no matter what, and then continue to run the loop while the specified condition evaluates to true - a do...while loop ensures that the code inside the loop will run at least once
- `forEach loops`: An array method that runs a function for each element in an array
- ***Recursion***: ???

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Miscellaneous

- When JS variables are declared, they have an initial value of `undefined`. If you do a mathematical operation on an `undefined` variable your result will be `NaN`
- Remainder operator `%` - gives the remainder of the division of two numbers
- Escaping: use a backslash (`\`) in front of the quote in a string: `\'` or `\"`
- Bracket notation to find the Nth-to-last character: `string.length - n`, where `n` is a # from end
- **_Falsy_** = [`false`, `0`, `""` or `''`, `NaN`, `undefined`, and `null`]. Make sure to filter falsy values out of an array. 
- Variables which are declared without the `let` or `const` keywords are automatically created in the global scope
- Another use of bracket notation on objects is to access a property which is stored as the value of a variable (?)
- You should always name variables you don't want to reassign using the `const` keyword
- Use the spread operator to evaluate arrays, `Math.max(...arr);`
- Use destructuring assignment to extract values from objects (?)
- Use destructuring assignment w\ the rest parameter to reassign array elements
- Objects do not maintain an ordering to stored keys like arrays do; thus a key's position on an object, or the relative order in which it appears is irrelevant when referencing or accessing that key
- An algorithm is a series of step-by-step instructions that describe how to do something 
- To write an effective algorithm, it helps to break a problem down into smaller parts and think carefully about how to solve each part with code
- Constructors define properties and behaviors instead of returning a value as other functions might 
- The function passed to High Order Array Methods will run as many times as the # of items in the array it is called on 

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Basics

- Any programming language accomplishes all or some of the CRUD operations:
  - C = Create: e.g., writing to the dom, creating a copy of an array
  - R = Read: e.g., reading values from arrays, or objects
  - U = Update: Changing a value for an existing record like client/customer contact information
  - D = Delete: Removing a record
- But before you can Read, Update, or Delete, you need to check if that piece of data exists. If it does not, then you can Create it. This is done with some kind of conditional statement, often as part of an if statment, though you can also use the methods that check for something:
  - Review [Boolean methods](#boolean-methods) and [Operators and conditionals](#operators-and-conditionals) and [Loops](#loops) and [Regex](#regex) sections.

If `the thing` exists, then you can read, update and/or delete. First are READ methods. 

You can read for the purpose of 1) returning the value, or 2) returning the length or the index # (arr, str) of an item, or 3) the key name for an object:
<!--  
Return position:
| Method | Does: | Data Type:
| :----  | :----  | :---- | 
| indexOf()     | returns position | str & arr |
| lastIndexOf() | returns position | str & arr |
| .length | returns the count of items | str & arr |
| [i] | returns the value at position | str & arr |
-->

### Read and return index and length

Read / Return index # and length (no variable required unless to be used later): 
| Method          | Returns: |
| :----           | :----  |
| indexOf()       | index # |
| lastIndexOf()   | index # |
| arr.findIndex() | index # for first occurrence that passes test | 
| .length         | length of arr/str |
| arr.push()      | length of new arr after mutating arr | 
| arr.unshift()   | length of new arr after mutating arr | 

### Read and return values

Simple returns / read (more than likely requires a variable to be useful, though not necessary):
| Method        | Returns: |
| :----         | :----  |
| str[i]        | str value at index position |
| str.charAt(i) | same as above |
| arr[i]        | arr value at index position |
| arr.at(i)     | same as above, try `arr.at(-1)` for last item |
| obj.prop      | obj value for prop |
| obj[prop]     | variation of above |
| obj.prop[i]   | arr value at index position for obj prop |
| obj[prop][i]  | variation of above |

<br>

More involved returns / read:
| Method        | Returns: |
| :----         | :----  |
| arr.find()    | arr value for first occurrence that passes test |   
| arr.reduce()  | single value after function | 
| arr.shift()   | item value removed from arr | 
| arr.pop()     | item value removed from arr | 
| str.match()   | str value(s) that matches RegEx |
| Number methods | formatted number, e.g.: | 
| num.toFixed(2) | returns number with 2 decimal places |
| Math methods  | calculated number, e.g.: | 
| Math.abs(x)   | returns the absolute value of a number |
| Date Methods  | date values in various formats | 

### Create

Create (requires a variable):
| Method            | Creates: |
| :----             | :----  |
| str.trim()        | new str |
| str.substring(i)  | new str | 
| str.replace()     | new str | 
| arr.join()        | new string from array | 
| arr or str.concat() | new array or string | 
| arr.slice()       | new array | 
| arr.splice()      | new array | 
| str.split()       | new array | 
| arr.filter()      | new array |
| arr.map()         | new array |
| obj.keys()        | new array of object keys | 
| obj.values()      | new array of object values | 

### Update and mutate

Update / Mutate (assign to a variable):
| Method          | Returns: |
| :----           | :----  |
| str.replace()   | new str with updated values |
| str.toLowerCase() | returns str as lowercase |  
| str.toUpperCase() | returns str as uppercase |
| arr.splice(i)   | changes array contents | 
| arr.push()      | changes array contents | 
| arr.unshift()   | changes array contents | 
| arr.shift()     | changes array contents | 
| arr.pop()       | changes array contents | 
| arr.sort()      | changes array order | 
| arr.reverse()   | changes array order | 
| obj[prop] = val | change property value, or set if empty |
| obj.prop = val  | variation of above |


> Look into `arr.entries()` in conjuction with `.next().value`. Also, obj.entries() is confusing as well.

> What about assigning with a variable name and value? Where does that fit in?

BOOLEAN:
- includes()
- endsWith(()
- obj.hasOwnProperty()
- str.test()
- arr.every()
- arr.some() 