<details> <summary><strong>1. What is a callback?</strong></summary> A **callback** is a function passed as an argument to another function, which is then executed inside the outer function. It allows you to ensure certain code is executed after an asynchronous operation has completed.
Example:

javascript
Copy code
function greet(name, callback) {
    console.log(`Hello, ${name}`);
    callback();
}

function sayGoodbye() {
    console.log('Goodbye!');
}

greet('Alice', sayGoodbye);
</details>
<details> <summary><strong>2. What is currying in JavaScript?</strong></summary> Currying is a technique where a function is transformed into a sequence of functions, each accepting a single argument.
Example:

javascript
Copy code
function multiply(a) {
    return function (b) {
        return a * b;
    };
}

const multiplyBy2 = multiply(2);
console.log(multiplyBy2(3)); // Output: 6
</details>
<details> <summary><strong>3. What is async/await? Explain with an example.</strong></summary> **Async/await** simplifies working with promises and makes asynchronous code look synchronous.
Example:

javascript
Copy code
async function fetchData() {
    try {
        const response = await fetch('https://api.example.com/data');
        const data = await response.json();
        console.log(data);
    } catch (error) {
        console.error('Error fetching data:', error);
    }
}

fetchData();
</details>
<details> <summary><strong>4. What is a promise in JavaScript?</strong></summary> A **promise** is an object that represents the eventual completion (or failure) of an asynchronous operation.
Example:

javascript
Copy code
const promise = new Promise((resolve, reject) => {
    const success = true;
    if (success) {
        resolve('Promise resolved!');
    } else {
        reject('Promise rejected!');
    }
});

promise
    .then((message) => console.log(message))
    .catch((error) => console.error(error));
</details>
<details> <summary><strong>5. What is Promise.all in JavaScript?</strong></summary> **Promise.all** takes an array of promises and returns a single promise that resolves when all promises in the array resolve or rejects if any promise rejects.
Example:

javascript
Copy code
const promise1 = Promise.resolve(3);
const promise2 = 42;
const promise3 = new Promise((resolve, reject) => {
    setTimeout(resolve, 100, 'foo');
});

Promise.all([promise1, promise2, promise3])
    .then((values) => console.log(values)) // Output: [3, 42, 'foo']
    .catch((error) => console.error(error));
</details>

<details> <summary><strong>6. What is event handling in JavaScript?</strong></summary> Event handling in JavaScript refers to the process of responding to events (like clicks, keypresses, etc.) in the DOM. This is typically done by attaching event listeners to elements.
Example:

javascript
Copy code
document.getElementById('button').addEventListener('click', function () {
    alert('Button clicked!');
});
</details>
<details> <summary><strong>7. Explain call, apply, and bind in JavaScript.</strong></summary>
call(): Invokes a function with a specified this value and arguments provided individually.
apply(): Similar to call, but arguments are provided as an array.
bind(): Returns a new function with a specific this value and arguments bound to it.
Example:

javascript
Copy code
const person = {
    name: 'John',
};

function greet(age, city) {
    console.log(`Hello, my name is ${this.name}. I am ${age} years old and live in ${city}.`);
}

greet.call(person, 30, 'New York'); // Using call
greet.apply(person, [30, 'New York']); // Using apply

const boundGreet = greet.bind(person, 30, 'New York'); // Using bind
boundGreet();
</details>
<details> <summary><strong>8. Explain localStorage and sessionStorage and how to secure both storages.</strong></summary>
localStorage: Stores data with no expiration. Data persists even after the browser is closed.
sessionStorage: Stores data for the session duration. Data is cleared once the tab or browser is closed.
Security Tips:

Avoid storing sensitive information.
Encrypt data before storing.
Use secure origins (HTTPS).
Example:

javascript
Copy code
// localStorage
localStorage.setItem('name', 'Alice');
console.log(localStorage.getItem('name'));

// sessionStorage
sessionStorage.setItem('sessionKey', '12345');
console.log(sessionStorage.getItem('sessionKey'));
</details>
<details> <summary><strong>9. What are web workers?</strong></summary> Web workers allow you to run JavaScript code in the background without affecting the main thread, enhancing performance for intensive tasks.
Example:

Main script:

javascript
Copy code
const worker = new Worker('worker.js');
worker.postMessage('Hello Worker');
worker.onmessage = function (event) {
    console.log('Received from worker:', event.data);
};
Worker script (worker.js):

