---
bank_name: "Session 25: Final Examination — Comprehensive"
---

1. Which keyword declares a variable that cannot be reassigned after it is set?
a) let
b) var
*c) const
d) static

2. What is the value of `typeof null` in JavaScript?
a) "null"
b) "undefined"
*c) "object"
d) "boolean"

3. What does `===` check that `==` does not?
a) Whether the values are exactly equal in magnitude
*b) Whether the values are equal AND of the same type
c) Whether two variables point to the same memory location
d) Whether a value is truthy

4. True or false: Variables declared with `var` are function-scoped, not block-scoped.
*a) True
b) False

5. What is the result of `"5" + 3` in JavaScript?
a) 8
b) 53
*c) "53"
d) NaN

6. Which string method returns a new string with all characters converted to uppercase?
a) `.upper()`
b) `.caps()`
*c) `.toUpperCase()`
d) `.uppercase()`

7. What does a template literal use to embed a JavaScript expression inside a string?
a) `#{expression}`
b) `{{expression}}`
*c) `${expression}`
d) `(expression)`

8. What value does an `if` statement treat as falsy?
a) Any non-zero number
b) Any non-empty string
*c) `0`, `""`, `null`, `undefined`, `NaN`, and `false`
d) Only the boolean value `false`

9. What is the difference between `null` and `undefined`?
a) They are exactly the same thing
*b) `undefined` means a variable was declared but not assigned; `null` is an intentional empty value
c) `null` is a number type; `undefined` is an object type
d) `undefined` only occurs in strict mode

10. What does `Number.isNaN("hello")` return?
a) true
*b) false
c) NaN
d) undefined

11. What does the `push()` method do to an array?
a) Removes the first element
b) Removes the last element
c) Adds an element to the beginning
*d) Adds an element to the end

12. What does `arr.length` return for an array with 4 elements?
a) 3
*b) 4
c) 5
d) The index of the last element

13. Which loop is best for iterating directly over the values of an array?
a) `for...in`
b) `while`
*c) `for...of`
d) `do...while`

14. What does `arr.indexOf("banana")` return if "banana" is not in the array?
a) 0
b) null
*c) -1
d) undefined

15. True or false: `for...in` is designed to iterate over the keys (indices) of an array or the properties of an object.
*a) True
b) False

16. What does a function return if it has no `return` statement?
a) 0
b) null
*c) undefined
d) false

17. What is the purpose of a default parameter in a function?
a) It sets the maximum number of arguments allowed
*b) It provides a fallback value if no argument is passed for that parameter
c) It makes the parameter required
d) It converts the argument to a specific type automatically

18. Which array method creates and returns a new array by applying a function to each element?
a) `.filter()`
b) `.forEach()`
*c) `.map()`
d) `.reduce()`

19. What does `.filter()` return?
a) The first element that matches the condition
b) A boolean indicating whether any element matches
*c) A new array containing only elements for which the callback returned true
d) The index of the first matching element

20. What does `.find()` return if no element matches the callback condition?
a) -1
b) null
*c) undefined
d) false

21. What does `.reduce()` do?
a) Removes duplicate elements from an array
b) Finds the smallest element in an array
*c) Processes each element and accumulates a single result value
d) Returns a new array with elements in reverse order

22. What does `arr.some(fn)` return?
a) The first element for which fn returns true
*b) true if at least one element passes the fn test, otherwise false
c) A new array of elements that pass the fn test
d) The total count of elements that pass the fn test

23. How do you create an object literal in JavaScript?
a) `let obj = []`
b) `let obj = new Object()`
*c) `let obj = {}`
d) Both b and c are correct, but not a

24. What is the difference between dot notation and bracket notation for accessing object properties?
a) Dot notation is faster; bracket notation is slower
b) They are completely identical in all situations
*c) Bracket notation allows property names stored in variables; dot notation requires a literal name
d) Bracket notation only works with numeric indexes

25. What does `"name" in person` check?
a) Whether person.name is truthy
*b) Whether the property "name" exists on the person object, regardless of its value
c) Whether person is a string named "name"
d) Whether person has a method called name

26. True or false: When you assign an object to a new variable and change a property through the new variable, the original object is also changed.
*a) True
b) False

27. What is the `this` keyword inside an object method?
a) The global window object
b) The function itself
*c) The object the method is called on
d) The prototype of the object

28. What does `Object.keys(obj)` return?
a) An array of the object's values
*b) An array of the object's own property names
c) A string of all keys joined by commas
d) The number of properties the object has

