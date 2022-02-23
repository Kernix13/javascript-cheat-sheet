# Arrays and Strings

There are methods in common to both arrays and strings so I am combining them for more easily visualixe them. Check out the following MDN links:

- [MDN String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)
- [MDN Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

## Strings and Arrays: Same Methods, Same Effect

|    Method   | Purpose: | Returns:   | Arr basic code | Str basic code | 
| :---------- | -------: | :------:   | :------------: | :-----------:  |
| slice()     | creates: | new str/arr | arr.slice(start, end) | str.slice(start, end) | 
| concat()    | creates: | new str/arr | arr1.concat(arr2) | str1.concat(' ', str2)  | 
| includes()  | checks:  | Boolean    | includes(searchVal) | includes(searchStr) | 
| endsWith(()* | checks: | Boolean    | -                   | endsWith(searchString) | 
| indexOf()   | returns: | index #    | indexOf(searchVal)  | indexOf(searchStr) | 
| lastIndexOf() | returns: | index #  | lastIndexOf(searchVal) | lastIndexOf(searchStr) |
| [index]     | returns: | specific value | arr.[index]     | str[index] | 
| length      | returns: | str/arr len | arr.length         | str.length | 

In detail:
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

## Strings and Arrays: Different Methods, Same Effect

|    Method       | Returns:               |  Code         | 
| :-------------  | :--------------------: | :-----------: |
| str.charAt() | Returns the character at the specified index | str.charAt(index) | 
| arr.at()     | Returns the array item at the given index    | arr.at(index)     | 
| str.substring() | Returns part of a string                  | str.substring(indexStart)|
| arr.splice() | Adds/Removes elements from an array          | arr.splice(start) |

Additional notes:
- `arr.at()`: Accepts negative #’s, which counts from back
- `str.substring()`: returns the part of the string between the start and end indexes, or to the end of the string
  - Alernate: `substring(indexStart, indexEnd)`
- `arr.splice()`: changes the contents of an array by removing or replacing existing elements and/or adding new elements
  - Alternate: `splice(start, deleteCount)`

## Strings and Arrays: Different Methods, Opposite Effect

> These two are used in unison, first to split a string, then to join. 

|    Method       | Returns:               |  Code         | 
| :-------------  | :--------------------: | :-----------: |
| split()  | divides str into substrings | str.split() | 
| join()  | Joins all elements of an array into a string | arr.join() | 

Additional notes:
- `str.split()` alternate code: `split(separator)`, `split(separator, limit)`
- `arr.join()` alternate code: `join(separator)`


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

## Array Methods Notes

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