javascript
Copy code
onmessage = function (event) {
    postMessage(`Worker says: ${event.data}`);
};
</details>
<details> <summary><strong>10. What is a Progressive Web App (PWA)?</strong></summary> A **Progressive Web App (PWA)** is a web application that provides a native app-like experience using modern web technologies. It is: 1. Reliable (works offline using service workers). 2. Fast. 3. Engaging (can be installed on the home screen).
Key features:

Service Workers
Web App Manifest
Example:

json
Copy code
{
  "name": "My PWA",
  "short_name": "PWA",
  "start_url": "/index.html",
  "display": "standalone",
  "background_color": "#ffffff",
  "theme_color": "#000000"
}
</details>
<details> <summary><strong>11. Difference between single-page and multi-page applications.</strong></summary>
Feature	Single Page Application (SPA)	Multi Page Application (MPA)
Navigation	Uses client-side routing.	Uses server-side routing.
Page Reloads	No full reloads; only updates parts	Full page reloads on navigation.
Speed	Faster after initial load.	Slower due to multiple requests.
Examples	React, Angular apps.	Traditional websites like blogs.
</details>
<details> <summary><strong>12. Explain API calls and their process.</strong></summary> An **API call** is a request sent to a server to retrieve or send data. It involves: 1. **Client Request**: Browser or app sends a request. 2. **Server Processing**: Server processes the request and prepares the response. 3. **Response**: Server sends back the response (data, status, etc.).
Example using Fetch API:

javascript
Copy code
fetch('https://api.example.com/data')
    .then((response) => response.json())
    .then((data) => console.log(data))
    .catch((error) => console.error('Error:', error));
</details>

<details> <summary><strong>13. What is microservices architecture?</strong></summary> **Microservices architecture** is an approach to software development where an application is divided into small, independent services. Each service is responsible for a specific functionality and communicates with others via APIs.
Advantages:

Independent Deployment
Scalability
Fault Isolation
Example:
In an e-commerce app, separate microservices can handle:

User authentication
Inventory management
Payment processing
Communication typically happens over REST or messaging protocols like RabbitMQ or Kafka.

</details>
<details> <summary><strong>14. Difference between Map and Reduce in JavaScript.</strong></summary>
Feature	Map	Reduce
Purpose	Creates a new array by transforming each element.	Reduces array to a single value.
Return Type	Array	Any data type.
Use Case	Transform data.	Aggregate data.
Example of Map:

javascript
Copy code
const numbers = [1, 2, 3];
const doubled = numbers.map(num => num * 2);
console.log(doubled); // Output: [2, 4, 6]
Example of Reduce:

javascript
Copy code
const numbers = [1, 2, 3];
const sum = numbers.reduce((acc, num) => acc + num, 0);
console.log(sum); // Output: 6
</details>
<details> <summary><strong>15. What is batching in JavaScript?</strong></summary> **Batching** refers to grouping multiple operations together to optimize performance. For example, React uses batching to combine multiple state updates into a single re-render.
Example:

javascript
Copy code
console.log('Start');
setTimeout(() => console.log('Timeout'), 0);
Promise.resolve().then(() => console.log('Promise'));
console.log('End');

// Output:
// Start
// End
// Promise
// Timeout
Here, operations are batched and processed according to the event loop phases.

</details>
<details> <summary><strong>16. What is a pure function?</strong></summary> A **pure function** always returns the same output for the same input and has no side effects (e.g., modifying external variables).
Example:

javascript
Copy code
function add(a, b) {
    return a + b; // No side effects
}

console.log(add(2, 3)); // Output: 5
</details>
<details> <summary><strong>17. What is callback hell?</strong></summary> **Callback hell** occurs when multiple nested callbacks make the code difficult to read and maintain.
Example:

javascript
Copy code
setTimeout(() => {
    console.log('Step 1');
    setTimeout(() => {
        console.log('Step 2');
        setTimeout(() => {
            console.log('Step 3');
        }, 1000);
    }, 1000);
}, 1000);
Solution: Use Promises or async/await.

</details>
<details> <summary><strong>18. What is closure in JavaScript?</strong></summary> A **closure** is created when a function remembers its lexical scope, even if the function is executed outside that scope.
Example:

javascript
Copy code
function outerFunction(outerVariable) {
    return function innerFunction(innerVariable) {
        console.log(`Outer: ${outerVariable}, Inner: ${innerVariable}`);
    };
}

const closureFunc = outerFunction('OuterValue');
closureFunc('InnerValue'); // Output: Outer: OuterValue, Inner: InnerValue
</details>
<details> <summary><strong>19. What is hoisting in JavaScript?</strong></summary> **Hoisting** is JavaScript's behavior of moving variable and function declarations to the top of their scope before code execution.
Example:

