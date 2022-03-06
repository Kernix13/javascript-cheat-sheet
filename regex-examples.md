# Regular Expressions Examples

Basic syntax followed by more advanced examples

## Syntax and symbol meanings

Forward slashes to enclose your Regular Expression (RegEx):

```js
/regex/
```

Match literal strings:
```js
/jim/gi
```

"or" matches:
```js
/dog|cat|rabbit/gi
```

match anything with wildcard `.` e.g. fun, gun, pun, 

```js
/.un/gi
```

Character classes/sets with `[]`, e.g. bag, big, bug

```js
/b[aiu]g/gi
```

Character classes/sets with hyphens (`-`) for ranges

```js
/[a-e]/gi
/[a-z0-9]/ig
```

Anything but/except with the caret symbol INSIDE character set `[^]`:

```js
/[^aeiou]/gi
```

match 1 or more times with `+` symbol:
```js
/s+/gi 
```
> WHY DOES `[]` NOT WORK WITH `+`?

Match 0 or more times with asterisk (`*`), lowercase `a` optional

```js
/Aa*/
```

Lazy Matching with `?` for 'titanic':  
```js
/t[a-z]*?i/
```

use ^ outside a charter set to match the beginning of the string:
 `/^This/` returns `This` vs `/^[This]/` which returns `T`
```js
/^This/ 
```

use `$` to match the end of a string
`/end.$/` for `end.` vs `/[end.]$/` just returning `.`
```js
/end.$/
```

Shorthand:
- \w is the same as [A-Za-z0-9_]
- \W is the same as [^A-Za-z0-9_]
- \d is the same as [0-9]
- \D is the same as [^0-9]

## Practical examples

1. Match and replace
1. Validation
1. something else 

### Match and replace

Reorder and reformat a pet object from species, last name, first name:
```js
const pets = [
  "cat: Smith, Meowsalot",
  "young dog: Jones, Barksalot",
  "rabbit: Doe, Fluffy"
];

const petPattern = /([a-z\s]+):\s([a-z]+),\s([a-z]+)/i;

const petsUpdated = pets.map(pet => pet.replace(petPattern, '$3 $2 <span class="description">$1</span>'));
```
To HTML Output of first name, last name, species:

- Meowsalot Smith cat
- Barksalot Jones young dog
- Fluffy Doe rabbit

Uses: character sets, `\s`, `+`, `.replace()` method with capture groups `$3`, `$2`, `$1`

- - - 

Format phone numbers into preferred format. Examples:

```
12345678920
123-456-7890
321.321.4321
555 555 5555
1 555 555 5555
(555) 123 1234
555 555-5555
1.987.654.3210
```

Find and replace phone numbers:

```js
const phonePattern = /1?[-.\s]?\(?(\d{3})\)?[-.\s]?(\d{3})[-.\s]?(\d{4})/g;

let results = input.match(phonePattern); // input = source text with phone #'s
if (!results) results = [];

const resultsUniform = results.map(x => x.replace(phonePattern, '($1) $2-$3'));
```

Find and replace common HTML entities (<, >, ', ", &) with a function

```js
function replaceEntity(str) {
const entityPattern = /[&<>"']/g;
let  replacements = {
    "&":"&amp;",
    "<":"&lt;",
    ">":"&gt;",
    "\"":"&quot;",
    "'":"&apos;"
  }
  return str.replace(entityPattern, match => replacements[match]);
}

replaceEntity(`<?php the_post_thumbnail() ?>`)
console.log(replaceEntity(`<?php the_post_thumbnail() ?>`))
```

### User name validation

Create a regular expression here that does the following:

1. Can only contain letters and the 26 letters of the alphabet
2. Must begin with a letter, not a number
3. Must be at least 8 characters long, and not more than 30 characters

```js
const usernamePattern = /^[a-z][a-z0-9]{7,29}$/i

  if (usernamePattern.test(userInput)) {
    showSuccess()
  } else {
    showError()
  }
}
```

User name 2:

1. Usernames can only use alpha-numeric characters.
1. The only numbers in the username have to be at the end. There can be zero or more of them at the end. Username cannot start with the number.
1. Username letters can be lowercase and uppercase.
1. Usernames have to be at least two characters long. A two-character username can only use alphabet letters as characters.

```js
let username = "SomeUserName12";
let userCheck = /^[a-z][a-z]+\d*$|^[a-z]\d\d+$/i;
let result = userCheck.test(username);
// RegEx 2:
let userCheck2 = /^[a-z]([0-9]{2,}|[a-z]+\d*)$/i;
```