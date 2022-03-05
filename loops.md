# Loops and iterations

Notes for not so common loop code snippets.

## Continue and reak out of a loop

```js
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
```

## While loop

```js
let i = 0;
while(i < 10) {

}
```

## Loops for arrays

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

## `for `in` and `for of` loops

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
```

`for of`, syntax:
```js
for (variable of iterable) {
  statement
}
```

