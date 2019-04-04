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
- `.test()` lets you run the results and returns a boolean
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
- `|` will match more multiple words if you use the `|` operator
```js
let petString = "James has a pet cat.";
let petRegex = /dog|cat|bird|fish/;
let result = petRegex.test(petString);
console.log(result); // returns true because cat is one of the possibilities
```

## 5. Ignore Cases While Matching
- `i` flag to ignore cases when searching
```js
let myString = "freeCodeCamp";
let fccRegex = /freecodecamp/i;
let result = fccRegex.test(myString);
console.log(result); // returns true because the C's case are ignored
```

## 6. Extract Matches
- `.match()` method extract the matches
- returns and array with the matches
```js
let extractStr = "Extract the word 'coding' from this string.";
let codingRegex = /coding/; 
let result = extractStr.match(codingRegex); 

console.log(result);
```

## 7. Find more than the first match
- `g` flag lets you search the whole string
- 1st example: meets exactly the regex without ignoring cases and returns an arr
- 2nd example: ignores case and looks globally to return an array with matches
```js
let testStr = "Repeat, Stop, Repeat, Stop, Repeat";
let ourRegex = /Repeat/g;
const result = testStr.match(ourRegex);
console.log(result); // ['Repeat', 'Repeat', 'Repeat']

let twinkleStar = "Twinkle, twinkle, little star";
let starRegex = /twinkle/ig;
let result2 = twinkleStar.match(starRegex); 
console.log(result2); // ['Twinkle', 'twinkle']
```

## 8. Match Anything with Wildcard Period
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
- `[]` will match only certain characters
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
- `negated character sets` use `^` inside `[]`
- after the `^`, will match everything except those specified
```js
let quoteSample = "3 blind mice.";
let myRegex = /[^0-9aeiou]/ig; 
let result = quoteSample.match(myRegex); 
console.log(result); // [' ', 'b', 'l', 'n', 'd', ' ', 'm', 'c', '.']
```

## 13. Match characters that occur one or more times
- `+`will match the same character that follows after the first
- if there's only 1 character, it will also return that also
```js
let difficultSpelling = "Mississipspi";
let myRegex = /s+/g; 
let result = difficultSpelling.match(myRegex);
console.log(result); // returns ['ss', 'ss', 's'];

let randomSpelling = "abbcdfghiijj";
let randomRegex = /b+|i+/g;
let result2 = randomSpelling.match(randomRegex);
console.log(result2); // ['bb', 'ii']
```

## 14. Match characters that occur one or more times
- `*` will return only if the subsequent characters following the last match charater match, o, like in go
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
let chewieRegex = /Aa*/;
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
let reCriminals = /C+/;
let crowd = 'P1P2P3P4P5P6CCCP7P8P9';
let matchedCriminals = crowd.match(reCriminals);
console.log(matchedCriminals); // returns ["CCC"]
```

## 17. Match Beginning String Patterns
- matches only when `Cal` is at the beginning of the string using `^`
- spaces and other characters do matter
```js
let calRegex = /^Cal/;
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
let lastRegex = /caboose$/;
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
let alphabetRegexV2 = /\w/g;
console.log(quoteSample.match(alphabetRegexV2).length); // 32, includes the underscore also
console.log(quoteSample2.match(alphabetRegexV2).length); // still 32, excludes spaces, exclamation point, and period
```

## 20. Match everything but letters and numbers with `\W`
- `\W` is everything except a-z, 0-9, underscore
- `\W` is the reverse of `\w\`
```js
let quoteSample = "The five boxing wizards jump quickly.";
let nonAlphabetRegex = /\W/g;
let result = quoteSample.match(nonAlphabetRegex).length;
console.log(result); // 6, matches 5 spaces and period
```

## 21. Match All Numbers
- `\d` matches all numbers
```js
let numString = "Your sandwich will be $5.00";
let numRegex = /\d/g;
let result = numString.match(numRegex);
let resultLength = numString.match(numRegex);
console.log(result); // ['5', '0', '0']
console.log(resultLength); // 3
```

## 22. Match all none numbers
- `\D` matches all non-numbers
```js
let numString = "Your sandwich will be $5.00";
let numRegex = /\D/g;
let result = numString.match(numRegex);
let resultLength = numString.match(numRegex);
console.log(result); // returns long array
console.log(resultLength); // 24
```

## 23. Restrict Possible Usernames
- `^[A-Za-z]` matches all letters that start the strings
- `{2,}` requires 2 matches minimum and infinity maximum
- `\d*$` matches any number of digits, `*` means 0 or more numbers, and `$` means at the end
```js
/*
1) If there are numbers, they must be at the end.
2) Letters can be lowercase and uppercase.
3) At least two characters long. Two-letter names can't have numbers.
*/ 

