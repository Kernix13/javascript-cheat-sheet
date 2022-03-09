# String and Array examples

Examples for the more difficult to understand methods or the standard syntax for the most popular methods.

## Table of contents

<div id="back-to-top"></div>

1. [Simple array methods](#simple-array-methods)
   1. [push](#push)
   1. [unshift](#unshift)
   1. [pop](#pop)
   1. [shift](#shift)
   1. [join](#join)
   1. [Really basic sort](#really-basic-sort)
   1. [reverse](#reverse)
   1. [splice](#splice)
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
1. [Strings](#strings)
   1. [Common string methods](#common-string-methods)
1. [Spread and Rest syntax](#spread-and-rest-syntax)
   1. [Spread operator for arrays and strings](#spread-operator-for-arrays-and-strings)
   1. [Rest parameter and rest syntax](#rest-parameter-and-rest-syntax)

## Simple array methods

Basic syntax for simple versions of `push()`, `unshift()`, `pop()`, `shift()`, `sort()`, and `reverse()`:

- [MDN push](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push)
- [MDN unshift](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift)
- [MDN pop](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/pop)
- [MDN shift](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/shift)
- [MDN join](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join)
- [MDN reverse](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse)
- [MDN splice](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)

### push

```js
// arr.push(val1, ...)
let arr = ['a', 'b', 'c', 'd'];
let addedItem = arr.push('e');
console.log(addedItem); // 5
console.log(arr); // ['a', 'b', 'c', 'd', 'e']

// Merge 2 arrays, alterntive to concat():
let vegetables = ['parsnip', 'potato']
let moreVegs = ['celery', 'beetroot']
vegetables.push(...moreVegs);
console.log(vegetables)  // ['parsnip', 'potato', 'celery', 'beetroot']
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### unshift

```js
// syntax
arr.unshift(val1, ...)

// arr.unshift(val)
let arr = [1, 2, 3, 4];
let addedItem = arr.unshift(0);
console.log(addedItem); // 5
console.log(arr); // [0, 1, 2, 3, 4]
console.log(arr.unshift([-7, -6], [-5])) // [[-7, -6], [-5], 0, 1, 2, 3, 4]

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
const myFish = ['angel', 'clown', 'mandarin', 'surgeon'];
console.log('myFish before:', JSON.stringify(myFish));
const shifted = myFish.shift();
console.log('myFish after:', myFish);
console.log('Removed this element:', shifted);

// Using shift() method in while loop
const names = ["Andrew", "Edward", "Paul", "Chris" ,"John"];
while( typeof (i = names.shift()) !== 'undefined' ) {
    console.log(i);
}
// Andrew, Edward, Paul, Chris, John
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### join

`arr.join()`, commonly used with str.split():
```js
// syntax:
join()
join(separator)

// MDN Example:
const a = ['Wind', 'Water', 'Fire'];
a.join();      // 'Wind,Water,Fire'
a.join(', ');  // 'Wind, Water, Fire'
a.join(' + '); // 'Wind + Water + Fire'
a.join('');    // 'WindWaterFire'

// Here is an example using toLowerCase() and split() for a URL page slug
const blogTitle = "Common Array Methods You Should Know"
const pageSlug = blogTitle.toLowerCase().split(' ').join('-')
console.log(pageSlug); // "common-array-methods-you-should-know"
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Really basic sort

If you use the spread operator to access the array, the original array is not mutated; otherwise it is. For example, if you do `let newArr = arr.sort()`, then `arr` is sorted. Same with `reverse()`. Note, don't use a callback function for sorting text. Check out [MDN sort](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort#description) for how to sort ny the key of an object.

```js
// Sorting an array of strings using spread operating to NOT mutate original:
const arr = ["John", "Jim", "Mary", "Adam", "Zac", "Susan"];
let newArr = [...arr].sort();
console.log(newArr); // ["Adam","Jim","John","Mary","Susan","Zac"]
console.log("original: " + arr); // "original: John,Jim,Mary,Adam,Zac,Susan"

// Use this method to sort numbers as a string value:
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

// Alternate to the palindrome problem:
const word = "racecar";
const letters = word.toLowerCase().split(''); 
// the spread operator is a must here for reverse() to work
const revWord = [...letters].reverse().join('');

if (word === revWord) {
  console.log(word + " Is a palindrome");
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
  { name: 'Edward', value: 21 },
  { name: 'Sharpe', value: 37 },
  { name: 'And', value: 45 },
  { name: 'The', value: -12 },
  { name: 'Magnetic', value: 13 },
  { name: 'Zeros', value: 37 }
];
let itemsSort = items.sort(function (a, b) {
  return a.value - b.value;
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

let str = 'JavaScript String';
console.log(str.includes('Script')); // true
console.log(str.includes('script')); // false

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
```

**NOTE**: Look into [**Array.from()**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from) and constrast with `.map()`. Check out [Stackoverflow: Array.from vs Array.prototype.map](https://stackoverflow.com/questions/26052699/array-from-vs-array-prototype-map).

<br />

`arr.map()` freeCodeCamp examples:
```js
const users = [
  { name: 'John', age: 34 },
  { name: 'Amy', age: 20 },
  { name: 'camperCat', age: 10 }
];
const names = users.map(user => user.name);
console.log(names);

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
  // return item.name
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

<br />

`arr.filter()` simple examples:
```js
const ages = [33, 12, 20, 16, 5, 54, 21, 44, 61, 13, 15, 45, 25, 64, 32];
const canDrink = ages.filter(age => age >= 21);
console.log(canDrink);
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

## Strings

`str.toLowerCase()`, `str.toUpperCase()`, and `str.trim()` are so basic that I am not providing examples. Just attach one of these methods to the variable name for your string: e.g., 
```js
let badString = "   oOPS, caps LOCK ON. nEED TO FIX.   "
console.log(badString.toLowerCase().trim()); // "oops, caps lock on. need to fix."
```

### Common string methods

`regex.test(str)`:
```js
const str = 'table football';
const regex = /foo*/;
console.log(regex.test(str));

const str = 'hello world!';
const result = /^hello/.test(str);
console.log(result); // true
```

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

`str.replace()` syntax:
```js
replace(regexp, newSubstr)
replace(regexp, replacerFunction)

replace(substr, newSubstr)
replace(substr, replacerFunction)
```

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

typeof:
```js
let typeOfTest;
typeOfTest = "";  // string
typeOfTest = true; // boolean
typeOfTest = false; // boolean
typeOfTest = undefined; // undefined
```

escape sequences in strings:
```js
const myStr = "FirstLine\n\t\\SecondLine\nThirdLine";
```

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

concatenate arrays:
```js
var arr3 = [0, 1, 2];
var arr4 = [3, 4, 5];
arr3 = [...arr3, "spread", ...arr4, "operator"];
// same as arr1.concat(arr2);
```

another copy / concatenate example:
```js
const arr5 = ['JAN', 'FEB', 'MAR', 'APR', 'MAY'];
let arr6;
arr6 = [...arr5, 'JUN', 'JUL']; 
```

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

with a high order array method:
```js
const sum = (...args) => {
  return args.reduce((a, b) => a + b, 0);
}
console.log(sum(2, 3, 4)); // 9
```

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

High order array method 3:
```js
function multiply2(multiplier, ...nums) {
  return nums.map((num) => {
    return multiplier * num
  })
}
console.log("Multiply2: " + multiply2(15, 1, 3, 5, 1.5));
```

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