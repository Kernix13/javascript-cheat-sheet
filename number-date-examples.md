# Number and date methods

Simple number, Math, and Date examples.

<div id="back-to-top"></div>

## Table of contents

1. [Number examples](#number-examples)
   1. [Number methods](#number-methods)
   1. [Math methods](#math-methods)
1. [Spread operator](#spread-operator)
1. [Rest parameter](#rest-parameter)
1. [Date examples](#date-examples)
   1. [Date get methods](#date-get-methods)
	 1. [Date set methods](#date-set-methods)
1. [Miscellaneous](#miscellaneous)
1. [Syntax tables](#syntax-tables)

## Number examples

Number and Math methods.

### Number methods

Here are links to MDN docs for the methods below:

|       |       |       | 
| :---: | :---: | :---: | 
| [MDN toExponential](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toExponential) | [MDN toFixed](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toFixed) | [MDN toPrecision](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toPrecision) | 
| [MDN isFinite](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/isFinite) | [MDN isInteger](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/isInteger)  | [MDN parseFloat](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/parseFloat) | 

toExponential(): Don't see the practical application of this one
```js
// syntax
toExponential()
toExponential(fractionDigits)

// MDN examples
function expo(x, f) {
  return Number.parseFloat(x).toExponential(f);
}
console.log(expo(123456, 2));
console.log(expo('123456'));
console.log(expo('word'));
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

toFixed(n)
```js
// syntax
toFixed()
toFixed(digits)

// example
function financial(x) {
  return Number.parseFloat(x).toFixed(2);
}
console.log(financial(123.456));
console.log(financial(0.004));
console.log(financial('1.23e+5'));

let numObj = 12345.6789

numObj.toFixed()       // '12346': note rounding, no fractional part
numObj.toFixed(1)      // '12345.7': note rounding
numObj.toFixed(6)      // '12345.678900': note added zeros
(1.23e+20).toFixed(2)  // '123000000000000000000.00'
(1.23e-10).toFixed(2)  // '0.00'
2.34.toFixed(1)        // '2.3'
2.35.toFixed(1)        // '2.4'. Note it rounds up
2.55.toFixed(1)        // '2.5'. Note it rounds down - see warning above
-2.34.toFixed(1)       //  -2.3
(-2.34).toFixed(1)     // '-2.3'
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

toPrecision(n)
```js
// syntax
toPrecision()
toPrecision(precision)

// examples
function precise(x) {
  return x.toPrecision(4);
}
console.log(precise(123.456)); // "123.5"
console.log(precise(0.004)); // "0.004000"

let numObj = 5.123456

console.log(numObj.toPrecision())    // logs '5.123456'
console.log(numObj.toPrecision(5))   // logs '5.1235'
console.log(numObj.toPrecision(2))   // logs '5.1'
console.log(numObj.toPrecision(1))   // logs '5'

numObj = 0.000123

console.log(numObj.toPrecision())    // logs '0.000123'
console.log(numObj.toPrecision(5))   // logs '0.00012300'
console.log(numObj.toPrecision(2))   // logs '0.00012'
console.log(numObj.toPrecision(1))   // logs '0.0001'
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

isFinite(): Return value = `false` if the argument is (or will be coerced to) positive or negative Infinity or `NaN` or `undefined`; otherwise, `true`.
```js
// syntax
isFinite(testValue)

// examples
function div(x) {
  if (isFinite(1000 / x)) {
    return 'Number is NOT Infinity.';
  }
  return 'Number is Infinity!';
}
console.log(div(0)); // "Number is Infinity!""
console.log(div(1)); // "Number is NOT Infinity."

isFinite(Infinity);  // false
isFinite(NaN);       // false
isFinite(-Infinity); // false
isFinite(0);         // true
isFinite(2e64);      // true
isFinite(910);       // true
isFinite(null);      // true, would've been false with the more robust Number.isFinite(null)
isFinite('0');       // true, would've been false with the more robust Number.isFinite("0")
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

Number.isInteger()
```js
// syntax
Number.isInteger(value)

// Examples:
function fits(x, y) {
  if (Number.isInteger(y / x)) {
    return 'Fits!';
  }
  return 'Does NOT fit!';
}
console.log(fits(5, 10)); // "Fits!"
console.log(fits(5, 11)); // "Does NOT fit!"

Number.isInteger(0);         // true
Number.isInteger(1);         // true
Number.isInteger(-100000);   // true
Number.isInteger(99999999999999999999999); // true

Number.isInteger(0.1);       // false
Number.isInteger(Math.PI);   // false

Number.isInteger(NaN);       // false
Number.isInteger(Infinity);  // false
Number.isInteger(-Infinity); // false
Number.isInteger('10');      // false
Number.isInteger(true);      // false
Number.isInteger(false);     // false
Number.isInteger([1]);       // false

Number.isInteger(5.0);       // true
Number.isInteger(5.000000000000001); // false
Number.isInteger(5.0000000000000001); // true
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

Number.parseFloat()
```js
// synta  x
Number.parseFloat(string)

// examples:
// confusing
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>


### Math methods

Here are links to MDN docs for the most common Math methods:

|       |       |       | 
| :---: | :---: | :---: | 
| [MDN Math.abs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/abs) | [MDN Math.ceil](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/ceil) | [MDN Math.floor](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/floor) |
| [MDN Math.random](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/random) | [MDN Math.round](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/round) | [MDN Math.sign](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/sign) |
| [MDN Math.sqrt](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/sqrt) | [MDN Math.trunc](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/trunc) | [MDN Math.max](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/max) |
| [MDN Math.min](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/min) | [MDN Math.pow](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/pow) |  | 

Math.abs(x)
```js
// syntax
Math.abs(x)

// examples
function difference(a, b) {
  return Math.abs(a - b);
}
console.log(difference(3, 5)); // 2
console.log(difference(5, 3)); // 2
console.log(difference(1.23456, 7.89012)); // 6.6555599999999995

Math.abs('-1');     // 1
Math.abs(-2);       // 2
Math.abs(null);     // 0
Math.abs('');       // 0
Math.abs([]);       // 0
Math.abs([2]);      // 2
Math.abs([1,2]);    // NaN
Math.abs({});       // NaN
Math.abs('string'); // NaN
Math.abs();         // NaN
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

Math.ceil(x)
```js
// syntax
Math.ceil(x)

// examples
console.log(Math.ceil(.95)); // 1
console.log(Math.ceil(7.004)); // 8
console.log(Math.ceil(-7.004)); // -7
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

Math.floor(x)
```js
// syntax
Math.floor(x)

// examples
Math.floor( 45.95); //  45
Math.floor( 45.05); //  45
Math.floor(  4   ); //   4
Math.floor(-45.05); // -46
Math.floor(-45.95); // -46
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

Math.random(x)
```js
// syntax
Math.random()

// examples
function getRandomInt(max) {
  return Math.floor(Math.random() * max);
}
console.log(getRandomInt(3)); // 1
console.log(getRandomInt(1)); // 0
console.log(Math.random()); // 0.random numbers
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

Math.round(x)
```js
// syntax
Math.round(x)

// examples
console.log(Math.round(0.9)); // 1 
console.log(Math.round(5.95), Math.round(5.5), Math.round(5.05)); // 6 6 5
console.log(Math.round(-5.05), Math.round(-5.5), Math.round(-5.95)); // -5 -5 -6

Math.round( 20.49); //  20
Math.round( 20.5 ); //  21
Math.round( 42   ); //  42
Math.round(-20.5 ); // -20
Math.round(-20.51); // -21
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

Math.sign(x)
```js
// syntax
Math.sign(x)

// examples
console.log(Math.sign(3)); // 1
console.log(Math.sign(-3)); // -1
console.log(Math.sign(0)); // 0
console.log(Math.sign('-3')); // -1

Math.sign(3);     //  1
Math.sign(-3);    // -1
Math.sign('-3');  // -1
Math.sign(0);     //  0
Math.sign(-0);    // -0
Math.sign(NaN);   // NaN
Math.sign('foo'); // NaN
Math.sign();      // NaN
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

Math.sqrt(x)
```js
// syntax
Math.sqrt(x)

// examples
function calcHypotenuse(a, b) {
  return (Math.sqrt((a * a) + (b * b)));
}
console.log(calcHypotenuse(3, 4)); // 5
console.log(calcHypotenuse(5, 12)); // 13
console.log(calcHypotenuse(0, 0)); // 0

Math.sqrt(9); // 3
Math.sqrt(2); // 1.414213562373095
Math.sqrt(1);  // 1
Math.sqrt(0);  // 0
Math.sqrt(-1); // NaN
Math.sqrt(-0); // -0
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

Math.trunc(x)
```js
// syntax
Math.trunc(x)

// examples
console.log(Math.trunc(13.37)); // 13
console.log(Math.trunc(42.84)); // 42
console.log(Math.trunc(0.123)); // 0
console.log(Math.trunc(-0.123)); // 0

Math.trunc(13.37);    // 13
Math.trunc(42.84);    // 42
Math.trunc(0.123);    //  0
Math.trunc(-0.123);   // -0
Math.trunc('-1.123'); // -1
Math.trunc(NaN);      // NaN
Math.trunc('foo');    // NaN
Math.trunc();         // NaN
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

Math.max(n1, n2, ...)
```js
// syntax
Math.max()
Math.max(value0)
Math.max(value0, value1)
Math.max(value0, value1, /* ... ,*/ valueN)

// examples
console.log(Math.max(1, 3, 2)); // 3
console.log(Math.max(-1, -3, -2)); // -1
const array1 = [1, 3, 2];
console.log(Math.max(...array1)); // 3

Math.max(10, 20);   //  20
Math.max(-10, -20); // -10
Math.max(-10, 20);  //  20

// with reduce
var arr = [1,2,3];
var max = arr.reduce(function(a, b) {
    return Math.max(a, b);
}, -Infinity);
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

Math.min(n1, n2, ...))
```js
// syntax
Math.min()
Math.min(value0)
Math.min(value0, value1)
Math.min(value0, value1, ... , valueN)

// examples
console.log(Math.min(2, 3, 1)); // 1
console.log(Math.min(-2, -3, -1)); // -3
const array1 = [2, 3, 1];
console.log(Math.min(...array1));  1

var x = 10, y = -20;
var z = Math.min(x, y);
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

Math.pow(x, y)
```js
// syntax
console.log(Math.pow(7, 3)); // 343
console.log(Math.pow(4, 0.5)); // 2
console.log(Math.pow(7, -2)); // 0.02040816326530612
console.log(Math.pow(-7, 0.5)); // NaN

// simple
Math.pow(7, 2);    // 49
Math.pow(7, 3);    // 343
Math.pow(2, 10);   // 1024
// fractional exponents
Math.pow(4, 0.5);  // 2 (square root of 4)
Math.pow(8, 1/3);  // 2 (cube root of 8)
Math.pow(2, 0.5);  // 1.4142135623730951 (square root of 2)
Math.pow(2, 1/3);  // 1.2599210498948732 (cube root of 2)
// signed exponents
Math.pow(7, -2);   // 0.02040816326530612 (1/49)
Math.pow(8, -1/3); // 0.5
// signed bases
Math.pow(-7, 2);   // 49 (squares are positive)
Math.pow(-7, 3);   // -343 (cubes can be negative)
Math.pow(-7, 0.5); // NaN (negative numbers don't have a real square root)
Math.pow(-7, 1/3); // NaN
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

Math.floor(Math.random())

USe this as part of a way to ...


<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Spread operator

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

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Rest parameter

REST SYNTAX: opposite, individual elements into an array:
```js
const secondArray = [7, 8, 9, 10, 11, 12];
const [firstNum, secondNum, ...rest] = secondArray;
console.log(firstNum); // 7
console.log(rest); // [9, 10, 11, 12]
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Date examples

### Date get methods

Here is a link for the [MDN Date docs](). Here are links to MDN docs for the most common Date `get` methods:

|       |       |       | 
| :---: | :---: | :---: | 
| [MDN getDate]() | [MDN getDay]() | [MDN getFullYear]() |
| [MDN getHours]() | [MDN getMilliseconds]() | [MDN getMinutes]() |
| [MDN getMonth]() | [MDN getSeconds]() | [MDN getTime]() |

new Date()
```js
// syntax

```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

getDate()
```js
// syntax

```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

getDay()
```js
// syntax

```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

getFullYear()
```js
// syntax

```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

getHours()
```js
// syntax

```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

getMilliseconds()
```js
// syntax

```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

getMinutes()
```js
// syntax

```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

getMonth()
```js
// syntax

```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

getSeconds()
```js
// syntax

```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

getTime()
```js
// syntax

```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Date set methods

Here are links to MDN docs for the most common Date `set` methods: 

|       |       |       | 
| :---: | :---: | :---: | 
| [MDN setDate]() | [MDN setFullYear]() | [MDN setHours]() | 
| [MDN setMilliseconds]() | [MDN setMinutes]() | [MDN setMonth]() | 
| [MDN setSeconds]() | [MDN setTime]() | [MDN setUTCDate]() | 

setDate()
```js
// syntax

```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

setFullYear()
```js
// syntax

```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

setHours()
```js
// syntax

```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

setMilliseconds()
```js
// syntax

```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

setMinutes()
```js
// syntax

```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

setMonth()
```js
// syntax

```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

setSeconds()
```js
// syntax

```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

setTime()
```js
// syntax

```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

setUTCDate()
```js
// syntax

```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

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

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Miscellaneous

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

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Syntax tables

```js
toExponential()
toExponential(fractionDigits)

toFixed()
toFixed(digits)

toPrecision()
toPrecision(precision)

isFinite(testValue)

Number.isInteger(value)

Number.parseFloat(string)

Math.abs(x)

Math.ceil(x)

Math.floor(x)

Math.random()

Math.round(x)

Math.sign(x)

Math.sqrt(x)

Math.trunc(x)

Math.max()
Math.max(value0)
Math.max(value0, value1)
Math.max(value0, value1, /* ... ,*/ valueN)

Math.min()
Math.min(value0)
Math.min(value0, value1)
Math.min(value0, value1, ... , valueN)


```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>