let username = "JackOfAllTrades22";
let userCheck = /^[A-Za-z]{2,}\d*$/;
let result = userCheck.test(username);
console.log(result);
```

## 24. Match whitespace
- `\s` matches for spaces, tabs
```js
let sample = "Whitespace is important in separating words";
let countWhiteSpace = /\s/g;
let result = sample.match(countWhiteSpace);
console.log(result); [' ', ' ', ' ', ' ', ' ',]
```

## 25. Match non-whitespace characters
- `\S\` matches all non-whitespace characters
- needs the `g` flag or will only return the 1st occurence
```js
let sample = "Whitespace is important in separating words";
let countWhiteSpace = /\S/g;
let result = sample.match(countWhiteSpace);
console.log(result);
```

## 26. Specify upper and lower number of matches
- `{}` specifies ranges of lower and uppper bound of matches
- had the number of h's been outside of 3-6 range, `result2` would have returned null
```js
let ohStr = "Ohhh no";
let ohRegex = /Oh{3,6} no/;
let result = ohRegex.test(ohStr);
let result2 = ohStr.match(ohRegex);
console.log(result); // true
console.log(result2); // ['Ohhh no']
```

## 27. Specifying only the lower number of matches
- `{2,}` means 2 to infinity match
```js
let haStr = "Hazzzzah";
let haRegex = /z{4,}/;
let result = haRegex.test(haStr);
const result2 = haStr.match(haRegex);
console.log(result); // true
console.log(result2); // ['zzzz']
```

## 28. Specify exact nubmer of matches
- `{4}` specifies exactly the amount of matches
```js
let timStr = "Timmmmber";
let timRegex = /Tim{4}ber/;
let result = timRegex.test(timStr);
const result2 = timStr.match(timRegex);
console.log(result); // true
console.log(result2); // ['Timmmmber']
```

## 29. Check for All or None
- `?` after a letter means that it may or may not be there
- popular cases of english and british spelling of words
```js
let favWord = "favorite favourite";
let favRegex = /favou?rite/g;
let result = favRegex.test(favWord);
let result2 = favWord.match(favRegex);
console.log(result); // true
console.log(result2); // ['favorite', 'favourite']
```

## 30. Positive and Negative Lookahead
- `(?=\w{5})` checks for exactly 5 characters
- `(?=\D*\d{2})` checks for any number of characters for non digits and also makes sures there are 2 digits at the end
- IE passes for "astronaut22" but fails for "astronaut"
```js
let quit = "quote";
let noquit = "qtewaf";
let quRegex= /q(?=u)/; // checks for u presence RIGHT after q, returns only q
let qRegex = /q(?!u)/; // checks for u non-presence RIGHT after q, returns only q
console.log(quit.match(quRegex)); // Returns ["q"]
console.log(noquit.match(qRegex)); // Returns ["q"]

let sampleWord = "astronaut22";
let pwRegex = /(?=\w{5})(?=\D*\d{2})/;
let result = pwRegex.test(sampleWord);
console.log(result); // true
```

## 31. Reuse patterns using capture groups
- `()` is used as a capture group
- matched examples return the root match first, then the 1st index represented the match to the capture group
- 2nd example: we want specifically 3 42's in a row, no more no less
```js
let repeatStr = "regex regex";
let repeatRegex = /(\w+)\s\1/;
console.log(repeatRegex.test(repeatStr)); // true
console.log(repeatStr.match(repeatRegex)); // ["regex regex", "regex"]

