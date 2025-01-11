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
<details> <summary><strong>71. What is the `setTimeout()` function in JavaScript?</strong></summary> The **setTimeout()** function is used to execute a specified function or code after a delay in milliseconds.
Example:

javascript
Copy code
setTimeout(() => {
    console.log('This message appears after 2 seconds');
}, 2000);
In this example, the message will appear after 2 seconds.

Note: The setTimeout function returns a unique ID that can be used with clearTimeout() to cancel the timeout.

</details>
<details> <summary><strong>72. What is the `setInterval()` function in JavaScript?</strong></summary> The **setInterval()** function calls a specified function repeatedly with a fixed time delay between each call.
Example:

javascript
Copy code
let count = 0;
const intervalId = setInterval(() => {
    console.log('This message appears every 2 seconds');
    count++;
    if (count === 3) {
        clearInterval(intervalId); // Stops after 3 messages
    }
}, 2000);
In this example, the message will be printed every 2 seconds, and it will stop after 3 messages.

</details>
<details> <summary><strong>73. What is a "pure function" in JavaScript?</strong></summary> A **pure function** is a function that always produces the same output for the same input and has no side effects (does not modify any external state).
Example:

javascript
Copy code
function add(a, b) {
    return a + b;  // No side effects, same output for same inputs
}
In contrast, an impure function might modify a global variable or rely on outside states.

</details>
<details> <summary><strong>74. What is the `bind()` method in JavaScript?</strong></summary> The **bind()** method creates a new function that, when invoked, has its `this` keyword set to the provided value, with a given sequence of arguments preceding any provided when the new function is called.
Example:

javascript
Copy code
const person = {
    name: 'Alice',
    greet: function() {
        console.log('Hello, ' + this.name);
    }
};

const greetAlice = person.greet.bind(person);
greetAlice(); // Output: Hello, Alice
In this example, the greet() function is bound to the person object, ensuring the correct this value when called.

</details>
<details> <summary><strong>75. What is the `call()` method in JavaScript?</strong></summary> The **call()** method is used to call a function with a specific `this` value and individual arguments. It’s similar to `bind()`, but `call()` invokes the function immediately.
Example:

javascript
Copy code
function greet() {
    console.log('Hello, ' + this.name);
}

const person = { name: 'Alice' };
greet.call(person); // Output: Hello, Alice
In this example, greet() is called immediately with person as its this value.

</details>
<details> <summary><strong>76. What is the `apply()` method in JavaScript?</strong></summary> The **apply()** method is similar to `call()`, but instead of passing individual arguments, an array or array-like object of arguments is passed.
Example:

javascript
Copy code
function greet(greeting) {
    console.log(greeting + ', ' + this.name);
}

const person = { name: 'Alice' };
greet.apply(person, ['Hello']); // Output: Hello, Alice
In this example, greet() is invoked with an array as its argument, using apply() to pass the person object as this.

</details>
<details> <summary><strong>77. What is the difference between `call()` and `apply()` in JavaScript?</strong></summary> The **`call()`** and **`apply()`** methods are similar in that they allow you to invoke a function with a specific `this` value, but they differ in how arguments are passed. - **`call()`** passes arguments individually. - **`apply()`** passes arguments as an array or array-like object.
Example using call():

javascript
Copy code
function greet(greeting) {
    console.log(greeting + ', ' + this.name);
}
const person = { name: 'Alice' };
greet.call(person, 'Hello');
Example using apply():

javascript
Copy code
greet.apply(person, ['Hello']);
Both examples will output the same result: Hello, Alice

</details>
<details> <summary><strong>78. What is a "closure" in JavaScript?</strong></summary> A **closure** is a function that remembers and can access its lexical scope (the scope in which it was defined) even when the function is executed outside that scope. This allows the function to "close over" its environment.
Example:

javascript
Copy code
function outer() {
    let count = 0;
    return function inner() {
        count++;
        console.log(count);
    };
}

const counter = outer();
counter(); // Output: 1
counter(); // Output: 2
In this example, the inner() function retains access to the count variable from the outer() function even after outer() has finished executing.

