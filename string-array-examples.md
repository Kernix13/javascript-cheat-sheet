# String and Array examples


## Table of contents

1. Arrays
1. Strings
   1. Spread operator for arrays and strings
   1. Rest parameter and rest syntax

## Arrays

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

Examples for high order array methods:

`arr.join()`, commonly used with str.split():
```js
// Here is an example using toLowerCase() and split() for a URL page slug
const blogTitle = "Common Array Methods You Should Know"
let slugTitle = blogTitle.toLowerCase().split(' ').join('-')
console.log(slugTitle) // "common-array-methods-you-should-know"
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

`arr.some() examples:
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

`arr.map()`:
```js

```

<br />

`arr.filter()`:
```js

```

<br />

`arr.forEach()`:
```js

```

<br />

`arr.reduce()`:
```js

```

## Strings

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