29. What keyword is used to define a class in JavaScript?
a) `type`
b) `struct`
*c) `class`
d) `blueprint`

30. What is the purpose of the `constructor()` method inside a class?
a) It is called when the class is defined
*b) It is called when a new instance of the class is created with `new`
c) It is called when the instance is destroyed
d) It sets the prototype of the class

31. What is inheritance in the context of JavaScript classes?
a) Copying all methods from one class to another manually
*b) Using `extends` to create a child class that has all the properties and methods of its parent class
c) Importing one class into another file
d) Sharing variables between two class instances

32. What does `super()` do inside a child class constructor?
a) Creates a new instance of the parent class
b) Calls all methods on the parent class
*c) Calls the parent class constructor, setting up the parent's properties on the new instance
d) Checks if the class has a valid parent

33. What is a closure in JavaScript?
a) A function that cannot be called after it is defined
b) A class that has no public methods
*c) A function that remembers and has access to variables from its outer scope even after that outer function has returned
d) A loop that closes automatically when it finishes

34. What is the difference between block scope and function scope?
a) There is no difference in modern JavaScript
*b) Block scope (let/const) is limited to the nearest set of curly braces; function scope (var) is limited to the whole function
c) Function scope applies to arrow functions only
d) Block scope only applies inside loops

35. What is the result of calling a function before it is declared when the function is defined with the `function` keyword?
a) An error — function declarations cannot be called before they appear in the code
*b) It works correctly — function declarations are hoisted to the top of their scope
c) It returns undefined
d) It depends on whether strict mode is enabled

36. What does the spread operator `...` do when used in a function call like `Math.max(...arr)`?
a) Copies the array into a new array
b) Converts the array to a string
*c) Spreads the array's elements as individual arguments to the function
d) Joins the array elements with commas

37. What does destructuring allow you to do?
a) Break a string into individual characters
b) Delete properties from an object
*c) Unpack values from arrays or properties from objects into separate variables in a single statement
d) Convert an array to an object

38. What is a callback function?
a) A function that calls itself recursively
b) A function that only runs if no error occurs
*c) A function passed as an argument to another function and called at the appropriate time
d) A function that returns another function

39. What does `setTimeout(fn, 2000)` do?
a) Runs fn every 2 seconds repeatedly
b) Cancels fn after 2 seconds
*c) Runs fn once after a 2-second delay
d) Pauses the entire program for 2 seconds

40. What is "callback hell"?
a) A function that calls itself in an infinite loop
b) When callbacks throw errors that cannot be caught
*c) Deeply nested callbacks where each step depends on the result of the previous, creating a hard-to-read pyramid of indentation
d) A pattern where callbacks run in the wrong order

41. What does a Promise represent?
a) A guarantee that a function will always succeed
b) A synchronous operation that might fail
*c) A placeholder for a value that will be available in the future, representing an eventual success or failure
d) A function that runs immediately when called

42. What are the three possible states of a Promise?
a) waiting, done, cancelled
b) start, middle, end
*c) pending, fulfilled, rejected
d) created, running, complete

43. What does `.then()` receive as its argument when a Promise resolves?
a) The rejected reason
b) The Promise object itself
*c) The resolved value
d) A new Promise

44. What does `Promise.all([p1, p2, p3])` do?
a) Runs p1, p2, and p3 in sequence, one after another
b) Returns the result of whichever Promise finishes first
*c) Returns a new Promise that resolves when ALL three Promises have resolved, with an array of their results
d) Returns a new Promise that resolves when at least one Promise has resolved

45. What keyword turns a regular function into an async function?
*a) `async`
b) `await`
c) `promise`
d) `defer`

46. What does `await` do inside an async function?
a) It makes the rest of the program pause while the Promise resolves
*b) It pauses execution of the async function until the Promise resolves, then continues with the resolved value
c) It converts a synchronous function to a Promise
d) It cancels any pending Promises

47. True or false: You can only use `await` inside an `async` function (or at the top level of a module).
*a) True
b) False

48. What does `new Date()` create?
a) A string with today's date formatted as "YYYY-MM-DD"
b) A number representing the current time in seconds
*c) A Date object representing the current date and time
d) An array of year, month, day values

49. What does `JSON.stringify(obj)` do?
a) Converts a JSON string to a JavaScript object
*b) Converts a JavaScript object to a JSON string
c) Validates whether a string is valid JSON
d) Parses a JSON file from the file system