javascript
Copy code
console.log(hoistedVar); // Output: undefined
var hoistedVar = 5;

hoistedFunc(); // Output: Hoisted function
function hoistedFunc() {
    console.log('Hoisted function');
}
Note: let and const are also hoisted but are not initialized.

</details>
<details> <summary><strong>20. Explain let, const, and var.</strong></summary>
Feature	var	let	const
Scope	Function	Block	Block
Redeclaration	Allowed	Not allowed	Not allowed
Reassignment	Allowed	Allowed	Not allowed
Hoisting	Yes (initialized as undefined)	Yes (in Temporal Dead Zone)	Yes (in Temporal Dead Zone)
Example:

javascript
Copy code
var x = 1; // Function scope
let y = 2; // Block scope
const z = 3; // Cannot reassign
</details>
<details> <summary><strong>21. What is the event loop?</strong></summary> The **event loop** is a mechanism in JavaScript that handles the execution of synchronous and asynchronous code.
Example:

javascript
Copy code
console.log('Start');

setTimeout(() => console.log('Timeout'), 0);

Promise.resolve().then(() => console.log('Promise'));

console.log('End');

// Output:
// Start
// End
// Promise
// Timeout
</details>

<details> <summary><strong>22. Write a function to check if a string is a palindrome in JavaScript.</strong></summary>
Palindrome: A string that reads the same forward and backward (e.g., "madam").

Example Function:

javascript
Copy code
function isPalindrome(str) {
    const reversed = str.split('').reverse().join('');
    return str === reversed;
}

console.log(isPalindrome('madam')); // Output: true
console.log(isPalindrome('hello')); // Output: false
</details>
<details> <summary><strong>23. Write a function to get duplicate values from an array and their count in JavaScript.</strong></summary>
Example Function:

javascript
Copy code
function findDuplicates(arr) {
    const count = {};
    const duplicates = {};

    arr.forEach(item => {
        count[item] = (count[item] || 0) + 1;
    });

    for (let key in count) {
        if (count[key] > 1) {
            duplicates[key] = count[key];
        }
    }

    return duplicates;
}

const numbers = [1, 2, 3, 1, 2, 4, 5];
console.log(findDuplicates(numbers)); // Output: { '1': 2, '2': 2 }
</details>
<details> <summary><strong>24. What is event delegation in JavaScript?</strong></summary> **Event Delegation** is a technique to handle events efficiently by attaching a single event listener to a parent element that monitors events for its child elements.
Example:

javascript
Copy code
document.getElementById('parent').addEventListener('click', function (event) {
    if (event.target && event.target.nodeName === 'BUTTON') {
        console.log('Button clicked:', event.target.textContent);
    }
});

// HTML:
// <div id="parent">
//     <button>Button 1</button>
//     <button>Button 2</button>
// </div>
</details>
<details> <summary><strong>25. How to call multiple APIs at the same time?</strong></summary> To call multiple APIs simultaneously, use `Promise.all()`.
Example:

javascript
Copy code
const fetch1 = fetch('https://api.example.com/data1');
const fetch2 = fetch('https://api.example.com/data2');

Promise.all([fetch1, fetch2])
    .then(responses => Promise.all(responses.map(res => res.json())))
    .then(data => {
        console.log('Data 1:', data[0]);
        console.log('Data 2:', data[1]);
    })
    .catch(error => console.error('Error:', error));
</details>
<details> <summary><strong>26. What is the difference between synchronous and asynchronous code?</strong></summary>
Feature	Synchronous Code	Asynchronous Code
Execution	Runs line by line.	Can run tasks in parallel.
Blocking	Blocks further execution.	Non-blocking.
Example	Regular functions.	Callbacks, Promises, async/await.
Example:

javascript
Copy code
// Synchronous
console.log('Start');
console.log('End');

// Asynchronous
console.log('Start');
setTimeout(() => console.log('Async Task'), 1000);
console.log('End');
</details>
<details> <summary><strong>27. What are the rest and spread operators in JavaScript?</strong></summary> - **Rest (`...`)**: Collects all remaining elements into an array. - **Spread (`...`)**: Spreads an array or object into individual elements.
Example:

javascript
Copy code
// Rest
function sum(...numbers) {
    return numbers.reduce((total, num) => total + num, 0);
}
console.log(sum(1, 2, 3)); // Output: 6