let repeatNum = "42 42 42";
let reRegex = /^(\d+)\s\1\s\1$/;
let result = reRegex.test(repeatNum);
const result2 = repeatNum.match(reRegex);
console.log(result); // true
console.log(result2); // ['42 42 42', '42']
```

## 32. Use capture groups to search and replace
- `.replace()` lets you search and replace
- many ways to do the same thing
- notice in example 2 we can move the capture groups
```js
let wrongText = "The sky is silver.";
let silverRegex = /silver/;
const result = wrongText.replace(silverRegex, "blue");
console.log(result) // "The sky is blue."

const result2 = "Code Camp".replace(/(\w+)\s(\w+)/, '$2 $1');
console.log(result2) // "Camp Code"

let huhText = "This sandwich is good.";
let fixRegex = /good/;
let replaceText = "okey-dokey";
let result3 = huhText.replace(fixRegex, replaceText);
console.log(result3); "This sandwich is okey-dokey."
```

## 33. Remove whitespace from start and end
- we are removing all white spaces
- `^\s+` captures all spaces at start, `\s+$` captures all spaces at end
- we add `|` to check for both and add `g` to check the whole string
```js
let hello = "   Hello, World!  ";
let wsRegex = /^\s+|\s+$/g;
let result = hello.replace(wsRegex, '');
console.log(result); // "Hello, World!"
```

## 34. Regular Expressions Outro
- more projects found in link below
```js
console.log("Congratulations!!!");

// JavaScript Projects: https://www.youtube.com/playlist?list=PLWKjhJtqVAbleDe3_ZA8h3AO2rXar-q2V
```

# Introduction to TypeScript by Dylan C. Israel
- [Course](https://scrimba.com/g/gintrototypescript)

## 1. TypeScript: Introduction
- **WHAT AND WHY?**
1) superset of javascript
2) built by microsoft
3) compiles down to regular javascript
4) tends to be less error prone.
5) Lends to code readability and maintainability

- **TOPICS**
- variable types
- return types
- classes
- enums (string and number)
- interfaces
- intersection types
- access modifiers
- etc.

## 2. Typescript: Variable Types
- lets to specify types for variables
```ts
let example1: boolean = true;

let example2: number = 35;

let example3: string = 'Hello World';
```

## 3. Typescript: Multiple Types
- goal to get to a single type but not always possible
- `|` lets us specifies multiple types
```ts
let example1: boolean | number = 35;
```

## 4. Typescript: Implicit and Explicit Typing
- explicit typing is when you know what type it is an assign the type like `number[]` or `boolean`, see `example1`
- implicit is when you don't declare the type but the computer can grasp what type base on the value you set the example as, see `arrayExample`
```ts
const arrayExample = [1, 3, 4, 5];

let example1: boolean | number = 35;

let example2 = arrayExample.reduce((num1, num2) => num1 + num2);

let example3 = 'Hello world';

let example4: undefined = undefined;

let example5: null = null;
```

## 5. TypeScript: Checking Types
- using `instanceof` is the way to test the type
- using `typeof` is not the same and can only check primitives
- we are checking if `bear` is an instance of the class `Bear`
```ts
import { Bear } from './bear.model'; 

const bear = new Bear(3);

if (bear instanceof Bear) {
    console.log("Hello from TypeScript");
}

```

## 6. TypeScript: Type Assertions
- in cases where you want to cast a variable as a certain type, you can do it as
1) <string>
2) as string

```ts
let definetlyNotAString: any = 'I am a string';

let strLength = (<string> definetlyNotAString).length;
let strLength2 = (definetlyNotAString as string).length;
```

## 7. TypeScript: Arrays
- `any[]` is the default if you don't explicitly say
- `example1`: `string[]` is saying that an array will consist of an array of strings
- `example2`: you can also assign multiple types
- `example3`: is a nested array with booleans
```ts
const example1: string[] = ['Hello World'];

const example2: (number | boolean)[] = [1, 2, true];

