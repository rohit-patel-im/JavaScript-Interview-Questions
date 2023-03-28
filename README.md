# JavaScript-Interview-Questions

- What is callback

- What is currying

- What is async await explain with an example

- What is promise in javascript

- What is promise.All in javaScript

- What is event handling

- Explain call, apply, and bind

- Explain local storage and session storage and how to secure both storages

- What are web workers

- What is PWA

- Difference between single page application and multipage application

- Explain API calls and its process

- What is microservices

- Difference between Map and reduce

- What is batching

- What is pure function

- What are async and await

- What is callback hell

- What is closure

- What is hoisting

- Explain let const and var

- What is the event loop

- Write a function to check a string palindrome(madam) or not in JavaScript

- Write a function to get duplicate values from the array and its count in JavaScript

- What is event delegation

- How to call multiple APIs in one time

- What is Currying in JavaScript

- sync v/s async

- What is rest and spread operator

- Give an example of object destructuring

- Remove a duplicate element from the array

- How to check your event in different browsers

- What is event emitter

- What is the output of this snippet
  x = 5;
  console.log(x);
  var x; 

  y = 5;
  console.log(y);
  let y;
  
- Remove a property from the snippet
    var user = {
      'name':'User1',
      'age':'20',
      'mail':'test@gmail.com'
    }

- Remove duplicate elements from the array
  const numbers = [10, 20, 30, 40, 10, 20, 30, 50];

- What is the output of this snippet
  var myObject = {
      foo: "bar",
      func: function() {
          var self = this;
          console.log("outer func:  this.foo = " + this.foo);
          console.log("outer func:  self.foo = " + self.foo);
          (function() {
              console.log("inner func:  this.foo = " + this.foo);
              console.log("inner func:  self.foo = " + self.foo);
          }());
      }
  };
  myObject.func();
  
- What is the output of this snippet
  (function () {
    try {
        throw new Error();
    } catch (x) {
        var x = 1, y = 2;
        console.log(x);
    }
    console.log(x);
    console.log(y);
})();

- Write a program in javascript to swap two strings after two strings till the string length
Example : 
//input = ABCDEFGHIJK
//output = ABDCEFHGIJK
