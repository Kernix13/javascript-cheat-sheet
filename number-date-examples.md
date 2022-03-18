# Number and date methods

Simple number, Math, and Date examples.

<div id="back-to-top"></div>

## Table of contents

1. [Number methods](#number-methods)
1. [Math methods](#math-methods)
1. [Spread operator](#spread-operator)
1. [Rest parameter](#rest-parameter)
1. [Date examples](#date-examples)
   1. [Date get methods](#date-get-methods)
	 1. [Date set methods](#date-set-methods)
1. [Miscellaneous](#miscellaneous)
1. [Syntax tables](#syntax-tables)
   1. [Numbers](#numbers)
   1. [Get dates](#get-dates)
   1. [Set dates](#set-dates)

## Number methods

Here are links to MDN docs for the methods below:

|       |       |       | 
| :---: | :---: | :---: | 
| [MDN toExponential](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toExponential) | [MDN toFixed](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toFixed) | [MDN toPrecision](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toPrecision) | 
| [MDN isFinite](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/isFinite) | [MDN isInteger](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/isInteger)  | [MDN parseFloat](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/parseFloat) | 

<br />

The `toExponential()` method returns a string representing the Number object in exponential notation. 

toExponential(): Don't see the practical application of this one
```js
// syntax
toExponential()
toExponential(fractionDigits)
// fractionDigits: Optional. An integer specifying the number of digits after the decimal point

// MDN examples
function expo(x, f) {
  return Number.parseFloat(x).toExponential(f);
}
console.log(expo(123456, 2)); // "1.23e+5"
console.log(expo('123456')); // "1.23456e+5"
console.log(expo('word')); // NaN
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br />

The `toFixed()` method formats a number using fixed-point notation. 

toFixed(n)
```js
// syntax
toFixed()
toFixed(digits)
// digits: The number of digits (0-20) to appear after the decimal point

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

<br />

The `toPrecision() `method returns a string representing the Number object to the specified precision. 

toPrecision(n)
```js
// syntax
toPrecision()
toPrecision(precision)
// precision: An integer specifying the number of significant digits

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

<br />

The global `isFinite()` function determines whether the passed value is a finite number. If needed, the parameter is first converted to a number.

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

<br />

The `Number.isInteger()` method determines whether the passed value is an integer.

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

<br />

The `Number.parseFloat()` method parses an argument and returns a floating point number. If a number cannot be parsed from the argument, it returns `NaN`.

Number.parseFloat()
```js
// synta  x
Number.parseFloat(string)

// examples:
// confusing
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>


## Math methods

Here are links to MDN docs for the most common Math methods:

|       |       |       | 
| :---: | :---: | :---: | 
| [MDN Math.abs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/abs) | [MDN Math.ceil](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/ceil) | [MDN Math.floor](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/floor) |
| [MDN Math.random](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/random) | [MDN Math.round](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/round) | [MDN Math.sign](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/sign) |
| [MDN Math.sqrt](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/sqrt) | [MDN Math.trunc](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/trunc) | [MDN Math.max](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/max) |
| [MDN Math.min](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/min) | [MDN Math.pow](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/pow) |  | 

<br />

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

<br />

Math.ceil(x): always rounds a number up to the next largest integer.
```js
// syntax
Math.ceil(x)

// examples
console.log(Math.ceil(.95)); // 1
console.log(Math.ceil(7.004)); // 8
console.log(Math.ceil(-7.004)); // -7
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br />

Math.floor(x): returns the largest integer less than or equal to a given number
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

<br />

Math.random(x): returns a floating-point, pseudo-random number in the range 0 to less than 1 (inclusive of 0, but not 1) with approximately uniform distribution over that range — which you can then scale to your desired range

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

<br />

Math.round(x): returns the value of a number rounded to the nearest integer
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

<br />

Math.sign(x): returns either a positive or negative +/- 1, indicating the sign of a number passed into the argument. If the number passed into `Math.sign()` is 0, it will return a +/- 0. Note that if the number is positive, an explicit (+) will not be returned.

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

<br />

Math.sqrt(x): returns the square root of a number
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

<br />

Math.trunc(x): returns the integer part of a number by removing any fractional digits
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

<br />

Math.max(): returns the largest of the zero or more numbers given as input parameters, or `NaN` if any parameter isn't a number and can't be converted into one. 

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
let arr = [1,2,3];
let max = arr.reduce(function(a, b) {
    return Math.max(a, b);
}, -Infinity);
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br />

Math.min(): returns the lowest-valued number passed into it, or `NaN` if any parameter isn't a number and can't be converted into one.

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

let x = 10, y = -20;
let z = Math.min(x, y);
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br />

Math.pow(x, y): static method, given two arguments, _base_ and _exponent_, returns `base` <sup>`exp`</sup>.

```js
// syntax
Math.pow(base, exponent)

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

**NOTE**: to find the `nth` root of a number use `Math.pow(num, 1/n)`. 

**NOTE 2**: The value of Phi &Phi; can be calculated with `(sqrt. of 5 + 1) / 2` or 

```js
const phi = ((Math.pow(5, 0.5) + 1) / 2)
console.log(phi) // 1.618033988749895
```

<br />

Math.floor(Math.random()): 105 generate random  whole numbers w\in a range:
```js
function randomRange(myMin, myMax) {
  return Math.floor(Math.random() * (myMax - myMin + 1) + myMin);
}
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Spread operator

ignores nums afer the 3rd
```js
function addThreeNumbers(x, y, z) { 
	return (x + y + z);
}
let args = [1, 10, 22, 3];
console.log(addThreeNumbers(...args));
```

copy array then push onto it:
```js
let arr = [1, 2, 3];
let arr2 = [...arr]; // like arr.slice()
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

Here is a link for the [MDN Date docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date). Here are links to MDN docs for the most common Date `get` methods:

|       |       |       | 
| :---: | :---: | :---: | 
| [MDN getDate](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/getDate) | [MDN getDay](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/getDay) | [MDN getFullYear](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/getFullYear) |
| [MDN getHours](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/getHours) | [MDN getMilliseconds](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/getMilliseconds) | [MDN getMinutes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/getMinutes) |
| [MDN getMonth](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/getMonth) | [MDN getSeconds](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/getSeconds) | [MDN getTime](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/getTime) |

<br />

getDate()
```js
// syntax
getDate()

// examples
const birthday = new Date('August 19, 1975 23:15:30');
const date1 = birthday.getDate();
console.log(date1); // 19
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br />

getDay()
```js
// syntax
getDay()

// example
const birthday = new Date('August 19, 1975 23:15:30');
const day1 = birthday.getDay();
console.log(day1); // 2


// example 2:
let dayOfWeek = new Date().getDay() // returns weekday as a number 0-6
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br />

getFullYear()
```js
// syntax
getFullYear()

// example
const moonLanding = new Date('July 20, 69 00:20:18');
console.log(moonLanding.getFullYear()); // 1969

// assign the four-digit value of the current year to the variable
let today = new Date();
let year = today.getFullYear();
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br />

getHours()
```js
// syntax
getHours()

// example
const birthday = new Date('March 13, 08 04:20');
console.log(birthday.getHours()); // 4

let Xmas95 = new Date('December 25, 1995 23:15:30');
let hours = Xmas95.getHours();
console.log(hours); // 23
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br />

getMilliseconds()
```js
// syntax
getMilliseconds()

// example
const moonLanding = new Date('July 20, 69 00:20:18');
moonLanding.setMilliseconds(123);
console.log(moonLanding.getMilliseconds()); // 123

// assign the milliseconds portion of the current time to the variable milliseconds
let today = new Date();
let milliseconds = today.getMilliseconds();
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br />

getMinutes()
```js
// syntax
getMinutes()

// example
const birthday = new Date('March 13, 08 04:20');
console.log(birthday.getMinutes()); // 20

// assign the value 15 to the variable minutes
let Xmas95 = new Date('December 25, 1995 23:15:30');
let minutes = Xmas95.getMinutes();
console.log(minutes); // 15
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br />

getMonth()
```js
// syntax
getMonth()

// example
const moonLanding = new Date('July 20, 69 00:20:18');
console.log(moonLanding.getMonth()); // 6

// assign the value 11 to the variable month
let Xmas95 = new Date('December 25, 1995 23:15:30');
let month = Xmas95.getMonth();
console.log(month); // 11
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br />

getSeconds()
```js
// syntax
getSeconds()

// example
const moonLanding = new Date('July 20, 69 00:20:18');
console.log(moonLanding.getSeconds()); // 18

// assign the value 30 to the variable seconds
let Xmas95 = new Date('December 25, 1995 23:15:30');
let seconds = Xmas95.getSeconds();
console.log(seconds); // 30
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br />

getTime()
```js
// syntax
getTime()

// example
const moonLanding = new Date('July 20, 69 20:17:40 GMT+00:00');
console.log(moonLanding.getTime()); // -14182940000

// Using getTime() for copying dates
// Since month is zero based, birthday will be January 10, 1995
let birthday = new Date(1994, 12, 10);
let copy = new Date();
copy.setTime(birthday.getTime());
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Date set methods

Here are links to MDN docs for the most common Date `set` methods: 

|       |       |       | 
| :---: | :---: | :---: | 
| [MDN setDate](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/setDate) | [MDN setFullYear](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/setFullYear) | [MDN setHours](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/setHours) | 
| [MDN setMilliseconds](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/setMilliseconds) | [MDN setMinutes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/setMinutes) | [MDN setMonth](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/setMonth) | 
| [MDN setSeconds](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/setSeconds) | [MDN setTime](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/setTime) | [MDN setUTCDate](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/setUTCDate) | 

Formatting the date and time values is quite involved. Check out the following links
- freeCodeCamp: [How to Format Dates in JavaScript](https://www.freecodecamp.org/news/how-to-format-dates-in-javascript/)
- Stackoverflow: [How to format a JavaScript date](https://stackoverflow.com/questions/3552461/how-to-format-a-javascript-date)
- CSS Tricks: [Everything You Need to Know About Date in JavaScript](https://css-tricks.com/everything-you-need-to-know-about-date-in-javascript/)

<br />

setDate()
```js
// syntax
setDate(dayValue)

// example
const eventDate = new Date('August 19, 1975 23:15:30');
eventDate.setDate(24);
console.log(eventDate.getDate()); // 24
console.log(eventDate.getDate()); // 1
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br />

setFullYear()
```js
// syntax
setFullYear(yearValue)
setFullYear(yearValue, monthValue)
setFullYear(yearValue, monthValue, dateValue)

// example
const eventDate = new Date('August 19, 1975 23:15:30');
eventDate.setFullYear(1969);
console.log(eventDate.getFullYear()); // 1969
eventDate.setFullYear(0);
console.log(eventDate.getFullYear()); // 0

// example 2
let theBigDay = new Date();
theBigDay.setFullYear(1997); // 858196084256
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br />

setHours()
```js
// syntax
setHours(hoursValue)
setHours(hoursValue, minutesValue)
setHours(hoursValue, minutesValue, secondsValue)
setHours(hoursValue, minutesValue, secondsValue, msValue)

// example
const eventDate = new Date('August 19, 1975 23:15:30');
eventDate.setHours(20);
console.log(eventDate); // Tue Aug 19 1975 20:15:30 GMT-0400 (Eastern Daylight Time)
eventDate.setHours(20, 21, 22);
console.log(eventDate); // Tue Aug 19 1975 20:21:22 GMT-0400 (Eastern Daylight Time)

let theBigDay = new Date();
theBigDay.setHours(7); // 1647089217263
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br />

setMilliseconds()
```js
// syntax
setMilliseconds(millisecondsValue)

// example
const eventDate = new Date('August 19, 1975 23:15:30');
console.log(eventDate.getMilliseconds()); // 0
eventDate.setMilliseconds(456);
console.log(eventDate.getMilliseconds()); // 456

let theBigDay = new Date();
theBigDay.setMilliseconds(100); // 1647114589100
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br />

setMinutes()
```js
// syntax
setMinutes(minutesValue)
setMinutes(minutesValue, secondsValue)
setMinutes(minutesValue, secondsValue, msValue)

// example
const eventDate = new Date('August 19, 1975 23:15:30');
eventDate.setMinutes(45);
console.log(eventDate.getMinutes()); // 45
console.log(eventDate); // Tue Aug 19 1975 23:45:30 GMT-0400 (Eastern Daylight Time)

let theBigDay = new Date();
theBigDay.setMinutes(45); // 1647114346721
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br />

setMonth()
```js
// syntax
setMonth(monthValue)
setMonth(monthValue, dayValue)

// example
const eventDate = new Date('August 19, 1975 23:15:30');
eventDate.setMonth(3);
console.log(eventDate.getMonth()); // 3
console.log(eventDate); // Sat Apr 19 1975 23:15:30 GMT-0400 (Eastern Daylight Time)

let theBigDay = new Date();
theBigDay.setMonth(6); // 1657651927798

// Watch out for end of month transitions
let endOfMonth = new Date(2016, 7, 31);
endOfMonth.setMonth(1);
console.log(endOfMonth); // Wed Mar 02 2016 00:00:00 GMT-0500 (Eastern Standard Time)
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br />

setSeconds()
```js
// syntax
setSeconds(secondsValue)
setSeconds(secondsValue, msValue)

// example
const eventDate = new Date('August 19, 1975 23:15:30');
eventDate.setSeconds(42);
console.log(eventDate.getSeconds()); // 42
console.log(eventDate); // Tue Aug 19 1975 23:15:42 GMT-0400 (Eastern Daylight Time)

let theBigDay = new Date();
theBigDay.setSeconds(30); // 1647114870198
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br />

setTime()
```js
// syntax
setTime(timeValue)

// example
const eventDate1 = new Date('July 1, 1999');
const eventDate2 = new Date();
eventDate2.setTime(eventDate1.getTime());
console.log(eventDate1); // Thu Jul 01 1999 00:00:00 GMT-0400 (Eastern Daylight Time)
console.log(eventDate2); // Thu Jul 01 1999 00:00:00 GMT-0400 (Eastern Daylight Time)

let theBigDay = new Date('July 1, 1999');
let sameAsBigDay = new Date();
sameAsBigDay.setTime(theBigDay.getTime()); // 930801600000
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br />

setUTCDate()
```js
// syntax
setUTCDate(dayValue)

// example
const eventDate = new Date('August 19, 1975 23:15:30 GMT-3:00');
console.log(eventDate.getUTCDate()); // 20
eventDate.setUTCDate(19);
console.log(eventDate.getUTCDate()); // 19

let theBigDay = new Date();
theBigDay.setUTCDate(20); // 1647806212312
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

Why use `toString()`?

current date is Sunday March 6th 2022:
```js
const date = new Date();
console.log("date: " + date);
// date: Sat Mar 12 2022 14:57:16 GMT-0500 (Eastern Standard Time)

// Day of the month from 1 -31
console.log("Date: " + date.getDate()); // 6

// Day of the week from 0 (Sunday) to 6 (Saturday)
console.log("Day of the week: " + date.getDay()); // 0

// Hours from 0 - 23
console.log("Hours: " + date.getHours()); // 12

// Month from 0 - 11
console.log("Month: " + date.getMonth()); // 2

// Number of ms since Jan 1st 1970, used to compare dates
console.log("Time: " + date.getTime()); // Time: 1647115085769

console.log("Full year: " + date.getFullYear()); // 2022
console.log("Minutes: " + date.getMinutes()); // 28
console.log("Seconds: " + date.getSeconds()); // 31
```

<br />

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

<br />

Pass in year month and day:
```js
// syntax: (year, month, day, hour, minutes, seconds, milliseconds)
let d2 = new Date(2022, 2, 6, 12, 19, 23, 23);
console.log(d2); // Sun Mar 06 2022 12:19:23 GMT-0500 (Eastern Standard Time)
```

<br />

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

<br />

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

- `NaN`: 
- remainder operator `%`: 
- compound operators: `+=`, `-=`, `*=`, `/=`
- Radix

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Syntax tables

### Numbers

No parameter
| method        | syntax            | Notes           | 
| :----         | :----             | :----           |
| toExponential | num.toExponential() | Skip this one   |  
| toFixed       | num.toFixed()     | Definitely use  |
| toPrecision   | num.toPrecision() | Maybe           |
| Math.random   | Math.random()     | Definitely use  |
| Math.max      | Math.max()        | Returns `-infinity`? |
| Math.min      | Math.min()        | Returns `-infinity`? |

<br />

One parameter
| method  | syntax                  | Notes         | 
| :----   | :----                   | :----         |
| toExponential | toExponential(decimals) | Skip |
| toFixed       | num.toFixed(digits) | Definitely use  |
| toPrecision   | num.toPrecision(digits) | Maybe  |
| isFinite      | isFinite(val)     | Test? |
| isInteger     | Number.isInteger(val) | Test? | 
| parseFloat    | Number.parseFloat(str) | No clue |
| Math.abs      | Math.abs(x)     | Definitely use  |
| Math.ceil     | Math.ceil(x)    | Definitely use  |
| Math.floor    | Math.floor(x)   | Definitely use  |
| Math.round    | Math.round(x)   | Definitely use  |
| Math.sign     | Math.sign(x)    | Definitely use  |
| Math.sqrt     | Math.sqrt(x)    | Definitely use  |
| Math.trunc    | Math.trunc(x)   | Definitely use  |
| Math.max      | Math.max(value0) | Why use 1 value? | 
| Math.min      | Math.min(value0) | Why use 1 value? | 

<br />

2 or more parameters:
| method  | syntax                  | Notes         | 
| :----   | :----                   | :----         |
| Math.max | Math.max(val1, val2)    | Definitely use |
|         | Math.max(val1, val2, ...valN) | Definitely use |
| Math.min | Math.min(val1, val2)   | 
|         | Math.min(val1, val2, ...valN) | Definitely use |

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Get dates


No parameter (`d` is the var name for the date/time):

| syntax              | Notes           | 
| :----               | :----           |
| let d = new Date()  | Current date and time   | 
| d.getFullYear()     | year as yyyy            |
| d.getMonth()        | the month (0-11)        | 
| d.getDate()         | day of the month (1-31) |
| d.getDay()          | day of the week (0-6)   |
| d.getHours()        | the hour (0-23)         |
| d.getMinutes()      | the minutes (0-59)      |
| d.getSeconds()      | the seconds (0-59)      |
| d.getMilliseconds() | millisecs (0-999, WHY?) |
| d.getTime()         | ms since Jan 1st, 1970 (Why?) |

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Set dates

Single parameter (`d` is the var name for the date/time):
| syntax              | Notes                         | 
| :----               | :----                         |
| d.setDate(dayVal)     | need corresponding get method? |
| d.setFullYear(yearVal) | need corresponding get method? |
| d.setHours(hoursVal)  | not sure                      |
| d.setMilliseconds(msVal) | need corresponding get method? |
| d.setMinutes(minsVal) | need corresponding get method? |
| d.setMonth(moVal)     | need corresponding get method? |
| d.setSeconds(secsVal) | need corresponding get method? |
| d.setTime(timeVal)    | need corresponding get method? |
| d.setUTCDate(dayVal)  | need corresponding get method? |
| new Date(value)     | Codepen messsed up? |
| new Date(dateString) | Codepen messsed up? |
| new Date(dateObject) | Codepen messsed up? |

<br />

Two parameters:
| syntax                      | Notes           | 
| :----                       | :----           |
| d.setFullYear(yearVal, moVal) | need corresponding get method? |
| d.setHours(hrsVal, minsVal)   | not sure |
| d.setMinutes(minsVal, secsVal) | need corresponding get method? |
| d.setMonth(moVal, dayVal)     | need corresponding get method? |
| d.setSeconds(secsVal, msValue) | need corresponding get method? |
| new Date(yr, moIndex)       | Codepen messsed up? |

<br />

Three parameters:
| syntax                              | Notes           | 
| :----                               | :----           |
| d.setFullYear(yearVal, moVal, dateVal) | need corresponding get method? |
| d.setHours(hrsVal, minsVal, secsVal)  | not sure |
| d.setMinutes(minsVal, secsVal, msVal) | need corresponding get method? |
| new Date(yr, moIndex, day)          | Codepen messsed up? |

<br />

Four or more parameters:
| syntax                                    | Notes           | 
| :----                               | :----           |
| d.setHours(hrsVal, minsVal, secsVal, msVal) | not sure  |
| new Date(yr, moIndex, day, hrs)           | Codepen messsed up? |
| new Date(yr, moIndex, day, hrs, mins)     | Codepen messsed up? |
| new Date(yr, moIndex, day, hrs, mins, secs) | Codepen messsed up? |
| new Date(yr, moIndex, day, hrs, mins, secs, ms) | Codepen messsed up? |

<br />

Date object examples: 
```js
let today = new Date() // "202203-11T22:13:35.413Z" Codepen?
let sameDay = new Date(today)
let birthday = new Date(1995, 11, 17) // "1995-12-17T5:00:00.000Z"
let birthday = new Date(1995, 11, 17, 13, 24, 0) // "1995-12-17T5:00:00.000Z"
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>