</details>
<details> <summary><strong>79. What is hoisting in JavaScript?</strong></summary> **Hoisting** is JavaScript's default behavior of moving declarations (variable and function declarations) to the top of their containing scope before code execution. However, only the declarations are hoisted, not the initializations.
Example with variables:

javascript
Copy code
console.log(x); // Output: undefined
var x = 5;
console.log(x); // Output: 5
Example with functions:

javascript
Copy code
foo(); // Output: "Hello"
function foo() {
    console.log("Hello");
}
In the second example, the function declaration is hoisted, so foo() can be called before it appears in the code.

</details>
<details> <summary><strong>80. What is the `this` keyword in JavaScript?</strong></summary> The **`this`** keyword refers to the context in which a function is executed. It represents the object that is executing the current piece of code.
Example with an object method:

javascript
Copy code
const person = {
    name: 'Alice',
    greet: function() {
        console.log('Hello, ' + this.name);
    }
};

person.greet(); // Output: Hello, Alice
In this example, this refers to the person object inside the greet method.

</details>
<details> <summary><strong>81. What are arrow functions in JavaScript?</strong></summary> Arrow functions provide a concise syntax for writing functions. They also bind the `this` keyword lexically, meaning that the `this` value inside an arrow function is inherited from the outer scope.
Example:

javascript
Copy code
const add = (a, b) => a + b;
console.log(add(3, 5)); // Output: 8
Example with this:

javascript
Copy code
const person = {
    name: 'Alice',
    greet: function() {
        setTimeout(() => {
            console.log('Hello, ' + this.name);
        }, 1000);
    }
};

person.greet(); // Output: Hello, Alice
In this example, the this inside the arrow function refers to the person object, whereas a regular function would have its own this context.

</details>

details> <summary><strong>82. What is the `find()` method in JavaScript?</strong></summary> The **`find()`** method returns the first element in an array that satisfies the provided testing function. If no elements are found, it returns `undefined`.
Example:

javascript
Copy code
const numbers = [1, 2, 3, 4, 5];
const result = numbers.find(num => num > 3);
console.log(result); // Output: 4
In this example, the find() method returns the first number greater than 3.

</details>
<details> <summary><strong>83. What is the `filter()` method in JavaScript?</strong></summary> The **`filter()`** method creates a new array with all elements that pass the test implemented by the provided function.
Example:

javascript
Copy code
const numbers = [1, 2, 3, 4, 5];
const result = numbers.filter(num => num % 2 === 0);
console.log(result); // Output: [2, 4]
In this example, the filter() method returns an array containing only the even numbers from the original array.

</details>
<details> <summary><strong>84. What is the `map()` method in JavaScript?</strong></summary> The **`map()`** method creates a new array populated with the results of calling a provided function on every element in the calling array.
Example:

javascript
Copy code
const numbers = [1, 2, 3, 4];
const doubled = numbers.map(num => num * 2);
console.log(doubled); // Output: [2, 4, 6, 8]
In this example, the map() method creates a new array with the numbers doubled.

</details>
<details> <summary><strong>85. What is the `reduce()` method in JavaScript?</strong></summary> The **`reduce()`** method applies a function against an accumulator and each element in the array (from left to right) to reduce it to a single value.
Example:

javascript
Copy code
const numbers = [1, 2, 3, 4];
const sum = numbers.reduce((acc, num) => acc + num, 0);
console.log(sum); // Output: 10
In this example, the reduce() method sums up all the numbers in the array.

</details>
<details> <summary><strong>86. What is the `reduceRight()` method in JavaScript?</strong></summary> The **`reduceRight()`** method works the same as `reduce()`, but it processes the array elements from right to left.
Example:

javascript
Copy code
const numbers = [1, 2, 3, 4];
const sum = numbers.reduceRight((acc, num) => acc + num, 0);
console.log(sum); // Output: 10
In this example, the array is reduced from the right to left, but the result remains the same as reduce() in this case.

</details>
<details> <summary><strong>87. What is `Object.freeze()` in JavaScript?</strong></summary> The **`Object.freeze()`** method freezes an object, preventing new properties from being added, and existing properties from being modified or deleted.
Example:

