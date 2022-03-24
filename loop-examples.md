# Loops and iterations

Notes for not so common loop code snippets.

<div id="back-to-top"></div>

## Table of contents

1. [while loop](#while-loop)
1. [do while loop](#do-while-loop)
1. [for loop](#for-loop)
1. [for in and for of loops](#for-in-and-for-of-loops)
1. [Array methods](#array-methods)
1. [Continue and break](#continue-and-break)
1. [Miscellaneous](miscellaneous)


## while loop

The `while` statement creates a loop that executes a specified statement as long as the test `condition` evaluates to true. The condition is evaluated before executing the statement.

- `condition`: An expression evaluated before each pass through the loop. If this condition evaluates to `true`, statement is executed. When condition evaluates to `false`, execution continues with the statement after the while loop

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

## do while loop

The do...while statement creates a loop that executes a specified statement until the test condition evaluates to false. The condition is evaluated after executing the statement, resulting in the specified statement executing at least once. 

- `condition`: An expression evaluated after each pass through the loop. If condition evaluates to `true`, the statement is re-executed. When condition evaluates to `false`, control passes to the statement following the `do...while`

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

A `for` loop repeats until a specified condition evaluates to `false`.

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

> The difference between a `for...of` loop and a `for...in` loop: while `for...in` iterates over property **<ins>names/keys</ins>**, `for...of` iterates over property **<ins>values</ins>**.

### for in

The `for...in` statement iterates a specified variable over all the enumerable properties of an object. For each distinct property, JavaScript executes the specified statements.

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

<br />

### for of

The `for...of` statement creates a loop Iterating over iterable objects (including `Array`, `Map`, `Set`, `arguments` object and so on), invoking a custom iteration hook with statements to be executed for the value of each distinct property (?)

Syntax:
```js
for (variable of iterable) {
  statement
}
```

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

// my example: Sum All Odd Fibonacci Numbers
function sumFibs(num) {
  if (num <= 0) return 0;

  const startNums = [1, 1];
  let nextNum = 0;
  // can you use a for loop here?
  for (let i of startNums) {
    let nextNum = startNums[i - 1] + startNums[i];
    if (nextNum <= num) {
      startNums.unshift(nextNum);
    }
  }
  return startNums.filter(x => x % 2 != 0).reduce((a, b) => a + b);
}
sumFibs(4);
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Array methods

Use high order array methods like `map` and `forEach` instead of a `for` loop when working with arrays:

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

Use the `break` statement to terminate a loop, `switch`, or in conjunction with a labeled statement. See [MDN break statement](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Loops_and_iteration#break_statement).

The `continue` statement can be used to restart a `while`, `do-while`, `for`, or `label` statement. See [MDN continue statement](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Loops_and_iteration#continue_statement).

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