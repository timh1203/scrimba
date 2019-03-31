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

# Learn Regular Expressions by Free Code Camp

## 1. Regular Expressions Intro
- helps define a search pattern for a string
- we are doing RegEx in Javascript
- part of FCC curriculum but this is a standalone on Scrimba

## 2. Using the Test Method
- test lets you run the results and returns a boolean
- test for `Hello` will NOT work for `hello`
- tests are case-sensitive
```js
let sentence = "The dog chased the cat."
let regex = /the/

let myString = "Hello, World!";
let myRegex = /Hello/;
let result = myRegex.test(myString);
console.log(result); // returns true
```

## 3. Match Literal Strings
- again, it is case sensitive
```js
let waldoIsHiding = "Somewhere Waldo is hiding in this text.";
let waldoRegex = /Waldo/;
let result = waldoRegex.test(waldoIsHiding);
console.log(result); // returns true
```

## 4. Match a Literal String with Different Possibilities
- will match more multiple words if you use the `|` operator
```js
let petString = "James has a pet cat.";
let petRegex = /dog|cat|bird|fish/;
let result = petRegex.test(petString);
console.log(result); // returns true because cat is one of the possibilities
```

## 5. Ignore Cases While Matching
- we use the `i` flag to ignore cases when searching
```js
let myString = "freeCodeCamp";
let fccRegex = /freecodecamp/i;
let result = fccRegex.test(myString);
console.log(result); // returns true because the C's case are ignored
```

## 6. Extract Matches
- we can extract the matches with `.match()` method
- returns and array with the matches
```js
let extractStr = "Extract the word 'coding' from this string.";
let codingRegex = /coding/; 
let result = extractStr.match(codingRegex); 

console.log(result);
```

## 7. Find more than the first match
- 1st example: meets exactly the regex without ignoring cases and returns an arr
- 2nd example: ignores case and looks globally to return an array with matches
```js
let testStr = "Repeat, Stop, Repeat, Stop, Repeat";
let ourRegex = /Repeat/g;
const result = testStr.match(ourRegex);
console.log(result);

let twinkleStar = "Twinkle, twinkle, little star";
let starRegex = /twinkle/ig;
let result2 = twinkleStar.match(starRegex); 
console.log(result2);
```

## 8. Match Anythign with Wildcard Period
- `.` is a wildcard character in regex
- 1st example: match does not look for characters before or after the match
- 2nd example: will look for fun, sun, run, nun, etc.
```js
let humStr = "I'll hum a song";
let hugStr = "Bear hugging";
let huRegex = /hu./;
const result = humStr.match(huRegex); 
const result2 = hugStr.match(huRegex); 
console.log(result); // Returns ["hum"]
console.log(result2); // Returns ["hug"] only, not "hugging"

let exampleStr = "Let's have fun with regular expressions! imrunning";
let unRegex = /.un/g;
let result3 = unRegex.test(exampleStr);
const result4 = exampleStr.match(unRegex);
console.log(result3); // returns true
console.log(result4); // returns ['fun', 'run']
```

## 9. Match Single Character with Multiple Possibilities
- will match only certain characters also if put in `[]`
```js
let bgRegex = /b[aiu]g/;
let quoteSample = "Beware of bugs in the above code; I have only proved it correct, not tried it.";
let vowelRegex = /b[aeiou]/ig;
let result = quoteSample.match(vowelRegex);
console.log(result); // returns ['Be', 'bu', 'bo']
```

## 10. Match Letters of the Alphabet
- matches every letter in the string
- returns an array with each single letter as an item
```js
let quoteSample = "The quick brown fox jumps over the lazy dog.";
let alphabetRegex = /[a-z]/ig; 
let result = quoteSample.match(alphabetRegex); 

console.log(result);
```

## 11. Match Numbers and Letters of the Alphabet
- returns an array of matching numbers and letters in the regex
```js
let quoteSample = "Blueberry 3.141592653s are delicious.";
let myRegex = /[2-6h-s]/ig;
let result = quoteSample.match(myRegex); 

console.log(result); // returns each matching letter and number
```

## 12. Match characters that occur one or more times with `^` operator
- `negated character sets` use `^`
- will match everything except after the `^`
```js
let quoteSample = "3 blind mice.";
let myRegex = /[^0-9aeiou]/ig; 
let result = quoteSample.match(myRegex); 

console.log(result);
```