javascript
Copy code
const person = {
    name: 'Alice',
    age: 25
};

Object.freeze(person);

person.age = 26; // Won't work because the object is frozen
console.log(person.age); // Output: 25
In this example, the object person is frozen, and attempts to change its properties fail.

</details>
<details> <summary><strong>88. What is `Object.seal()` in JavaScript?</strong></summary> The **`Object.seal()`** method seals an object, meaning you cannot add or delete properties, but you can still modify the values of existing properties.
Example:

javascript
Copy code
const person = {
    name: 'Alice',
    age: 25
};

Object.seal(person);

person.age = 26; // Works because the object is sealed but not frozen
delete person.name; // Won't work because properties cannot be deleted
console.log(person); // Output: { name: 'Alice', age: 26 }
In this example, the object person is sealed, so we can modify its properties, but we cannot delete them or add new ones.

</details>
<details> <summary><strong>89. What is the `typeof` operator in JavaScript?</strong></summary> The **`typeof`** operator is used to determine the data type of a variable or an expression.
Example:

javascript
Copy code
let x = 5;
console.log(typeof x); // Output: 'number'

let y = 'Hello';
console.log(typeof y); // Output: 'string'

let z = true;
console.log(typeof z); // Output: 'boolean'
In this example, typeof returns the data type of each variable.

</details>
<details> <summary><strong>90. What is a "callback function" in JavaScript?</strong></summary> A **callback function** is a function that is passed as an argument to another function and is executed after a certain task is completed.
Example:

javascript
Copy code
function greet(name, callback) {
    console.log('Hello, ' + name);
    callback(); // Call the callback function after greeting
}

function farewell() {
    console.log('Goodbye!');
}

greet('Alice', farewell);
// Output:
// Hello, Alice
// Goodbye!
In this example, the farewell function is passed as a callback and executed after greet finishes logging the greeting.

</details>
<details> <summary><strong>91. What is an "Immediately Invoked Function Expression" (IIFE)?</strong></summary> An **IIFE** is a function that is defined and executed immediately after its declaration. It is often used to create a new scope and avoid polluting the global scope.
Example:

javascript
Copy code
(function() {
    let message = 'Hello, world!';
    console.log(message);
})(); // Output: Hello, world!
In this example, the function is executed immediately after it is defined, and the variable message is scoped within the IIFE.

</details>
<details> <summary><strong>92. What is the difference between `Object.create()` and the `new` keyword in JavaScript?</strong></summary> - **`Object.create()`** creates a new object with the specified prototype object and properties. - **`new`** creates a new instance of a constructor function and sets up the inheritance chain using the function's prototype.
Example using Object.create():

javascript
Copy code
const animal = {
    speak() {
        console.log('Animal speaks');
    }
};

const dog = Object.create(animal);
dog.speak(); // Output: Animal speaks
Example using new:

javascript
Copy code
function Animal() {}
Animal.prototype.speak = function() {
    console.log('Animal speaks');
};

const dog = new Animal();
dog.speak(); // Output: Animal speaks
Both methods can be used to create new objects, but Object.create() directly sets up the prototype chain, while new also handles the construction process.

</details>
<details> <summary><strong>93. What is the `super()` keyword in JavaScript?</strong></summary> The **`super()`** keyword is used to call functions on an object's parent class (in the case of inheritance). It must be called in the constructor of a subclass.
Example:

javascript
Copy code
class Animal {
    constructor(name) {
        this.name = name;
    }

    speak() {
        console.log(`${this.name} makes a sound`);
    }
}

class Dog extends Animal {
    constructor(name, breed) {
        super(name); // Calls the parent class constructor
        this.breed = breed;
    }

    speak() {
        super.speak(); // Calls the parent class method
        console.log(`${this.name} barks`);
    }
}

const dog = new Dog('Buddy', 'Golden Retriever');
dog.speak(); 
// Output:
// Buddy makes a sound
// Buddy barks
In this example, super() is used to call the constructor and methods of the parent class Animal from the Dog subclass.

</details>
<details> <summary><strong>94. What is the `get` method in JavaScript?</strong></summary> The **`get`** method is a special method used to define a getter property on an object. It allows you to access the value of a property as if it were a simple field.
Example:

