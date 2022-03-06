# Math and date methods


typeof:
```js
let typeOfTest;
typeOfTest = 0; // number
typeOfTest = -0; // number
typeOfTest = NaN; // number
typeOfTest = "word" / 0; // number
typeOfTest = 2.37 / 1.4562; // number
typeOfTest = new Date(); // object
```



## Number examples

### Spread operator

ignores nums afer the 3rd
```js
function addThreeNumbers(x, y, z) { 
	return (x + y + z);
}
var args = [1, 10, 22, 3];
console.log(addThreeNumbers(...args));
```

copy array then push onto it:
```js
var arr = [1, 2, 3];
var arr2 = [...arr]; // like arr.slice()
arr2.push(4); 
```

1st console.log shows an array, 2nd are the values
```js
const grades = [99, 100, 65, 72];
const grades2 = [...grades, 97, 80, 52];
console.log(grades2)
console.log(...grades2)
```

### Rest parameter

REST SYNTAX: opposite, individual elements into an array:
```js
const secondArray = [7, 8, 9, 10, 11, 12];
const [firstNum, secondNum, ...rest] = secondArray;
console.log(firstNum); // 7
console.log(rest); // [9, 10, 11, 12]
```

## Date examples
