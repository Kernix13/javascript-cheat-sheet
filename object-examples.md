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