javascript
Copy code
const person = {
    firstName: 'John',
    lastName: 'Doe',
    
    get fullName() {
        return this.firstName + ' ' + this.lastName;
    }
};

console.log(person.fullName); // Output: John Doe
In this example, fullName is a getter property that concatenates firstName and lastName when accessed.

</details>
<details> <summary><strong>95. What is the `set` method in JavaScript?</strong></summary> The **`set`** method is a special method used to define a setter property on an object. It allows you to assign a value to a property using a function.
Example:

javascript
Copy code
const person = {
    firstName: 'John',
    lastName: 'Doe',

    set fullName(name) {
        const [firstName, lastName] = name.split(' ');
        this.firstName = firstName;
        this.lastName = lastName;
    }
};

person.fullName = 'Jane Smith';
console.log(person.firstName); // Output: Jane
console.log(person.lastName);  // Output: Smith
In this example, fullName is a setter property that allows setting both firstName and lastName by splitting the input string.

</details>
<details> <summary><strong>96. What is the purpose of the `finally` block in JavaScript?</strong></summary> The **`finally`** block is used in conjunction with `try` and `catch`. It is always executed after the `try` and `catch` blocks, regardless of whether an exception was thrown or not. It is commonly used to clean up resources or finalize operations.
Example:

javascript
Copy code
try {
    let result = 10 / 0;
    console.log(result); // Output: Infinity
} catch (error) {
    console.log('Error occurred');
} finally {
    console.log('This will always be executed');
}
// Output:
// This will always be executed
In this example, the finally block executes even if there was no error.

</details>
<details> <summary><strong>97. What is the `new.target` in JavaScript?</strong></summary> The **`new.target`** refers to the constructor that was invoked when using the `new` keyword. It is useful inside a constructor to determine if it was called with `new`.
Example:

javascript
Copy code
function MyConstructor() {
    if (!new.target) {
        console.log('Constructor must be called with new');
    } else {
        console.log('Constructor called with new');
    }
}

MyConstructor(); // Output: Constructor must be called with new
new MyConstructor(); // Output: Constructor called with new
In this example, new.target helps us check whether the constructor was called with new.

</details>
<details> <summary><strong>98. What is the `for...of` loop in JavaScript?</strong></summary> The **`for...of`** loop is used to iterate over iterable objects like arrays, strings, maps, and more. It gives direct access to the values of the iterable.
Example:

javascript
Copy code
const numbers = [10, 20, 30];

for (const num of numbers) {
    console.log(num);
}
// Output:
// 10
// 20
// 30
In this example, for...of is used to iterate through the array and print each number.

</details>
<details> <summary><strong>99. What is the `Symbol.iterator` in JavaScript?</strong></summary> The **`Symbol.iterator`** is a built-in symbol that defines the default iterator for an object. Objects that have this symbol can be iterated over with `for...of` loops.
Example:

javascript
Copy code
const myIterable = {
    items: ['apple', 'banana', 'cherry'],
    
    [Symbol.iterator]() {
        let index = 0;
        const items = this.items;
        
        return {
            next() {
                if (index < items.length) {
                    return { value: items[index++], done: false };
                } else {
                    return { done: true };
                }
            }
        };
    }
};

for (const fruit of myIterable) {
    console.log(fruit);
}
// Output:
// apple
// banana
// cherry
In this example, we define a custom iterable object with the Symbol.iterator method, allowing it to be used in a for...of loop.

</details>
<details> <summary><strong>100. What is the purpose of `console.log()` in JavaScript?</strong></summary> The **`console.log()`** method is used to output messages to the browser's console, typically for debugging purposes.
Example:

javascript
Copy code
const name = 'John';
console.log('Hello, ' + name); // Output: Hello, John
In this example, console.log() is used to print a greeting message to the console.

</details>

<details> <summary><strong>101. What is `JSON.stringify()` and `JSON.parse()` in JavaScript?</strong></summary> **`JSON.stringify()`** is used to convert a JavaScript object into a JSON string, while **`JSON.parse()`** is used to convert a JSON string into a JavaScript object.
Example:

