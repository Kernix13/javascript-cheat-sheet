# JAVASCRIPT CHEAT SHEET

This is not an all-inclusive list of every possible JavaScript method, property, etc. 

**use `every()` to compare one array to other arrays and to return a match:**

```js
   const hasSameElements = (a, b) => {
       return a.length === b.length && a.every((v,i) => v===b[i])
   }
```

Js methods and functions that return true or false: 
- Comparison operators: ==, ===, !=, !==, <, <=, >, >=, &&, ||, 
- valueOf(): 
- hasOwnProperty(): Checks for
- Object.is(a, b): Checks for
- isArray(): Checks for
- every(): Checks for
- some(): Checks for
- incudes(): Checks for
- endsWith(): Checks for
- `in` operator: Checks for
- `isInteger()`: Checks for
- typeof with a comparison operator, <, <=, >, or >= with return before the comparison: ????????

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

Operators:
| Type       | Type 1 | Type 2 | Type 3  | Type 4  | Type 5 | 
| :--------- | :----- | :----- | :------ | :------ | :------ | 
| Assigment  | =      | +, +=  | -, -=   | *, -=   | /, /=   |
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
| if `a` exists             | (a)    |
| if `a` doesn't exist      | (!a)   |
| **all** things true      | &&     |
| 2 **or** more things true | \|\|   |
| ternary operator          | a ? b : c |

<br>

var, let, const:
| Topic  | var  | let     | const  |
| :--------  | :----: | :---: | :----: |
| Scope      | Global | Block | Block |
| Overwrite? | Yes    | No    | No    |
| Updated?   | Yes    | Yes   | No    |
| Redeclared? | Yes  | No    | No    |
| Hoisted?   | Yes    | Yes   | Yes   | 
| initialized? | undefined | No | No  |

<br>

Strings and Arrays: Same Methods, Same Effect:
|    Method   | Purpose: | Returns:   | Arr basic code | Str basic code | 
| :---------- | -------: | :------:   | :------------: | :-----------:  |
| slice()     | creates: | new str/arr | arr.slice(start, end) | str.slice(start, end) | 
| concat()    | creates: | new str/arr | arr1.concat(arr2) | str1.concat(' ', str2)  | 
| includes()  | checks:  | Boolean    | includes(searchVal) | includes(searchStr) | 
| endsWith(()* | checks: | Boolean    | -                   | endsWith(searchStr) | 
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