50. What does `localStorage.setItem("key", "value")` do?
a) Saves data to a file on the user's computer
b) Sends data to a server
*c) Stores a key-value pair in the browser's local storage, which persists after the page closes
d) Creates a cookie

51. Which error type is thrown when code has a typo that prevents the JavaScript engine from parsing it?
*a) SyntaxError
b) TypeError
c) ReferenceError
d) ParseError

52. What does `throw new RangeError("Out of range")` do?
a) Logs the message to the console and stops execution
b) Returns the error object from the function
*c) Stops execution and throws a RangeError that can be caught by a surrounding try/catch
d) Creates a warning but does not stop execution

53. True or false: The `finally` block runs even if the `try` block has a `return` statement.
*a) True
b) False

54. What happens if an error is thrown inside a `catch` block?
a) It is automatically caught by the same catch block
b) It is silently ignored
*c) It propagates up — the outer try/catch handles it, or it becomes an unhandled error
d) JavaScript automatically logs it and continues

55. What does `fetch("data.json")` return?
a) The parsed JSON data directly
b) A string of the raw file contents
*c) A Promise that resolves to a Response object
d) A boolean indicating whether the file exists

56. After receiving a Response from fetch, which method do you call to parse the body as JSON?
a) `response.parse()`
b) `response.data()`
*c) `response.json()`
d) `JSON.parse(response)`

57. True or false: If you fetch a file that does not exist (404), JavaScript automatically throws an error and the .catch() handler runs.
a) True
*b) False

58. What does `response.status` contain?
a) A string description of the response (like "OK")
b) Whether the response was successful (true/false)
*c) The numeric HTTP status code (like 200, 404, or 500)
d) The time it took for the response to arrive

59. What is the correct way to make a POST request with fetch?
a) `fetch(url, "POST")`
b) `fetch(url).post(data)`
*c) `fetch(url, { method: "POST", headers: {"Content-Type": "application/json"}, body: JSON.stringify(data) })`
d) `fetch.post(url, data)`

60. In an async fetch function, what should happen after `const response = await fetch(url)` if the response is not ok?
a) Call response.json() and check the result
b) Return null immediately
*c) Throw a new Error with a message that includes the status code
d) Call response.ok() to fix the issue

61. What is a JavaScript module?
a) A built-in object like Math or Date
b) A third-party library installed with npm
*c) A JavaScript file that explicitly exports values and can import values from other files
d) A special type of function that runs in isolation

62. What is the difference between a named export and a default export?
a) Named exports can only export functions; default exports can export anything
*b) Named exports can be many per file and require curly braces to import; default exports are one per file and need no curly braces
c) Default exports are faster to load than named exports
d) Named exports are only for constants; default exports are for functions

63. Which of the following correctly exports a function called `greet` as a named export?
a) `module.export function greet() {}`
b) `public function greet() {}`
*c) `export function greet() {}`
d) `share function greet() {}`

64. You have a file `utils.js` with a default export. How do you import it in `app.js`?
a) `import { utils } from "./utils.js"`
*b) `import utils from "./utils.js"` (or any name you choose)
c) `import default from "./utils.js"`
d) `require("./utils.js")`

65. True or false: In an ES module, variables declared at the top level are NOT automatically added to the global scope.
*a) True
b) False

66. What does `.map()` return?
a) A boolean
b) The first matching element
*c) A new array of the same length, with each element transformed by the callback
d) A modified version of the original array

67. What does `arr.includes(value)` return?
a) The index of value in arr
b) A new array with the value removed
*c) true if arr contains value, false otherwise
d) The count of how many times value appears

68. What does `Object.entries(obj)` return?
a) An array of the object's keys only
b) An array of the object's values only
*c) An array of [key, value] pairs for each property of the object
d) A string representation of the object

69. What is the purpose of `Array.from()`?
a) It creates a new empty array
b) It converts a number to an array
*c) It creates an array from an array-like or iterable object (like a string or NodeList)
d) It creates a deep copy of an existing array

70. What does `Math.floor(4.9)` return?
a) 5
b) 4.9
*c) 4
d) NaN

71. What is the result of `[1, 2, 3].reduce((acc, val) => acc + val, 0)`?
a) [1, 2, 3]
b) [0, 1, 3, 6]
*c) 6
d) 3

72. What does the `delete` operator do when used on an object property?
a) Sets the property value to null
b) Sets the property value to undefined
*c) Removes the property from the object entirely
d) Throws an error if the property does not exist

