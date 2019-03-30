# Introduction to ES6+ by Dylan Israel

## 1. Intro
## 2. Template Literals
- helps to perform js operations and easier concatenations
```js
let word1 = 'Dylan';
let word2 = 'Israel';
let num1 = 2;
let num2 = 3;

const fullName = `${word1} ${word2}`;
const fullName = `${num1 + num2} ${word2}`;
let example = `${word1}
${word2}
`;
console.log(fullName);
console.log(example);
```

## 3. Destructuring Objects
- pulls out values by objects to help shorthand code
- can also rename the destructured key
```js
const personalInformation = {
    firstName: 'Dylan',
    lastName: 'Israel',
    city: 'Austin',
    state: 'Texas',
    zipCode: 73301
};

const {firstName: fn, lastName: ln} = personalInformation;

console.log(`${fn} ${ln}`);
```

## 4. Destructuring Arrays
- destructures according to index
- `lastName` is a reference to item in array so it can be redefined
```js
let [firstName, middleName, lastName] = ['Dylan', 'Coding God', 'Israel'];

lastName = 'Clements';

console.log(lastName)

```

## 5. Object Literal
- makes the key and value the same
- saves extra redundant code
- IE city: city, state: state
```js
function addressMaker(city, state) {
    const newAdress = {city, state};
    
    console.log(newAdress);
}

addressMaker('Austin', 'Texas');
```

## 6. Object Literal (Challenge)
```js
function addressMaker(address) {
    const { city, state } = address
    const country = 'United States'
    const newAddress = {
        city,
        state,
        country
    };
    console.log(`${newAddress.city}, ${newAddress.state}, ${newAddress.country}`)
}

addressMaker({city: 'Austin', state: 'Texas'});
```

## 7. For of Loop
- for of loop prints out values
```js
let incomes = [62000, 67000, 75000];
let total = 0;

for (const income of incomes) {
    console.log(income);
    total += income;
}

// console.log(total);
```
```js
let fullName = "Dylan Coding God Israel";


for (const char of fullName) {
    console.log(char);
}
```

## 8. For of Loop (Challenge)
- This is not what it was designed to do and will not work
```js
let incomes = [62000, 67000, 75000];

for (let income of incomes) {
  income += 5000;
}

console.log(incomes);
```

## 9. Spread Operator
- spread operator making a new array, not a reference to example1
```js
let example1 = [1,2,3,4,5,6];
let example2 = [...example1];
example2.push(true);

console.log(example2);
```

- spreading items in an object
```js
let example1 = {
    firstName: 'Dylan'
};

let example2 = {
    ...example1
}

console.log(example2);
```

## 10. Rest Operator
- makes inputed items as array by spreading them out
```js
function add(...nums) {
  console.log(nums);
}

add(4, 5, 7, 8, 12);
```

## 11. Arrow Functions
- helps reduce lines of code
```js
function add(...nums) {
    let total = nums.reduce((x, y) => x + y);
    
    console.log(total);
}

add(4, 5, 7, 8, 12)
```

## 12. Default Params
- sets default to [] to avoid error
```js
function add(numArray = []) {
    let total = 0;
    numArray.forEach((element) => {
        total += element;
    });
    
    console.log(total);
}

add();
```

## 13. includes()
- check array for item
- not supported by IE
```
let numArray = [1,2,3,4,5];

console.log(numArray.includes(2))
```

## 14. Let & Const
- let and const is blocked scope
- can push items into array/objects for const but can't reassign the name
```js
// works
const example = [];
example.push(5)
console.log(example)

// works
const example = {};
example.firstName = 'Dylan';
console.log(example)

// does not work
const example = [];
example = 3;
console.log(example)
```

## 15. Import & Export
- lets you export data to other files
- helps follow SOLID principles
```js
// exported
export const data = [1,2,3];

// imported
import { data } from './example.js';
let updatedData = data;
updatedData.push(5);
console.log(updatedData)
```

## 16. padStart() & padEnd()
- helps add extra spaces
```
let example = 'Dylan';
console.log(example.padstart(10, 'a'));
console.log(example.padEnd(10, 'a'));
```

## 17. padStart() & padEnd() (challenge)
- padEnd() is ignored
```
let example = 'YouTube.com/CodingTutorials360';

console.log(example.padStart(100).length);
// console.log(example.padEnd(1));
```

## 18. Classes
- classes serve as a scaffold which can have properties and methods
- static methods are methods that you can use without having to instantiate a class first to use that method
- `metaData()` is a getter method that returns data when called
- `extends` lets you inherit properties and methods
- we use `super(type, legs)` to bring in root class properties
```js
class Animal {
  constructor(type, legs) {
    this.type = type;
    this.legs = legs;
  }

  makeNoise(sound = 'loud noise') {
    console.log(sound);
  }

  get metaData() {
    return `Type: ${this.type}, Legs: ${this.legs}`
  }

  static return10() {
    return 10;
  }
}

class Cat extends Animal {
  constructor(type, legs, tail) {
    super(type, legs);
    this.tail = tail;
  }

  // overwriting base makeNoise() method
  makeNoise(sound = 'meow') {
    console.log(sound);
  }
}

// let cat = new Animal('mammal', 4);
// cat.legs = 3;
// cat.makeNoise('Meow');
// console.log(cat);
// console.log(cat.metaData);

// let cat = new Cat('cat', 4);
// cat.makeNoise(); // does 'meow' instead
// console.log(cat.metaData);

// console.log(Animal.return10());
```

## 19. Trailing Commas
- helps prevent errors with trailing commas
- it's there now
```js
function add(param1,){
    const example = {
        name: 'Dylan',
    };
    
    console.log(example)
};

add(2);
```

## 20. Async & Await
- async await cleans up the code versus the .then() chainings
```js
const apiUrl = 'https://fcctop100.herokuapp.com/api/fccusers/top/alltime';

async function getTop100Campers() {
    const response = await fetch(apiUrl);
    const json = await response.json();
    
    console.log(json[0]);
}

// function getTop100Campers() {
//     fetch(apiUrl)
//     .then((r) => r.json())
//     .then((json) => {
//         console.log(json[0])
//     }).catch((error) =>{
//         console.log('failed');
//     });
// }

getTop100Campers();
```

## 21. Async & Await (Challenge)
- we write an async function here simulated with a setTimeout()
```js
function resolveAfter3Seconds() {
  return new Promise(resolve => {
    setTimeout(() => {
      resolve('resolved');
    }, 3000);
  });
}

// resolveAfter3Seconds().then((data) => {
//     console.log(data);
// });

async function getAsyncData() {
    const result = await resolveAfter3Seconds();
    console.log(result);
}

getAsyncData();
```

## 22. Sets
- sets are iterable
- can use forEach or for Of
```js
const exampleSet = new Set([1,1,1,1,2,2,2,2]);

exampleSet.add(5);
exampleSet.add(5); // this gets ignored

console.log(exampleSet);
console.log(exampleSet.size);
console.log(exampleSet.delete(5)); // if item is in the set, returns boolean
console.log(exampleSet.has(5)); // checks if set has an item, returns boolean
exampleSet.clear(); // clears out the set
```
