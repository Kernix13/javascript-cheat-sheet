# Conditional statements

- [MDN if statements](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else)
- [MDN ternary operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator)
- [MDN swtich](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/switch)

<div id="back-to-top"></div>

## Table of contents

1. [if else statements](#if-else-statements)
1. [else if](#else-if)
1. [Ternary operator](#ternary-operator)
   1. [Conditional chains](#conditional-chains)
1. [Switch](#switch)
1. [Miscellaneous](#miscellaneous)
   1. [Notes](#notes)

## if else statements

Syntax:
```js
if (condition) {
   statement1
} else {
   statement2
}

// example
function strEntry(str) {
  if (str !== "") {
   return str.split('');
  } else {
     return "Field is empty";
  }
}
console.log(strEntry("string")); // ["s","t","r","i","n","g"]
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### else if

Syntax:
```js
if (condition1)
  statement1
else if (condition2)
  statement2
else if (condition3)
  statement3
...
else
  statementN
```

To execute multiple statements within a clause, use a block statement ({ /* ... */ }) to group those statements. In general, it is a good practice to always use block statements, especially in code involving nested if statements:

```js
if (x > 50) {
  /* do something */
} else if (x > 5) {
  /* do something */
} else {
  /* do something */
}
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Ternary operator

Syntax:
```js
condition ? exprIfTrue : exprIfFalse
a ? b : c

// example:
var age = 26;
var beverage = (age >= 21) ? "Beer" : "Juice";
console.log(beverage); // "Beer"

// Handling null values
let greeting = person => {
    let name = person ? person.name : `stranger`
    return `Howdy, ${name}`
}
console.log(greeting({name: `Alice`}));  // "Howdy, Alice"
console.log(greeting(null));             // "Howdy, stranger"
```

### Conditional chains

The ternary operator is right-associative, which means it can be "chained" in the following way, similar to an if … else if … else if … else chain:

```js
function example(…) {
    return condition1 ? value1
         : condition2 ? value2
         : condition3 ? value3
         : value4;
}

// Equivalent to:
function example(…) {
    if (condition1) { return value1; }
    else if (condition2) { return value2; }
    else if (condition3) { return value3; }
    else { return value4; }
}
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Switch

Syntax:
```js
switch (expression) {
  case value1:
    //Statements executed when the
    //result of expression matches value1
    [break;]
  case value2:
    //Statements executed when the
    //result of expression matches value2
    [break;]
  ...
  case valueN:
    //Statements executed when the
    //result of expression matches valueN
    [break;]
  [default:
    //Statements executed when none of
    //the values match the value of the expression
    [break;]]
}
```

<br />

Examples:
```js
switch (expr) {
  case 'Oranges':
    console.log('Oranges are $0.59 a pound.');
    break;
  case 'Apples':
    console.log('Apples are $0.32 a pound.');
    break;
  case 'Bananas':
    console.log('Bananas are $0.48 a pound.');
    break;
  case 'Cherries':
    console.log('Cherries are $3.00 a pound.');
    break;
  case 'Mangoes':
  case 'Papayas':
    console.log('Mangoes and papayas are $2.79 a pound.');
    break;
  default:
    console.log('Sorry, we are out of ' + expr + '.');
}
console.log("Is there anything else you'd like?");

// Example 2:

// Get day of week for November 1st for the current year
const d = new Date();
const year = d.getFullYear();
let currentNovFirst = '11/01/' + year;
let novFirstDay = new Date(currentNovFirst).getDay();

// For the current year, find the day of the week for the 1st of November 
switch (novFirstDay) {
  case 0:
    weekOne = new Date(`11/1/${year}`)
    break;
  case 1:
    weekOne = new Date(`11/1/${year}`)
    break;
  case 2:
    weekOne = new Date(`11/1/${year}`)
    break;
  case 3:
    weekOne = new Date(`11/1/${year}`)
    break;
  case 4:
    weekOne = new Date(`11/1/${year}`)
    break;
  case 5:
    weekOne = new Date(`11/1/${year}`)
    break;
  case 6:
    weekOne = new Date(`11/1/${year}`)
}
```

<br />

Methods for multi-criteria case:
```js
var Animal = 'Giraffe';
switch (Animal) {
  case 'Cow':
  case 'Giraffe':
  case 'Dog':
  case 'Pig':
    console.log('This animal is not extinct.');
    break;
  case 'Dinosaur':
  default:
    console.log('This animal is extinct.');
}
```

<br />

Multi-case : chained operations
```js
var foo = 1;
var output = 'Output: ';
switch (foo) {
  case 0:
    output += 'So ';
  case 1:
    output += 'What ';
    output += 'Is ';
  case 2:
    output += 'Your ';
  case 3:
    output += 'Name';
  case 4:
    output += '?';
    console.log(output);
    break;
  case 5:
    output += '!';
    console.log(output);
    break;
  default:
    console.log('Please pick a number from 0 to 5!');
}
```

Also: [Block-scope variables within switch statements](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/switch#block-scope_variables_within_switch_statements)

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Miscellaneous

- type conversion
- `==` vs `===`

### Notes

A **switch** statement first evaluates its expression. It then looks for the first `case` clause whose expression evaluates to the same value as the result of the input expression (using the strict comparison, `===`) and transfers control to that clause, executing the associated statements. (If multiple cases match the provided value, the first `case` that matches is selected, even if the cases are not equal to each other.)

If no matching `case` clause is found, the program looks for the optional `default` clause, and if found, transfers control to that clause, executing the associated statements. If no `default` clause is found, the program continues execution at the statement following the end of `switch`. By convention, the `default` clause is the last clause, 

- expression: An expression whose result is matched against each `case` clause
- `case valueN`: A `case` clause used to match against expression. If the expression matches the specified `valueN`, the statements inside the `case` clause are executed until either the end of the `switch` statement or a `break`
- break: The optional statement associated with each case label ensures that the program breaks out of switch once the matched statement is executed and continues execution at the statement following `switch`. If `break` is omitted, the program continues execution at the next statement in the switch statement. The `break` statement is not required if a `return` statement precedes it.
- default: A default clause; if provided, this clause is executed if the value of expression doesn't match any of the `case` clauses

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>