# JAVASCRIPT CHEAT SHEET

This is not an all-inclusive list of every possible JavaScript method, property, etc. This file has tables of comparisons or for quick reference. 

<div id="back-to-top"></div>

## Table of Contents

1. Table Comparisons
   1. [Data types](#data-types)
   1. [Math and variables](#math-and-variables)
   1. [Boolean methods](#boolean-methods)
   1. [Operators and conditionals](#operators-and-conditionals)
   1. [String and array methods](#string-and-array-methods)
   1. [Object methods](#object-methods)
   1. [Number Methods](#number-methods)
   1. [Date methods](#date-methods)
   1. [Console Commands](#console-commands)
1. [Important Notes](#important-otes)
1. [Miscellaneous](#miscellaneous)
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
1. [Date Notes](#date-notes)

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
| `keys`   | keys are strings and are the *name* of the property |
| `value`  | the value that foloows `"keyName": value`|

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Math and variables

Basic math operators:
|    Purpose      | Symbol | 
| :-----------    | :----: |
| Addition        | +      |
| Subtraction     | -      | 
| Multiplication  | *      |
| Division        | /      | 
| **Remainder**       | %      |

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

| Type:                | Checks against:                      |
| :----------          | :--------------                      |
| <, >, <=, >= | number, .length, typeof, ...         |
| !=, !==          | Anything                             |
| &&, \|\|         | Checking multiple and/or conditions  |
| hasOwnProperty()   | If an object has a property          | 
| obj.is(a, b)       | if 2 values are the same value       |
| isArray()          | If item checked is an array          |
| every()            | if ALL elements pass a test          |
| some()             | if at least ONE element passes a test |
| incudes(val)       | if arr or str contains the search value |
| endsWith(val)      | if str ends with the search value    |
| isInteger()        | if value is an integer               |
| in operator        | if property is in the object or prototype | 
| typeof             | used with ==, ===, !=, !==           |

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Operators and conditionals

Operators:
| Type       | Ex. 1  | Ex. 2  | Ex. 3   | Ex. 4   | Ex. 5  | 
| :--------- | :----- | :----- | :------ | :------ | :------ | 
| Assigment  | =      | +=     | -=      | *=      | /=      |
| Comparison | <, >   | <=, >= | ==, === | !=, !== |         |
| Arithmetic | +, -, *, /      | %      | ++      | --      |         |
| Logical    | &&     | \|\|   | !       |         |         |
| String     | =      | +      | +=      |         |         |

<br>

Loop specific:
|    Purpose          | Symbol | 
| :-----------        | :----: |
| Loop addition       | +=     |
| Loop subtraction    | -=     |
| Loop multiplication | *=     |
| Loop division       | /=     |
| Loop increment      | ++     |
| Loop decrement      | --     |

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
| else if | if (a) {run} | else if (a) {run} | `else {run}` |          |           |
| ternary | a ? b : c       |                      |              |          |           |
| switch  | switch(val)     |  case "a":           | {run}        | `break`  | `default` | 

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### String and array methods

Strings and Arrays: Same Methods, Same Effect:
|    Method   | Purpose: | Returns:   | Arr basic code | Str basic code | 
| :---------- | -------: | :------:   | :------------: | :-----------:  |
| slice()     | creates: | new str/arr | arr.slice(start, end) | str.slice(start, end) | 
| concat()    | creates: | new str/arr | arr1.concat(arr2) | str1.concat(' ', str2)  | 
| concat. operator| creates: | new str | -             | str1 + str2    |
| includes()  | checks:  | Boolean    | includes(searchVal) | includes(searchStr) | 
| endsWith(() | checks:  | Boolean    | -                   | endsWith(searchStr) | 
| indexOf()   | returns: | index #    | indexOf(searchVal)  | indexOf(searchStr) | 
| lastIndexOf() | returns: | index #  | lastIndexOf(searchVal) | lastIndexOf(searchStr) |
| [index]     | returns: | specific value | arr[index]     | str[index] | 
| length      | returns: | str/arr len | arr.length         | str.length | 

<br>

Strings and Arrays: Different Methods, Same Effect: 
|    Method       | Returns:               |  Code         | 
| :-------------  | :--------------------: | :-----------: |
| str.charAt() | Returns the character at the specified index | str.charAt(index) | 
| arr.at()     | Returns the array item at the given index    | arr.at(index)     | 
| str.substring() | Returns part of a string                  | str.substring(indexStart)|
| arr.splice() | Adds/Removes elements from an array          | arr.splice(start) |

<br>

Strings and Arrays: Different Methods, Opposite Effect

|    Method       | Returns:               |  Code         | 
| :-------------  | :--------------------: | :-----------: |
| split()  | divides str into substrings | str.split() | 
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
| obj.prop[i] or obj.[prop][i] | value | values for array in object at position i |
| obj.prop.length      | value    | length of array in object |

<br>

Object Class syntax and terms (Fx = 'function'):
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

Number Methods

| Method | Returns: | Result/Purpose: | 
| :---   | :------ | :---- |
| toExponential() | string | rounded, exp. notation |
| toFixed() | string | specified decimal places | 
| toPrecision() | string | specified length |
| toString() | string | number to string | 

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

## Miscellaneous

- When JS variables are declared, they have an initial value of `undefined`. If you do a mathematical operation on an `undefined` variable your result will be `NaN`
- Remainder operator `%` - gives the remainder of the division of two numbers
- Escaping: use a backslash (`\`) in front of the quote in a string: `\'` or `\"`
- Bracket notation to find the Nth-to-last character: `string.length - n`, where `n` is a # from end

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

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
- `trim()`: removes whitespace from both ends of a string and returns a new string, without modifying the original string
- `test()`:	Though, not a string method, it executes a search for a match between a regular expression and a specified string. Returns true or false: `test(str)`
- `match()`: Used to match regular expression against a string; retrieves the result of matching a string against a regular expression: `match(RegEx)`
- `replace()`: returns a new string with some or all matches of a pattern replaced by a replacement. The pattern can be a string or a RegExp, and the replacement can be a string or a function to be called for each match. If pattern is a string, only the first occurrence will be replaced: `replace(regexp, newSubstr)`, `replace(regexp, replacerFunction)`, `replace(substr, newSubstr)`, or `replace(substr, replacerFunction)`

### String Methods Notes

- `charCodeAt(index)` — Gives you the Unicode of a character at that position
- `fromCharCode(num1, num2, ...)` — Returns a string created from the specified sequence of UTF-16 code units
- `valueOf()` — Returns the primitive value (that has no properties or methods) of a string object

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Other Methods unique to Arrays

- `push()`: adds one or more elements to the end of an array and returns the new length of the array: 'push(elem1, elem2, ...)`
- `unshift()`: adds one or more elements to the beginning of an array and returns the new length of the array: `unshift(elem1, elem2, ...)`
- `shift()`: removes the first element from an array and returns that removed element. This method changes the length of the array (no arguments). To get the removed item make sure to set it to a var: `let removedItem = arr.shift();`
- `pop()`: removes the last element from an array and returns that element. This method changes the length of the array (no arguments)

### High Order Array Methods

- `forEach()`: function to run on each item of an array, common in `for` loops, performs a function on each item in your array, similar to using a "for" loop to apply a function to an array but with much less work to code. Unlike map(), forEach() does not create a new array automatically, you would have to code a specific function to do so
- `filter()`: takes a function containing a test and returns a new array with all the elements that pass that test. The filtration is done using a function that returns a boolean value
- `map()`: performs a function on every element in your array and places the result in a new array
- `reduce()`: takes a reducer function and executes it on each array element to output a single value while returning. It takes a `reducer` function with an `accumulator` variable and a `current` element variable as required parameters. The accumulator's value is remembered across all the iterations and is ultimately returned after the final iteration
- `every()`: Checks if **every** element in an array pass a test, returns boolean. This have a number of variations for the syntax. Check the MDN doc [Array.prototype.every](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every).
- `some()`: tests whether at least one element in the array passes the test implemented by the provided function. It returns true if, in the array, it finds an element for which the provided function returns true; otherwise it returns false. It doesn't modify the array. This have a number of variations for the syntax. Check the MDN doc [Array.prototype.some](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some).
- `sort()`: one of the most common operations performed on an array, used to sort an array of numbers or even strings with just a single line of code, returns original array but modified
- `reverse()`: reverses the order of the array items, does NOT do a reverse sort
- `find()`: return the first element value (for find) or index (for findIndex) in the array that passes on the test provided by callback. If there is no match, it returns undefined (for find) or -1 (for findIndex).
- Link: [Mastering ES6 higher-order functions for Arrays](https://www.airpair.com/javascript/posts/mastering-es6-higher-order-functions-for-arrays).

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Array Methods Notes

- `.length`: used often in `for` loops
- arr.[index]: to return a value at a specific index
- Returns Boolean: `every()`, `includes()`, `some()`
- Returns String: `join()`, `toString()`
- Various: `forEach()`, `reduce()`
- Return New Array: `filter()`, `map()`, `concat()`
- Return Value/Position: `find()`, `indexOf()`, `lastIndexOf()`, 
- Add:  `push()', `unshift()`,  
- Remove: `pop()`, shift()`, `slice(start, end)`, `splice()`
- Index change: `reverse()`, `sort()`

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Object Notes

- instead of using indexes to access and modify their data, you access the data in objects through what are called `properties`
- Properties are often `strings` - you can omit the quotes for single-word string properties; property names with spaces in them must be in quotes
- Objects can be thought of as a `key`/`value` storage, like a dictionary `{word: definition}`
- There are two ways to access the properties of an object: dot notation (`.`) and bracket notation (`[]`), similar to an array. 
- Dot notation is what you use when you know the name of the property you're trying to access
- If the property of the object you are trying to access has a space in its name, you will need to use bracket notation
- Use dot or bracket notation to update a property
- Testing objects for properties: use the `.hasOwnProperty(propname)` method of objects to determine if that object has the given property name
- The sub-properties of objects can be accessed by chaining together the dot or bracket notation

Defining getters and setters
- A **getter** is a method that gets the value of a specific property. A **setter** is a method that sets the value of a specific property. You can define getters and setters on any predefined core object or user-defined object that supports the addition of new properties.

- `Object.prototype.toString()`:	Returns a string representation of the object.
- `Object.prototype.valueOf()`:	Returns the primitive value of the specified object.
- `Object.prototype.hasOwnProperty()`:	Returns a boolean indicating whether an object contains the specified property as a direct property of that object and not inherited through the prototype chain.

There are three native ways to list/traverse object properties:
- `for...in` loops: This method traverses all enumerable properties of an object and its prototype chain.
- `Object.keys(o)`: This method returns an array with all the own (not in the prototype chain) enumerable properties' names ("keys") of an object o.
- `Object.getOwnPropertyNames(o)`: This method returns an array containing all own properties' names (enumerable or not) of an object o.

- `Object.keys()`:	Returns an array containing the names of all of the given object's own enumerable string properties.
- `Object.values()`:	Returns an array containing the values that correspond to all of a given object's own enumerable string properties

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Date Notes

Pulling Date and Time Values:
- `getUTCDate()` — The day (date) of the month in the specified date according to universal time (also available for day, month, full year, hours, minutes etc.)
- `parse` — Parses a string representation of a date and returns the number of milliseconds since January 1, 1970

Pulling Date and Time Values:

- `getDate()`: returns the day of the month for the specified date according to local time as a number (1-31)
- `getDay()`: returns the day of the week as a number (0-6) for the specified date according to local time, where 0 represents Sunday 
- `getFullYear()`: returns the year as a four-digit number (yyyy) of the specified date according to local time 
- `getHours()`: Get the hour (0-23), returns the hour for the specified date, according to local time
- `getMilliseconds()`: The millisecond (0-999), returns the milliseconds in the specified date according to local time
- `getMinutes()`: Get the minute (0-59), returns the minutes in the specified date according to local time
- `getMonth()`: Month as a number (0-11)m returns the month in the specified date according to local time, as a zero-based value (where zero indicates the first month of the year)
- `getSeconds()`: Get the second (0-59), returns the seconds in the specified date according to local time
- `getTime()`: Get the milliseconds since January 1, 1970, returns the number of milliseconds since the ECMAScript epoch

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