## 13. Match characters that occur one or more times with `+` operator
- will match the same character that follows after the first
- if there's only 1 character, it will also return that also
```js
let difficultSpelling = "Mississipspi";
let myRegex = /s+/g; 
let result = difficultSpelling.match(myRegex);
console.log(result); // returns ['ss', 'ss', 's'];

let randomSpelling = "abbcdfghiijj";
let randomRegex = /b+|i+/g;
let result2 = randomSpelling.match(randomRegex);
console.log(result2);
```

## 14. Match characters that occur one or more times with `+` operator
- will return only if the subsequent characters following the last match charater match like in go
- we can do this with the `*`, meaning the number of occurence tags
```js
let soccerWord = "gooooooooal!";
let gPhrase = "gut feeling";
let oPhrase = "over the moon";
let goRegex = /go*/;
console.log(soccerWord.match(goRegex)); // Returns ["goooooooo"]
console.log(gPhrase.match(goRegex)); // Returns ["g"]
console.log(oPhrase.match(goRegex)); // Returns null

let chewieQuote = "Aaaaaaaaaaaaaaaarrrgh!";
let chewieRegex = /Aa*/; // Change this line
let result4 = chewieQuote.match(chewieRegex);
console.log(result4); // returns ["Aaaaaaaaaaaaaaaa"]
```

## 15. Find Characters with lazy matching and `?` operator
- regex patterns defaults to "greedy" matching
- but what if we want to do a "lazy" match
- we can do this with the `?`, it will cut off at the first ending
- 1st example: would return "titani" without the `?`, but we want it to terminate at the "ti"
- 2nd example: we want to return "<h1>" only
```js
let string = "titanic";
let regex = /t[a-z]*?i/; 
console.log(string.match(regex)); // returns ['ti']

let text = "<h1>Winter is coming</h1>";
let myRegex = /<.*?>/; 
let result = text.match(myRegex); // returns ['<h1>']

console.log(result);
```

## 16. Find Characters with lazy matching (challenge)
- this is a challenge to find the criminals at once represented by "C"
```js
let reCriminals = /C+/; // Change this line
let crowd = 'P1P2P3P4P5P6CCCP7P8P9';
let matchedCriminals = crowd.match(reCriminals);
console.log(matchedCriminals); // returns ["CCC"]
```

## 17. Match Beginning String Patterns
- matches only when `Cal` is at the beginning of the string using `^`
- spaces and other characters do matter
```js
let calRegex = /^Cal/; // Change this line
let rickyAndCal = "Cal and Rickyboth like racing.";
let rickyAndCal2 = "and Ricky Cal both like racing.";
let rickyAndCal3 = " Cal Ricky Cal both like racing.";
let result = calRegex.test(rickyAndCal);
let result2 = calRegex.test(rickyAndCal2);
let result3 = calRegex.test(rickyAndCal3);
console.log(result); // returns true
console.log(result2); // returns false
console.log(result3); // returns false, spaces also matter
```

## 18. Match Ending String Patterns
- matches only when `caboose` is at the end of the string using `$`
- spaces and other characters do matter
```js
let lastRegex = /caboose$/; // Change this line
let caboose = "The last car on a train is the caboose";
let caboose2 = "The last car on a train is the caboose?";
console.log(lastRegex.test(caboose)); // true
console.log(lastRegex.test(caboose2)); // false, last character does matter
```

## 19. Match all letters and numbers with `\w`
- short hand character class called `\w` to match the alphabet, 0-9, and underscore instead of using `[a-z]`
- excludes spaces and period
```js
let quoteSample = "The five boxing wizards jump quickly._";
let quoteSample2 = "The five boxing! wizards? jump; quickly._";
let alphabetRegexV2 = /\w/g; // Change this line
console.log(quoteSample.match(alphabetRegexV2).length); // 32, includes the underscore also
console.log(quoteSample2.match(alphabetRegexV2).length); // still 32, excludes spaces, exclamation point, and period
```

## 20. Match everything but letters and numbers with `\W`
- `\W` is everything except a-z, 0-9, underscore
- `\W` is the reverse of `\w\`
```js
let quoteSample = "The five boxing wizards jump quickly.";
let nonAlphabetRegex = /\W/g; // Change this line
let result = quoteSample.match(nonAlphabetRegex).length;
console.log(result); // 6, matches 5 spaces and period
```

## 
-
```js
```