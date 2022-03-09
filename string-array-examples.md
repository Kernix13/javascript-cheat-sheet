# String and Array examples

Examples for standard syntax of the most coomon methods and the more difficult methods to understand.

## Table of contents

<div id="back-to-top"></div>

1. [Simple array methods](#simple-array-methods)
   1. [push](#push)
   1. [unshift](#unshift)
   1. [pop](#pop)
   1. [shift](#shift)
   1. [join](#join)
   1. [Basic sort](#basic-sort)
   1. [reverse](#reverse)
   1. [splice](#splice)
   1. [indexOf](#indexOf)
   1. [lastIndexOf](#lastIndexOf)
   1. [concat](#concat)
1. [High order array methods](#high-order-array-methods)
   1. [Sort](#sort)
   1. [Includes](#includes)
   1. [Find](#find)
   1. [Every](#every)
   1. [Some](#some)
   1. [Map](#map)
   1. [Filter](#filter)
   1. [forEach](#forEach)
   1. [Reduce](#reduce)
1. [String methods](#string-methods)
   1. [substring](#substring)
   1. [endsWith](#endsWith)
   1. [test](#test)
   1. [match](#match)
   1. [replace](#replace)
   1. [Miscellaneous](#Miscellaneous)
1. [Spread and Rest syntax](#spread-and-rest-syntax)
   1. [Spread operator for arrays and strings](#spread-operator-for-arrays-and-strings)
   1. [Rest parameter and rest syntax](#rest-parameter-and-rest-syntax)
1. [Syntax tables](#syntax-tables)

## Simple array methods

Basic syntax for simple versions of `push()`, `unshift()`, `pop()`, `shift()`, `sort()`, `reverse()`, and `splice()`:

- [MDN push](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push)
- [MDN unshift](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift)
- [MDN pop](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/pop)
- [MDN shift](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/shift)
- [MDN join](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join)
- [MDN sort](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)
- [MDN reverse](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse)
- [MDN splice](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)
- [MDN indexOf](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf)
- [MDN lastIndexOf](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/lastIndexOf)
- [MDN concat](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat)

### push

```js
// arr.push(val1, ...)
let arr = ['a', 'b', 'c', 'd'];
let addedItem = arr.push('e');
console.log(addedItem); // 5
console.log(arr); // ['a', 'b', 'c', 'd', 'e']

// Merge 2 arrays, alterntive to concat():
let rhythm = ['bass', 'drums']
let harmony = ['guitar', 'piano']
rhythm.push(...harmony);
console.log(rhythm)  // ['bass', 'drums', 'guitar', 'piano']
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### unshift

```js
// syntax
arr.unshift(val1, ...)

let arr = [1, 2, 3, 4];
let addedItem = arr.unshift(0);
console.log(addedItem); // 5
console.log(arr); // [0, 1, 2, 3, 4]
arr.unshift([-7, -6], [-5]) // result: [[-7, -6], [-5], 0, 1, 2, 3, 4]

// reset array
let arr = [1, 2, 3, 4, 5, 6]
arr.unshift(1)
arr.unshift(2)
arr.unshift(3) // [3, 2, 1, 4, 5, 6]
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### pop

```js
// arr.pop()
let arr = ['a', 'b', 'c', 'd'];
let removedItem = arr.pop();
console.log(removedItem); // "d"
console.log(arr); // ["a","b","c"]
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### shift

```js
// arr.shift()
let arr = [1, 2, 3, 4];
let removedItem = arr.shift();
console.log(removedItem); // 1
console.log(arr); // [2,3,4]

// Removing an element from an array
const myJobs = ['lifeguard', 'coach', 'analyst', 'developer'];
console.log('myJobs before:', JSON.stringify(myJobs));
// "myJobs before:" "['lifeguard','coach','analyst','developer']"
const shifted = myJobs.shift();
console.log('myJobs after:', myJobs);
// "myJobs after:" "["coach","analyst","developer"]"
console.log('Removed this element:', shifted); // "Removed this element:" "lifeguard"

// Using shift() method in while loop with a great typeof condition
const names = ["John", "Paul", "George", "Ringo" ,"Richard"];
while( typeof (i = names.shift()) !== 'undefined' ) {
    console.log(i);
}
// John, Paul, George, Ringo, Richard
console.log(names) // []
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### join

`arr.join()`, commonly used with str.split():
```js
// syntax:
join()
join(separator)

// MDN Example:
const a = ['Fire', 'Water', 'Air', 'Earth'];
a.join();      // 'Fire,Water,Air,Earth'
a.join(', ');  // 'Fire, Water, Air, Earth'
a.join(' + '); // 'Fire + Water + Air + Earth'
a.join('');    // 'FireWaterAirEarth'

// Here is an example using toLowerCase() and split() for a URL page slug
const blogTitle = "Common Array Methods You Should Know"
const urlSlug = blogTitle.toLowerCase().split(' ').join('-')
console.log(urlSlug); // "common-array-methods-you-should-know"
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Basic sort

If you use the spread operator to access the array, the original array is not mutated; otherwise it is. Same with `reverse()`. Note, don't use a callback function for sorting text. Check out [MDN sort description](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort#description) for how to sort by the key of an object.

```js
// Sorting an array of strings using spread operating to NOT mutate original:
const arr = ["Squeaks", "Charlie", "Little Rascal", "Buddy", "Luna", "Jim"];
let newArr = [...arr].sort();
console.log(newArr); // ["Buddy","Charlie","Jim","Little Rascal","Luna","Squeaks"]
console.log("original: " + arr); // "original: Squeaks,Charlie,Little Rascal,Buddy,Luna,Jim"

// Use this method to sort numbers as a string value (e.g. item/part numbers):
const nums = [5, 1, 27, 101, 55, 12, 44, 10001, 3];
const numSort = [...nums].sort();
console.log(numSort) // [1,10001,101,12,27,3,44,5,55]
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### reverse

You can use `reverse()` with the spread operator on the original array as a more concise way to check for palindromes.

```js
const arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const countDown = arr.reverse();
console.log(countDown); // [10,9,8,7,6,5,4,3,2,1]

// But it also reverses the original array:
console.log(arr); // [10,9,8,7,6,5,4,3,2,1]

// Reverse array using spread operator without mutating original:
const countDown = [...arr].reverse();
console.log(countDown); [10,9,8,7,6,5,4,3,2,1]
console.log(arr); [1,2,3,4,5,6,7,8,9,10]

// Alternate solution to the palindrome problem:
const word = "racecar";
const letters = word.toLowerCase().split(''); 
// the spread operator is a must here for reverse() to work
const revWord = [...letters].reverse().join('');

if (word === revWord) {
  console.log(word + " is a palindrome");
} else {
  console.log(word + " is NOT a palindrome");
}
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### splice

MDN syntax:
```js
splice(start)
splice(start, deleteCount)
splice(start, deleteCount, item1)
splice(start, deleteCount, item1, item2, itemN)
```

Examples:
```js
// Add items, then remove and add 
const months = ['Jan', 'March', 'April', 'June'];
months.splice(1, 0, 'Feb');
months.splice(4, 1, 'May');
console.log(months); // ["Jan","Feb","March","April","May"]

// remove all items after specified index #
const alpha =  ['a', 'b', 'c', 'd', 'e']
alpha.splice(3)
console.log(alpha) // ["a","b","c"]

// remove nth from last item (-2 = 2nd from end):
const alpha =  ['a', 'b', 'c', 'd', 'e']
alpha.splice(-2, 1)
console.log(alpha) // ["a","b","c","e"]

```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### indexOf

Examples:
```js
// syntax
indexOf(searchElement)
indexOf(searchElement, fromIndex)

const datatypes = ['number', 'string', 'boolean', 'object', 'string', 'null'];
console.log(datatypes.indexOf('number')); // 0
console.log(datatypes.indexOf('string', 4)); // 4
console.log(datatypes.indexOf('function')); // -1

// This example is confusing. Finding all the occurrences of an element:
const indices = [];
const array = ['a', 'b', 'a', 'c', 'a', 'd'];
const element = 'a';
let idx = array.indexOf(element);
while (idx != -1) {
  indices.push(idx);
  idx = array.indexOf(element, idx + 1);
}
console.log(indices); // [0, 2, 4]

// Finding if an element exists in the array or not and updating the array
function updateVegetablesCollection (veggies, veggie) {
    if (veggies.indexOf(veggie) === -1) {
        veggies.push(veggie);
        console.log('New veggies collection is: ' + veggies);
    } else {
        console.log(veggie + ' already exists in the veggies collection.');
    }
}

const veggies = ['potato', 'tomato', 'chillies', 'green-pepper'];

updateVegetablesCollection(veggies, 'spinach');
updateVegetablesCollection(veggies, 'spinach');
```


```js

```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### lastIndexOf

Examples: returns the last index at which a given element can be found in the array, or -1 if it is not present
```js
// syntax
lastIndexOf(searchElement)
lastIndexOf(searchElement, fromIndex)

const instruments = ['Guitar', 'Bass', 'Drums', 'Guitar'];
console.log(instruments.lastIndexOf('Guitar')); // 3
console.log(instruments.lastIndexOf('Bass')); // 1

// Finding all the occurrences of an element (confusing), using push to add them to another array as they are found:
const indices = [];
const array = ['a', 'b', 'a', 'c', 'a', 'd'];
const element = 'a';
let idx = array.lastIndexOf(element);
while (idx !== -1) {
  indices.push(idx);
  idx = (idx > 0 ? array.lastIndexOf(element, idx - 1) : -1);
}
console.log(indices); // [4, 2, 0]
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### concat

Examples:
```js
// syntax
concat()
concat(value0)
concat(value0, value1)
concat(value0, value1, ... , valueN)

const array1 = ['a', 'b', 'c'];
const array2 = ['d', 'e', 'f'];
const array3 = array1.concat(array2);
console.log(array3); // ["a", "b", "c", "d", "e", "f"]
console.log(array1.concat(array2)); // ["a", "b", "c", "d", "e", "f"]

// Concatenating three arrays
const num1 = [1, 2, 3];
const num2 = [4, 5, 6];
const num3 = [7, 8, 9];
const numbers = num1.concat(num2, num3);

console.log(numbers); // [1, 2, 3, 4, 5, 6, 7, 8, 9]

// Concatenating values to an array
const letters = ['a', 'b', 'c'];
const alphaNumeric = letters.concat(1, [2, 3]);

console.log(alphaNumeric); // ['a', 'b', 'c', 1, 2, 3]

// Concatenating nested arrays
const num1 = [[1]];
const num2 = [2, [3]];
const numbers = num1.concat(num2);

console.log(numbers); // [[1], 2, [3]]
num1[0].push(4);
console.log(numbers); // [[1, 4], 2, [3]]
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## High order array methods

High Order Array Methods = methods that use a callback function. The most used ones are `sort`, `map`, `filter`, `forEach`, and `reduce`; but also `includes`, `find`, `every`, and `some` are useful.

- [MDN includes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/includes)
- [MDN find](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find)
- [MDN every](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every)
- [MDN some](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some)
- [MDN map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
- [MDN filter](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)
- [MDN forEach](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)
- [MDN reduce](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)

### Sort

`arr.sort()` callback examples:
```js
// mutates original array:
const arr = [4, 2, 1, 5, 3];
arr.sort(function(a, b) {
  return a - b;
});
console.log(arr); // [1,2,3,4,5]

// this does not mutate original:
let sortedArr = [...arr].sort(function(a, b) {
  return a - b;
});
console.log(sortedArr); // [1,2,3,4,5]
console.log("original: " + arr); // "original: 4,2,1,5,3"

// Arrow function
const nums = [1, 10, 72, 1000, 5, 55, 101, 17, 11, 19, 100, ]
const numSort = [...nums].sort((a, b) => a - b); //[1,5,10,11,17,19,55,72,100,101,1000]

// Arrays of objects can be sorted by comparing the value of one of their properties
const items = [
  { name: 'Homer', barBill: 21 },
  { name: 'Moe', barBill: 37 },
  { name: 'Bud', barBill: 45 },
  { name: 'Jim', barBill: -12 },
  { name: 'Johnny', barBill: 13 },
  { name: 'someGuy', barBill: 37 }
];
let itemsSort = items.sort(function (a, b) {
  return a.barBill - b.barBill;
});
// Sorting by 'name' is more involved: 

// Sorting non-ASCII characters
const items = ['réservé', 'premier', 'communiqué', 'café', 'adieu', 'éclair'];
items.sort(function (a, b) {
  return a.localeCompare(b);
});
// items is ['adieu', 'café', 'communiqué', 'éclair', 'premier', 'réservé']
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Includes

```js
// syntax:
arr.includes(item)
arr.includes(item, fromIndex)

const items = [1, 2, 3, 4, 5]
const inItems = items.includes(7)
console.log(inItems) // false

let str = 'Lorem ipsum';
console.log(str.includes('ipsum')); // true
console.log(str.includes('Ipsum')); // false

let str = 'JavaScript String';
console.log(str.includes('Script', 5)); // false
console.log(str.includes('Script', 4)); // true
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Find

`arr.find()` MDN syntax:
```js
// Arrow function
find((element) => { /* ... */ } )
find((element, index) => { /* ... */ } )

// Callback function
find(callbackFn)
find(callbackFn, thisArg)

// Inline callback function
find(function(element) { /* ... */ })
find(function(element, index) { /* ... */ })
```

`arr.find()` MDN examples
```js
const array1 = [5, 12, 8, 130, 44];
const found = array1.find(element => element > 10);
console.log(found); // 12

// using an array of objects
const items = [
  { name: 'Bike', price: 100 },
  { name: 'TV', price: 200 },
  { name: 'Album', price: 10 },
  { name: 'Book', price: 5 },
  { name: 'Phone', price: 500 },
  { name: 'Computer', price: 1000 },
  { name: 'Keyboard', price: 25 }
]
const foundItem = items.find(item => {
  return item.name == 'Book'
})
console.log(foundItem) // {"name": "Book", "price": 5}

// Object with callback:
const inventory = [
  {name: 'apples', quantity: 2},
  {name: 'bananas', quantity: 0},
  {name: 'cherries', quantity: 5}
];

function isCherries(fruit) {
  return fruit.name === 'cherries';
}
console.log(inventory.find(isCherries)); // {"name": "cherries", "quanity": 5}

// Using arrow function and destructuring
const inventory = [
  {name: 'apples', quantity: 2},
  {name: 'bananas', quantity: 0},
  {name: 'cherries', quantity: 5}
];

const result = inventory.find( ({ name }) => name === 'cherries' );
console.log(result) // { name: 'cherries', quantity: 5 }

// Find a prime number in an array (example in filter section as well)
function isPrime(element, index, array) {
  let start = 2;
  while (start <= Math.sqrt(element)) {
    if (element % start++ < 1) {
      return false;
    }
  }
  return element > 1;
}
console.log([4, 6, 8, 12].find(isPrime)); // undefined
console.log([4, 5, 8, 12].find(isPrime)); // 5
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Every

Returns a boolean if EVERY element in an array passes a test

`arr.every()` MDN syntax:
```js
// Arrow function
every((item) => { /* ... */ } )
every((item, index) => { /* ... */ } )
every((item, index, array) => { /* ... */ } )

// Callback function
every(callbackFn)
every(callbackFn, thisArg)

// Inline callback function
every(function(item) { /* ... */ })
every(function(item, index) { /* ... */ })
every(function(item, index, array){ /* ... */ })
every(function(item, index, array) { /* ... */ }, thisArg)
```

<br />

`arr.every()` examples:
```js
// My preferred syntax
let nums = [27, 2.5, 1, 3, 5];
let checkNums = nums.every(function(num) {
    return num > 0;
});
console.log(checkNums); // true

// Alternative to above:
let checkNums = [27, 2.5, 1, 3, 5].every(function(num){
    return num > 0;
})

// Arrow example, my next preferred syntax:
let nums = [-2, 2.5, 1, 3, 5];
let checkNums = nums.every(num  => num > 0);
console.log(checkNums); // false

// Callback function example:
let nums = [-2, 2.5, 1, 3, 5];
function findPositive(num) {
  return num > 0;
}
let checkNums = nums.every(findPositive);
console.log(checkNums) // false

// Check if one array is a subset of another array
const isSubset = (array1, array2) => array2.every(element => array1.includes(element));
console.log(isSubset([1, 2, 3, 4, 5, 6, 7], [5, 7, 6])); // true
console.log(isSubset([1, 2, 3, 4, 5, 6, 7], [5, 8, 7])); // false
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Some

Returns a boolean if at least one element passes a test

`arr.some()` MDN syntax:
```js
// Arrow function
some((element) => { /* ... */ } )
some((element, index) => { /* ... */ } )
some((element, index, array) => { /* ... */ } )

// Callback function
some(callbackFn)
some(callbackFn, thisArg)

// Inline callback function
some(function(element) { /* ... */ })
some(function(element, index) { /* ... */ })
some(function(element, index, array){ /* ... */ })
some(function(element, index, array) { /* ... */ }, thisArg)
```

<br />

`arr.some()` arrow examples:
```js
// Arrow
const array = [1, 2, 3, 5, 7];
const even = (item) => item % 2 === 0;
console.log(array.some(even)); // true

// Arrow 2:
const array = [3, 5, 7, 30, 6, 2];
const even = item => item < 3;
console.log(array.some(even)); // true

// Arrow exampe with strings:
const names = ['John', 'Peter', 'Mary'];
const firstName = 'John'
const hasMyName = names.some(name => name === firstName);
console.log(hasMyName); // true
```

<br />

`arr.some()` callback examples:
```js
// Callback function
const arr = [2, 5, 8, 1, 4];
const arr2 = [12, 5, 8, 1, 4];
function isBiggerThan10(item) {
  return item > 10;
}
console.log(arr.some(isBiggerThan10));  // false
console.log(arr2.some(isBiggerThan10)); // true

// Anonymous/inline function:
const arr = [10, 20, 30, 40, 3];
const lessThanTen = arr.some(function(item) {
  return item < 10;
})
console.log(lessThanTen); // true

// Check if an array of objects have a specific property name/key:
const users = [
  { firstName: 'Harry' },
  { firstName: 'Peter', lastName: 'Parker' }, 
  { firstName: 'Mary' }
];

let hasLastName = users.some(function(user) {
  return user.lastName;
})
console.log(hasLastName); // true

// Checking whether a value exists in an array
const fruits = ['apple', 'banana', 'mango', 'guava'];

function checkAvailability(arr, val) {
  return arr.some(function(arrVal) {
    return val === arrVal;
  });
}
checkAvailability(fruits, 'kela');   // false
checkAvailability(fruits, 'banana'); // true

// Arrow version
function checkAvailability(arr, val) {
  return arr.some(arrVal => val === arrVal);
}
```

**NOTE**: I've seen examples where `some()` is used to check for the existence of a value in an array - why not just use `includes()`? You can not use `hasOwnProperty` for the `hasLastName` object example because the variable is an array, not an object.

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Map

`arr.map()` MDN syntax:
```js
// Arrow function
map((element) => { /* ... */ })
map((element, index) => { /* ... */ })
map((element, index, array) => { /* ... */ })

// Callback function
map(callbackFn)
map(callbackFn, thisArg)

// Inline callback function
map(function(element) { /* ... */ })
map(function(element, index) { /* ... */ })
map(function(element, index, array){ /* ... */ })
map(function(element, index, array) { /* ... */ }, thisArg)
```

<br />

`arr.map()` simple MDN examples:
```js
const arr = [1, 2, 3]
const mapArr = arr.map(n => n * 3)
console.log(mapArr)

const array1 = [1, 4, 9, 16];
const map1 = array1.map(x => x * 2);
console.log(map1);

const numbers = [1, 4, 9];
const roots = numbers.map((num) => Math.sqrt(num)); // roots is now [1, 2, 3]
```

<br />

`arr.map()` more advanced MDN examples:
```js
// reformat objects in an array (WHY?)
const kvArray = [
  { key: 1, value: 10 },
  { key: 2, value: 20 },
  { key: 3, value: 30 }
  ];
const reformattedArray = kvArray.map(({ key, value}) => ({ [key]: value }));
console.log(reformattedArray) // {"1": 10}, {"2": 20}, {"3": 30}
```

**NOTE**: Look into [**Array.from()**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from) and constrast with `.map()`. Check out [Stackoverflow: Array.from vs Array.prototype.map](https://stackoverflow.com/questions/26052699/array-from-vs-array-prototype-map).

<br />

`arr.map()` freeCodeCamp examples:
```js
// Get object key values, similar to what Object.values does on a single object
const users = [
  { name: 'John', age: 34 },
  { name: 'Amy', age: 20 },
  { name: 'camperCat', age: 10 }
];
const names = users.map(user => user.name);
console.log(names); // ["John","Amy","camperCat"]

// Challenge 11 CONVERT HTML ENTITIES
function convertHTML(str) {
  const convertSymbols = {
    "&": "&amp;",
    "<": "&lt;",
    ">": "&gt;",
    '"': "&quot;",
    "'": "&apos;"
  };

  return str.split("").map(symbol => convertSymbols[symbol] || symbol).join("");
}
convertHTML("Dolce & Gabbana");

// lesson 4 3rd solution
function findLongestWordLength(str) {
  return Math.max(...str.split(" ").map(word => word.length));
}
findLongestWordLength("The quick brown fox jumped over the lazy dog");
```

<br />

`arr.map()` other examples:
```js
// Capitalize all words in a string:
const str = "why is title case important"
let capitalize = str.split(' ').map(word => word[0].toUpperCase() + word.slice(1)).join(' ')
console.log(capitalize) // "Why Is Title Case Important"

// working with objects
const items = [
  { name: 'Bike', price: 100 },
  { name: 'TV', price: 200 },
  { name: 'Album', price: 10 },
  { name: 'Book', price: 5 },
  { name: 'Phone', price: 500 },
  { name: 'Computer', price: 1000 },
  { name: 'Keyboard', price: 25 }
]

const itemNames = items.map(item => {
  // return item.name // ["Bike","TV","Album","Book","Phone","Computer","Keyboard"]
  return item.price
})
console.log(itemNames) // [100,200,10,5,500,1000,25]
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Filter

`arr.filter()` MDN syntax:
```js
// Arrow function
filter((element) => { /* ... */ } )
filter((element, index) => { /* ... */ } )

// Callback function
filter(callbackFn)
filter(callbackFn, thisArg)

// Inline callback function
filter(function(element) { /* ... */ })
filter(function(element, index) { /* ... */ })
```

<br />

`arr.filter()` simple examples:
```js
const ages = [33, 12, 20, 16, 5, 54, 21, 44, 61, 13, 15, 45, 25, 64, 32];
const canDrink = ages.filter(age => age >= 21);
console.log(canDrink);
```

<br />

`arr.filter()` examples:
```js
// Find all prime numbers in an array
const array = [-3, -2, -1, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13];

function isPrime(num) {
  for (let i = 2; num > i; i++) {
    if (num % i == 0) {
      return false;
    }
  }
  return num > 1;
}
console.log(array.filter(isPrime)); // [2, 3, 5, 7, 11, 13]

// Searching an array
let fruits = ['apple', 'banana', 'grapes', 'mango', 'orange']

function filterItems(arr, query) {
  return arr.filter(function(el) {
    return el.toLowerCase().indexOf(query.toLowerCase()) !== -1
  })
}
console.log(filterItems(fruits, 'ap'))  // ['apple', 'grapes']
console.log(filterItems(fruits, 'an'))  // ['banana', 'mango', 'orange']
```

<br />

`arr.filter()` freeCodeCamp examples:
```js
// algo.js, Challenge 2
function diffArray(arr1, arr2) {
  return arr2
    .concat(arr1)
    .filter(item => !arr2.includes(item) || !arr1.includes(item));
}
console.log(diffArray([1, 2, 3, 5, 7], [1, 2, 3, 4, 5]));

// Challenge 3 SEEK DESTROY
function destroyer(arr, ...otherArgs) {
  // return the arr values that are not in otherArgs
  return arr.filter(item => !otherArgs.includes(item));
}
console.log(destroyer([1, 2, 3, 1, 2, 3], 2, 3));

// Challenge 4 WHEREFORE ARE THOU
function whatIsInAName(collection, source) {
  let getKeys = Object.keys(source);

  return collection.filter(function (item) {
    return getKeys.every(function (key) {
      return item.hasOwnProperty(key) && item[key] === source[key];
    });
  });

}
whatIsInAName(
  [
    { first: "Romeo", last: "Montague" },
    { first: "Mercutio", last: null },
    { first: "Tybalt", last: "Capulet" }
  ],
  { last: "Capulet" }
);

// functional.js, lesson 16
const squareList = (arr) => {
  return arr
    .filter(num => num > 0 && num % parseInt(num) === 0)
    .map(num => Math.pow(num, 2));
};

const squaredIntegers = squareList([-3, 4.8, 5, 3, -3.2]);
// console.log(squaredIntegers);

// lesson 21 - NOT AS GOOD AS MY JOIN EXAMPLE IN STRING SECTION
let webTitle = "Dog breeds good with cats";
function urlSlug(title) {
  return title
    .split(" ")
    .filter(substr => substr !== "")
    .join("-")
    .toLowerCase();
}
console.log(urlSlug(webTitle));
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### forEach

`arr.forEach()` MDN syntax:
```js
// Arrow function
forEach((element) => { /* ... */ })
forEach((element, index) => { /* ... */ })

// Callback function
forEach(callbackFn)
forEach(callbackFn, thisArg)

// Inline callback function
forEach(function(element) { /* ... */ })
forEach(function(element, index) { /* ... */ })
```

<br />

`arr.forEach()` MDN and other examples
```js
const array1 = ['a', 'b', 'c'];
array1.forEach(element => console.log(element)); // "a" "b" "c"

const items = [
  { name: 'Bike', price: 100 },
  { name: 'TV', price: 200 },
  { name: 'Album', price: 10 },
  { name: 'Book', price: 5 },
  { name: 'Phone', price: 500 },
  { name: 'Computer', price: 1000 },
  { name: 'Keyboard', price: 25 }
]
items.forEach(item => {
  console.log(item.name)
})
// "Bike" "TV" "Album" "Book" "Phone" "Computer" "Keyboard"

const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];
const result = words.filter(word => word.length > 6);
console.log(result); // ["exuberant","destruction","present"]

// Filtering out all small values
function isBigEnough(value) {
  return value >= 10
}
let filtered = [12, 5, 8, 130, 44].filter(isBigEnough)
console.log(filtered); // [12,130,44]

// Converting a for loop to forEach
const items = ['item1', 'item2', 'item3'];
const copyItems = [];

// before
for (let i = 0; i < items.length; i++) {
  copyItems.push(items[i]);
}

// after
items.forEach((item) => {
  copyItems.push(item);
});

// Other examples are really confusing - look at Traversy
```

<br />

`arr.forEach()` my examples:
```js
// Example from my guitar chord namer app
let position = chromaticSharps.indexOf(uniqueNotes[i]);
let noteAsRoot = chromaticSharps.slice(position, position + 12);
uniqueNotes.forEach(note => noteSteps.push(noteAsRoot.indexOf(note)));
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Reduce

`arr.reduce()` MDN syntax:
```js
// Arrow function
reduce((previousValue, currentValue) => { /* ... */ } )
reduce((previousValue, currentValue, currentIndex) => { /* ... */ } )

// Callback function
reduce(callbackFn)
reduce(callbackFn, initialValue)

// Inline callback function
reduce(function(previousValue, currentValue) { /* ... */ })
reduce(function(previousValue, currentValue, currentIndex) { /* ... */ })
```

<br /> 

`arr.reduce()` MDN Examples
```js
const array1 = [1, 2, 3, 4];
const initialValue = 0;
const sumWithInitial = array1.reduce(
  (previousValue, currentValue) => previousValue + currentValue,
  initialValue
);
console.log(sumWithInitial); // 10

// another example
const getMax = (a, b) => Math.max(a, b);
const arr = [1, 100, 5, 72];
// callback is invoked for each element in the array starting at index 0
console.log(arr.reduce(getMax, 50)); // 100

// How reduce() works without an initial value
const array = [15, 16, 17, 18, 19];

function reducer(previous, current, index, array) {
  const returns = previous + current;
  console.log(`previous: ${previous}, current: ${current}, index: ${index}, returns: ${returns}`);
  return returns;
}
array.reduce(reducer);

// Sum all the values of an array
let sum = [0, 1, 2, 3].reduce(function (previousValue, currentValue) {
  return previousValue + currentValue
}, 0)
// sum is 6, or an arrow function:
let total = [ 0, 1, 2, 3 ].reduce(
  ( previousValue, currentValue ) => previousValue + currentValue,
  0
)

// Sum of values in an object array
let initialValue = 0
let sum = [{x: 1}, {x: 2}, {x: 3}].reduce(function (previousValue, currentValue) {
    return previousValue + currentValue.x
}, initialValue)
console.log(sum) // logs 6, or as an arrow function:

let initialValue = 0
let sum = [{x: 1}, {x: 2}, {x: 3}].reduce(
    (previousValue, currentValue) => previousValue + currentValue.x
    , initialValue
)
console.log(sum)

// Counting instances of values in an object
let names = ['Alice', 'Bob', 'Tiff', 'Bruce', 'Alice']

let countedNames = names.reduce(function (allNames, name) {
  if (name in allNames) {
    allNames[name]++
  }
  else {
    allNames[name] = 1
  }
  return allNames
}, {})
// countedNames is:
// { 'Alice': 2, 'Bob': 1, 'Tiff': 1, 'Bruce': 1 }

// Also really complex - find other examples from my courses
```

<br />

`arr.reduce()` freeCodeCamp examples:
```js
// Example with strings:
function findLongestWordLength(str) {
  return str.split(' ')
    .reduce(function(longest, word) {
      return Math.max(longest, word.length)
    }, 0);
}
findLongestWordLength("Find the longest word in this sentence"); // 8

// algo.js, Challenge 13 SUM ALL PRIMES
function sumPrimes(num) {
  // Check all numbers for primality
  let primes = [];
  for (let i = 2; i <= num; i++) {
    if (primes.every((prime) => i % prime !== 0))
      primes.push(i);
  }
  return primes.reduce((sum, prime) => sum + prime, 0);
}
console.log(sumPrimes(10));

// es6.js, use the rest parameter w\ Fx parms
const sum = (...args) => {
  return args.reduce((a, b) => a + b, 0);
}

// lesson 15, functional.js
const myPets = [
  { name: "Buddy", species: "dog", age: 10 },
  { name: "Lttle Rascal", species: "cat", age: 8 },
  { name: "Charlie", species: "cat", age: 10 },
  { name: "Squeeks", species: "cat", age: 2 },
  { name: "Luna", species: "cat", age: 7 }
]
const sumOfAges = myPets.reduce((sum, pet) => sum + pet.age, 0);
console.log(sumOfAges); // 37
```

<br />

`arr.reduce()` other examples:
```js
// example 1
const items = [
  { name: 'Bike', price: 100 },
  { name: 'TV', price: 200 },
  { name: 'Album', price: 10 },
  { name: 'Book', price: 5 },
  { name: 'Phone', price: 500 },
  { name: 'Computer', price: 1000 },
  { name: 'Keyboard', price: 25 }
]
const total = items.reduce((currentTotal, item) => {
  return item.price + currentTotal
}, 0)
console.log(total) // 1840

// example 2
const arr = [1, 2, 3, 4, 5, 6];
const total = arr.reduce((accum, currVal) => (accum + currVal), 10);
console.log(total); // 31

// Combine Methods
const combined = ages
  .map(age => age * 2)
  .filter(age => age >= 40)
  .sort((a, b) => a - b)
  .reduce((a, b) => a + b, 0);
console.log(combined); // 798
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## String methods

`str.toLowerCase()`, `str.toUpperCase()`, and `str.trim()` are so basic that I am not providing examples. Just attach one of these methods to the variable name for your string: e.g.:

```js
let badString = "   oOPS, caps LOCK ON. nEED TO FIX.   "
console.log(badString.toLowerCase().trim()); // "oops, caps lock on. need to fix."
// need to capitalize first letter and add a regex for the first char after the period.
```

- [MDN substring](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/substring)
- [MDN endsWith](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/endsWith)
- [MDN test](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/test)
- [MDN match](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/match)
- [MDN replace](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace)

### substring

`str.substring()`:
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

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### endsWith

`str.endsWith()`:
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

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### test

`regex.test(str)`:
```js
const str = 'table football';
const regex = /foo*/;
console.log(regex.test(str));

const str = 'hello world!';
const result = /^hello/.test(str);
console.log(result); // true
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### match

`str.match()`:
```js
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

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### replace

`str.replace()` syntax:
```js
replace(regexp, newSubstr)
replace(regexp, replacerFunction)

replace(substr, newSubstr)
replace(substr, replacerFunction)
```

<br />

`str.replace()`:
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

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Miscellaneous

typeof:
```js
let typeOfTest;
typeOfTest = "";
console.log(typeof typeOfTest) // string
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

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Spread and Rest syntax

Exampes of how to use the spread operator and rest parameter.

### Spread operator for arrays and strings

add other array items to an array:
```js
const diffSubjects = ['spread operator', 'while loop', 'destructuring assignment', 'high order array methods', 'classes'];
let jsSubjects = ['variables', 'functions', 'data types', ...diffSubjects ];
```

<br />

concatenate arrays:
```js
var arr3 = [0, 1, 2];
var arr4 = [3, 4, 5];
arr3 = [...arr3, "spread", ...arr4, "operator"];
// same as arr1.concat(arr2);
```

<br />

another copy / concatenate example:
```js
const arr5 = ['JAN', 'FEB', 'MAR', 'APR', 'MAY'];
let arr6;
arr6 = [...arr5, 'JUN', 'JUL']; 
```

<br />

concat and changing values:
```js
const jimsfood = ["Chips", "Fish", "Beer"]
const lunasfood = [...jimsfood, "Chicken", "Pork", "Tuna"]
lunasfood[0] = "Catnip";
lunasfood[2] = "Milk";
// console.log(lunasfood)
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Rest parameter and rest syntax

Rest syntax, pie eating contest scores:
```js
const pieContest = [
  ["Jenny", 95], ["Betty", 90], ["Jacob", 85], ["Mary", 82], ["Owen", 80], ["Becky", 75], ["Nancy", 70], ["Edward", 65], ["Clyde", 61], ["Beth", 59]
];
const [firstPlace, secondPlace, thirdPlace, ...losers] = pieContest;

console.log(`Pie Contest:\nFirst Place: ${firstPlace[0]}, Score: ${firstPlace[1]} 🥇\nSecond Place: ${secondPlace[0]}, Score: ${secondPlace[1]} 🥈\nThird Place: ${thirdPlace[0]}, Score: ${thirdPlace[1]}  🥉`);
console.log(losers);
```

<br />

with a high order array method:
```js
const sum = (...args) => {
  return args.reduce((a, b) => a + b, 0);
}
console.log(sum(2, 3, 4)); // 9
```

<br />

High order array method 2: The rest param MUST be the LAST parameter:
```js
function multiply(multiplier, ...theArgs) {
  return theArgs.map(function(element) {
    return multiplier * element;
  });
}

var arr7 = multiply(2, 4, 5, 6); 
console.log(arr7)
```

<br />

High order array method 3:
```js
function multiply2(multiplier, ...nums) {
  return nums.map((num) => {
    return multiplier * num
  })
}
console.log("Multiply2: " + multiply2(15, 1, 3, 5, 1.5));
```

<br />

REST AND SPREAD: forEach instead of reduce
```js
function sumNumberRest(...numbers) {
  // above is the rest operator
  let mySum = 0;
  numbers.forEach(number => mySum += number);
  return mySum;
}
const numbers = [1, 2, 3, 4, 5, 6];

// below is the spread operator
console.log(sumNumberRest(...numbers))
```

<br />

REST again but with great examples and with forEach:
```js
function getTodaysMenu(...items) {
  let myStr = `Today's menu: `;
  items.forEach(item => myStr += `\n${item[0]}: ${item[1]}`);
  return myStr;
}
console.log(getTodaysMenu(["Pizza", "$8"], ["Chips", "$1"], ["Beer", "$3"]));
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Syntax tables

Common methods with NO arguments/parameters:
| method  | syntax            | 
| :----   | :----             | 
| pop     | arr.pop()         |                            
| shift   | arr.shift()       |                            
| reverse | arr.reverse()     |                            
| sort    | arr.sort()        |   
| join    | arr.join()        |         


<br />

Common methods with a single argument, or multiple repeated arguments:
| method  | syntax1                     | syntax2                     | 
| :----   | :----                       | :----                       | 
| join    | arr.join(sep)               |                             | 
| test    | regex.test(str)             |                             |          
| match   | str.match(regex)            |                             |
| push    | arr.push(item)              | push(item1, item2, ...)     | 
| unshift | arr.unshift(item)           | unshift(item1, item2, ...)  |
| replace | str.replace(regex, newStr)  | str.replace(substr, newStr) |
| indexOf | arr.indexOf(searchVal)      | str.indexOf(searchVal, fromIndex) |
| lastIndexOf | str.lastIndexOf(searchVal) | arr.lastIndexOf(searchVal, fromIndex) |
| includes | arr.includes(searchVal)    | str.includes(searchVal, fromIndex) |
| substring | str.substring(indStart)   | str.substring(indStart, indEndex) |
| endsWith | str.endsWith(subStr)       | str.endsWith(subStr, length) | 
| concat  | arr.concat(arr2)            | arr.concat(arr2, arr3, ...)     | 
|         | arr.concat(item)            | arr.concat(item1, item2, ...)   | 
| splice  | arr.splice(start)           | splice(start, deleteCt) |
|         | splice(start, deleteCt, item1) | splice(start, deleteCt, item1, item2, ...) |

<br />

`replace` method with an argument and a callback function:
| method    | syntax1                 | syntax2                     | 
| :----     | :----                   | :----                       | 
| replace() | str.replace(regex, Fx)  | str.replace(substr, Fx)     |

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

<br />

High order array methods with **callback** function:
| method  | syntax1           | syntax2                   |
| :----   | :----             | :----                     |
| sort    | sort(callbackFn)  |                           |
| find    | find(callbackFn)  | find(callbackFn, thisArg) |
| every   | every(callbackFn) | every(callbackFn, thisArg) |
| some    | some(callbackFn)  | some(callbackFn, thisArg) |
| map     | map(callbackFn)   | map(callbackFn, thisArg) |
| filter  | filter(callbackFn) | filter(callbackFn, thisArg) |
| forEach | forEach(callbackFn) | forEach(callbackFn, thisArg) |
| reduce  | reduce(callbackFn) | reduce(callbackFn, initialValue) |

`thisArg` for `find`: Object to use as `this` inside `callbackFn`

`thisArg` for the other 5 methods: Value to use as `this` when executing `callbackFn` (same thing?)

<br />

High order array methods with **arrow** and inline functions.

Single argument/parameter:
| method  | syntax                          | 
| :----   | :----                           | 
| find    | arr.find((item) => { ... } )    |
|         | arr.find(function(item) { ... } ) |
| every   | arr.every((item) => { ... } )   |
|         | arr.every(function(item) { ... } ) |
| some    | arr.some((item) => { ... } )    |
|         | arr.some(function(item) { ... } ) |
| map     | arr.map((item) => { ... } )      |
|         | arr.map(function(item) { ... } ) |
| filter  | arr.filter((item) => { ... } )  |
|         | arr.filter(function(item) { ... } ) |
| forEach | arr.forEach((item) => { ... } ) |
|         | forEach(function(item) { ... } ) | 

<br />

**arrow** and inline functions with two arguments/parameters:
| method  | syntax                                | 
| :----   | :----                                 | 
| sort    | arr.sort((a, b) => { ... } )          | 
|         | arr.sort(function (a, a) { ... } )    |
| find    | arr.find((item, index) => { ... } )   |
|         | arr.find(function(item, index) { ... } ) |
| every   | arr.every((item, index) => { ... } )  |
|         | arr.every(function(item, index) { ... }) |
| some    | arr.some((item, index) => { ... } )   |
|         | arr.some(function(item, index) { ... }) |
| map     | arr.map((item, index) => { ... })     |
|         | arr.map(function(item, index) { ... } ) |
| filter  | arr.filter((item, index) => { ... } ) |
|         | arr.filter(function(item, index) { ... } ) |
| forEach | arr.forEach((item, index) => { ... } ) |
|         | arr.forEach(function(item, index) { ... } ) |
| reduce  | arr.reduce((prevVal, currVal) => { ... } ) |
|         | arr.reduce(function(prevVal, currVal) { ... } ) | 

<br />

**arrow** and inline functions with three arguments/parameters:
| method  | syntax                                | 
| :----   | :----                                 | 
| find    | arr.find((item, index, array) => { ... } )  |
|         | arr.find(function(item, index, array) { ... } ) |
| every   | arr.every((item, index, array) => { ... } )  |
|         | arr.every(function(item, index, array){ ... } ) |
| some    | arr.some((item, index, array) => { ... } )  |
|         | arr.some(function(item, index, array){ ... }) |
| map     | arr.map((item, index, array) => { ... })     |
|         | arr.map(function(item, index, array){ ... } ) |
| filter  | arr.filter((item, index, array) => { ... } ) |
|         | arr.filter(function(item, index, array){ ... } ) |
| forEach | arr.forEach((item, index, array) => { ... } ) |
|         | arr.forEach(function(item, index, array){ ... } ) |
| reduce  | arr.reduce((prevVal, currVal, currInd) => { ... } ) |
|         | arr.reduce(function(prevVal, currVal, currIndex) { ... } ) |

<br />

**arrow** and inline functions with four and five arguments/parameters:
| method  | syntax                                | 
| :----   | :----                                 | 
| find    | arr.find(function(item, index, array) { ... }, thisArg) |
| every   | arr.every(function(item, index, array) { ... }, thisArg) |
| some    | arr.some(function(item, index, array) { ... }, thisArg) |
| map     | arr.map(function(item, index, array) { ... }, thisArg) |
| filter  | arr.filter(function(item, index, array) { ... }, thisArg) |
| forEach | arr.forEach(function(item, index, array) { ... }, thisArg) | 
| reduce  | arr.reduce((prevVal, currVal, currInd, array) => { ... } ) |
|         | arr.reduce(function(prevVal, currVal, currInd, array) { ... } ) |
|         | **arr.reduce((prevVal, currVal, currInd, array) => { ... }, initVal)** |
|         | arr.reduce(function(prevVal, currVal, currInd, array) { ... }, initVal) |
