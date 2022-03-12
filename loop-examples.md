# Loops and iterations

Notes for not so common loop code snippets.

<div id="back-to-top"></div>

## Table of contents

1. [While loop](#while-loop)
1. [Do while loop](#do-while-loop)
1. [for loop](#for-loop)
1. [for in and for of loops](#for-in-and-for-of-loops)
1. [Array methods](#array-methods)
1. [Continue and break](#continue-and-break)
1. [Miscellaneous](miscellaneous)


## While loop

Syntax:
```js
while (condition)
  statement

// example
let i = 0;
do {
  i += 1;
  console.log(i);
} while (i < 5);
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Do while loop

Syntax:
```js
do
  statement
while (condition);

// example
let n = 0;
let x = 0;
while (n < 3) {
  n++;
  x += n;
}
```


<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## for loop

Syntax:
```js
for ([initialExpression]; [conditionExpression]; [incrementExpression])
  statement
// or 
for  (initialization; condition; final-expression)

// example
let arr = [1, 2, 3, 4, 5, 6, 7];
function someFx() {
  for (let i = 0; i < arr.length; i++) {
    // code here
  }
}
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## for in and for of loops

### for in

`for in`, syntax:
```js
for (variable in object) {
  statement
}
```

Example:
```js
const user = {
  first: "Jim",
  last: "Kernix",
  age: 56
}

for (let x in user) {
  console.log(x); // returns the keys
  console.log(user[x]); // returns the values
}

// example 2
function dump_props(obj, obj_name) {
  let result = '';
  for (let i in obj) {
    result += obj_name + '.' + i + ' = ' + obj[i] + '<br>';
  }
  result += '<hr>';
  return result;
}
// For an object car with properties make and model, result would be:
car.make = Ford
car.model = Mustang
```

### for of

Syntax:
```js
for (variable of iterable) {
  statement
}
```

The difference between a `for...of` loop and a `for...in` loop. While `for...in` iterates over property names, `for...of` iterates over property values.

Example:
```js
const arr = [3, 5, 7];
arr.foo = 'hello';

for (let i in arr) {
   console.log(i); // logs "0", "1", "2", "foo"
}

for (let i of arr) {
   console.log(i); // logs 3, 5, 7
}
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Array methods

Use these over a `for` loop when working with arrays:

`forEach()` 

syntax:
```js
cars.forEach(function(a, b, c) {})
```

Example:
```js
const cars = ["Ford", "Honda", "Toyota", "Chevy"];

cars.forEach(function(car) {
  console.log(car);
});

```

<br />

`map()`: array of objects

```js
const users = [
  {id: 1, name: "Jim"},
  {id: 2, name: "Buddy"},
  {id: 3, name: "Luna"}
];

const ids = users.map(function(user) {
  return user.id;
});
console.log(ids); // (3) [1, 2, 3]
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Continue and break

Break syntax:
```js
break;
break [label];

// example
for (let i = 0; i < a.length; i++) {
  if (a[i] === theValue) {
    break;
  }
}
```

<br />

Continue syntax:
```js
continue [label];

// example 1
for (let i = 0; i > 10, i++) {
  if (i === 2) {
    console.log("The number 2 is great");
    continue;
  }

  if (i === 5) {
    break;
  }

  console.log("Number " + i)
}

// example 2
let i = 0;
let n = 0;
while (i < 5) {
  i++;
  if (i === 3) {
    continue;
  }
  n += i;
  console.log(n);
}
//1,3,7,12

let i = 0;
let n = 0;
while (i < 5) {
  i++;
  if (i === 3) {
     // continue;
  }
  n += i;
  console.log(n);
}
// 1,3,6,10,15

// example 3
let i = 0;
let j = 10;
checkiandj:
  while (i < 4) {
    console.log(i);
    i += 1;
    checkj:
      while (j > 4) {
        console.log(j);
        j -= 1;
        if ((j % 2) === 0) {
          continue checkj;
        }
        console.log(j + ' is odd.');
      }
      console.log('i = ' + i);
      console.log('j = ' + j);
  }
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Miscellaneous

- accumulators
- recursion: examples in [function-examples.md](https://github.com/Kernix13/javascript-cheat-sheet/blob/master/function-examples.md)

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>