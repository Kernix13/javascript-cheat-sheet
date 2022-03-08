# String and Array examples


## Table of contents

1. Arrays
   1. Common array methods
   1. High order array methods
1. Strings
   1. Spread operator for arrays and strings
   1. Rest parameter and rest syntax

## Arrays

### Common array methods

Basic syntax `push()`, `unshift()`, `pop()`, `shift()`:
```js
// push(val)
let arr = ['a', 'b', 'c', 'd'];
let addedItem = arr.push('e');
console.log(addedItem); // 5
console.log(arr); // ['a', 'b', 'c', 'd', 'e']

// unshift(val)
let arr = [1, 2, 3, 4];
let addedItem = arr.unshift(0);
console.log(addedItem); // 5
console.log(arr); // [0, 1, 2, 3, 4]

// pop()
let arr = ['a', 'b', 'c', 'd'];
let removedItem = arr.pop();
console.log(removedItem); // "d"
console.log(arr); // ["a","b","c"]

// shift()
let arr = [1, 2, 3, 4];
let removedItem = arr.shift();
console.log(removedItem); // 1
console.log(arr); // [2,3,4]
```
<br />

### High order array methods

`arr.join()`, commonly used with str.split():
```js
// Here is an example using toLowerCase() and split() for a URL page slug
const blogTitle = "Common Array Methods You Should Know"
const pageSlug = blogTitle.toLowerCase().split(' ').join('-')
console.log(pageSlug); // "common-array-methods-you-should-know"
```

<br />

`arr.reverse()`:
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
```

<br />

`arr.sort()`:
```js
// mutaes original array:
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

// Sorting an array of strings using spread operating to NOT mutate original:
const arr = ["John", "Jim", "Mary", "Adam", "Zac", "Susan"];
newArr = [...arr].sort();
console.log(newArr); // ["Adam","Jim","John","Mary","Susan","Zac"]
console.log("original: " + arr); // "original: John,Jim,Mary,Adam,Zac,Susan"
```

<br />

Basic `arr.every()`: returns a boolean if EVERY element in an array passes a test, syntax:
```js
// Arrow function
every((element) => {...} )

// Inline callback function
every(function(element) {...}) 

// Callback function
every(callBackFx)
```

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


// Callback function example (Why do it this way?):
let nums = [-2, 2.5, 1, 3, 5];
function findPositive(num) {
  return num > 0;
}
let checkNums = nums.every(findPositive);
console.log(checkNums) // false
```

<br />

`arr.some()`, returns a boolean if at least one element passes a test, syntax::
```js
// Arrow function
some((element) => {...} )

// Inline callback function
some(function(element) {...}) 

// Callback function
some(callBackFx)
```

`arr.some()` examples:
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

// Callback function
const arr = [2, 5, 8, 1, 4];
const arr2 = [12, 5, 8, 1, 4];
function isBiggerThan10(item) {
  return item > 10;
}
console.log(arr.some(isBiggerThan10));  // false
console.log(arr2.some(isBiggerThan10)); // true

// Anonymous/inline function :
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
```

**NOTE**: I've seen examples where `some()` is used to check for the existence of a value in an array - why not just use `includes()`? You can not use `hasOwnProperty` for the last example because the "object" in an array, not an object.

<br />

`arr.map()` syntax:
```js
// Arrow function
map((element) => { /* ... */ })
map((element, index) => { /* ... */ })

// Callback function
map(callbackFn)

// Inline callback function
map(function(element) { /* ... */ })
map(function(element, index) { /* ... */ })
```

`arr.map()` MDN examples:
```js
const arr = [1, 2, 3]
const mapArr = arr.map(n => n * 3)
console.log(mapArr)

const array1 = [1, 4, 9, 16];
const map1 = array1.map(x => x * 2);
console.log(map1);

const numbers = [1, 4, 9];
const roots = numbers.map((num) => Math.sqrt(num)); // roots is now [1, 2, 3]

// reformat objects in an array
const kvArray = [
  { key: 1, value: 10 },
  { key: 2, value: 20 },
  { key: 3, value: 30 }
  ];
const reformattedArray = kvArray.map(({ key, value}) => ({ [key]: value }));

// Using map generically
const map = Array.prototype.map;
const charCodes = map.call('Hello World', (x) => x.charCodeAt(0));
// charCodes now equals [72, 101, 108, 108, 111, 32, 87, 111, 114, 108, 100]

// Using map generically querySelectorAll
const elems = document.querySelectorAll('select option:checked');
const values = Array.prototype.map.call(elems, ({ value }) => value);
```

freeCodeCamp examples:
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

`arr.filter()` syntax:
```js
// Arrow function
filter((element) => { /* ... */ } )
filter((element, index) => { /* ... */ } )

// Callback function
filter(callbackFn)

// Inline callback function
filter(function(element) { /* ... */ })
filter(function(element, index) { /* ... */ })
```

MDN Examples:
```js
const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];
const result = words.filter(word => word.length > 6);
console.log(result); // ["exuberant","destruction","present"]

// Filtering out all small values
function isBigEnough(value) {
  return value >= 10
}
let filtered = [12, 5, 8, 130, 44].filter(isBigEnough)
console.log(filtered); // [12,130,44]

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

// Searching in array
let fruits = ['apple', 'banana', 'grapes', 'mango', 'orange']

function filterItems(arr, query) {
  return arr.filter(function(el) {
    return el.toLowerCase().indexOf(query.toLowerCase()) !== -1
  })
}

console.log(filterItems(fruits, 'ap'))  // ['apple', 'grapes']
console.log(filterItems(fruits, 'an'))  // ['banana', 'mango', 'orange']
```

`arr.filter()` examples:
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

`arr.forEach()` syntax:
```js

```

MDN Examples
```js

```

`arr.forEach()` examples:
```js
// Example from my guitar chord namer app
let position = chromaticSharps.indexOf(uniqueNotes[i]);
let noteAsRoot = chromaticSharps.slice(position, position + 12);
uniqueNotes.forEach(note => noteSteps.push(noteAsRoot.indexOf(note)));


```

<br />

`arr.reduce()` syntax:
```js

```

MDN Examples
```js

```

`arr.reduce()` examples:
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
- - - 

## Strings

`str.toLowerCase()`, `str.toUpperCase()`, and `str.trim()` are so basic that I am not providing examples.

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








