# Arrays and Strings

### Strings and Arrays: Same Methods, Same Effect

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

Strings and Arrays: Different Methods, Same Effect
|    Method       | Returns:               |  Code         | 
| :-------------  | :--------------------: | :-----------: |
| str.charAt() | Returns the character at the specified index | charAt(index) | 
| arr.at()     | Returns the array item at the given index    | at(index)     | 
| str.substring() | Returns part of a string              | substring(indexStart)|
| arr.splice() | Adds/Removes elements from an array | splice(start) |

Additional notes:
- `arr.at()`: Accepts negative #’s, which counts from back
- `str.substring()`: returns the part of the string between the start and end indexes, or to the end of the string
  - Alernate: `substring(indexStart, indexEnd)`
- `arr.splice()`: changes the contents of an array by removing or replacing existing elements and/or adding new elements
  - Alternate: `splice(start, deleteCount)`



### Strings and Arrays: Different Methods, Opposite Effect

> These two are used in unison, first to split a string, then to join. 

|    Method       | Returns:               |  Code         | 
| :-------------  | :--------------------: | :-----------: |
| split()  | divides str into substrings | str.split() | 
| join()  | Joins all elements of an array into a string | arr.join() | 

Additional notes:
- `str.split()` alternate code: `split(separator)`, `split(separator, limit)`
- `arr.join()` alternate code: `join(separator)`


### Common Methods unique to Strings

- toLowerCase(): self-explanatory
- toUpperCase(): self-explanatory
- trim(): removes whitespace from both sides of a string


### Common Methods unique to Arrays
- every(): Checks if **every** element in an array pass a test, returns boolean
- some(): Checks if any of the elements in an array pass a test, returns boolean
- push(): adds item onto the end of an array, requires an argument, mutates array
- unshift(): adds item onto the beginning of an array, requires an argument, mutates array
- shift(): removes 1st item in an array, no argument, mutates array
- pop(): removes last item in an array, no argument, mutates array


### Higher Order Array Methods
- `filter()`: ?
- `forEach()`: function to run on each item of an array, common in `for` loops
- `map()`: ?
- `reduce()`: ?
- `sort()`: self-explanatory
- `reverse()`: reverse sort (why use?)

## Array Methods Notes

- `.length`: used often in `for` loops
- arr.[index]: to return a value at a specific index

Returns Boolean:
- `every()`:	Checks if every element in an array pass a test
- `includes()`:	Check if an array contains the specified element
- `some()`: Checks if any of the elements in an array pass a test

Returns String
- `join()`: **Combines** elements of an array into a single string and **returns** the string
- `toString()`: **Converts** an array to a string  and returns the result

Anything:
- `forEach()`: Calls a function for each array element

Returns Array
- `filter()`:	**Creates** a new array with every element in an array that pass a test
- `map()`: **Creates** a new array with the result of calling a function for each array element
- `concat()`:	**Joins** two or more arrays and returns a copy of the joined arrays

Return Value/Position
- `find()`	Returns the **value** of the first element in an array that pass a test
- `indexOf()`: Returns the first **position** at which a given element appears in an array. Compare with `lastIndexOf()`.
- `reduce()`: Reduce the **values** of an array to a single value (going left-to-right)

Add, remove, sort
- `pop()`: Removes the last element of an array and returns that element
- `shift()`: Removes the first element of an array and returns that element
- `push()` Adds new elements to the end of an array and returns the new length
- `unshift()`: Adds new elements to the beginning of an array and returns the new length
- `slice(start, end)`: Selects a part of an array and returns the **new** array
- `splice()`: Adds/Removes elements from an array. Changes the contents of an array by removing or replacing existing elements and/or adding new elements
- `reverse()`: Sort elements in a descending order
- `sort()`: Sorts elements alphabetically


# Strings

## String Methods Notes

There are many different ways to work with strings:

- `charAt()` — Returns a character at a specified position inside a string
- `charCodeAt()` — Gives you the Unicode of a character at that position
- `concat()` — Concatenates (joins) two or more strings into one
- `fromCharCode()` — Returns a string created from the specified sequence of UTF-16 code units
- `indexOf()` — Provides the position of the first occurrence of a specified text within a string
- `lastIndexOf() `— Same as indexOf() but with the last occurrence, searching backward
- `match()` — Retrieves the matches of a string against a search pattern
- `replace()` — Find and replace specified text in a string
- `search()` — Executes a search for a matching text and returns its position
- `slice()` — Extracts a section of a string and returns it as a new string
- `split()` — Splits a string object into an array of strings at a specified position
- `substr()` —  Similar to slice() but extracts a substring depending on a specified number of characters
- `substring()` — Also similar to slice() but can’t accept negative indices
- `toLowerCase()` — Convert strings to lower case
- `toUpperCase()` — Convert strings to upper case
- `valueOf()` — Returns the primitive value (that has no properties or methods) of a string object