javascript
Copy code
const obj = { name: 'John', age: 30 };
const jsonString = JSON.stringify(obj); // Convert object to JSON string
console.log(jsonString); // Output: {"name":"John","age":30}

const jsonObject = JSON.parse(jsonString); // Convert JSON string to object
console.log(jsonObject); // Output: { name: 'John', age: 30 }
These methods are commonly used when sending data to a server or storing it locally.

</details>
<details> <summary><strong>102. What is the `localStorage` API in JavaScript?</strong></summary> **`localStorage`** is a web storage API that allows you to store data persistently in the browser. The data is saved across sessions and remains until it is explicitly deleted.
Example:

javascript
Copy code
// Store data
localStorage.setItem('username', 'JohnDoe');

// Retrieve data
const username = localStorage.getItem('username');
console.log(username); // Output: JohnDoe

// Remove data
localStorage.removeItem('username');

// Clear all data
localStorage.clear();
Data stored in localStorage is not cleared when the browser is closed and persists across page reloads.

</details>
<details> <summary><strong>103. What is the `sessionStorage` API in JavaScript?</strong></summary> **`sessionStorage`** is similar to `localStorage`, but its data is only available for the duration of the page session. Once the page is closed, the data is cleared.
Example:

javascript
Copy code
// Store data
sessionStorage.setItem('sessionName', 'Rohit');

// Retrieve data
const sessionName = sessionStorage.getItem('sessionName');
console.log(sessionName); // Output: Rohit

// Remove data
sessionStorage.removeItem('sessionName');

// Clear all data
sessionStorage.clear();
The data is available only within the same browser tab during the page session.

</details>
<details> <summary><strong>104. What are JavaScript modules?</strong></summary> JavaScript modules allow you to break up your code into smaller, reusable pieces. You can export functions, variables, or objects from one module and import them into another.
Example:

javascript
Copy code
// In math.js
export const add = (a, b) => a + b;
export const subtract = (a, b) => a - b;

// In app.js
import { add, subtract } from './math.js';

console.log(add(2, 3)); // Output: 5
console.log(subtract(5, 3)); // Output: 2
Modules are typically used to improve code organization and maintainability.

</details>
<details> <summary><strong>105. What is the `Object.freeze()` method in JavaScript?</strong></summary> The **`Object.freeze()`** method is used to prevent modification of an object's properties. Once an object is frozen, it cannot be changed.
Example:

javascript
Copy code
const person = { name: 'John', age: 30 };
Object.freeze(person);

person.age = 31; // This will have no effect
console.log(person.age); // Output: 30
Freezing an object prevents the addition, removal, or modification of properties.

</details>
<details> <summary><strong>106. What is `Array.prototype.map()` in JavaScript?</strong></summary> The **`map()`** method creates a new array populated with the results of calling a provided function on every element in the calling array.
Example:

javascript
Copy code
const numbers = [1, 2, 3, 4];
const doubled = numbers.map(num => num * 2);
console.log(doubled); // Output: [2, 4, 6, 8]
It is useful when you need to apply a transformation to each element in an array.

</details>
<details> <summary><strong>107. What is the `filter()` method in JavaScript?</strong></summary> The **`filter()`** method creates a new array with all elements that pass the test implemented by the provided function.
Example:

javascript
Copy code
const numbers = [1, 2, 3, 4, 5];
const evenNumbers = numbers.filter(num => num % 2 === 0);
console.log(evenNumbers); // Output: [2, 4]
It is commonly used to filter out elements based on specific conditions.

</details>
<details> <summary><strong>108. Explain the `reduce()` method in JavaScript.</strong></summary> The **`reduce()`** method applies a function against an accumulator and each element in the array (from left to right) to reduce it to a single value.
Example:

javascript
Copy code
const numbers = [1, 2, 3, 4];
const sum = numbers.reduce((acc, num) => acc + num, 0);
console.log(sum); // Output: 10
In this example, the reduce() method calculates the sum of the numbers in the array.

