# String method examples

Syntax and code examples for the most coomon string methods.

<div id="back-to-top"></div>

## Table of contents

| Topic               | Sub-topic | Sub-topic | Sub-topic | Sub-topic |  
| ----:               | :-------    | :------     | :------     | :------     |
| 1. [String methods](#string-methods): | i. [Skipped methods](#skipped-methods) | ii. [split](#split) | iii. [substring](#substring) | iv. [repeat](#repeat) |
|           | v. [endsWith](#endsWith) | vi. [test](#test) | vii. [charAt](#charat) | viii. [charCodeAt](#charcodeat) |
|           | ix. [fromCharCode](#fromcharcode) | x. [match](#match) | xi. [replace](#replace) | xii. [toString](#tostring) |
|           | xiii. [Miscellaneous](#Miscellaneous) |  | |  |
| 2. [Array string methods](#array-string-methods): | i. [String slice](#string-slice) | ii. [concat](#concat) | iii. [indexOf](#indexof) | iv. [lastIndexOf](#lastindexof) |
|           | i. [includes](#includes) |  | |  |
| 3. [Syntax tables](#syntax-tables) |  |  |  |  |


## String methods

`str.toLowerCase()`, `str.toUpperCase()`, and `str.trim()` are so basic that I am not providing examples. Just attach one of these methods to the variable name for your string, e.g.:

```js
let badString = "   oOPS, caps LOCK ON. nEED TO FIX.   "
console.log(badString.toLowerCase().trim()); // "oops, caps lock on. need to fix."
// need to capitalize first letter and add a regex for the first char after the period.
```

### Skipped methods

I skipped these methods: 

- [at()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/at): takes an integer value and returns a new String consisting of the single UTF-16 code unit located at the specified offset. This method allows for positive and negative integers. Negative integers count back from the last string character.
- [codePointAt()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/codePointAt): returns a non-negative integer that is the Unicode code point value at the given position.
- [fromCodePoint()](): returns a string created by using the specified sequence of code points.
- [localeCompare()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/localeCompare): returns a number indicating whether a reference string comes before, or after, or is the same as the given string in sort order.
- [matchAll()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/matchAll): returns an iterator of all results matching a string against a regular expression, including capturing groups.
- [normalize()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/normalize): returns the Unicode Normalization Form of the string.
- [padEnd()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/padEnd): pads the current string with a given string (repeated, if needed) so that the resulting string reaches a given length. The padding is applied from the end of the current string.
- [padStart()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/padStart): pads the current string with another string (multiple times, if needed) until the resulting string reaches the given length. The padding is applied from the start of the current string.
- [replaceAll()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replaceAll): returns a new string with all matches of a pattern replaced by a replacement. The pattern can be a string or a RegExp, and the replacement can be a string or a function to be called for each match.
- [search()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/search): executes a search for a match between a regular expression and this String object.
- [startsWith()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/startsWith): determines whether a string begins with the characters of a specified string, returning true or false as appropriate.
- [toLocaleLowerCase()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/toLocaleLowerCase): returns the calling string value converted to lower case, according to any locale-specific case mappings. 
- [toLocaleUpperCase()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/toLocaleUpperCase): returns the calling string value converted to upper case, according to any locale-specific case mappings. 
- [trimEnd()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/trimEnd): removes whitespace from the end of a string. trimRight() is an alias of this method.
- [trimStart()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/trimStart): removes whitespace from the beginning of a string. trimLeft() is an alias of this method.
- [valueOf()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/valueOf): returns the primitive value of a String object.

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### split

Divides a string into substrings, puts these substrings into an array, and **<ins>returns that array</ins>**. Does not mutate the string.

MDN syntax:
```js
split()
split(separator)
split(separator, limit)
```

<br /> 

Examples:
```js
// split()
let str = "The split method"
console.log(str.split()) // "The split method"
// split(separator)
console.log(str.split('')) // ["T","h","e"," ","s","p","l","i","t"," ","m","e","t","h","o","d"]
let str2 = str.split(' ')
console.log(str2, str) // ["The","split","method"] "The split method"
// split(separator, limit)
let str2 = str.split('', 2)
console.log(str2, str) // ["T","h"] "The split method"
let str2 = str.split(' ', 2)
console.log(str2, str) // ["The","split"] "The split method"


let str = "this is a sentence";
let letters = str.split('');
console.log(letters); // ["t","h","i","s"," ","i","s"," ","a"," ","s","e","n","t","e","n","c","e"]
let letters = str.split(' ');
console.log(letters); // ["this","is","a","sentence"]


const str = 'Using the split method on this string';
const words = str.split(' ');
console.log(words[3]); // "method"
const chars = str.split('');
console.log(chars[8]); // e


// Removing spaces from a string - EXCELLENT!
const names = 'Harry Trump ;Fred Barney; Helen Rigby ; Bill Abel ;Chris Hand ';
const re = /\s*(?:;|$)\s*/
const nameList = names.split(re)
console.log(nameList) // ["Harry Trump","Fred Barney","Helen Rigby","Bill Abel","Chris Hand",""]


// Returning a limited number of splits
const myString = 'Hello World. How are you doing?'
const splits = myString.split(' ', 3)
console.log(splits) // ["Hello","World.","How"]
```

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/split">MDN Split</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### substring

**<ins>Returns the part of the string</ins>** between the start and end indexes, or to the end of the string. Does not mutate the string.

MDN syntax and examples:
```js
// syntax:
substring(indexStart)
substring(indexStart, indexEnd)


const str = 'Mozilla';
console.log(str.substring(1, 3)); // "oz"
console.log(str.substring(2)); // "zilla"


// Using substring() with length property
let anyString = 'Mozilla'
let anyString4 = anyString.substring(anyString.length - 4)
console.log(anyString4); // "illa"

let anyString = 'Mozilla'
let anyString5 = anyString.substring(anyString.length - 5)
console.log(anyString5) // "zilla"


// Differences between substring() and slice()
let text = 'Mozilla'
console.log(text.substring(5, 2)) // => "zil"
console.log(text.slice(5, 2)) // => ""


// Replacing a substring within a string
function replaceString(oldS, newS, fullS) {
  for (let i = 0; i < fullS.length; ++i) {
    if (fullS.substring(i, i + oldS.length) == oldS) {
      fullS = fullS.substring(0, i) + newS + fullS.substring(i + oldS.length, fullS.length)
    }
  }
  return fullS
}
console.log(replaceString('World', 'Web', 'Brave New World')) // "Brave New Web"
// Better method for replacing strings:
function replaceString(oldS, newS, fullS) {
  return fullS.split(oldS).join(newS)
}
```

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/substring">MDN substring</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### repeat

Constructs and **<ins>returns a new string</ins>** which contains the specified number of copies of the string on which it was called, concatenated together.

MDN syntax and examples::
```js
// syntax
repeat(count)

const chorus = 'Because I\'m happy. ';
console.log(`Chorus lyrics for "Happy": ${chorus.repeat(5)}`);
'abc'.repeat(2) // 'abcabc'
'abc'.repeat(3.5)   // 'abcabcabc' (count will be converted to integer)
'abc'.repeat(-1)    // RangeError
```

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/repeat">MDN Repeat</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### endsWith

Determines whether a string ends with the characters of a specified string. **<ins>Returns `true` or `false`</ins>**.

MDN syntax and eamples:
```js
// syntax:
endsWith(searchString)
endsWith(searchString, length)


const str1 = 'Cats are the best!';
console.log(str1.length) // 18
console.log(str1.endsWith('best', 17));


const str2 = 'Is this a question'; // true
console.log(str2.endsWith('?')); // false


let str = 'To be, or not to be, that is the question.'
console.log(str.endsWith('question.'))  // true
console.log(str.endsWith('to be'))      // false
console.log(str.endsWith('to be', 19))  // true
```

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/endsWith">MDN endsWith</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### test

Executes a search for a match between a regular expression and a specified string. **<ins>Returns `true` or `false`</ins>**. This is not a string method but it is often used on strings.

MDN syntax and examples:
```js
test(str)


const str = 'table football';
const regex = /foo*/;
console.log(regex.test(str)); // true


const str = 'hello world!';
const result = /^hello/.test(str);
console.log(result); // true
```

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/test">MDN Test</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### charAt

**<ins>Returns a new string</ins>** consisting of the single UTF-16 code unit located at the specified offset into the string.

```js
charAt(index)

const sentence = 'The quick brown fox jumps over the lazy dog.';
const index = 4;
console.log(`The character at index ${index} is ${sentence.charAt(index)}`);
// expected output: "The character at index 4 is q"

var anyString = 'Brave new world';
console.log("The character at index 1   is '" + anyString.charAt(1)   + "'"); // "B"
```

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/charAt">MDN charAt</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### charCodeAt

**<ins>Returns an integer</ins>** between `0` and `65535` representing the UTF-16 code unit at the given index.

```js
// syntax
charCodeAt(index)

// MDN examples
const sentence = 'The quick brown fox jumps over the lazy dog.';
const index = 4;
console.log(`The character code ${sentence.charCodeAt(index)} is equal to ${sentence.charAt(index)}`);
// expected output: "The character code 113 is equal to q"
console.log('ABC'.charCodeAt(0)); // 65
console.log('ABC'.charCodeAt(1)); // 66
console.log('ABC'.charCodeAt(2)); // 67
console.log('abc'.charCodeAt(0)); // 97, see below
```

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/charCodeAt">MDN charCodeAt</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### fromCharCode

**<ins>Returns a string</ins>** created from the specified sequence of UTF-16 code units.

```js
// syntax
String.fromCharCode(num1)
String.fromCharCode(num1, num2)
String.fromCharCode(num1, num2, ..., numN)

// Examples
console.log(String.fromCharCode(189, 43, 190, 61)); // "½+¾="
console.log(String.fromCharCode(65, 66, 67, 68)); // "ABCD"
console.log(String.fromCharCode(97, 98, 99, 100)); // "abcd"
```

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/fromCharCode">MDN fromCharCode</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### match

Used to match regular expression against a string. **<ins>Returns an array of the match(es)</ins>** or **`null`** if no matches are found.

MDN syntax and examples:
```js
match(regexp)

// Example 1
const paragraph = 'The quick brown FOX jumps over the lazy dog. It barked.';
const regex = /[A-Z]/g;
const found = paragraph.match(regex);
console.log(found); // ["T","F","O","X","I"]


// Example 2
const paragraph = 'The quick brown fox jumps over the lazy dog. It barked.';
const capturingRegex = /(?<animal>fox|cat) jumps over/;
const found = paragraph.match(capturingRegex);
console.log(found.groups); // {animal: "fox"}
```

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/match">MDN Match</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### replace

**<ins>Returns a new string</ins>** with some or all matches of a `pattern` replaced by a `replacement`. The `pattern` can be a string or a `RegExp`, and the `replacement` can be a string or a function to be called for each match. If `pattern` is a string, only the first occurrence will be replaced.

MDN syntax:
```js
replace(regexp, newSubstr)
replace(regexp, replacerFunction)

replace(substr, newSubstr)
replace(substr, replacerFunction)
```

<br />

Examples
```js
// Example 1
const p = 'The quick brown fox jumps over the lazy dog.';
console.log(p.replace('dog', 'monkey')); // "The quick brown fox jumps over the lazy monkey."


// Example 2
const regex = /Dog/i;
console.log(p.replace(regex, 'ferret')); // "The quick brown fox jumps over the lazy ferret."


// Example 3
let str = 'Twas the night before Xmas...';
let newstr = str.replace(/xmas/i, 'Christmas');
console.log(newstr); // "Twas the night before Christmas..."


// Switching words in a string
let re = /(\w+)\s(\w+)/;
let str = 'John Smith';
let newstr = str.replace(re, '$2, $1');
console.log(newstr);  // Smith, John
```

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace">MDN Replace</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### toString

'toString()`: Every JavaScript object has a `toString()` method. You can convert a number, boolean or array to a string. However, you can not use this to convert an object to a string (See [MDN Object.toString](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/toString)).


MDN syntax and examples:
```js
// num.toString:
num.toString()
num.toString(radix)
// all other
date.toString() 
obj.toString() 
bool.toString() 
arr.toString()
function.toString() 


// array to stringv(?)
function turnToString(val){
  return val.toString();
}
// let testObj = 108 // "string" "108"
// let testObj = false // "string" "false"
let testObj = [1, 2, 3, ['hey', 6]]
let strObj = turnToString(testObj)
console.log(typeof strObj, strObj) // "string" "1,2,3,hey,6"
```

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href=https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toString">MDN toString</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Miscellaneous

typeof:
```js
let typeOfTest;
typeOfTest = "";
console.log(typeof typeOfTest) // string
typeOfTest = []; // object
typeOfTest = true; // boolean
typeOfTest = false; // boolean
typeOfTest = undefined; // undefined
```

<br />

escape sequences in strings:
```js
const myStr = "FirstLine\n\t\\SecondLine\nThirdLine";
```

<br />

find the Nth-to-last character:
```js
let thirdToLastLetter = firstName[firstName.length - 3];
```

- arr[3][0][1]: access sub arrays

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Array string methods

These are methods that can be used on both strings and arrays.

### String slice

Extracts a section of a string and **<ins>returns it as a new string</ins>**, _without_ modifying the original string.

MDN syntax and examples:
```js
slice()
slice(beginIndex)
slice(beginIndex, endIndex)

// MDN slice()
const str = 'The quick brown fox jumps over the lazy dog.';
console.log(str.slice(31)); // "the lazy dog."
console.log(str.slice(4, 19)); // "quick brown fox"
console.log(str.slice(-4)); // "dog."
console.log(str.slice(-9, -5)); // "lazy"


let str = "The slice method"
// slice()
console.log(str.slice()) // "The slice method"
// slice(startIndex)
let str2 = str.slice(0) // "The slice method"
let str2 = str.slice(1) // "he slice method"
let str2 = str.slice(2) // "e slice method"
let str2 = str.slice(3) // " slice method"
let str2 = str.slice(4) // "slice method"
// slice(startIndex, endIndex)
let str2 = str.slice(4, 9)
console.log(str2) // "slice"
let str2 = str.slice(4, 11) // "slice m"
```

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/slice">MDN String Slice</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### concat

Joins two or more arrays and **<ins>returns a copy of the joined arrays</ins>**. Does not mutate the array. Can be used on strings.

Examples:
```js
// syntax
concat(str1)
concat(str1, str2)
concat(str1, str2, ... , strN)


const str1 = 'Hello';
const str2 = 'World';
console.log(str1.concat(' ', str2)); // "Hello World"
console.log(str2.concat(', ', str1)); // "World, Hello"

let hello = 'Hello, '
console.log(hello.concat('Kevin', '. Have a nice day.')) // Hello, Kevin. Have a nice day.
```

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/concat">MDN concat</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### indexOf

Given one argument: a substring to search for, searches the entire calling string, and returns the index of the first occurrence of the specified substring. Given a second argument: a number, the method returns the first occurrence of the specified substring at an index greater than or equal to the specified number.

```js
// syntax:
indexOf(searchString)
indexOf(searchString, position)

const paragraph = 'The quick brown fox jumps over the lazy dog. If the dog barked, was it really lazy?';

const searchTerm = 'dog';
const indexOfFirst = paragraph.indexOf(searchTerm);
console.log(`The index of the first "${searchTerm}" from the beginning is ${indexOfFirst}`);
// expected output: "The index of the first "dog" from the beginning is 40"
console.log(`The index of the 2nd "${searchTerm}" is ${paragraph.indexOf(searchTerm, (indexOfFirst + 1))}`);
// expected output: "The index of the 2nd "dog" is 52"


const str = 'Brave new world'
console.log('Index of first w from start is ' + str.indexOf('w'))   // logs 8
console.log('Index of "new" from start is ' + str.indexOf('new'))   // logs 6


// example 2
let str = 'finding substring in string';
let index = str.indexOf('str');
console.log(index); // 11


// find count (TIPS AND TRICKS)
let str = 'You do not know what you do not know until you know.';
let substr = 'know';
let count = 0;
let index = str.indexOf(substr);
while(index !== -1) {
    count++;
    index = str.indexOf(substr, index + 1);
}
console.log(count); // 3
```

&#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/indexOf">MDN indexOf</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### lastIndexOf

**<ins>Returns the last index</ins>** at which a given element can be found in the array, or `-1` if it is not present. Can be used on strings.

Examples:
```js
// syntax
lastIndexOf(searchString)
lastIndexOf(searchString, position)


const paragraph = 'The quick brown fox jumps over the lazy dog. If the dog barked, was it really lazy?';
const searchTerm = 'dog';
console.log(`The index of the first "${searchTerm}" from the end is ${paragraph.lastIndexOf(searchTerm)}`); 
// expected output: "The index of the first "dog" from the end is 52"


let anyString = 'Brave, Brave New World';
console.log('The index of the first "Brave" is ' + anyString.indexOf('Brave')); // 0
console.log('The index of the last "Brave" is ' + anyString.lastIndexOf('Brave')); // 7
```

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/lastIndexOf">MDN lastIndexOf</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### includes

Performs a case-sensitive search to determine whether one string may be found within another string, returning true or false as appropriate

```js
// syntax:
includes(searchString)
includes(searchString, position)


const sentence = 'The quick brown fox jumps over the lazy dog.';
const word = 'fox';
console.log(`The word "${word}" ${sentence.includes(word) ? 'is' : 'is not'} in the sentence`);
// expected output: "The word "fox" is in the sentence"


const str = 'To be, or not to be, that is the question.'
console.log(str.includes('To be'))        // true
console.log(str.includes('question'))     // true
console.log(str.includes('nonexistent'))  // false
console.log(str.includes('To be', 1))     // false
console.log(str.includes('TO BE'))        // false
console.log(str.includes(''))             // true


let str = 'Lorem ipsum';
console.log(str.includes('ipsum')); // true
console.log(str.includes('Ipsum')); // false


let str = 'JavaScript String';
console.log(str.includes('Script', 5)); // false
console.log(str.includes('Script', 4)); // true
```

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/includes">MDN includes</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Syntax tables

Tables by the number of arguments and whether or not the method mutates the original source.

### Common methods

Common methods with NO arguments/parameters:
| method  | syntax            | Mutates? |
| :----   | :----             | :----:   |
| split   | str.split()       | YES |
| sort    | str.sort()        | YES* |

**NOTE**: Use the rest paramter to not mutate the original source for `sort()` and `reverse()`.

<br />

Common methods with a single argument, or multiple repeated arguments:
| method  | syntax1                     | syntax2                     | Mutates? |
| :----   | :----                       | :----                       | :----:   |
| charCodeAt | str.charCodeAt(index)    |                             | NO |
| fromCharCode | String.fromCharCode(num1) | String.fromCharCode(num1, num2, ..., numN) | NO |
| concat  | str.concat(str2)            | concat(str1, str2, ... , strN) | NO |
| split   | str.split(separator)        |                             | NO |
| repeat  | str.repeat(count)           |                             | NO | 
| substring | str.substring(indStart)   | str.substring(indStart, indEndex) | NO |
| replace | str.replace(regex, newStr)  | str.replace(substr, newStr) | NO |
| test    | regex.test(str)             |                             | N/A |         
| match   | str.match(regex)            |                             | N/A |
| indexOf | str.indexOf(searchStr)      | str.indexOf(searchStr, position) | N/A |
| lastIndexOf | str.lastIndexOf(searchStr) | str.lastIndexOf(searchStr, position) | N/A |
| endsWith | str.endsWith(subStr)       | str.endsWith(subStr, length) | N/A |
| includes | str.includes(searchStr)    | str.includes(searchStr, position) | N/A |
|         | splice(start, deleteCt, item1) | splice(start, deleteCt, item1, item2, ...) | YES |

<br />

Common methods with two arguments:
| method    | syntax1                 | syntax2                 | Mutates? |
| :----     | :----                   | :----                   | :----:   |
| slice     | str.slice(start, end)   |                         | NO |
| split     | str.split(separator, limit) |                     | NO |
| replace   | str.replace(regex, Fx)  | str.replace(substr, Fx) | NO |

***NOTE**: Function for `replace()`: The function's result (return value) will be used as the replacement string. Note that the function will be invoked multiple times for each full match to be replaced if the regular expression in the first parameter is global. Check the [MDN replace docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace#specifying_a_function_as_a_parameter) since there is a lot to the function.

Example:
```js
function replacer(match, p1, p2, p3, offset, string) {
  // p1 is nondigits, p2 digits, and p3 non-alphanumerics
  return [p1, p2, p3].join(' - ');
}
let newString = 'abc12345#$*%'.replace(/([^\d]*)(\d*)([^\w]*)/, replacer);
console.log(newString);  // abc - 12345 - #$*%
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>