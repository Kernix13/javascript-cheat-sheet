# Object code examples

Syntax and code examples for the most coomon object methods

<div id="back-to-top"></div>

## Table of contents

1. [Object keys](#object-keys)
1. [Object values](#object-values)
1. [hasOwnProperty](#hasOwnProperty)
1. [for in loop](#for-in-loop)
1. [Modify values and remove keys](#modify-values-and-remove-keys)
1. [Classes](#classes)
   1. [prototype version](#prototype-version)
   1. [ES6 Class version](#es6-class-version)
1. [Destructuring an object](#destructuring-an-object)
1. [Spread operator](#spread-operator)
1. [Miscellaneous](#miscellaneous)

Common Object methods:


## Object keys

[MDN Object.keys docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/keys): Returns an array of the key names.

```js
// syntax
Object.keys(obj)

// Example
const chordIntervals = {
    "Chord": "maj",
    "Intervals": ["1", "3", "5"],
    "steps": [0, 4, 7],
		"Equal Chords": [{"key": "", "name": ""}],
    "Chord Substitutes": [{"key": "", "name": ""}],
		"scales": {
			"Major Scale": ["1st", " 4th", " 5th"],
			"Minor Pentatonic": ["2nd"],
			"Blues Scale": ["2nd"],
			"Harmonic Minor": ["5th", "6th"],
			"Melodic Minor": ["4th", "5th"],
			"Whole Tone": [""],
			"Augmented": ["1st", "3rd", "5th"],
			"HW Diminished": ["1st", "3rd", "5th", "7th"],
			"Major Bebop": ["1st", "4th", "5th"],
			"Minor Bebop": ["3rd", "5th", "8th"]
		}
  }
console.log(Object.keys(chordIntervals)) // ["Chord","Intervals","steps","Equal Chords","Chord Substitutes","scales"]
console.log(Object.keys(chordIntervals.scales)) // ["Major Scale","Minor Pentatonic","Blues Scale","Harmonic Minor", ...]
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Object values

[MDN Object.values docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_objects/Object/values): Returns an array of the vaalues for each key.

```js
// syntax
Object.values(obj)

// Examples:
const chordIntervals = {
    "Chord": "maj",
    "Intervals": ["1", "3", "5"],
    "steps": [0, 4, 7],
  }
console.log(Object.values(chordIntervals)) // ["maj", ["1","3","5"], [0,4,7]]
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## hasOwnProperty

[MDN hasOwnProperty](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/hasOwnProperty): Returns `true` if the object has the specified property as own property; `false` otherwise.

```js
// syntax
obj.hasOwnProperty(prop)	
// prop: The String name or Symbol of the property to test

// Example, RECORD COLLECTION 1:
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

// Example, RECORD COLLECTION 2:
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

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## for in loop

Using `for in`:
```js
// syntax:
obj.hasOwnProperty('Prop1');
'Prop1' in uobjsers;

for (let user in users) {...}

// Example
const users = {
  Alan: {
    online: false
  },
  Jeff: {
    online: true
  },
  Sarah: {
    online: false
  }
}

function countOnline(usersObj) {
  // Only change code below this line
  let result = 0;
  for (let user in usersObj) {
    if (usersObj[user].online === true) {
      result++;
    }
  }
  return result;
  // Only change code above this line
}

console.log(countOnline(users));
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Modify values and remove keys

```js
let something = {
  id: 23894201352,
  location: "New York",
  date: 'January 1, 2017',
  data: {
    totalUsers: 51,
    online: 42
  }
};
// Add:
something.data.offline = 100;
// Modify:
something.data.online = 45;
// Delete:
delete something.location;
```

Access values by using `obj[prop]` or `obj.prop[i]` or `obj.[prop][i]`.
```js
// something here
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Other



<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Classes

Excellent Video ES6 Classes: https://youtu.be/_vmLIClIJS8

### prototype version

```js
// Amusement park food pass example:
function Park (firstName, lastName, fastPass, mealPass) {
  this.firstName = firstName,
  this.lastName = lastName,
  this.fastPass = fastPass,
  this.mealPass = mealPass
}
Park.prototype.getFullName = function() {
  return `${this.firstName} ${this.lastName}`;
}
Park.prototype.canSkip = function() {
  return `${this.getFullName()} ${this.fastPass ? " can skip the line" : " can't skip the line"}.`;
}
Park.prototype.canEat = function() {
  return `${this.getFullName()} ${this.mealPass ? " can eat here" : " can't eat here"}.`;
}
const molly = new Park("Molly", "Stevens", false, false);
const steve = new Park("Steve", "Jones", true, true);
const sue = new Park("Sue", "Smith", true, false);
const joe = new Park("Joe", "Thomas", false, true);

console.log(molly.canEat());
console.log(steve.canEat());
console.log(joe);
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### ES6 Class version

**NOTE**: Click on the lass name to show yellow lightbulb, click the lightuld, convert to ES6 class syntax:

```JS
// syntax
const Name = function(arg) {

class Name {
  constructor(arg) {
}
```

```js
// Amusement park fast pass example:
class Park2 {
  constructor(firstName, lastName, fastPass, mealPass) {
    this.firstName = firstName,
      this.lastName = lastName,
      this.fastPass = fastPass,
      this.mealPass = mealPass;
  }
  getFullName() {
    return `${this.firstName} ${this.lastName}`;
  }
  canSkip() {
    return `${this.getFullName()} ${this.fastPass ? " can skip the line" : " can't skip the line"}.`;
  }
  canEat() {
    return `${this.getFullName()} ${this.mealPass ? " can eat here" : " can't eat here"}.`;
  }
}
const molly2 = new Park2("Molly", "Stevens", false, false);
const steve2 = new Park2("Steve", "Jones", true, true);
const sue2 = new Park2("Sue", "Smith", true, false);
const joe2 = new Park2("Joe", "Thomas", false, true);

console.log(steve2.canSkip());
console.log(joe2.canSkip());
```
Example with my clients:
```js
// petNames as an array of objects
const philMiller = new Client("Phil Miller", "2001 Hamilton # 305", "pmiller83@gmail.com", "215-834-8218", {"Dog": "Sadie"}, {"Dog": "Abby"}, {"Cat": "Luna"});
// petNames as an array
// const philMiller = new Client("Phil Miller", "2001 Hamilton # 305", "pmiller83@gmail.com", "215-834-8218", "Sadie", "Abby", "Bella");

console.log(philMiller);

class SecondClient {
  constructor(secondName, secondEmail, secondPhone) {
    this.secondName = secondName,
    this.secondEmail = secondEmail,
    this.secondPhone = secondPhone
  }
}

const philSpouse = new SecondClient("Rachel Miller", "soandso@gmail.com", "555-555-5555")
console.log(philSpouse);

let totalClient = {...philMiller, ...philSpouse};
console.log(totalClient);
```

Example object:
```js
const student1 = {
  firstName: "Mary",
  lastName: "Williams",
  gradeLevel: "Junior",
  currentAverage: "A"
};
```

Console.log empty function:
```js
function Student() {

}
console.log(Student()); // undefined
console.log(new Student()); // Student {}
```

The `new` keyword changes the behavior of how the function operates. You then get access to the object via the `this` keyword.

```js
// All students will have these properties:
function Student(first, last, lvl, avg) {
  this.firstName = first;
  this.lastName = last;
  this.gradeLevel = lvl;
  this.currentAverage = avg;
  this.getFullName = function() {
    return `${this.firstName} ${this.lastName}`
  }
}
const student1 = new Student("Mary", "Williams", "Junior", "A");
console.log(student1); // Student {firstName: 'Mary', lastName: 'Williams', gradeLevel: 'Junior', currentAverage: 'A'}

// update:
student1.firstName = "Marilyn";
student1.age = 28;
```

Create a class with a constructor, methods and properties. And you have a prototype for every class you create.

```js
// syntax
class ClassName {
  constructor(properties to set) {
    this.prop1 = prop1;
    this.ptop2 = prop2;
  }
}
// Person class
class Person {
  constructor(firstName, lastName, dob) {
    this.firstName = firstName;
    this.lastName = lastName;
    this.birthday = new Date(dob);
  }

  greeting() {
    return `Hello, ${this.firstName} ${this.lastName}.`;
  }
}

// create a new object based on the Person class
const jim = new Person("Jim", "Kernix");
jim.greeting();
```

sub classes with `extends` and `super` keywords:
```js
class Customer extends Person {
  constructor(firstName, lastName, phone, membership) {
    // super calls the paent class constructor
    super(firstName, lastName);

    this.phone = phone;
    this.membership = membership;
  }
}

const john = new Customer('John', 'Williams', '123-456-7890', 'Standard');
const mary = new Person('Mary', 'Thompson');
console.log(john.greeting());
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Destructuring an object

THE OLD WAY TO DESCTRUCTURE AN OBJECT, ASSIGN VARIABLES FROM OBJECTS:
```js
var voxel = {x: 3.6, y: 7.4, z: 6.54};

let x = voxel.x;
let y = voxel.y;
let z = voxel.z;
console.log(x);
```

HOW TO DO ABOVE WITH DESCTRUCTURING:
```js
var voxel = {x: 3.61, y: 7.4, z: 6.54};
const {x, y, z} = voxel; 
console.log(x);
```

Copy into new variable names:
```js
var voxel = {x: 3.61, y: 7.4, z: 6.59};
const {x: a, y: b, z: c} = voxel; 
console.log(c);
```

Assign variables FROM nested objects:
```js
const nest = {
  start: {x: 51, y: 6},
  end: {x: 6, y: -9}
}
const { start: { x: startX, y: startY }} = nest;
console.log("startX: " + startX);
```

Destructure arrays:
```js
const [q, , , , r] = [1, 2, 3, 4, 5];
console.log(q, r);
```

Rest operator to reassign array elements - the Rest gets the "rest":
```js
const [a, b, ...rest] = [1, 2, 3, 4, 5];
console.log(a, b, rest);
```

use destructuring tp pass an object as a functions parameters (???)
```js
const profileUpdates = ({name, age, nationality, location}) => {
  // do something with the vars (find the video and rewatch)
}
```

Video: #54 Destructuring Assignment Arrays
```js
const colors = ["yellow", "blue", "red", "green"];
const [c1, c2, c3, c4] = colors;
console.log(colors); // ["yellow","blue","red","green"]
console.log(c1, c2, c3, c4); // "yellow" "blue" "red" "green"
```

With a nested array - syntax is realy important
```js
const numbers2 = [1, 2, 3, [4, 5], 6];
const [n1, n2, n3, [n4, n5], n6] = numbers2;
console.log(n1, n2, n3, n4, n5, n6); // 1 2 3 4 5 6
```

you can use destructuring to switch the values that are held in variables:
```js
let myStr2 = "Cheese";
let myStr3 = "Butter";
[myStr2, myStr3] = [myStr3, myStr2]
console.log(myStr2, myStr3); // "Butter" "Cheese"
```

Another one:
```js
const myStore = {
    groceries: [["Milk", 5], ["Bread", 1], ["Butter", 3], ["Cereal", 2], ["Corn", 3], ["Rice", 2], ["Steak", 10]],
    generalItems: [["Cleaner", 3], ["Towels", 6], ["Mop", 10], ["Pans", 12], ["Shirts", 4]],
    purchaseItems: function (groceryIndex, generalIndex) {
        return [this.groceries[groceryIndex], this.generalItems[generalIndex]];
    }
}
const myOrder = myStore.purchaseItems(6, 1);
const [[item1, price1], [item2, price2]] = myOrder;
console.log(`Your item of ${item1} from grocery costs $${price1}.\nYour item of ${item2} from general costs $${price2}.`);
```

Huge example, #58 Object Destructuring Part 1:
```js
const mall = {
  mallName: "Mall of Irvine",
  address: {
    street: "555 Main Street",
    city: "Irvine",
    state: "CA",
    zip: "92620",
  },
  anchorStores: ["Macy's", "Sears", "Dick's Sporting Goods", "JCPenny"],
  fastFood: ["Panda Express 🐥", "Subway 🥪", "Burger King 🍔"],
  restaurants: [
    "Red Lobster",
    "Cheesecake Factory",
    "California Pizza Kitchen",
  ],
  takeOut: {
    appetizers: [
      "Garlic Bread",
      "Goat Cheese",
      "Spinach Dip and Chips",
      "Wings",
    ],
    main: [
      "Pasta and Meatballs",
      "Ribs and Potatoes",
      "Steak with Spanish Rice",
    ],
    drinks: ["Coke", "Sprite", "Water", "Beer"],
    deserts: ["Chocolate Cake", "Apple Pie", "Ice Cream"],
  },
  getDelivery: function ({
    appetizerIndex,
    mainIndex,
    drinkIndex,
    desertIndex,
    time,
    address,
  }) {
    const r = this.takeOut; // shorten the path to it 
    return `Your order has been received at ${time} for delivery at:\n${address}:\nAppetizer: ${r.appetizers[appetizerIndex]}\nMain Dish: ${r.main[mainIndex]}\nDrink: ${r.drinks[drinkIndex]}\nDesert: ${r.deserts[desertIndex]}`;
  },
};
const myFood = mall.getDelivery({
  desertIndex: 0,
  drinkIndex: 1,
  appetizerIndex: 2,
  mainIndex: 2,
  time: "7:00 PM",
  address: "123 Main Drive\nIrvine, CA 92620",
});
console.log(myFood);
const {mallName: localName, anchorStores, address: {street: streetName, city, state, zip}} = mall;
// console.log(mall.address.street)
// console.log(streetName)
// console.log(`Come vist ${localName}.\nWe are located at ${streetName}.`)
```

#59 Object Destructuring Part 2, 2nd example, assignment without declaration:
```js
const jason = {
  firstName: "Jason",
  lastName: "Fitzgerald",
  age: 35,
  city: "Destin",
  state: "FL",
  job: "Web Developer"
}
let jasonAge = "unknown", jasonJob = "unknown";
({age: jasonAge, job: jasonJob} = jason);
console.log(jasonAge, jasonJob); // 35 "Web Developer"  
```

LESSON 11 use destructuring assignment to extract values from objects
const HIGH_TEMPERATURES = {
  yesterday: 75,
  today: 77,
  tomorrow: 80
};

const { today, tomorrow } = HIGH_TEMPERATURES;

12. use destructuring assignment to assign variables from objects
const { name: userName, age: userAge } = user;

13. use destructuring assignment to assign variables from nested objects
const { johnDoe: { age: userAge, email: userEmail }} = user;

lesson 14 use destructuring assignment to assign variables from arrays
const [a, b, , , c] = [1, 2, 3, 4, 5, 6];
console.log(a, b, c);

lesson 15 use destructuring assignment w\ the rest parameter to reassign array elements
const [a, b, ...arr3] = [1, 2, 3, 4, 5, 7];

16. use destructuring assignment to pass an object as a Fx’s parameters

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Spread operator

pulling key-values from another object: 
```js
let contact = {
  firstName: "Jim",
  lastName: "Kernix",
  email: "test@test.com"
}

let myAddress = {
  ...contact,
  number: 123,
  street: "Main Street",
  city: "Anytown"
}
console.log(myAddress);
```

copy and change values:
```js
const myCar = {
  make: "Honda",
  model: "Accord",
  color: "Red",
  year: 1999,
  mpg: 25,
  price: "$1000"
}
const lunasCar = {...myCar, doors: 3, "Spare tires": 0};
lunasCar.color = "White";
// console.log(lunasCar);
```
with an example of renaming keys:
```js
const applicant = {
  firstName: "Jamie",
  lastName: "Smith",
  age: 29,
  job: "Teacher",
  city: "Houston",
  state: "TX",
  yearsExp: 5,
  recommendations: 3,
};

const {firstName: applicantFirstName, lastName: applicantLastName, ...otherinformation} = applicant;
console.log(otherinformation);
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Miscellaneous

Other methods: Object.entries(obj)| Object.getOwnPropertyNames()| Object.freeze(obj)| obj.toString() | obj.prop ???

typeof:
```js
let typeOfTest;
typeOfTest = [];  
console.log(typeof typeOfTest) // object
typeOfTest = {};  // object
typeOfTest = null; // object
```

WTF with [] working but not dot notation???? Something with if statements?
