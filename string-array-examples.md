# String and Array examples

Syntax and code examples for the most coomon string and array methods.

<div id="back-to-top"></div>

## Table of contents

| Topic               | Sub-topic | Sub-topic | Sub-topic | Sub-topic |  
| ----:               | :-------    | :------     | :------     | :------     |
| 1. [Simple array methods](#simple-array-methods): | i. [push](#push) | ii. [unshift](#unshift) | iii. [pop](#pop) | iv. [shift](#shift) |
|                     | v. [Basic sort](#basic-sort) | vi. [reverse](#reverse) | vii. [splice](#splice) | vii. [Array slice](#array-slice) |
|                     | ix. [concat](#concat) | x. [join](#join) | - | - | 
|                     | xi. [indexOf](#indexOf) | xii. [lastIndexOf](#lastIndexOf) | xiii. [Includes](#includes) | - |
| 2. [High order methods](#high-order-methods): | i. [Sort](#sort) | ii. [Find](#find) | iii. [Every](#every) | iv. [Some](#some) | 
|                     | v. [Map](#map) | vi. [Filter](#filter) | vii. [forEach](#forEach) | viii. [Reduce](#reduce) |
| 3. [String methods](#string-methods):  | i. [String slice](#string-slice) | ii. [split](#split) | iii. [substring](#substring) | iv. [repeat](#repeat) |
|                     | v. [endsWith](#endsWith) | vi. [test](#test) | - | - |
|                     | vii. [match](#match) | viii. [replace](#replace) | ix. [toString](#tostring) | x. [Miscellaneous](#Miscellaneous) |
| 4. [Spread operator](#spread-operator)  | | | | |
| 5. [Rest syntax](#rest-syntax)      | | | | | 
| 6. [Syntax tables](#syntax-tables): | i. [Common methods](#common-methods) | ii. [High order array](#high-order-array) | - | - | 


## Simple array methods

Basic syntax for the most common methods. I skipped `flat()`, `findIndex()` and `Array.isArray()`.

### push

Adds one or more elements to the end of an array and returns the new length of the array. Requires at least 1 argument, mutates the array.

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

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push">MDN Push</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### unshift

Adds one or more elements to the beginning of an array and returns the new length of the array. Requires at least 1 argument, mutates the array.

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

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift">MDN Unshift</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### pop

Removes the last element from an array and returns that element. No arguments required, mutates the array.

```js
// arr.pop()
let arr = ['a', 'b', 'c', 'd'];
let removedItem = arr.pop();
console.log(removedItem); // "d"
console.log(arr); // ["a","b","c"]
```

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/pop">MDN Pop</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### shift

Removes the first element from an array and returns that element. No arguments required, mutates the array.

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

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/shift">MDN Shift</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Basic sort

Sorts an array in ascending order. When no arguments are passed, numbers are sorted as strings. Mutates the array. Can be used on strings.

If you use the spread operator to access the array, the original array is not mutated; otherwise it is. Same with `reverse()`. Note, don't use a callback function for sorting text. Also, check out [MDN sort description](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort#description) for how to sort by the key of an object.

```js
// Syntax:
sort()

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

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort">MDN Sort</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### reverse

Reverses the order of an array, mutates the array.

```js
// Syntax
reverse()

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

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse">MDN Reverse</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### splice

Changes the contents of an array by removing or replacing existing elements and/or adding new elements. Mutates the array.

MDN syntax (MUTATES!):
```js
splice(startIndex)
splice(startIndex, deleteCount)
splice(startIndex, deleteCount, item1)


// splice(startIndex):
let arr = [1, 2, 3, 4, 5, 6]
console.log(arr.splice(2)) // [1,2]
// splice(startIndex, deleteCount):
console.log(arr.splice(2,2)) // [1,2,5,6]
// splice(startIndex, deleteCount, item1, item2, itemN):
console.log(arr.splice(2,2,100,101)) // [1,2,100,1015,6]


// Assign to a new array
let arr = [1, 2, 3, 4, 5, 6]
let arr2 = arr.splice(2)
console.log(arr2, arr) // [3,4,5,6] [1,2]
let arr2 = arr.splice(2,2)
console.log(arr2, arr) // [3,4] [1,2,5,6]
let arr2 = arr.splice(2,2)
console.log(arr2, arr) // [3,4] [1,2,100,101,5,6]
```

<br />

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

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice">MDN Splice</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Array slice

Extracts a section of the calling array and returns a new array, does not mutate the array. Can be used on strings.

MDN syntax:
```js
slice()
slice(startIndex)
slice(startIndex, endIndex)


let arr = [1, 2, 3, 4, 5, 6]
console.log(arr.slice()) // [1,2,3,4,5,6]
// slice(startIndex)
arr.slice(2) // [1,2,3,4,5,6]
let arr2 = arr.slice(2)
console.log(arr2, arr) // [3,4,5,6] [1,2,3,4,5,6]
// slice(startIndex, endIndex) endIndex must be greater than start
let arr2 = arr.slice(2,4)
console.log(arr2, arr) // [3,4] [1,2,3,4,5,6]
```

<br />

Examples:
```js
const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];
console.log(animals.slice()); // ["ant", "bison", "camel", "duck", "elephant"]
console.log(animals.slice(2)); // ["camel", "duck", "elephant"]
console.log(animals.slice(-2)); // ["duck", "elephant"]
console.log(animals.slice(2, 4)); // ["camel", "duck"]
console.log(animals.slice(1, 5)); // ["bison", "camel", "duck", "elephant"]
console.log(animals.slice(2, -1)); // ["camel", "duck"]


// Example 2:
let myHonda = { color: 'red', wheels: 4, engine: { cylinders: 4, size: 2.2 } }
let myCar = [myHonda, 2, 'cherry condition', 'purchased 1997']
let newCar = myCar.slice(0, 3)
console.log(newCar)
// // [{ color: 'red', wheels: 4, engine: { cylinders: 4, size: 2.2 } }, 2, "cherry condition"]
```

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice">MDN Array Slice</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### concat

Joins two or more arrays and returns a copy of the joined arrays. Does not mutate the array. Can be used on strings.

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

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat">MDN concat</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### join

Returns a new string by concatenating all of the elements in an array. Does not mutate the array.

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
// add this on: filter(word => word !== "")
console.log(urlSlug); // "common-array-methods-you-should-know"
```

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join">MDN Join</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### indexOf

Returns the first index at which a given element can be found in the array, or -1 if it is not present. Can be used on strings.

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


// another example
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

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf">MDN indexOf</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### lastIndexOf

Returns the last index at which a given element can be found in the array, or -1 if it is not present. Can be used on strings.

Examples:
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

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/lastIndexOf">MDN lastIndexOf</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Includes

Determines whether an array includes a certain value among its entries, returning `true` or `false` accordingly.

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

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/includes">MDN includes</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## High order methods

High Order Array Methods = methods that use a callback function. The most used ones are `sort`, `map`, `filter`, `forEach`, and `reduce`; but also `find`, `every`, and `some` are useful.

### Sort

Sorts an array in ascending order. Mutates the array. Can be used on strings.

Callback examples:
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

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort">MDN Sort</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Find

Returns the first element in the provided array that satisfies the provided testing function. If no values satisfy the testing function, `undefined` is returned.

MDN syntax:
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

<br />

MDN examples
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

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find">MDN Find</a></div></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Every

Returns a boolean if EVERY element in an array passes a test.

MDN syntax:
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

Examples:
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

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every">MDN Every</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Some

Returns a boolean if at least one element passes a test.

MDN syntax:
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

Arrow examples:
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

Callback examples:
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

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some">MDN Some</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Map

Performs a function on every element in an array and places the result in a new array.

MDN syntax:
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

Basic / simple examples:
```js
//      MDN examples
const arr = [1, 2, 3]
const mapArr = arr.map(n => n * 3)
console.log(mapArr)


const array1 = [1, 4, 9, 16];
const map1 = array1.map(x => x * 2);
console.log(map1);


const numbers = [1, 4, 9];
const roots = numbers.map((num) => Math.sqrt(num)); // roots is now [1, 2, 3]


//      Other examples:
const numArray = [1, 2, 3, 4, 5, 6];
const divideNums = numArray.map(item => item / 2.5);
console.log(divideNums); // [0.4, 0.8, 1.2, 1.6, 2, 2.4]


const numArray = [1, 2, 3, 4, 0.5, -3];
const numRemainder = numArray.map(item => item % 2);
console.log(numRemainder); // [1, 0, 1, 0, 0.5, -1]


const numArray = [1, 2, 3, 4, 5, 6];
const cubedNum = numArray.map(item => Math.pow(item, 3));
console.log(cubedNum); // [1, 8, 27, 64, 125, 216]


// cubed root
const numArray = [8, 27, 1.61803];
const cubedRoot = numArray.map(item => Math.pow(item, 1 / 3));
console.log(cubedRoot); // [2, 3, 1.1739840320085808]


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
// A shorter version is to lose the 'return keyword and curly brackets:
const itemNames = items.map(item => item.price)


// Examples from Traversy courses: Double eveyones money
function doubleMoney() {
  data = data.map(user => {
    return { ...user, money: user.money * 2 };
  });
}


//      feeCodeCamp examples
// Great example of te spread operator for a string using Math and map methods!
function longestWord(str) {
  return Math.max(...str.split(" ").map(word => word.length));
}
longestWord("Find the longest word in this sentence"); // 8


// Get object key values, similar to what Object.values does on a single object, 
// but you can not use that because 'users' is an array of objects, not a single 
// object with multiple key-value pairs
const users = [
  { name: 'John', age: 34 },
  { name: 'Amy', age: 20 },
  { name: 'camperCat', age: 10 }
];
const names = users.map(user => user.name);
console.log(names); // ["John","Amy","camperCat"]
```

Intermediate examples:
```js
//      freeCodeCamp:
// CONVERT HTML ENTITIES
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
console.log(convertHTML("<li>List item one</li>")); // "&lt;li&gt;List item one&lt;/li&gt;"
// I would never thought of using an or operaator ||


// Examples from Traversy: creates the select element with options
function createBreedList(breedList) {
  document.getElementById("breed").innerHTML = `
    <select onchange="loadByBreed(this.value)">
      <option>Choose a dog breed</option>
      ${Object.keys(breedList).map(function (breed) {
    return `<option>${breed}</option>`
  }).join('')}
    </select>
  `
}
```

<br />

Difficult / advanced examples:
```js
//      MDN:
// reformat objects in an array (WHY?)
const kvArray = [
  { key: 1, value: 10 },
  { key: 2, value: 20 },
  { key: 3, value: 30 }
  ];
const reformattedArray = kvArray.map(({ key, value}) => ({ [key]: value }));
console.log(reformattedArray) // {"1": 10}, {"2": 20}, {"3": 30}
// what is { key, value}? Destructuring?
```

**NOTE**: Look into [**Array.from()**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from) and constrast with `.map()`. Check out [Stackoverflow: Array.from vs Array.prototype.map](https://stackoverflow.com/questions/26052699/array-from-vs-array-prototype-map).


<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map">MDN Map</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Filter

Takes a function containing a test and returns a new array with all the elements that pass that test. The filtration is done using a function that returns a boolean value. If no elements pass the test, an empty array will be returned.

MDN syntax:
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

Basic / simple examples:
```js
const ages = [33, 12, 20, 16, 5, 54, 21, 44, 61, 13, 15, 45, 25, 64, 32];
const canDrink = ages.filter(age => age >= 21);
console.log(canDrink);
// or better, sort the numbers as well:
const canDrink = ages.filter(age => age >= 21).sort((a, b) => { return a - b });


const ages = [5, 7, 9, 11, 13, 15, 16, 17, 19, 21, 23, 55]
const teen = ages.filter(age => age >= 13 && age <= 19)
console.log(teen) // [13, 15, 16, 17, 19]


//      MINE: In case of duplicate guitar notes, get only unique notes
let uniqueNotes = [];
uniqueNotes = chordTones.filter(tone => !uniqueNotes.includes(tone) && tone !== undefined ? uniqueNotes.push(tone) : null);


//      freeCodeCamp:
// functional 21: convert str to url slug (not as good as my ex. in string section)
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

<br />

Intermediate examples:
```js
//      Other examples:
// Traversy expense tracker
function updateValues() {
  const amounts = transactions.map(transaction => transaction.amount);

  const total = amounts.reduce((acc, item) => (acc += item), 0).toFixed(2);

  const income = amounts
    .filter(item => item > 0)
    .reduce((acc, item) => (acc += item), 0)
    .toFixed(2);

  const expense = (
    amounts.filter(item => item < 0).reduce((acc, item) => (acc += item), 0) * -1).toFixed(2);

  balance.innerText = `$${total}`;
  money_plus.innerText = `$${income}`;
  money_minus.innerText = `$${expense}`;
}


const companies= [
  {name: "Company One", category: "Finance", start: 1981, end: 2004},
  {name: "Company Two", category: "Retail", start: 1992, end: 2008},
  {name: "Company Three", category: "Auto", start: 1999, end: 2007},
  {name: "Company Four", category: "Retail", start: 1989, end: 2010},
  {name: "Company Five", category: "Technology", start: 2009, end: 2014},
  {name: "Company Six", category: "Finance", start: 1987, end: 2010},
  {name: "Company Seven", category: "Auto", start: 1986, end: 1996},
  {name: "Company Eight", category: "Technology", start: 2011, end: 2016},
  {name: "Company Nine", category: "Retail", start: 1981, end: 1989}
];
const retailCompanies = companies.filter(function(company) {
  if(company.category === 'Retail') {
    return companies;
  }
});
console.log(retailCompanies) // 3 objects, or try:
const retailCompanies = companies.filter(company => company.category === 'Retail');
const eightiesCompanies = companies.filter(company => (company.start >= 1980 && company.start < 1990));
console.log(eightiesCompanies) // 5 companies


//      freeCodeCamp:
//      DIFFICULTY: LOW-MODERATE
// Intermeidate Algorithms, 
// 2: Compare two arrays and return a new array with any items only found in one of the two given arrays - This is nice!
function diffArray(arr1, arr2) {
  return arr2
    .concat(arr1)
    .filter(item => !arr2.includes(item) || !arr1.includes(item));
}
console.log(diffArray([1, 2, 3, 5, 7], [1, 2, 3, 4, 5]));


// 3: Remove all elements from the initial array that are of the same value as the orther args
//          DIFFICULTY: LOW-MODERATE
function destroyer(arr, ...otherArgs) {
  return arr.filter(item => !otherArgs.includes(item));
}
console.log(destroyer([1, 2, 3, 1, 2, 3], 2, 3)); // [1,1]
// this is easier to read:
const inputArr = [1, 2, 3, 1, 2, 3];
destroyer(inputArr, 2, 3); // [1,1]


//      DIFFICULTY: LOW-MODERATE
// functional.js, lesson 16: return a new array containing the squares of only the positive integers
const squareList = (arr) => {
  return arr
    .filter(num => num > 0 && num % parseInt(num) === 0)
    .map(num => Math.pow(num, 2));
};
const squaredIntegers = squareList([-3, 4.8, 5, 3, -3.2]); // [25,9]
// console.log(squaredIntegers);
// What is parseInt doing? Aren't they all numbers?
```

<br />

Difficult / advanced examples:
```js
//      MDN:
//      DIFFICULTY: HIGH
//      Find all prime numbers in an array (REALLY CONFUSING)
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


//      Searching an array
//      DIFFICULTY: MEDIUM-HIGH
let fruits = ['apple', 'banana', 'grapes', 'mango', 'orange']

function filterItems(arr, query) {
  return arr.filter(function(el) {
    return el.toLowerCase().indexOf(query.toLowerCase()) !== -1
  })
}
console.log(filterItems(fruits, 'ap'))  // ['apple', 'grapes']
console.log(filterItems(fruits, 'an'))  // ['banana', 'mango', 'orange']
// how does the partial string 'ap' return apple and grape? 
// The return line can be shortened to: return el.indexOf(query) !== -1


//      freeCodeCamp:
//      DIFFICULTY: EXTREMELY HIGH!!!
// 4: Make a function that looks through an array of objects (1st arg) and returns an array of all 
// objects that have matching name and value pairs (2nd arg).

function whatIsInAName(collection, source) {
  let getKeys = Object.keys(source); // array of key(s) ["last"]

  // What is confusing here is the triple return - I would never have gotten this
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
); // [ { "first": "Tybalt", "last": "Capulet" } ]
```

<br />

`filter()` solution "skeletons" (looking for patterns):
```js
1) .filter(item => ...).sort((a, b) => ...)
2) .filter(function(item) => for loop)
3) return arr.filter(function( {return (item) return item.indexOf(str))})
4) return arr2.concat(arr1).filter(item => !arr2.includes(item) ...)
5) .filter(item => !args.includes(item))
6) Object.keys, return arr.filter(function(item) return .every(function(key) return item.hasOwnProperty ...))
7) .filter(item => parseInt(item)... .map(item => Math.pow))
8) .split.filter(item => .join().toLowerCase())
9) .filter(item => !arr.includes(item) && item ... .push(item))
Traversy) .filter .reduce .toFixed

COUNT TOTALS: "if's" (4), includes (3), multiple returns (3), reduce(2), rest op, map, concat, indexOf, sort, hasOwnProperty => the multiple returns really throws me off!
```

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter">MDN Filter</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### forEach

Executes a provided function once for each array element; calls a provided `callbackFn` function once for each element in an array in ascending index order. It is not invoked for index properties that have been deleted or are uninitialized.

MDN syntax:
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

**NOTE**: `forEach` expects a synchronous function. `forEach` does not wait for promises. Make sure you are aware of the implications while using promises (or async functions) as `forEach` callback.

<br />

Basic / simple examples:
```js
//      MDN:
const array1 = ['a', 'b', 'c'];
array1.forEach(element => console.log(element)); // "a" "b" "c"


//      Other examples:
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
  console.log(item.name) // "Bike" "TV" "Album" "Book" "Phone" "Computer" "Keyboard"
})


const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];
const result = words.filter(word => word.length > 6);
console.log(result); // ["exuberant","destruction","present"]


// Example from my guitar chord namer app
let position = chromaticSharps.indexOf(uniqueNotes[i]);
let noteAsRoot = chromaticSharps.slice(position, position + 12);
uniqueNotes.forEach(note => noteSteps.push(noteAsRoot.indexOf(note)));


//      freeCodeCamp:
// Filtering out all small values
function isBigEnough(value) {
  return value >= 10
}
let filtered = [12, 5, 8, 130, 44].filter(isBigEnough)
console.log(filtered); // [12,130,44]
```

<br />

Intermediate examples:
```js
//      MDN:
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


// Modifying the array during iteration
// any number if the condition removes "one"
// why was "three" removed?
const words = ['one', 'two', 'three', 'four'];
words.forEach((word) => {
  console.log(word);
  if (word === 'two') {
    words.shift(); //'one' will delete from array
  }
}); // "one" "two" "four"
console.log(words); // ['two', 'three', 'four']


//      Other examples:

//      freeCodeCamp:

```

<br />

Difficult / advanced examples:
```js
//      MDN:
// An object copy function: This is one way to create a copy of an object:
const copy = (obj) => {
  const copy = Object.create(Object.getPrototypeOf(obj));
  const propNames = Object.getOwnPropertyNames(obj);
  propNames.forEach((name) => {
    const desc = Object.getOwnPropertyDescriptor(obj, name);
    Object.defineProperty(copy, name, desc);
  });
  return copy;
};
const obj1 = { a: 1, b: 2 };
const obj2 = copy(obj1); // obj2 looks like obj1 now (WHY?)

//      Other examples:

//      freeCodeCamp:

```

Examples from Traversy courses:
```js
const customers = JSON.parse(this.responseText);
  let output = '';

  customers.forEach(function(customer) {
    output += `
    <ul>
      <li>ID: ${customer.id}</li>
      <li>Name: ${customer.name}</li>
      <li>Company: ${customer.company}</li>
      <li>Phone: ${customer.phone}</li>
    </ul>
  `;
});


// Get Tasks from Local Storage
function getTasks() {
  let tasks;
  if (localStorage.getItem('tasks') === null) {
    tasks = [];
  } else {
    tasks = JSON.parse(localStorage.getItem('tasks'));
  }

  tasks.forEach(function (task) {
    const li = document.createElement('li');
    li.className = 'collection-item';
    li.appendChild(document.createTextNode(task));
    const link = document.createElement('a');
    link.className = 'delete-item secondary-content';
    link.innerHTML = '<i class="fa fa-remove"></i>';
    li.appendChild(link);
    taskList.appendChild(li);
  });
}

// Remove from Local Storage
function removeTaskFromLocalStorage(taskItem) {
  let tasks;
  if (localStorage.getItem('tasks') === null) {
    tasks = [];
  } else {
    tasks = JSON.parse(localStorage.getItem('tasks'));
  }

  tasks.forEach(function (task, index) {
    if (taskItem.textContent === task) {
      tasks.splice(index, 1);
    }
  });
  localStorage.setItem('tasks', JSON.stringify(tasks));
}


// posts object
function getPosts() {
  setTimeout(function() {
    let output = '';
    posts.forEach(function(post){
      output += `<li>${post.title}</li>`;
    });
    document.body.innerHTML = output;
  }, 1000);
}
createPost({title: 'Post Three', body: 'This is post three'}, getPosts);


// get local json file
function getJson() {
  fetch('posts.json')
    .then(res => res.json())
    .then(data =>  {
      console.log(data);
      let output = '';
      data.forEach(function(post) {
        output += `<li>${post.title}</li>`;
      });
      document.getElementById('output').innerHTML = output;
    })
    .catch(err => console.log(err));
}


// get external API data from api.github/users
function getExternal() {
  fetch('https://api.github.com/users')
    .then(res => res.json())
    .then(data =>  {
      console.log(data);
      let output = '';
      data.forEach(function(user) {
        output += `<li>${user.login}</li>`;
      });
      document.getElementById('output').innerHTML = output;
    })
    .catch(err => console.log(err));
}


// Check required fields
function checkRequired(inputArr) {
  inputArr.forEach(function (input) {
    if (input.value.trim() === '') {
      showError(input, `${getFieldName(input)} is required`);
    } else {
      showSuccess(input);
    }
  });
}


// get data from localstorage and populate UI
function populateUI() {
  const selectedSeats = JSON.parse(localStorage.getItem('selectedSeats'));

  if (selectedSeats !== null && selectedSeats.length > 0) {
    seats.forEach((seat, index) => {
      if (selectedSeats.indexOf(index) > -1) {
        seat.classList.add('selected');
      }
    });
  }
```

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach">MDN forEach</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Reduce

Executes a user-supplied "_reducer_" callback function on each element of the array, passing in the return value from the calculation on the preceding element. The final result of running the _reducer_ across all elements of the array is **a single value**.

The first time that the callback is run there is no "return value of the previous calculation". If supplied, an initial value may be used in its place. Otherwise the array element at index 0 is used as the initial value and iteration starts from the next element (index 1 instead of index 0).

MDN syntax:
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

Basic / simple examples:
```js
//      MDN:
const array1 = [1, 2, 3, 4];
const initialValue = 0;
const sumWithInitial = array1.reduce(
  (previousValue, currentValue) => previousValue + currentValue,
  initialValue
);
console.log(sumWithInitial); // 10


const getMax = (a, b) => Math.max(a, b);
const arr = [1, 100, 5, 72];
// callback is invoked for each element in the array starting at index 0
console.log(arr.reduce(getMax, 50)); // 100


// Sum all the values of an array
let sum = [0, 1, 2, 3].reduce(function (previousValue, currentValue) {
  return previousValue + currentValue
}, 0) 
// sum is 6, or an arrow function:
let total = [ 0, 1, 2, 3 ].reduce(
  ( previousValue, currentValue ) => previousValue + currentValue,
  0
)


// Bonding arrays contained in an array of objects using the 
// spread operator and initialValue
let friends = [{
  name: 'Anna',
  books: ['Bible', 'Harry Potter'],
  age: 21
}, {
  name: 'Bob',
  books: ['War and peace', 'Romeo and Juliet'],
  age: 26
}, {
  name: 'Alice',
  books: ['The Lord of the Rings', 'The Shining'],
  age: 18
}]

let allbooks = friends.reduce(function(previousValue, currentValue) {
  return [...previousValue, ...currentValue.books]
}, ['Alphabet'])

// allbooks = [ 'Alphabet', 'Bible', 'Harry Potter', 'War and peace',
//              'Romeo and Juliet', 'The Lord of the Rings', 'The Shining' ]


//      Other examples:
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


//      freeCodeCamp:
// es6.js, use the rest parameter with function parameters
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

Intermediate examples:
```js
//      MDN:
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


// Remove duplicate items in an array
let dupsArr = ['a', 'b', 'a', 'b', 'c', 'e', 'e', 'c', 'd', 'd', 'd', 'd']
let noDups = dupsArr.reduce(function (prevVal, currVal) {
  if (prevVal.indexOf(currVal) === -1) {
    prevVal.push(currVal)
  }
  return prevVal
}, [])
console.log(noDups) // ["a","b","c","e","d"]


// Replace .filter().map() with .reduce()
const numbers = [-5, 6, 2, 0,];
const doubledPositiveNumbers = numbers.reduce((previousValue, currentValue) => {
  if (currentValue > 0) {
    const doubled = currentValue * 2;
    previousValue.push(doubled);
  }
  return previousValue;
}, []);
console.log(doubledPositiveNumbers); // [12, 4]


//      Other examples:
// Combine Methods
const combined = ages
  .map(age => age * 2)
  .filter(age => age >= 40)
  .sort((a, b) => a - b)
  .reduce((a, b) => a + b, 0);
console.log(combined); // 798


//      freeCodeCamp:
// Example with strings:
function findLongestWordLength(str) {
  return str.split(' ')
    .reduce(function(longest, word) {
      return Math.max(longest, word.length)
    }, 0);
}
findLongestWordLength("Find the longest word in this sentence"); // 8
```

<br />

Difficult / advanced examples:
```js
//      MDN:
// How reduce() works without an initial value
const array = [15, 16, 17, 18, 19];

function reducer(previous, current, index, array) {
  const returns = previous + current;
  console.log(`previous: ${previous}, current: ${current}, index: ${index}, returns: ${returns}`);
  return returns;
}
array.reduce(reducer);
// With an initial value:
array.reduce( (previousValue, currentValue, currentIndex, array) => previousValue + currentValue, 10 )


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
}, {}) // countedNames is: { 'Alice': 2, 'Bob': 1, 'Tiff': 1, 'Bruce': 1 }


// Grouping objects by a property
let people = [
  { name: 'Alice', age: 21 },
  { name: 'Max', age: 20 },
  { name: 'Jane', age: 20 }
];

function groupBy(objectArray, property) {
  return objectArray.reduce(function (acc, obj) {
    let key = obj[property]
    if (!acc[key]) {
      acc[key] = []
    }
    acc[key].push(obj)
    return acc
  }, {})
}

let groupedPeople = groupBy(people, 'age')
// groupedPeople is:
// { 20: [ { name: 'Max', age: 20 },
//         { name: 'Jane', age: 20 } ],
//   21: [ { name: 'Alice', age: 21 } ] }


//      freeCodeCamp:
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
```

Examples from Traversy courses:
```js
// update, balance, income, expense
function updateValues() {
  const amounts = transactions.map(transaction => transaction.amount);

  const total = amounts.reduce((acc, item) => (acc += item), 0).toFixed(2);

  const income = amounts
    .filter(item => item > 0)
    .reduce((acc, item) => (acc += item), 0)
  // .toFixed(2);

  const expense = (amounts
    .filter(item => item < 0)
    .reduce((acc, item) => (acc += item), 0)
    .toFixed(2)) * -1;

  balance.innerText = `$${total}`;
  money_plus.innerText = `$${income}`;
  money_minus.innerText = `$${expense}`;
}
```

<div align="left">&#8675; <a href="#syntax-tables" title="Syntax tables">To syntax tables</a> | &#10146; <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce">MDN Reduce</a></div>
<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## String methods

`str.toLowerCase()`, `str.toUpperCase()`, and `str.trim()` are so basic that I am not providing examples. Just attach one of these methods to the variable name for your string: e.g.:

```js
let badString = "   oOPS, caps LOCK ON. nEED TO FIX.   "
console.log(badString.toLowerCase().trim()); // "oops, caps lock on. need to fix."
// need to capitalize first letter and add a regex for the first char after the period.
```

### String slice

Extracts a section of a string and returns it as a new string, **_without_** modifying the original string.

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

### split

Divides a String into substrings, puts these substrings into an array, and returns the array. Does not mutate the string.

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

Returns the part of the string between the start and end indexes, or to the end of the string. Does not mutate the string.

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

Constructs and returns a new string which contains the specified number of copies of the string on which it was called, concatenated together.

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

Determines whether a string ends with the characters of a specified string. Returns `true` or `false`.

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

Executes a search for a match between a regular expression and a specified string. Returns `true` or `false`.

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

### match

Used to match regular expression against a string. Returns an array of the match(es) or `null` if no matches are found.

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

Returns a new string with some or all matches of a `pattern` replaced by a `replacement`. The `pattern` can be a string or a `RegExp`, and the `replacement` can be a string or a function to be called for each match. If `pattern` is a string, only the first occurrence will be replaced.

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


## Spread operator

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

## Rest syntax

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

Tables by the number of arguments and whether or not the method mutates the original source.

### Common methods

Common methods with NO arguments/parameters:
| method  | syntax            | Mutates? |
| :----   | :----             | :----:   |
| pop     | arr.pop()         | YES |                 
| shift   | arr.shift()       | YES |                     
| reverse | arr.reverse()     | YES* |
| sort    | arr.sort()        | YES* |
| join    | arr.join()        | YES |
| split   | str.split()       | YES |
| slice   | arr.slice()       | NO  |     
| toString | num.toString(radix) | NO  | 
|         | arr.toString()    | NO  | 
|         | date.toString()   | NO  | 
|         | bool.toString()   | NO  | 
|         | obj.toString() | NO  | 
|         | function.toString() | NO  | 

**NOTE**: Use the rest paramter to not mutate the original source for `sort()` and `reverse()`.

<br />

Common methods with a single argument, or multiple repeated arguments:
| method  | syntax1                     | syntax2                     | Mutates? |
| :----   | :----                       | :----                       | :----:   |
| join    | arr.join(separator)         |                             | NO |
| slice   | arr.slice(start)            |                             | NO |
| split   | str.split(separator)        |                             | NO |
| repeat  | str.repeat(count)           |                             | NO | 
| substring | str.substring(indStart)   | str.substring(indStart, indEndex) | NO |
| replace | str.replace(regex, newStr)  | str.replace(substr, newStr) | NO |
| concat  | arr.concat(arr2)            | arr.concat(arr2, arr3, ...)     | NO |
|         | arr.concat(item)            | arr.concat(item1, item2, ...)   | NO |
| test    | regex.test(str)             |                             | N/A |         
| match   | str.match(regex)            |                             | N/A |
| indexOf | arr.indexOf(searchVal)      | str.indexOf(searchVal, fromIndex) | N/A |
| lastIndexOf | str.lastIndexOf(searchVal) | arr.lastIndexOf(searchVal, fromIndex) | N/A |
| endsWith | str.endsWith(subStr)       | str.endsWith(subStr, length) | N/A |
| includes | arr.includes(searchVal)    | str.includes(searchVal, fromIndex) | N/A |
| push    | arr.push(item)              | push(item1, item2, ...)     | YES |
| unshift | arr.unshift(item)           | unshift(item1, item2, ...)  | YES |
| splice  | arr.splice(start)           | splice(start, deleteCt) | YES | 
|         | splice(start, deleteCt, item1) | splice(start, deleteCt, item1, item2, ...) | YES |

<br />

Common methods with two arguments:
| method    | syntax1                 | syntax2                 | Mutates? |
| :----     | :----                   | :----                   | :----:   |
| slice     | arr.slice(start, end)   |                         | NO |
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

<br />

### High order array

High order array methods with **callback** function:
| method  | syntax1           | syntax2                   | Mutates? |
| :----   | :----             | :----                     | :------: |
| sort    | sort(callbackFn)  |                           | YES* |
| every   | every(callbackFn) | every(callbackFn, thisArg) | N/A |
| some    | some(callbackFn)  | some(callbackFn, thisArg) | N/A |
| find    | find(callbackFn)  | find(callbackFn, thisArg) | NO |
| map     | map(callbackFn)   | map(callbackFn, thisArg) | NO |
| filter  | filter(callbackFn) | filter(callbackFn, thisArg) | NO |
| forEach | forEach(callbackFn) | forEach(callbackFn, thisArg) | NO |
| reduce  | reduce(callbackFn) | reduce(callbackFn, initialValue) | NO |

- `thisArg` for `find`: Object to use as `this` inside `callbackFn`
- `thisArg` for the other 5 methods: Value to use as `this` when executing `callbackFn` (same thing?)

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

High order array methods with **arrow** and inline functions.

Single argument/parameter:
| method  | syntax                            | Mutates? |
| :----   | :----                             | :------: |
| every   | arr.every((item) => { ... } )     | N/A |
|         | arr.every(function(item) { ... } ) | - |
| some    | arr.some((item) => { ... } )      | N/A |
|         | arr.some(function(item) { ... } ) | - |
| find    | arr.find((item) => { ... } )      | NO |
|         | arr.find(function(item) { ... } ) | - |
| map     | arr.map((item) => { ... } )       | NO |
|         | arr.map(function(item) { ... } )  | - |
| filter  | arr.filter((item) => { ... } )    | NO |
|         | arr.filter(function(item) { ... } ) | - |
| forEach | arr.forEach((item) => { ... } )   | NO |
|         | forEach(function(item) { ... } )  | - |

<br />

**arrow** and inline functions with two arguments/parameters:
| method  | syntax                                | Mutates? |
| :----   | :----                                 | :------: |
| sort    | arr.sort((a, b) => { ... } )          | YES* |
|         | arr.sort(function (a, a) { ... } )    | - |
| every   | arr.every((item, index) => { ... } )  | N/A |
|         | arr.every(function(item, index) { ... }) | - |
| some    | arr.some((item, index) => { ... } )   | N/A |
|         | arr.some(function(item, index) { ... }) | - |
| find    | arr.find((item, index) => { ... } )   | NO |
|         | arr.find(function(item, index) { ... } ) | - |
| map     | arr.map((item, index) => { ... })     | NO |
|         | arr.map(function(item, index) { ... } ) | - |
| filter  | arr.filter((item, index) => { ... } ) | NO |
|         | arr.filter(function(item, index) { ... } ) | - |
| forEach | arr.forEach((item, index) => { ... } ) | NO |
|         | arr.forEach(function(item, index) { ... } ) | - |
| reduce  | arr.reduce((prevVal, currVal) => { ... } ) | NO |
|         | arr.reduce(function(prevVal, currVal) { ... } ) | - |

<br />

**arrow** and inline functions with three arguments/parameters:
| method  | syntax                                          | Mutates? |
| :----   | :----                                           | :------: |
| every   | arr.every((item, index, array) => { ... } )     | N/A |
|         | arr.every(function(item, index, array){ ... } ) | - |
| some    | arr.some((item, index, array) => { ... } )      | N/A |
|         | arr.some(function(item, index, array){ ... })   | - |
| find    | arr.find((item, index, array) => { ... } )      | NO |
|         | arr.find(function(item, index, array) { ... } ) | - |
| map     | arr.map((item, index, array) => { ... })        | NO |
|         | arr.map(function(item, index, array){ ... } )   | - |
| filter  | arr.filter((item, index, array) => { ... } )    | NO |
|         | arr.filter(function(item, index, array){ ... } ) | - |
| forEach | arr.forEach((item, index, array) => { ... } )   | NO |
|         | arr.forEach(function(item, index, array){ ... } ) | - |
| reduce  | arr.reduce((prevVal, currVal, currInd) => { ... } ) | NO |
|         | arr.reduce(function(prevVal, currVal, currIndex) { ... } ) | - |

<br />

**arrow** and inline functions with four and five arguments/parameters:
| method  | syntax                                                  | Mutates? |
| :----   | :----                                                   | :----:   |
| every   | arr.every(function(item, index, array) { ... }, thisArg) | N/A |
| some    | arr.some(function(item, index, array) { ... }, thisArg) | N/A |
| find    | arr.find(function(item, index, array) { ... }, thisArg) | NO |
| map     | arr.map(function(item, index, array) { ... }, thisArg) | NO |
| filter  | arr.filter(function(item, index, array) { ... }, thisArg) | NO |
| forEach | arr.forEach(function(item, index, array) { ... }, thisArg) | NO |
| reduce  | arr.reduce((prevVal, currVal, currInd, array) => { ... } ) | NO |
|         | arr.reduce(function(prevVal, currVal, currInd, array) { ... } ) | - |
|         | **arr.reduce((prevVal, currVal, currInd, array) => { ... }, initVal)** | - |
|         | arr.reduce(function(prevVal, currVal, currInd, array) { ... }, initVal) | - |

- `array`: The array on which the method was called
- `initialValue`: A value to which `previousValue` is initialized the first time the callback is called. If `initialValue` is specified, that also causes `currentValue` to be initialized to the first value in the array. If `initialValue` is not specified, `previousValue` is initialized to the first value in the array, and `currentValue` is initialized to the second value in the array.
- `TypeError`: The array contains no elements and `initialValue` is not provided

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>