// Spread
const arr1 = [1, 2, 3];
const arr2 = [...arr1, 4, 5];
console.log(arr2); // Output: [1, 2, 3, 4, 5]
</details>
<details> <summary><strong>28. Remove duplicate elements from an array.</strong></summary>
Example Function:

javascript
Copy code
const numbers = [10, 20, 30, 40, 10, 20, 30, 50];
const uniqueNumbers = [...new Set(numbers)];
console.log(uniqueNumbers); // Output: [10, 20, 30, 40, 50]
</details>
<details> <summary><strong>29. What is event emitter in Node.js?</strong></summary> The **EventEmitter** class in Node.js is used to create and handle custom events.
Example:

javascript
Copy code
const EventEmitter = require('events');
const emitter = new EventEmitter();

emitter.on('event', (message) => {
    console.log('Event triggered:', message);
});

emitter.emit('event', 'Hello, EventEmitter!');
</details>
<details> <summary><strong>30. Write a program to swap two strings after every two characters.</strong></summary>
Example Function:

javascript
Copy code
function swapStrings(str1, str2) {
    let result = '';
    const maxLength = Math.max(str1.length, str2.length);

    for (let i = 0; i < maxLength; i += 2) {
        result += str1.slice(i, i + 2) + str2.slice(i, i + 2);
    }

    return result;
}

const str1 = 'ABCDE';
const str2 = 'FGHIJ';
console.log(swapStrings(str1, str2)); // Output: "ABFGCDHIJ"
</details>
<details> <summary><strong>31. Write a function to count each string occurrence in a sentence.</strong></summary>
Example Function:

javascript
Copy code
function countOccurrences(sentence) {
    const words = sentence.split(' ');
    const wordCount = {};

    words.forEach(word => {
        wordCount[word] = (wordCount[word] || 0) + 1;
    });

    return wordCount;
}

const sentence = "my name is Rohit my name is unique";
console.log(countOccurrences(sentence));
// Output: { my: 2, name: 2, is: 2, Rohit: 1, unique: 1 }
</details>
<details> <summary><strong>32. Call an API in plain JavaScript and implement a list of records in HTML.</strong></summary>
Example:

html
Copy code
<!DOCTYPE html>
<html>
<head>
    <title>API Call Example</title>
</head>
<body>
    <ul id="recordList"></ul>

    <script>
        fetch('https://jsonplaceholder.typicode.com/posts')
            .then(response => response.json())
            .then(data => {
                const list = document.getElementById('recordList');
                data.forEach(record => {
                    const listItem = document.createElement('li');
                    listItem.textContent = record.title;
                    list.appendChild(listItem);
                });
            })
            .catch(error => console.error('Error:', error));
    </script>
</body>
</html>
</details>
<details> <summary><strong>33. What is the difference between null and undefined?</strong></summary>
Feature	null	undefined
Type	Object	Undefined
Meaning	Explicitly set to "no value".	Variable declared but not initialized.
Use Case	Intentional absence of value.	Default value for uninitialized variables.
Example:

javascript
Copy code
let a = null; // Explicitly set to null
let b;        // Declared but not initialized

console.log(a); // Output: null
console.log(b); // Output: undefined
</details>
<details> <summary><strong>34. What is an Immediately Invoked Function Expression (IIFE)?</strong></summary> An **IIFE** is a function that runs immediately after it is defined.
Example:

javascript
Copy code
(function () {
    console.log('IIFE executed!');
})();

// Output: IIFE executed!
Use Case: Avoid polluting the global scope.

</details>
<details> <summary><strong>35. What is the difference between slice() and splice() in JavaScript?</strong></summary>
Feature	slice()	splice()
Purpose	Extracts a portion of an array.	Modifies the original array by adding/removing elements.
Modifies Original?	No	Yes
Return Value	A new array.	The removed elements.
Example of slice():

javascript
Copy code
const arr = [1, 2, 3, 4];
console.log(arr.slice(1, 3)); // Output: [2, 3]
console.log(arr); // Original array remains unchanged
Example of splice():

javascript
Copy code
const arr = [1, 2, 3, 4];
console.log(arr.splice(1, 2)); // Output: [2, 3]
console.log(arr); // Modified array: [1, 4]
</details>
<details> <summary><strong>36. What is Object.freeze() in JavaScript?</strong></summary> **Object.freeze()** prevents modifications to an object, making it immutable.
Example:

javascript
Copy code
const obj = { name: 'Alice' };
Object.freeze(obj);

obj.name = 'Bob'; // Will not change the value
console.log(obj.name); // Output: Alice
Note: Nested objects are not frozen by default.

