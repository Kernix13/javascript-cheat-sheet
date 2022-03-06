# Object code examples


typeof:
```js
let typeOfTest;
typeOfTest = [];  // object
typeOfTest = {};  // object
typeOfTest = null; // object
```

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

### ES6 Class version

**NOTE**: Click on the lass name to show yellow lightbulb, click the lightuld, convert to ES6 class syntax:

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
console.log(colors);
console.log(c1, c2, c3, c4);
```

With a nested array - syntax is realy important
```js
const numbers2 = [1, 2, 3, [4, 5], 6];
const [n1, n2, n3, [n4, n5], n6] = numbers2;
console.log(n1, n2, n3, n4, n5, n6);
```

you can use destructuring to switch the values that are held in variables:
```js
let myStr2 = "Cheese";
let myStr3 = "Butter";
[myStr2, myStr3] = [myStr3, myStr2]
console.log(myStr2, myStr3);
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

## Unordered notes (fix later)

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

## ES6 classes

Create a class with a constructor, methods and properties.

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
  constructor(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
  }
  // add a method:
  greeting() {
    return `Hello there ${this.firstName}`;
  }
}

// create a new object based on t he Person class
const jim = new Person("Jim", "Kernix");
jim.greeting();
```

And you have a prototype for every class you create.