# Object code examples

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