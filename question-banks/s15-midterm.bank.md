---
bank_name: "Session 15: Midterm Synthesis — Comprehensive Practice (s01–s15)"
---

1. Which of the following is a valid JavaScript identifier?
*a) `myScore`
b) `1stPlace`
c) `my score`
d) `let`

2. What is the difference between `let` and `const`?
*a) `let` allows reassignment; `const` does not
b) `const` allows reassignment; `let` does not
c) `let` is for numbers; `const` is for strings
d) There is no difference — they work the same way

3. What does `typeof "hello"` return?
*a) `"string"`
b) `"text"`
c) `"word"`
d) `"object"`

4. What does the `===` operator check?
*a) Both value and type are equal
b) Only the value is equal, ignoring type
c) The variables point to the same memory address
d) Whether one value is larger than the other

5. Which method converts a string to all uppercase letters?
*a) `.toUpperCase()`
b) `.uppercase()`
c) `.capitalize()`
d) `.upper()`

6. What does `parseInt("42px")` return?
*a) `42`
b) `"42px"`
c) `NaN`
d) `0`

7. What is a template literal and which character is used to create one?
*a) A string that can include expressions using `${}`, created with backticks (`` ` ``)
b) A string with single quotes that can include variables directly
c) A special kind of comment that appears in the output
d) A multi-line string created with double quotes

8. What does `Number.isNaN(NaN)` return?
*a) `true`
b) `false`
c) `undefined`
d) `0`

9. An `if...else if...else` chain runs only the block that:
*a) Matches the first condition that is `true`
b) Matches the last condition listed
c) Has the simplest condition
d) Runs all blocks in order

10. What is the result of this expression: `5 > 3 && 2 < 1`?
*a) `false` — both conditions must be true for `&&`, and `2 < 1` is false
b) `true` — at least one condition is true
c) `5` — the first truthy value is returned
d) An error is thrown

11. What does the ternary operator `condition ? a : b` return?
*a) `a` if the condition is true, `b` if it is false
b) `b` if the condition is true, `a` if it is false
c) Always `a`
d) The condition itself

12. Which array method adds one or more items to the END of an array?
*a) `push()`
b) `unshift()`
c) `concat()`
d) `splice()`

13. What index does the first item in an array have?
*a) 0
b) 1
c) -1
d) The length of the array

14. What does `array.length` return?
*a) The number of items in the array
b) The index of the last item
c) The size of each item in bytes
d) The maximum number of items the array can hold

15. Which of the following correctly creates a `for` loop that counts from 1 to 5?
*a) `for (let i = 1; i <= 5; i++) { }`
b) `for (let i = 0; i < 5; i++) { }`
c) `for (let i = 1; i < 5; i++) { }`
d) `for (let i = 1; i <= 5; i--) { }`

16. What does a `while` loop check before each iteration?
*a) Whether its condition is still `true`
b) Whether the loop has run at least once
c) Whether the iterator variable is a number
d) Whether the previous iteration had an error

17. What does `break` do inside a loop?
*a) Exits the loop immediately
b) Skips the current iteration and goes to the next one
c) Restarts the loop from the beginning
d) Pauses the loop for one iteration

18. What is a function parameter?
*a) A variable listed in the function definition that receives a value when the function is called
b) The value that a function returns
c) A variable declared inside the function body
d) The name of the function

19. What does `return` do in a function?
*a) Sends a value back to wherever the function was called and exits the function
b) Prints the value to the console
c) Stores the value in a global variable
d) Restarts the function with the new value

20. What is an arrow function?
*a) A shorter syntax for writing a function using `=>`
b) A function that only works with arrays
c) A function that automatically returns `this`
d) A function that runs immediately when declared

21. What does `array.map(callback)` return?
*a) A new array where each item is the result of calling the callback on the original item
b) The original array with items modified in place
c) A filtered version of the array with some items removed
d) The sum of all items in the array

22. What does `array.filter(callback)` return?
*a) A new array containing only the items for which the callback returns `true`
b) A new array with every item transformed by the callback
c) The first item in the array that matches the condition
d) A count of how many items match the condition

23. Which array method runs a callback once for each item but does NOT return a new array?
*a) `forEach()`
b) `map()`
c) `filter()`
d) `reduce()`

24. What does `array.find(callback)` return?
*a) The first item in the array for which the callback returns `true`
b) The index of the first matching item
c) All items that match the condition
d) `true` or `false` depending on whether any item matches

25. What does `array.includes(value)` return?
*a) `true` if the value is in the array, `false` if it is not
b) The index of the value in the array
c) A new array with the value added
d) The number of times the value appears

26. Which of the following creates an object with two properties?
*a) `const book = { title: "Dune", year: 1965 };`
b) `const book = [ title: "Dune", year: 1965 ];`
c) `const book = ("title", "Dune", "year", 1965);`
d) `const book = new Object["title", "year"];`

27. Given `const p = { name: "Lee", age: 30 }`, what does `"age" in p` return?
*a) `true`
b) `false`
c) `30`
d) `undefined`

28. What is the result of this code?
```javascript
const x = { val: 5 };
const y = x;
y.val = 99;
console.log(x.val);
```
*a) 99 — objects are passed by reference, so `x` and `y` point to the same object
b) 5 — `x` was not changed directly
c) undefined — `val` was overwritten
d) An error — you cannot reassign properties of `const`

29. What does `Object.keys({ a: 1, b: 2 })` return?
*a) `["a", "b"]`
b) `[1, 2]`
c) `[["a", 1], ["b", 2]]`
d) `2`

30. Inside an object method, `this.name` refers to:
*a) The `name` property of the object the method belongs to
b) The name of the method itself
c) The name of the file
d) The global `name` variable

31. Which of the following correctly destructures `name` and `age` from a `person` object?
*a) `const { name, age } = person;`
b) `const [name, age] = person;`
c) `const name, age = person;`
d) `const {person.name, person.age} = person;`

32. What does this code log?
```javascript
const settings = { theme: "dark" };
const { theme, fontSize = 16 } = settings;
console.log(fontSize);
```
*a) 16 — `fontSize` is not in the object, so the default is used
b) undefined — defaults are not allowed in destructuring
c) "dark" — it takes the existing property value
d) An error is thrown

33. What does `const merged = { ...obj1, ...obj2 }` do when both objects have a key called `color`?
*a) The `color` value from `obj2` overwrites the one from `obj1`
b) Both values are kept in an array under `color`
c) The `color` value from `obj1` is kept and `obj2`'s is ignored
d) An error is thrown because of the duplicate key

34. What does `new` do when used with a class?
*a) Creates a new instance of the class and runs the constructor
b) Resets all existing instances to their default values
c) Creates a copy of the class definition
d) Converts the class to a plain object

35. Why do class names start with a capital letter?
*a) It is a strong convention that tells other developers the name refers to a class
b) JavaScript requires it — lowercase class names cause errors
c) It makes the class run faster
d) It prevents the class from being accidentally called without `new`

36. Given `class Shape { constructor(color) { this.color = color; } }`, what is `new Shape("red").color`?
*a) "red"
b) undefined
c) "color"
d) An error is thrown

37. Which statement about class methods is true?
*a) All instances of a class share the same method definitions
b) Each instance stores its own copy of every method
c) Methods can only be called using `new`
d) Methods cannot use `this`

38. What does `instanceof` return?
*a) `true` if the object was created from a specific class, `false` otherwise
b) The class name as a string
c) The number of instances of a class
d) `true` if the object is any kind of object

39. What type of scope does a variable declared with `let` inside an `if` block have?
*a) Block scope — accessible only inside that `if` block
b) Function scope — accessible anywhere in the enclosing function
c) Global scope — accessible everywhere in the file
d) Loop scope — accessible only on the first iteration

40. What is the output of this code?
```javascript
var x = "outer";
if (true) {
  var x = "inner";
}
console.log(x);
```
*a) "inner" — `var` is not block-scoped, so the inner `x` overwrites the outer one
b) "outer" — `var` inside a block is separate from the outer variable
c) undefined — `var` inside a block is deleted when the block ends
d) An error is thrown

41. What is the output of this code?
```javascript
const animal = "cat";
function test() {
  const animal = "dog";
  console.log(animal);
}
test();
```
*a) "dog" — the inner `animal` shadows the outer one inside the function
b) "cat" — functions always look at global variables
c) undefined — the inner declaration hides both values
d) An error because `animal` is declared twice

42. What is hoisting?
*a) JavaScript's behavior of processing variable and function declarations before running the code
b) Moving a variable's value to the top of the file
c) Running a function before it is needed
d) Copying a variable from inner scope to outer scope

43. What is a closure?
*a) A function that has access to variables from its outer scope, even after the outer function has returned
b) A function that runs immediately when defined
c) A special syntax for writing shorter functions
d) A function that cannot be called more than once

44. In a closure, why does the inner function still have access to the outer function's variable after the outer function has returned?
*a) The inner function holds a reference to the outer function's scope, keeping the variables alive
b) JavaScript automatically copies the variable into the inner function
c) The variable is stored in a global object called `closures`
d) `let` and `const` variables are never deleted

45. What will this code log?
```javascript
function outer() {
  let secret = 42;
  return function() {
    return secret;
  };
}
const getSecret = outer();
console.log(getSecret());
```
*a) 42 — the inner function has closed over the `secret` variable
b) undefined — `secret` no longer exists after `outer()` returns
c) An error — inner functions cannot access outer variables
d) null

46. Which array method would you use to get only the books that are available from an array of book objects?
*a) `filter()`
b) `map()`
c) `forEach()`
d) `find()`

47. Which array method would you use to create an array of just the titles from an array of book objects?
*a) `map()`
b) `filter()`
c) `forEach()`
d) `includes()`

48. What is the correct way to call a method `describe()` on an instance stored in `book1`?
*a) `book1.describe()`
b) `describe(book1)`
c) `Book.describe(book1)`
d) `book1->describe()`

49. You define `class Book { constructor(title) { this.title = title; } }`. What is wrong with `const b = Book("Dune")`?
*a) `new` is missing — classes must be called with `new Book("Dune")`
b) The argument must be a number, not a string
c) Classes cannot have constructors with parameters
d) Nothing — this code is correct

50. What does the `for...in` loop iterate over?
*a) The property names (keys) of an object
b) The values of an object
c) The items in an array by index
d) The characters in a string

51. Given `const nums = [10, 20, 30]`, what does `nums.map(n => n * 2)` return?
*a) `[20, 40, 60]`
b) `[10, 20, 30]` — map does not modify the original
c) `60`
d) `undefined`

52. What does `array.reduce(callback, initialValue)` do?
*a) Combines all array items into a single value by applying the callback repeatedly
b) Removes items from the array one by one
c) Creates a smaller version of the array
d) Finds the smallest value in the array

53. What type does `typeof null` return in JavaScript?
*a) `"object"` — this is a known quirk of JavaScript
b) `"null"`
c) `"undefined"`
d) `"empty"`

54. What is the difference between `==` and `===`?
*a) `==` checks value only (with type coercion); `===` checks both value and type
b) `===` checks value only; `==` checks both value and type
c) They are identical — there is no practical difference
d) `==` is for numbers; `===` is for strings

55. Which of the following correctly uses a template literal to build a greeting?
*a) `` `Hello, ${name}!` ``
b) `"Hello, " + ${name} + "!"`
c) `'Hello, {name}!'`
d) `` "Hello, `${name}`!" ``

56. What does `continue` do inside a loop?
*a) Skips the rest of the current iteration and moves to the next one
b) Exits the loop completely
c) Restarts the loop from the first iteration
d) Runs the loop body one more time before stopping

57. Which of the following is true about arrow functions?
*a) They do not have their own `this` binding
b) They always return `undefined` unless explicitly returning a value
c) They cannot accept parameters
d) They must be written on a single line

58. What does `array.some(callback)` return?
*a) `true` if at least one item passes the callback's test, `false` otherwise
b) `true` only if every item passes the test
c) The first item that passes the test
d) The number of items that pass the test

59. You have a closure-based counter. After calling `counter.increment()` five times and then `counter.reset()`, what should `counter.value()` return?
*a) 0 — reset sets the count back to zero
b) 5 — reset does not change the count
c) undefined — the count was deleted by reset
d) An error — closures cannot be reset

60. Which of the following best describes the JavaScript event loop?
*a) JavaScript runs one thing at a time; async tasks wait in a queue and run when the main thread is free
b) JavaScript runs multiple tasks at the same time using multiple threads
c) The event loop controls how variables are assigned values
d) The event loop is how `for` loops keep track of their counter

61. What does this code log?
```javascript
let x = "10";
x *= 2;
console.log(typeof x);
```
a) "string"
*b) "number"
c) "boolean"
d) "undefined"

62. What does this code log?
```javascript
const items = ["a", "b", "c", "d"];
items.splice(1, 2);
console.log(items);
```
a) ["a", "b", "c", "d"]
b) ["b", "c"]
*c) ["a", "d"]
d) ["a", "b"]

63. What does this code log?
```javascript
function add(a, b = 10) { return a + b; }
console.log(add(5));
```
a) 5
b) undefined
*c) 15
d) An error

64. What does this code log?
```javascript
const obj = { x: 1, y: 2, z: 3 };
const { x, ...rest } = obj;
console.log(Object.keys(rest).length);
```
a) 1
*b) 2
c) 3
d) undefined

65. What does this code log?
```javascript
class Animal {
  constructor(name) { this.name = name; }
}
class Cat extends Animal {
  speak() { return this.name + " says meow"; }
}
const c = new Cat("Whiskers");
console.log(c.speak());
```
*a) "Whiskers says meow"
b) "Cat says meow"
c) "Animal says meow"
d) undefined

66. What does this code log?
```javascript
const ops = [];
for (let i = 0; i < 3; i++) {
  ops.push(() => i);
}
console.log(ops[2]());
```
a) 3
*b) 2
c) 0
d) undefined

67. What does this code log?
```javascript
function outer() {
  let n = 5;
  return () => n * 2;
}
const fn = outer();
console.log(fn());
```
a) undefined
b) 5
*c) 10
d) An error — outer has already returned

68. What does this code log?
```javascript
const scores = [70, 85, 90, 60, 78];
const high = scores.filter(s => s >= 80).map(s => s + " pts");
console.log(high);
```
a) [70, 85, 90, 60, 78]
b) ["85 pts", "90 pts", "78 pts"]
*c) ["85 pts", "90 pts"]
d) ["80 pts", "85 pts", "90 pts"]

69. What does this code log?
```javascript
const car = { maker: "Volvo" };
function describe() { return "Made by " + this.maker; }
const bound = describe.bind(car);
console.log(bound());
```
a) "Made by undefined"
b) "Made by describe"
*c) "Made by Volvo"
d) An error

70. What does this code log?
```javascript
class Counter {
  #n = 0;
  add(x) { this.#n += x; return this; }
  value() { return this.#n; }
}
const c = new Counter();
c.add(5).add(3).add(2);
console.log(c.value());
```
a) 5
b) 8
*c) 10
d) undefined