</details>
<details> <summary><strong>37. What is the purpose of the setTimeout() function?</strong></summary> **setTimeout()** executes a function after a specified delay.
Syntax:

javascript
Copy code
setTimeout(function, delay);
Example:

javascript
Copy code
setTimeout(() => {
    console.log('Executed after 2 seconds');
}, 2000);
</details>
<details> <summary><strong>38. What is the difference between == and === in JavaScript?</strong></summary>
Operator	== (Equality)	=== (Strict Equality)
Type Check	Converts operands to the same type.	Does not perform type conversion.
Example	'5' == 5 // true	'5' === 5 // false
Example:

javascript
Copy code
console.log(5 == '5');  // Output: true
console.log(5 === '5'); // Output: false
</details>
<details> <summary><strong>39. What is the purpose of the finally block in JavaScript?</strong></summary> The **finally** block is executed after the try and catch blocks, regardless of the outcome.
Example:

javascript
Copy code
try {
    console.log('Try block');
    throw new Error('An error occurred');
} catch (error) {
    console.log('Catch block:', error.message);
} finally {
    console.log('Finally block executed');
}

// Output:
// Try block
// Catch block: An error occurred
// Finally block executed
</details>
<details> <summary><strong>40. What is the difference between Object.keys() and Object.values()?</strong></summary>
Method	Object.keys()	Object.values()
Purpose	Returns an array of keys.	Returns an array of values.
Example	Object.keys({ a: 1, b: 2 }) => ['a', 'b']	Object.values({ a: 1, b: 2 }) => [1, 2]
Example:

javascript
Copy code
const obj = { name: 'Alice', age: 25 };

console.log(Object.keys(obj));   // Output: ['name', 'age']
console.log(Object.values(obj)); // Output: ['Alice', 25]
</details>

<details> <summary><strong>41. What is the difference between for...in and for...of loops?</strong></summary>
Feature	for...in	for...of
Purpose	Iterates over enumerable properties (keys) of an object.	Iterates over iterable objects (values).
Use Case	Used for objects.	Used for arrays, strings, and other iterables.
Example	Object keys.	Array elements or string characters.
Example of for...in:

javascript
Copy code
const obj = { name: 'Alice', age: 25 };
for (let key in obj) {
    console.log(key); // Output: 'name', 'age'
}
Example of for...of:

javascript
Copy code
const arr = ['a', 'b', 'c'];
for (let value of arr) {
    console.log(value); // Output: 'a', 'b', 'c'
}
</details>
<details> <summary><strong>42. What is Math.random() and how is it used?</strong></summary> **Math.random()** generates a random floating-point number between 0 (inclusive) and 1 (exclusive).
Example:

javascript
Copy code
console.log(Math.random()); // Output: Random number between 0 and 1

// Generate random integer between 1 and 10
function getRandomInt(min, max) {
    return Math.floor(Math.random() * (max - min + 1)) + min;
}
console.log(getRandomInt(1, 10)); // Output: Random number between 1 and 10
</details>
<details> <summary><strong>43. What is Object.assign() in JavaScript?</strong></summary> **Object.assign()** is used to copy properties from one or more source objects to a target object.
Example:

javascript
Copy code
const target = { a: 1 };
const source = { b: 2, c: 3 };

Object.assign(target, source);
console.log(target); // Output: { a: 1, b: 2, c: 3 }
Use Case: Merge objects or create a shallow copy.

