# JAVASCRIPT CHEAT SHEET

This is not an all-inclusive list of every possible JavaScript method, property, etc. This file has tables of comparisons or for quick reference. 

**use `every()` to compare one array to other arrays and to return a match:**

```js
const hasSameElements = (a, b) => {
    return a.length === b.length && a.every((v,i) => v===b[i])
}
// But do the elements need to be in the same order?
```



## Table Comparisons

Math:
|    Purpose      | Symbol | 
| :-----------    | :----: |
| Addition        | +      |
| Subtraction     | -      | 
| Multiplication  | *      |
| Division        | /      | 
| Remainder       | %      |

<br>

var, let, const:
| Topic                | var       | let                  | const                |
| :--------            | :----:    | :---:                | :----:               |
| Scope                | Global    | Block                | Block                |
| Declared (no value)  | undefined | undefined            | Uncaught SyntaxError |
| Redeclared?          | Yes       | Uncaught SyntaxError | Uncaught SyntaxError |
| Reassigned?          | Yes       | Yes                  | Uncaught TypeError   |

Code examples showing results with `console.log()`:

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


<br>

Js methods and functions that return true or false: 

| Comparison:       | Checks against:               |
| :----------       | :--------------               |
| <, >, <=, >, >=   | number, .length, typeof, ...  |
| !=, !==           | Anything |
| &&. \|\|          | Checking multiple and/or conditions |
| hasOwnProperty()  | If an object has a property   | 
| Object.is(a, b)   | if 2 values are the same value |
| isArray()         | If item checked is an array   |
| every()           | if ALL elements pass a test   |
| some()            | if at least ONE element passes a test |
| incudes()         | if arr or str contains the search value |
| endsWith()        | if str ends with the search value |
| isInteger()       | if value is an integer            |
| in operator       | if property is in the object or prototype | 
| typeof            | Check for a specific type         | 

<br>

Operators:
| Type       | Type 1 | Type 2 | Type 3  | Type 4  | Type 5 | 
| :--------- | :----- | :----- | :------ | :------ | :------ | 
| Assigment  | =      | +=     | -=      | *=      | /=      |
| Comparison | <, >   | <=, >= | ==, === | !=, !== |         |
| Arithmetic | %      | ++     | --      |         |         |
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
| if      | if (cond) {run} |                      |              |          |           |   
| else    | if (cond) {run} | else {run}           |              |          |           |
| else if | if (cond) {run} | else if (cond) {run} | `else {run}` |          |           |
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
| [index]     | returns: | specific value | arr.[index]     | str[index] | 
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
| Method               | Returns: | Returns what?       |
| :------------------- | :------- | :-------            |       
| obj.keys()           | array    | obj property names  |
| obj.values()         | array    | obj property values |
| obj.toString()       | string   | obj as a string     |
| obj.hasOwnProperty() | boolean  | if obj has (prop)   |
| obj.getOwnPropertyNames() | array | all prop names except symbols |

<br>

Number Methods

| Method | Returns: | Result/Purpose: | 
| :---   | :------ | :---- |
| toExponential() | string | rounded, exp. notation |
| toFixed() | string | specified decimal places | 
| toPrecision() | string | specified length |
| toString() | string | number to string | 