</details>
<details> <summary><strong>109. What is the difference between `Object.create()` and `new` keyword in JavaScript?</strong></summary> **`Object.create()`** creates a new object with the specified prototype object and properties, while **`new`** is used to create an instance of a constructor function.
Example with Object.create():

javascript
Copy code
const personPrototype = { greet() { console.log('Hello!'); } };
const person = Object.create(personPrototype);
person.greet(); // Output: Hello!
Example with new:

javascript
Copy code
function Person() {
    this.greet = function() { console.log('Hello!'); };
}
const person = new Person();
person.greet(); // Output: Hello!
The key difference is that Object.create() is used to create objects with a specific prototype, while new creates an instance of a constructor.

</details>
<details> <summary><strong>110. What is a "pure function" in JavaScript?</strong></summary> A **pure function** is a function that always produces the same output for the same input and does not cause any side effects (such as modifying external variables).
Example:

javascript
Copy code
function add(a, b) {
    return a + b;
}
console.log(add(2, 3)); // Output: 5
In this example, add() is a pure function because it does not modify any external state and always returns the same result for the same inputs.

</details>

<details> <summary><strong>1. What will be the output for the below code?</strong></summary> ```javascript if(Symbol("test") === Symbol("test")){ console.log("Hello, welcome"); }else{ console.log("Bye, see you soon!"); } ``` **Answer:** The output will be: ``` Bye, see you soon! ``` **Explanation:** Each call to `Symbol()` creates a unique symbol. Even though the descriptions are the same ("test"), the symbols are distinct objects, so the comparison `Symbol("test") === Symbol("test")` returns `false`. </details>
<details> <summary><strong>2. How to swap 2 values without taking an extra variable?</strong></summary> **Example:** ```javascript let a = 20; let b = 35; [a, b] = [b, a]; console.log(a); // 35 console.log(b); // 20 ``` **Explanation:** In ES6, you can use array destructuring to swap two values in one line without the need for an extra variable. </details>
<details> <summary><strong>3. Write a function to get output with nth dynamic value.</strong></summary> **Example:** ```javascript function flatten(arr) { return arr.flat(Infinity); }
let input = [1, [2, [3, 4, [12, 13], 5]]]; let output = flatten(input); console.log(output); // [1, 2, 3, 4, 12, 13, 5]

sql
Copy code
**Explanation:**  
Using `Array.prototype.flat()` with `Infinity` will recursively flatten all levels of an array.
</details>

---

<details>  
<summary><strong>4. Write a function to get a duplicate character count and return them in an object.</strong></summary>
**Example:**
```javascript
function countDuplicates(str) {
    const result = {};
    str.split('').forEach(char => {
        if (char !== ' ' && isNaN(char)) {
            result[char] = (result[char] || 0) + 1;
        }
    });
    return Object.fromEntries(Object.entries(result).filter(([_, count]) => count > 1));
}

let strValues = "welcome 2 abroad";
console.log(countDuplicates(strValues));
// Output: { w: 1, e: 2, l: 1, c: 1, o: 2, m: 1, a: 2, b: 1, r: 1, d: 1 }
Explanation:
This function filters out spaces and numbers, counts the occurrences of characters, and returns only those characters that appear more than once.

</details>
<details> <summary><strong>5. Write a program to remove blank and undefined values from a nested array and make it unique.</strong></summary> **Example:** ```javascript function cleanArray(arr) { return arr.flat(Infinity) .filter(item => item !== undefined && item !== null && item !== '') .filter((value, index, self) => self.indexOf(value) === index); // Remove duplicates }
const myNestedArray = [1, 2, [undefined, null, '', [3, 4, [5, undefined], null]], 6, undefined, [7, [8, 9, [null, undefined], 10]]]; console.log(cleanArray(myNestedArray)); // Output: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

sql
Copy code
**Explanation:**  
The function first flattens the array, removes undefined, null, and empty string values, and then removes any duplicate values.
</details>

---

<details>  
<summary><strong>6. Swap values using ES6</strong></summary>
**Example:**
```javascript
let a = 5;
let b = 10;
[b, a] = [a, b];
console.log(a); // 10
console.log(b); // 5
Explanation:
This is a simple example of swapping two variables using array destructuring in ES6.