73. What is the output of:
```js
const nums = [10, 20, 30];
console.log(nums[1]);
```
a) 10
*b) 20
c) 30
d) undefined

74. What does `arr.slice(1, 3)` return for `arr = [10, 20, 30, 40]`?
a) [10, 20, 30]
*b) [20, 30]
c) [20, 30, 40]
d) [10, 20]

75. What does `arr.splice(1, 2)` do to `arr = [10, 20, 30, 40]`?
a) Removes the element at index 1 only
*b) Removes 2 elements starting at index 1, modifying the original array
c) Returns a new array without elements at indexes 1 and 2
d) Inserts 2 new elements at index 1

76. True or false: Arrow functions have their own `this` binding.
a) True
*b) False

77. What is a getter method in a class?
a) A method that constructs a new instance
b) A method that deletes a property
*c) A method defined with `get` that is accessed like a property, not called like a function
d) A method that returns the class name

78. What does `Promise.race([p1, p2, p3])` return?
a) A Promise that waits for all three to resolve
b) A Promise that resolves with all three results
*c) A Promise that resolves or rejects as soon as the first Promise settles
d) A Promise that always rejects if any one rejects

79. What happens when you `await` a value that is not a Promise?
a) An error is thrown
b) undefined is returned
*c) The value is returned immediately as-is, wrapped in a resolved Promise
d) The function pauses indefinitely

80. Which of the following correctly combines async/await with error handling for a fetch call?
a) `const data = fetch(url).then(r => r.json());`
b) `async function load() { const res = fetch(url); return res.json(); }`
*c) `async function load() { try { const res = await fetch(url); if (!res.ok) throw new Error(res.status); return await res.json(); } catch(e) { console.log(e.message); return null; } }`
d) `function load() { await fetch(url).then(r => r.json()); }`

81. What does this code log?
```javascript
let score = 100;
score -= 15;
score *= 2;
console.log(score);
```
a) 185
*b) 170
c) 200
d) 85

82. What does this code log?
```javascript
const words = ["hi", "hello", "hey", "howdy"];
console.log(words.filter(w => w.length > 3).map(w => w.toUpperCase()));
```
a) ["HI", "HELLO", "HEY", "HOWDY"]
*b) ["HELLO", "HOWDY"]
c) ["HELLO", "HEY", "HOWDY"]
d) ["hello", "howdy"]

83. What does this code log?
```javascript
class Stack {
  #items = [];
  push(x) { this.#items.push(x); }
  pop() { return this.#items.pop(); }
  peek() { return this.#items[this.#items.length - 1]; }
}
const s = new Stack();
s.push(1); s.push(2); s.push(3);
s.pop();
console.log(s.peek());
```
a) 3
*b) 2
c) 1
d) undefined

84. What does this code log?
```javascript
async function getNum() { return 42; }
async function main() {
  const n = await getNum();
  console.log(n + 8);
}
main();
```
a) 42
b) A Promise
*c) 50
d) undefined

85. What does this code log?
```javascript
try {
  null.property;
} catch (e) {
  console.log(e instanceof TypeError);
}
```
*a) true
b) false
c) undefined
d) An unhandled error

86. What does this code log?
```javascript
import { double } from "./math.js";
// math.js: export const double = x => x * 2;
console.log(double(7));
```
a) 7
*b) 14
c) An error — you must use default export
d) undefined

87. What does this code log?
```javascript
const ops = [];
for (var i = 0; i < 3; i++) {
  ops.push(() => i * 2);
}
console.log(ops[0]());
```
a) 0
b) 2
*c) 6
d) undefined

88. What does this code log?
```javascript
function makeAdder(x) {
  return y => x + y;
}
const add5 = makeAdder(5);
const add10 = makeAdder(10);
console.log(add5(3) + add10(2));
```
a) 15
b) 20
*c) 20
d) 10

89. What does this code log?
```javascript
const obj = { a: 1 };
const copy = Object.assign({}, obj, { a: 99, b: 2 });
console.log(copy.a + copy.b);
```
a) 3
b) 100
*c) 101
d) undefined

90. What does this code log?
```javascript
async function run() {
  const results = await Promise.all([
    Promise.resolve(10),
    Promise.resolve(20)
  ]);
  return results.map(n => n * n);
}
run().then(v => console.log(v));
```
a) [10, 20]
b) [20, 40]
*c) [100, 400]
d) A Promise
