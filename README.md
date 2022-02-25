# JAVASCRIPT CHEAT SHEET

This is not an all-inclusive list of every possible JavaScript method, property, etc. This file has tables of comparisons or for quick reference. 

## Table Comparisons

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

<br>

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

<br>

Js methods that return true or false: 

| Comparison:       | Checks against:               |
| :----------       | :--------------               |
| `<`, `>`, `<=`, `>=`      | number, .length, typeof, ...  |
| `!=`, `!== `          | Anything |
| `&&`, `\|\|`         | Checking multiple and/or conditions |
| `hasOwnProperty()`  | If an object has a property   | 
| `obj.is(a, b)`   | if 2 values are the same value |
| `isArray() `        | If item checked is an array   |
| `every()`           | if ALL elements pass a test   |
| `some() `           | if at least ONE element passes a test |
| `incudes(val)`         | if arr or str contains the search value |
| `endsWith(val) `       | if str ends with the search value |
| `isInteger() `      | if value is an integer            |
| `in` operator       | if property is in the object or prototype | 

<br>

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

<br>

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

> These two are used in unison, first to split a string, then to join. 

|    Method       | Returns:               |  Code         | 
| :-------------  | :--------------------: | :-----------: |
| split()  | divides str into substrings | str.split() | 
| join()  | Joins all elements of an array into a string | arr.join() | 

<br>

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

<br>

Number Methods

| Method | Returns: | Result/Purpose: | 
| :---   | :------ | :---- |
| toExponential() | string | rounded, exp. notation |
| toFixed() | string | specified decimal places | 
| toPrecision() | string | specified length |
| toString() | string | number to string | 

<br>

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

- console.time: requires timeEnd as well to work. Put time before the function and timeEnd after the function