</details>
<details> 
    <summary><strong>7. What will be the output of the following code?</strong></summary>
    ```javascript 
    a = 5; 
    var a; 
    console.log(a); 
    ``` 
    **Answer:** 
    ``` 5 ``` **Explanation:** Due to **hoisting**, the `var` declaration is moved to the top, so the value of `a` is 5 when logged. 
</details>
<details> <summary><strong>8. What will be the output of the following code?</strong></summary> ```javascript a = 5; let a; console.log(a); ``` **Answer:** ``` Cannot access 'a' before initialization ``` **Explanation:** Since `let` is block-scoped and does not hoist its value, it causes a `ReferenceError` when accessed before its initialization. </details>
<details> <summary><strong>9. What will be the output of the following code?</strong></summary> ```javascript const obj1 = {name: "Ramesh", age: 24}; const obj2 = obj1; obj2.name = 'Praveen'; console.log(obj1); ``` **Answer:** ``` {name: 'Praveen', age: 24} ``` **Explanation:** In JavaScript, objects are reference types, so modifying `obj2` will also affect `obj1` because they refer to the same object. </details>
<details> <summary><strong>10. How can we protect this when we copy the first object to another object?</strong></summary> **Example:** ```javascript const obj1 = {name: 'Anil', age: 24}; const obj2 = {...obj1}; // Using spread operator for shallow copy obj2.name = 'Praveen'; console.log(obj1); // Output: { name: 'Anil', age: 24 } ``` **Explanation:** By using the spread operator, we create a shallow copy of the object. Changes to `obj2` will not affect `obj1`. </details>
<details> <summary><strong>11. Is this valid code?</strong></summary> ```javascript let name = 'Ramesh'; let age = 35; let obj = { name, age }; console.log(obj); ``` **Answer:** Yes, this is valid code. **Explanation:** In ES6, you can use shorthand property names when the variable name and the object property name are the same. </details>
<details> <summary><strong>12. How can I get the max number value from an array?</strong></summary> **Example:** ```javascript const numbers = [1, 2, 35, 4, 7, 9]; console.log(Math.max(...numbers)); // Output: 35 ``` **Explanation:** The `Math.max()` function returns the largest of the numbers provided. The spread operator (`...`) is used to pass the array elements as individual arguments. </details>
<details> <summary><strong>13. What will be the output for the below code?</strong></summary> ```javascript let numbers = [1, 2, 35, 4, 7, 9]; console.log(Math.max(numbers)); // Output: NaN ``` **Explanation:** `Math.max()` does not accept arrays directly. Since `numbers` is an array, it returns `NaN`. You need to use the spread operator to pass the elements individually. </details>
<details> <summary><strong>14. Mysql query to get nth highest number from a table</strong></summary> ```sql SELECT id AS 4thHighestEarningEmployee FROM payments ORDER BY id DESC LIMIT 3,1; ``` **Explanation:** In the above query, `LIMIT 3,1` is used to fetch the nth highest record by skipping 3 records and fetching the 4th highest. </details>
<details> <summary><strong>15. What is the output of the following code?</strong></summary> ```javascript function cb(){ console.log("hello 1"); } process.nextTick(cb); console.log("hello 2"); ``` **Answer:** ``` hello 2 hello 1 ``` **Explanation:** `process.nextTick()` queues the callback to be executed after the current event loop phase. Since `console.log("hello 2")` is already in the current phase, it is printed first. </details>
<details> <summary><strong>16. What is the output of the following code?</strong></summary> ```javascript console.log(4 + "3" + 2 + 6); ``` **Answer:** ``` "43326" ``` **Explanation:** The `+` operator is used for string concatenation. So, `4 + "3"` becomes `"43"`, and the rest of the numbers are concatenated as strings. </details>
<details> <summary><strong>17. How can I get an array in the same level?</strong></summary> ```javascript const arr2 = [0, 1, [2, [3, [4, 5]]]]; console.log(arr2.flat(Infinity)); // Output: [0, 1, 2, 3, 4, 5] ``` **Explanation:** The `flat()` method with `Infinity` flattens the array recursively to all levels. </details>
