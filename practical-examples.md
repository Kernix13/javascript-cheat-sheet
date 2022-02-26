# Real life examples

Think of 1) actual (small) business applications, 2) common hobbies people have, 2a) ARTISTIC: an artistic application (guitar chord namer app, writer grammar checker, etc), 2b) AMATUER SCIENTIFIC: an astronomy app, botany app, archeology app, geology app

1. `push()` with `shift()`
   - consider inventory records where a recent item (newest date) is pushed onto the end of the inventory array for a product, as the oldest item is removed from the array. 
   - the item removed could be from a sale (oldest items sold first), or dated material (past due date), or oldest item used as display item.
1. push(): after creating an empty array, push on user input values for later use
1. includes(): boolean, I use !arr.includes() to only push onto an empty array the unique vales
1. objects: `class`, `new`, `prototype`, `hasOwnProperty`
   - client list updates - for my pet service business, or a large company with huge customer/client records. 
   - Having to update address or other contact information in a customer/client object 
   - searching for oldest clients, or clients/customers who are respo0nsible for the largest income, then offer them a special offer, discount, free item/service, questionaire, etc.
1. object record check, `hasOwnProperty`?
   - sign-in vs login
1. `switch()`
   - Given wind direction in degrees and a range of degrees set to different cardinal directions (from some source: N, NE, ENE, etc.), output the cardinal direction along with the wind speed
   - given a date, return the day of the week
1. if, if else, if else if:
   - if user logged in, show user options, else show login and sign-up buttons
   - if user id not found, show sign-up button AND link to send user name to account email address if user believes they already signed up
   - if user id correct AND password wrong, show send password reset link
   - if not a member, show
1. concat strings with + vs += - why? 
   - Greetings page or email subscription: "Hello " + ${username} + ", you have " + ${userMsgs} + " new messages." Or: ${username} + ", we have a special offer for you!"
   - for new messages you would use `usermsgs += usermsgs`
1. when to pass arguments into a function
1. when to use rest parameter and spread operator
1. split(/regex/): to return an array of words given an input string - used for my WriterAssist app, use for a search results app, 
1. check for properly formatted email with 
   - RegEx and match() although there are NPM packages for this
1. arithmetic
   - Multiply: itemPrice * itemQty = total amount for item 
   - Add: item1Total + item2Total + ... = total order amount
   - Subtract: refund amount 
   - Divide: posts per day, average read time in minutes = (total words) / (words read per minute), estimated drive time = (total miles) / (average speed) 
1. reduce(): calculate the sum of all the elements in the array, better approach to sum the total order value - actually, use reduce for all of the above instead of +
1. includes(): if statement in WriterAssist to search for end punctuation so as to capitalize the word or letter that follows used with chatAt()
1. charAt(): do something
1. classList.contains:

Other ideas:
- Photography: shutter > aperature > iso / sensitivity relationship
- Guitar / music theory - chrod namer app
- Bushcraft: orienterring?
- Botany? 
- Astronomy? 
- Coding: if you can't figure it out, then switch to thinking x, y, or z
- 

## Practical 2

- indexOf(str): why do you want to find where a substr or arr item starts?
```js
let str = 'finding substring in string';
let index = str.indexOf('str');

console.log(index); // 11
```

- indexOf(str): find count (TIPS AND TRICKS)
```js
let str = 'You do not know what you do not know until you know.';
let substr = 'know';
let count = 0;
let index = str.indexOf(substr);
while(index !== -1) {
    count++;
    index = str.indexOf(substr, index + 1);
}
console.log(count); // 3
```

RECORD COLLECTION 1:
```js
function updateRecords(records, id, prop, value) {
  if (prop !== 'tracks' && value !== "") {
    records[id][prop] = value;
  } else if (prop === "tracks" && records[id].hasOwnProperty("tracks") === false) {
    records[id][prop] = [value];
  } else if (prop === "tracks" && value !== "") {
    records[id][prop].push(value);
  } else if (value === "") {
    delete records[id][prop];
  }
  return records;
}
```

RECORD COLLECTION 2:
```js
function updateRecords(records, id, prop, value) {
  if (value === '') {
    delete records[id][prop];
  } else if (prop === 'tracks') {
    records[id][prop] = records[id][prop] || []; // this is called shortcircuit evaluation, see below for explanation
    records[id][prop].push(value);
  } else {
    records[id][prop] = value;
  }
  return records;
}
```