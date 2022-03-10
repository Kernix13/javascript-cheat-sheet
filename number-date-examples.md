# Math and date methods

- toExponential(n)
- toFixed(n) 
- toPrecision(n)
- isFinite()
- Number.isInteger()
- Number.parseFloat()
- Math.abs(x) 
- Math.ceil(x)
- Math.floor(x)
- Math.random(x)
- Math.round(x)
- Math.sign(x)
- Math.sqrt(x)
- Math.trunc(x)
- Math.max(n1, n2, ...) 
- Math.min(n1, n2, ...))
- Math.pow(x, y)
- Math.floor(Math.random())

- new Date() 
- getDate()  
- getDay()   
- getFullYear()
- getHours()
- getMilliseconds()
- getMinutes() 
- getMonth()
- getSeconds() 
- getTime()  
- getUTCDate() 

- setDate() 
- setFullYear()
- setHours() 
- setMilliseconds()
- setMinutes()
- setMonth()
- setSeconds()
- setTime()
- setUTCDate()


typeof:
```js
let typeOfTest;
typeOfTest = 0; 
console.log(typeof typeOfTest) // number
typeOfTest = -0; // number
typeOfTest = NaN; // number
typeOfTest = "word" / 0; // number
typeOfTest = 2.37 / 1.4562; // number
typeOfTest = new Date(); // object
```

## Number examples

....


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

Why use `toString()`?

current date is Sunday March 6th 2022:
```js
const date = new Date();
console.log("date: " + date);
// returns Sun Mar 06 2022 12:28:31 GMT-0500 (Eastern Standard Time)

// Day of the month from 1 -31
console.log("Date: " + date.getDate()); // 6

// Day of the week from 0 (Sunday) to 6 (Saturday)
console.log("Day of the week: " + date.getDay()); // 0

// Hours from 0 - 23
console.log("Hours: " + date.getHours()); // 12

// Month from 0 - 11
console.log("Month: " + date.getMonth()); // 2

// Number of ms since Jan 1st 1970, used to compare dates
console.log("Time: " + date.getTime()); // 1646587711307

console.log("Full year: " + date.getFullYear()); // 2022
console.log("Minutes: " + date.getMinutes()); // 28
console.log("Seconds: " + date.getSeconds()); // 31
```

Example 2: 
```js
// Date for the current date and time
let d1 = new Date();
console.log("Date toString: " + d1.toString()); 
// Sun Mar 06 2022 12:28:31 GMT-0500 (Eastern Standard Time)
console.log("Date as object: " + d1);           
// Sun Mar 06 2022 12:28:31 GMT-0500 (Eastern Standard Time)

console.log("Date toDateString: " + d1.toDateString()); // Sun Mar 06 2022
console.log("Date toTimeString: " + d1.toTimeString()); // 12:28:31 GMT-0500 (Eastern Standard Time)
console.log(typeof d1.toString()); // string
console.log(typeof d1); // object
```

Pass in year month and day:
```js
// syntax: (year, month, day, hour, minutes, seconds, milliseconds)
let d2 = new Date(2022, 2, 6, 12, 19, 23, 23);
console.log(d2); // Sun Mar 06 2022 12:19:23 GMT-0500 (Eastern Standard Time)
```

Dates with a date time string:
```js
// syntax 1:
let d3 = new Date("March 6, 2022 12:24:00"); // 06 or 6 is fine
console.log(d3);
// Sun Mar 06 2022 12:24:00 GMT-0500 (Eastern Standard Time)

// syntax 2:
let d4 = new Date("2022-03-06");
console.log(d4); // Sat Mar 05 2022 19:00:00 GMT-0500 (Eastern Standard Time)

// syntax 3:
let d5 = new Date("03-06-2022");
console.log(d5); // Sun Mar 06 2022 00:00:00 GMT-0500 (Eastern Standard Time)

// syntax 3:
let d6 = new Date("Mar 6 2022"); // or March
console.log(d6); // Sun Mar 06 2022 00:00:00 GMT-0500 (Eastern Standard Time)
```

Figure out elapsed time:
```js
let start = new Date();
elapsedTime();
let end = new Date();
let elapsed = end.getTime() - start.getTime();
console.log(elapsed); 
// 3ms for 1000000, 13 for 10000000, 110 for 100000000, ...

function elapsedTime() {
  for (let i = 0; i < 100000000; i++) {
    // nothing inside, shows ms to run the loop??? add more zeros
  }
}
```