</details>
<details> <summary><strong>44. What are template literals in JavaScript?</strong></summary> Template literals allow embedded expressions and multi-line strings using backticks (\`\`).
Example:

javascript
Copy code
const name = 'Alice';
const greeting = `Hello, ${name}!`; // Embedded expression
console.log(greeting); // Output: Hello, Alice!

const multiline = `This is
a multi-line string.`;
console.log(multiline);
// Output:
// This is
// a multi-line string.
</details>
<details> <summary><strong>45. What are higher-order functions in JavaScript?</strong></summary> A **higher-order function** is a function that takes another function as an argument or returns a function.
Example:

javascript
Copy code
function higherOrderFunction(callback) {
    callback();
}

function greet() {
    console.log('Hello!');
}

higherOrderFunction(greet); // Output: Hello!
Common Examples:

map(), filter(), reduce() are higher-order functions.
</details>
<details> <summary><strong>46. What is the difference between a shallow copy and a deep copy?</strong></summary>
Type	Shallow Copy	Deep Copy
Definition	Copies only the first layer of properties.	Copies all nested levels.
Effect	Changes in nested objects affect the copy.	Fully independent copy.
Shallow Copy Example:

javascript
Copy code
const obj = { name: 'Alice', address: { city: 'Paris' } };
const shallowCopy = { ...obj };

shallowCopy.address.city = 'London';
console.log(obj.address.city); // Output: 'London' (nested object shared)
Deep Copy Example:

javascript
Copy code
const obj = { name: 'Alice', address: { city: 'Paris' } };
const deepCopy = JSON.parse(JSON.stringify(obj));

deepCopy.address.city = 'London';
console.log(obj.address.city); // Output: 'Paris' (independent copy)
</details>
<details> <summary><strong>47. What is the instanceof operator in JavaScript?</strong></summary> **instanceof** checks whether an object is an instance of a specific constructor.
Example:

javascript
Copy code
class Person {}
const alice = new Person();

console.log(alice instanceof Person); // Output: true
console.log(alice instanceof Object); // Output: true
console.log(alice instanceof Array); // Output: false
</details>
<details> <summary><strong>48. What are JavaScript generators?</strong></summary> A **generator** is a function that can pause and resume its execution.
Syntax:

javascript
Copy code
function* generatorFunction() {
    yield 1;
    yield 2;
    yield 3;
}
Example:

javascript
Copy code
function* numbers() {
    yield 1;
    yield 2;
    yield 3;
}

const gen = numbers();
console.log(gen.next().value); // Output: 1
console.log(gen.next().value); // Output: 2
console.log(gen.next().value); // Output: 3
</details>
<details> <summary><strong>49. What is Object.seal() in JavaScript?</strong></summary> **Object.seal()** prevents adding or deleting properties but allows modification of existing properties.
Example:

javascript
Copy code
const obj = { name: 'Alice' };
Object.seal(obj);

obj.name = 'Bob'; // Allowed
obj.age = 25;     // Not allowed
delete obj.name;  // Not allowed

console.log(obj); // Output: { name: 'Bob' }
</details>
<details> <summary><strong>50. What is the new.target in JavaScript?</strong></summary> **new.target** refers to the constructor invoked by the `new` keyword.
Example:

javascript
Copy code
function Person() {
    if (!new.target) {
        throw new Error('Must be called with new');
    }
    this.name = 'Alice';
}

const obj = new Person(); // Works
const obj2 = Person();    // Error: Must be called with new
</details>

<details> <summary><strong>51. What is Symbol.iterator in JavaScript?</strong></summary> The **Symbol.iterator** is a built-in symbol used to define the default iterator for an object. It enables objects to be iterable.
Example:

javascript
Copy code
const iterableObject = {
    data: [1, 2, 3],
    [Symbol.iterator]() {
        let index = 0;
        const self = this;
        return {
            next() {
                if (index < self.data.length) {
                    return { value: self.data[index++], done: false };
                } else {
                    return { done: true };
                }
            }
        };
    }
};

for (const value of iterableObject) {
    console.log(value); // Output: 1, 2, 3
}
</details>
<details> <summary><strong>52. What is the purpose of console.log() in JavaScript?</strong></summary> The **console.log()** method is used to print messages, variables, or objects to the browser console for debugging purposes.
Example:

javascript
Copy code
const name = 'Alice';
console.log('Hello, ' + name); // Output: Hello, Alice

const obj = { key: 'value' };
console.log(obj); // Output: { key: 'value' }
</details>
<details> <summary><strong>53. What is a thunk in JavaScript?</strong></summary> A **thunk** is a function that wraps an expression to delay its evaluation. It is often used in asynchronous programming.
Example:

javascript
Copy code
const fetchData = (url) => () => fetch(url);

const thunk = fetchData('https://jsonplaceholder.typicode.com/posts/1');
thunk().then(response => response.json()).then(data => console.log(data));
</details>
<details> <summary><strong>54. What is the difference between a class and a constructor function in JavaScript?</strong></summary>
Feature	Class	Constructor Function
Syntax	Introduced in ES6 with the class keyword.	ES5 and earlier used functions for constructors.
Prototype-based?	Yes, but with cleaner syntax.	Yes.
Extensibility	Uses extends and super for inheritance.	Inheritance through prototype.
Class Example:

javascript
Copy code
class Person {
    constructor(name) {
        this.name = name;
    }
}

const alice = new Person('Alice');
console.log(alice.name); // Output: Alice
Constructor Function Example:

javascript
Copy code
function Person(name) {
    this.name = name;
}

const alice = new Person('Alice');
console.log(alice.name); // Output: Alice
</details>
<details> <summary><strong>55. What is the Promise.race() method?</strong></summary> The **Promise.race()** method returns a promise that resolves or rejects as soon as one of the promises in the iterable resolves or rejects.
Example:

javascript
Copy code
const promise1 = new Promise(resolve => setTimeout(() => resolve('First!'), 1000));
const promise2 = new Promise(resolve => setTimeout(() => resolve('Second!'), 500));

Promise.race([promise1, promise2]).then(result => console.log(result));
// Output: 'Second!' (The first to resolve)
</details>
<details> <summary><strong>56. What is the difference between forEach() and map()?</strong></summary>
Feature	forEach()	map()
Purpose	Iterates over an array without returning a new array.	Creates and returns a new array with transformed values.
Return Value	Undefined	A new array.
forEach Example:

javascript
Copy code
const arr = [1, 2, 3];
arr.forEach(num => console.log(num * 2)); // Output: 2, 4, 6
console.log(arr); // Original array remains unchanged
map Example:

javascript
Copy code
const arr = [1, 2, 3];
const newArr = arr.map(num => num * 2);
console.log(newArr); // Output: [2, 4, 6]
console.log(arr);    // Original array remains unchanged
</details>
<details> <summary><strong>57. What is a polyfill in JavaScript?</strong></summary> A **polyfill** is a piece of code that implements functionality that is not natively supported by some browsers.
Example: Polyfill for Array.prototype.includes():

javascript
Copy code
if (!Array.prototype.includes) {
    Array.prototype.includes = function (element) {
        return this.indexOf(element) !== -1;
    };
}

const arr = [1, 2, 3];
console.log(arr.includes(2)); // Output: true
</details>
<details> <summary><strong>58. What are JavaScript modules?</strong></summary> **Modules** are reusable pieces of code that can be exported from one file and imported into another.
Example of Exporting a Module (math.js):

javascript
Copy code
export function add(a, b) {
    return a + b;
}
Example of Importing a Module (main.js):

javascript
Copy code
import { add } from './math.js';
console.log(add(2, 3)); // Output: 5
Note: Use the type="module" attribute in the <script> tag to enable modules.

html
Copy code
<script type="module" src="main.js"></script>
</details>
<details> <summary><strong>59. What is memoization in JavaScript?</strong></summary> **Memoization** is an optimization technique to cache the results of expensive function calls and reuse them.
Example:

javascript
Copy code
function memoize(fn) {
    const cache = {};
    return function (...args) {
        const key = JSON.stringify(args);
        if (cache[key]) {
            return cache[key];
        }
        const result = fn(...args);
        cache[key] = result;
        return result;
    };
}

function slowFunction(num) {
    console.log('Expensive calculation');
    return num * num;
}

const memoizedFunction = memoize(slowFunction);
console.log(memoizedFunction(5)); // Output: Expensive calculation, 25
console.log(memoizedFunction(5)); // Output: 25 (from cache)
</details>
<details> <summary><strong>60. What is the difference between slice() and substring() in JavaScript?</strong></summary>
Method	slice()	substring()
Negative Indexes	Supports negative indexes.	Does not support negative indexes.
Usage	slice(start, end)	substring(start, end)
Example of slice():

javascript
Copy code
const str = 'Hello, World!';
console.log(str.slice(0, 5)); // Output: Hello
console.log(str.slice(-6));  // Output: World!
Example of substring():

javascript
Copy code
const str = 'Hello, World!';
console.log(str.substring(0, 5)); // Output: Hello
console.log(str.substring(5, 0)); // Output: Hello (reversed arguments are swapped)
</details>

<details> <summary><strong>61. What is the event loop in JavaScript?</strong></summary> The **event loop** is a mechanism in JavaScript that handles asynchronous operations. It constantly checks the call stack for any function to execute and then checks the event queue for tasks waiting to be executed once the call stack is empty.
Example:

javascript
Copy code
console.log('Start');

setTimeout(() => {
    console.log('Timeout');
}, 0);

console.log('End');
Output:

sql
Copy code
Start
End
Timeout
In this example, despite the setTimeout having a delay of 0ms, the Timeout log is printed last because it’s placed in the event queue after the synchronous code (the first two logs) is completed.

</details>
<details> <summary><strong>62. What is event delegation in JavaScript?</strong></summary> **Event delegation** is a technique where you assign a single event listener to a parent element rather than multiple listeners to each child element. This method uses event bubbling to catch events from child elements.
Example:

javascript
Copy code
const parentDiv = document.getElementById('parent');
parentDiv.addEventListener('click', (event) => {
    if (event.target && event.target.matches('button.classname')) {
        console.log('Button clicked:', event.target);
    }
});

const button1 = document.createElement('button');
button1.textContent = 'Button 1';
button1.classList.add('classname');
parentDiv.appendChild(button1);
In this example, we add a listener to parentDiv and delegate the click event to button elements inside it. This avoids adding an event listener to each individual button.

</details>
<details> <summary><strong>63. What is a higher-order function in JavaScript?</strong></summary> A **higher-order function** is a function that either takes one or more functions as arguments, returns a function as its result, or both.
Example:

javascript
Copy code
function higherOrderFunction(fn) {
    return function(x) {
        return fn(x) + 1;
    };
}

const addOne = higherOrderFunction(x => x + 2);
console.log(addOne(3)); // Output: 6 (3 + 2 + 1)
In this example, the function higherOrderFunction returns a new function, making it a higher-order function.

</details>
<details> <summary><strong>64. What is the difference between null and undefined?</strong></summary>
Feature	null	undefined
Type	It is an object.	It is a primitive value.
Assignment	null is explicitly assigned to indicate no value or object.	undefined is a default value for uninitialized variables.
Example	let a = null;	let b; console.log(b); // Output: undefined
Example:

javascript
Copy code
let x = null;
let y;
console.log(x); // Output: null
console.log(y); // Output: undefined
</details>
<details> <summary><strong>65. What is the difference between == and === in JavaScript?</strong></summary> The **`==`** operator compares two values for equality, but it allows type coercion, while the **`===`** operator compares both value and type, without type coercion.
Example:

javascript
Copy code
console.log(5 == '5');  // Output: true (due to type coercion)
console.log(5 === '5'); // Output: false (no type coercion)
</details>
<details> <summary><strong>66. What is the purpose of the finally block in JavaScript?</strong></summary> The **finally** block is always executed after the **try** and **catch** blocks, regardless of whether an exception is thrown or not. It's typically used for cleanup actions like closing connections.
Example:

javascript
Copy code
try {
    const result = riskyFunction();
    console.log(result);
} catch (error) {
    console.log('Error caught:', error);
} finally {
    console.log('This will always execute');
}
Even if riskyFunction() throws an error, the finally block will still run.

</details>
<details> <summary><strong>67. What is the purpose of the `eval()` function in JavaScript?</strong></summary> The **eval()** function evaluates or executes a string of JavaScript code. It can execute any valid JavaScript code, which could be a security risk if the string contains user-input code.
Example:

javascript
Copy code
const expression = '2 + 2';
console.log(eval(expression)); // Output: 4
Note: Use eval() cautiously, as it can introduce security vulnerabilities.

</details>
<details> <summary><strong>68. What is Object.freeze() in JavaScript?</strong></summary> The **Object.freeze()** method freezes an object, making it immutable. This means properties cannot be added, removed, or modified.
Example:

javascript
Copy code
const obj = { name: 'Alice', age: 25 };
Object.freeze(obj);
obj.age = 26; // Will not work
console.log(obj.age); // Output: 25 (no changes)
</details>
<details> <summary><strong>69. What is Object.seal() in JavaScript?</strong></summary> The **Object.seal()** method prevents the addition or removal of properties, but it allows modifications to existing properties.
Example:

javascript
Copy code
const obj = { name: 'Alice', age: 25 };
Object.seal(obj);
obj.age = 26; // Allowed (value can change)
delete obj.age; // Not allowed (property can't be deleted)
console.log(obj.age); // Output: 26
</details>
<details> <summary><strong>70. What is the difference between slice() and splice() in JavaScript?</strong></summary>
Method	slice()	splice()
Purpose	Extracts a portion of an array without modifying the original array.	Changes the content of an array by adding or removing elements.
Return Value	Returns a new array.	Modifies the array and returns the removed elements.
Parameters	slice(start, end)	splice(start, deleteCount, item1, item2, ...)
Example of slice():

javascript
Copy code
const arr = [1, 2, 3, 4, 5];
const slicedArr = arr.slice(1, 4);
console.log(slicedArr); // Output: [2, 3, 4]
Example of splice():

javascript
Copy code
const arr = [1, 2, 3, 4, 5];
arr.splice(2, 2, 6, 7);  // Removes 2 elements and adds 6, 7
console.log(arr); // Output: [1, 2, 6, 7, 5]
</details>