const example3: boolean[][] = [ [true, false] ];
```

## 8. TypeScript: Tuples
- tuples exist in python but they are essentially an array with 2 pair items
- the tuple just has to have a string or number, but NOT other types
- Notice `exampleTuple2` and `exampleTuple3` will pass because it matches this scheme
- `exampleTuple4`: once you introduce a boolean for example, it will fail
```ts
const exampleTuple: [string, number] = ['https://www.YouTube.com/CodingTutorials360', 30]; // passes
const exampleTuple2: [string, number] = ['https://www.YouTube.com/CodingTutorials360', 30, 50]; // passes
const exampleTuple3: [string, number] = ['https://www.YouTube.com/CodingTutorials360', 30, 'hello']; // passes
const exampleTuple4: [string, number] = ['https://www.YouTube.com/CodingTutorials360', 30, false]; // fails
```

## 9. TypeScript: Enums
- enums are a way to organize a collection of related value
- it seems that the function accepts the arguments in the order that it is declared in the Age enum
```ts
// index.ts
import { Age } from './age.enum.ts';
import { Names } from './name.enum.ts';

function totalAge(age1: Age, age2: Age) {
  return age1 + age2;
}

// age.enum.ts
export enum Age {
  dylan = 30,
  mother = 21
}

// name.enum.ts
export enum Names {
  mine,
  moms
}
```

## 10. TypeScript: Object
- the `Object` with the capital o is outdated, you should avoid
- you can assign `[]`, `{}`, or `NaN` to object, weird but it works
- can't declare Dylan because we set it as an empty object initially and doesn't have the key to be assigned a value
```ts
const example1: object = undefined;

const example2: Object = NaN;

const example3: {} = {};
example3.firstName = 'Dylan';
```

## 11. TypeScript: Parameters
- You can set default parameters if none declared
```ts
// index.ts
import { Person } from './person.model';

function add(val1: number, val2: number) {
  return val1 + val2;
}

add(1,10);

function sayHello(person: Person) {
  return `Say hello to ${person.firstName}!`;
}

sayHello(new Person({firstName: 'Dylan'}));

// person.model.ts
export class Person {
  firstName: string;
  middleName: string;
  lastName: string;

  constructor(data?: any) {
    this.firstName = data.firstName || 'Dylan';
    this.lastName = data.lastName || 'Israel';
    this.middleName = data.middleName;
  }
}
```

## 12. TypeScript: Return Types
- `: number` after the parameters specifies the return type to number
- can also be of type `: string`, `: never` or `: void`
- `: never` is for when throwing an error for a function
- you can see all 4 of the types being specified in the example
```ts
// index.ts
import { Person } from './person.model';

function add(val1: number, val2: number): number {
    return val1 + val2;
}

function sayHello(person: Person): string {
    return `Say Hello to My Little Friend, ${person.firstName}!`    
}

function voidExample(): void {
    add(1,2);
}

function neverExample(): never {
    throw Error;
}

// person.model.ts
export class Person {
  firstName: string;
  middleName: string;
  lastName: string;

  constructor(data?: any) {
    this.firstName = data.firstName || 'Dylan';
    this.lastName = data.lastName || 'Israel';
    this.middleName = data.middleName;
  }
}
```

## 13. TypeScript: Custom Types
- declaring this `type` line is being phased out
- this is also local only to that file
- most will use interfaces or classes so it can have more global access
```ts
type person = {firstName: string};

const example1: object = undefined;

const example2: Object = NaN;

const example3: person = {firstName: 'Dollan'};

example3.firstName = 'Dylan';
```

## 15. TypeScript: Interfaces
- the standard way to create a type, prefered over the method in the previous lesson
```ts
// index.ts
import { Person } from './person.interface.ts';

const example1: Person = {firstName: 'Dollan', middleName: 'Dollan', lastName: 'Dollan'};

example1.firstName = 'Dylan';
example1.middleName = 'Coding God';
example1.lastName = 'Israel';

// person.interface.ts
export interface Person {
  firstName: string;
  middleName: string;
  lastName: string;
}
```

## . TypeScript: 
-
```ts
```