# Regular Expressions Examples

Basic syntax followed by more advanced examples

<div id="back-to-top"></div>

## Table of contents

1. [Basics](#basics)
1. [Wildcard and quantifiers](#wildcard-and-quantifiers)
   1. [Matches with asterisk](#matches-with-asterisk)
   1. [Specific match count](#specific-match-count)
1. [Anchors](#anchors)
1. [Escaping symbols](#escaping-symbols)
1. [Character classes](#character-classes)
   1. [Shorthand](#shorthand)
1. [Capture groups](#capture-groups)
   1. [Named groups](#named-groups)
   1. [Lookaheads](#lookaheads)
   1. [Lookbehinds](#lookbehinds)
1. [Practical examples](#practical-examples)
	 1. [Match and replace](#match-and-replace)
	 1. [User name validation](#user-name-validation)


## Basics

USe forward slashes (`/`) to enclose your Regular Expression (RegEx):

```js
/regex/
```

Match literal strings:
```js
let myString = "Hello, World!";
let myRegex = /Hello/;
let result = myRegex.test(myString);

let waldoIsHiding = "Somewhere Waldo is hiding in this text.";
let waldoRegex = /Waldo/; 
let result = waldoRegex.test(waldoIsHiding);

let extractStr = "Extract the word 'coding' from this string.";
let codingRegex = /coding/;
let result = extractStr.match(codingRegex);
```

Use the pipe character (`|`) as an "or" conditional:
```js
let petString = "James has a pet cat.";
let petRegex = /dog|cat|bird|fish/;
let result = petRegex.test(petString);
```

Flags: `i` for case insensitive, and `g` for global matches or to maych all occurences. Here are the best ones:
```js
/regex/i // ignore upper or lowercase
/regex/g // to match every occurrence
/regex/m // multiline
/regex/x // ignore whitespace/verbose
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Wildcard and quantifiers

Period is the wildcard `.`. Quantifiers are: `+`, `?`, `*`, `*?`, `**`, `{#}`, `{#,}`, and `{#,#}` 

> WHY DO CHARCTER CLASSES (`[]`) NOT WORK WITH `+`?

Match Anything with Wildcard Period `.`: matches when a character occurs one or more times. Match characters that occur one or more times:
```js
// match anything with the wildcard . e.g. fun, gun, pun, run
/.un/gi

let exampleStr = "Let's have fun with regular expressions!";
let unRegex = /.un/; 
let result = unRegex.test(exampleStr);
```

<br />

Match Characters that Occur One or More Times with `+`
```js
// + Matches one or more consecutive characters: a aa aaa aaaa bab baab
/a+/gi 
// match s
let difficultSpelling = "Mississippi";
let myRegex = /s+/g; // this is the solution
let result = difficultSpelling.match(myRegex);
```

<br />

Check for All or None with `?`
```js
// ? Matches a character or nothing.: ba b a
/ba?/g

let american = "color";
let british = "colour";
let rainbowRegex= /colou?r/;
rainbowRegex.test(american); // true
rainbowRegex.test(british); // true

let favWord = "favorite";
let favRegex = /favou?rite/; 
let result = favRegex.test(favWord);
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Matches with asterisk

Match Characters that Occur Zero or More Times with `*`: 
```js

// * Matches zero or more consecutive characters: a ba baa aaa ba b
/ba*/g
/Aa*/

let phrase = "ba humbug";
let regexPlus = /bah+/;
let regexStar = /bah*/;
regexPlus.test(phrase); // returns false
regexStar.test(phrase); // returns true

let regexPlus = /wo+w/;
let regexStar = /wo*w/;
regexPlus.test(phrase); // returns true
regexStar.test(phrase); // returns true

let soccerWord = "gooooooooal!";
let gPhrase = "gut feeling";
let oPhrase = "over the moon";
let goRegex = /go*/;
soccerWord.match(goRegex); // ['goooooooo']
gPhrase.match(goRegex); // ['g']
oPhrase.match(goRegex); // null

let chewieQuote = "Aaaaaaaaaaaaaaaarrrgh!";
let chewieRegex = /Aa*/; // Change this line
let result = chewieQuote.match(chewieRegex);
```

<br />

Lazy matching: use the *? character
```js
/t[a-z]*?i/

// lazy quantifier with `*?`
let text = "<h1>Winter is coming</h1>";
let myRegex = /<.*?>/; // it's the answer!
let result = text.match(myRegex);
```

<br />

```js
// possessive quantifer with `**`
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Specific match count

Match a spcific number of times with `{#}`:
```js
let A4 = "haaaah";
let A3 = "haaah";
let A100 = "h" + "a".repeat(100) + "h";
let multipleHA = /ha{3}h/;
multipleHA.test(A4); // false
multipleHA.test(A3); // true
multipleHA.test(A100); // false

let timStr = "Timmmmber";
let timRegex = /Tim{4}ber/; 
let result = timRegex.test(timStr);
```

<br />

Specify Only the Lower Number of Matches with `{#,}` : 
```js
let A4 = "haaaah";
let A2 = "haah";
let A100 = "h" + "a".repeat(100) + "h";
let multipleA = /ha{3,}h/;
multipleA.test(A4); // true
multipleA.test(A2); // false
multipleA.test(A100); // true

let haStr = "Hazzzzah";
let haRegex = /Haz{4,}ah/; 
let result = haRegex.test(haStr);
```

<br />

Specify Upper and Lower Number of Matches `{#,#}`:
```js
let A4 = "aaaah";
let A2 = "aah";
let multipleA = /a{3,5}h/;
multipleA.test(A4); // true
multipleA.test(A2); // false

let threeAs = "aaa";
let fourAs = "aaaa";
let sevenAs = "aaaaaaa";

let myRegex = /a{2,4}/;
myRegex.test(threeAs); // true
myRegex.test(fourAs); // true
myRegex.test(sevenAs); // true
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Anchors

Anchors: the caret symbol (`^` or `\A`) both inside and outside of character classes, and the dollar sign (`$` or `\Z`).

To create a negated character set, you place a caret character (^) after the opening bracket and before the characters you do not want to match:
```js
// Anything but/except with the caret symbol INSIDE character set, ^ or \A:
/^This/  // returns 'T'

/[^aeiou]/gi
let quoteSample = "3 blind mice.";
let myRegex = /[^aeiou^0-9]/gi; 
let result = quoteSample.match(myRegex); 
```

<br />

```js
// match start of string qith ^ or \A OUTSIDE of a character set
let firstString = "Ricky is first and can be found.";
let firstRegex = /^Ricky/;
firstRegex.test(firstString);
let notFirst = "You can't find Ricky now.";
firstRegex.test(notFirst); // true

let rickyAndCal = "Cal and Ricky both like racing.";
let calRegex = /^Cal/; 
let result = calRegex.test(rickyAndCal);
```

<br />

use `$` to match the end of a string - this one if messed up???
```js
/end.$/
// match end of string with $ or \Z
/end.$/ // for 'end.' vs 
/[end.]$/ // just returning `.`

let theEnding = "This is a never ending story";
let storyRegex = /story$/;
storyRegex.test(theEnding);
let noEnding = "Sometimes a story will have to end";
storyRegex.test(noEnding); // true

let caboose = "The last car on a train is the caboose";
let lastRegex = /caboose$/; 
let result = lastRegex.test(caboose);
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Escaping symbols

Use the backslash `\` to escape special characters that are in your string
```js
// escape thw wildcard as part of your regex
/\./

// escape one or more character +
/\+/

// escape zero or more character *
/\*/

// escape end of string character $
/\$/

// escape star of string or negation character ^
/\^/

// escape zero or one character ?
/\?/

// escape backslash
/\\/

// escape parentheses
/\(\)/

// escape square brackets or character classes
/\[\]/

// escape curly brackets
/\{\}/
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Character classes

Character classes/sets with `[]`, e.g. bag, big, bug

```js
/b[aiu]g/gi

let quoteSample = "I have only proved it correct, but not tried it.";
let vowelRegex = /[aeiou]/gi; 
let result = quoteSample.match(vowelRegex);

let catStr = "cat";
let batStr = "bat";
let matStr = "mat";
let bgRegex = /[a-e]at/;
catStr.match(bgRegex); // ['cat']
batStr.match(bgRegex); // ['bat']
matStr.match(bgRegex); // null

let quoteSample = "The quick brown fox jumps over the lazy dog.";
let alphabetRegex = /[a-z]/gi; 
let result = quoteSample.match(alphabetRegex);
```

Character classes/sets with hyphens (`-`) for ranges

```js
/[a-e]/gi
/[a-z0-9]/ig
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Shorthand

Any digit and any non-digit with `\d` and `\D`:
```js
\d // match all numbers
let movieName = "2001: A Space Odyssey";
let numRegex = /\d/g;
let result = movieName.match(numRegex).length;

\D // match anything but a number
let movieName = "2001: A Space Odyssey";
let noNumRegex = /\D/g;
let result = movieName.match(noNumRegex).length;
```
<br />

Match word characters or non-word characters ith `\w` and `\W`:
```js
\w // shorthand for [A-Za-z0-9_]

let longHand = /[A-Za-z0-9_]+/;
let shortHand = /\w+/;
let numbers = "42";
let varNames = "important_var";
longHand.test(numbers); // true
shortHand.test(numbers); // true
longHand.test(varNames); // true
shortHand.test(varNames); // true

let quoteSample = "The five boxing wizards jump quickly.";
let alphabetRegexV2 = /\w/g; 
let result = quoteSample.match(alphabetRegexV2).length;

\W // shorthand for [^A-Za-z0-9_]
let shortHand = /\W/;
let numbers = "42%";
let sentence = "Coding!";
numbers.match(shortHand); // ['%']
sentence.match(shortHand); // ['!']

let quoteSample = "The five boxing wizards jump quickly.";
let nonAlphabetRegex = /\W/g;
let result = quoteSample.match(nonAlphabetRegex).length;
```

<br />

Match whitespace and non whitespace with `\w` and `\W`::
```js
let whiteSpace = "Whitespace. Whitespace everywhere!"
let spaceRegex = /\s/g;
whiteSpace.match(spaceRegex); // [" ", " "]

let sample = "Whitespace is important in separating words";
let countWhiteSpace = /\s\w*/;
let result = sample.match(countWhiteSpace);

let whiteSpace = "Whitespace. Whitespace everywhere!"
let nonSpaceRegex = /\S/g;
whiteSpace.match(nonSpaceRegex).length; // 32

let sample = "Whitespace is important in separating words";
let countNonWhiteSpace = /\S/g; 
let result = sample.match(countNonWhiteSpace); 

// Remove Whitespace from Start and End with, you could also use str.trim()
let hello = "   Hello, World!  ";
let wsRegex = /^\s+|\s+$/g; 
let result = hello.replace(wsRegex, "");
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Capture groups

Sometimes we want to check for groups of characters using a Regular Expression and to achieve that we use parentheses `()`.

```js
// find either Penguin or Pumpkin in a string
let testStr = "Pumpkin";
let testRegex = /P(engu|umpk)in/;
testRegex.test(testStr); // true

// check for the names of Franklin Roosevelt or Eleanor Roosevelt in a case sensitive manner
let myString = "Eleanor Roosevelt";
let myRegex = /(Franklin|Eleanor).*Roosevelt/;
let result = myRegex.test(myString);
```

<br />

Reuse Patterns Using Capture Groups: 
```js
let repeatRegex = /(\w+) \1 \1/;
repeatRegex.test(repeatStr); // Returns true
repeatStr.match(repeatRegex); // Returns ["row row row", "row"]

// match a string that consists of only the same number repeated exactly three times separated by single spaces
let repeatNum = "42 42 42";
let reRegex = /^(\d+)\s\1\s\1$/;
let result = reRegex.test(repeatNum);
```

<br />

Use Capture Groups to Search and Replace:
```js
let wrongText = "The sky is silver.";
let silverRegex = /silver/;
wrongText.replace(silverRegex, "blue"); // "The sky is blue."
```

<br />

access capture groups in the replacement string with dollar signs `($)`:
```js
"Code Camp".replace(/(\w+)\s(\w+)/, '$2 $1'); // returns "Code Camp"

// three capture groups that will search for each word in the string one two three then replace them 
let str = "one two three";
let fixRegex = /(\w+)\s(\w+)\s(\w+)/; 
let replaceText = "$3 $2 $1"; //
let result = str.replace(fixRegex, replaceText);
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Named groups

```js
// 
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Lookaheads

A positive lookahead is used as `(?=...)` where the ... is the required part that is not matched.

A negative lookahead is used as `(?!...)` where the ... is the pattern that you do not want to be there.

```js
let quit = "qu";
let noquit = "qt";
let quRegex= /q(?=u)/;
let qRegex = /q(?!u)/;
quit.match(quRegex); // ['q']
noquit.match(qRegex); // ['q']

// check two or more patterns in one string: a simple password checker that looks for between 3 and 6 characters and at least one number
let password = "abc123";
let checkPass = /(?=\w{3,6})(?=\D*\d)/;
checkPass.test(password);

// Use lookaheads in the pwRegex to match passwords that are greater than 5 characters long, and have two consecutive digits:
let sampleWord = "astronaut";
let pwRegex = /(?=\w{6})(?=\w*\d{2})/;
let result = pwRegex.test(sampleWord);
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Lookbehinds

```js
// 
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

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

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

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

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>