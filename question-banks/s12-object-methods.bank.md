---
bank_name: "Session 12: Object Methods and Destructuring — Practice"
---

1. What is a method in a JavaScript object?
*a) A function stored as a property of the object
b) A special type of variable used inside an object
c) A property that stores a number
d) A way to delete properties from an object

2. Inside an object method, what does `this` refer to?
*a) The object the method belongs to
b) The global window object
c) The function itself
d) The parent scope of the function

3. Which of the following correctly defines a method called `greet` inside an object?
*a) `greet() { return "Hello"; }`
b) `function greet() { return "Hello"; }`
c) `greet: return "Hello";`
d) `method greet() { return "Hello"; }`

4. Why should you avoid using arrow functions as object methods?
*a) Arrow functions do not have their own `this`, so `this` will not refer to the object.
b) Arrow functions cannot return values.
c) Arrow functions are slower than regular functions.
d) Arrow functions cannot be stored in objects.

5. What is object destructuring?
*a) A shortcut that extracts properties from an object into separate variables
b) A way to delete properties from an object
c) A method that breaks an object into an array
d) A loop that iterates over object properties

6. Given `const person = { name: "Alex", age: 28 };`, which line correctly uses destructuring to get the `name` property?
*a) `const { name } = person;`
b) `const name = person;`
c) `const [name] = person;`
d) `const name == person.name;`

7. Using destructuring, how do you extract the `name` property from `person` and store it in a variable called `fullName`?
*a) `const { name: fullName } = person;`
b) `const { fullName: name } = person;`
c) `const fullName = { name } = person;`
d) `const { name as fullName } = person;`

8. Given `const settings = { theme: "light" };`, what is the value of `fontSize` after this destructuring: `const { fontSize = 14 } = settings;`?
*a) 14 — because `fontSize` is not in the object, the default value is used
b) undefined — defaults are not allowed in destructuring
c) "light" — it takes the first available value
d) An error is thrown because `fontSize` does not exist

9. What does the spread operator (`...`) do when used with objects?
*a) It copies all properties from one object into another
b) It joins two arrays together
c) It removes all properties from an object
d) It converts an object to a string

10. Which line creates a shallow copy of `original` using the spread operator?
*a) `const copy = { ...original };`
b) `const copy = original.spread();`
c) `const copy = Object.copy(original);`
d) `const copy = [...original];`

11. You have `const a = { x: 1 }` and `const b = { y: 2 }`. Which line merges both into a new object `c`?
*a) `const c = { ...a, ...b };`
b) `const c = a.merge(b);`
c) `const c = Object.join(a, b);`
d) `const c = [a, b];`

12. When merging two objects with spread and both have the same key, which value wins?
*a) The value from the object spread last (rightmost) wins
b) The value from the object spread first (leftmost) wins
c) JavaScript throws an error when keys overlap
d) Both values are stored as an array

13. What is a "shallow copy" of an object?
*a) A new object where top-level properties are copied, but nested objects are still shared by reference
b) A complete, fully independent copy of the object and all nested objects
c) A copy that only includes string properties
d) A reference to the same object with a different variable name

14. What does `Object.assign({}, a, b)` do?
*a) Merges objects `a` and `b` into a new empty object and returns it
b) Creates a deep copy of `a` and `b`
c) Checks whether `a` and `b` have the same properties
d) Overwrites `a` with the properties of `b`

15. Given this code, what is logged?
```javascript
const original = { name: "Alex" };
const copy = { ...original };
copy.name = "Sam";
console.log(original.name);
```
*a) "Alex" — the spread creates an independent copy, so the original is not changed
b) "Sam" — the spread still shares the reference
c) undefined — name was deleted when copied
d) An error is thrown

16. What does `bind()` return?
a) The result of calling the function with the given `this`
b) The original object
*c) A new function with `this` permanently set to the specified object
d) A copy of the object

17. What is the difference between `call()` and `apply()`?
a) `call()` runs the function later; `apply()` runs it now
b) `call()` sets `this` to null; `apply()` sets `this` to the first argument
*c) Both run the function immediately with a given `this`, but `call` takes arguments one by one while `apply` takes them as an array
d) There is no difference — they are aliases for the same function

18. What does this code log?
```javascript
const dog = { name: "Rex" };
function bark() {
  console.log(this.name + " says woof!");
}
bark.call(dog);
```
a) "undefined says woof!"
b) "dog says woof!"
*c) "Rex says woof!"
d) An error — bark is not a method of dog

19. Which call passes `100` correctly to the `drive` function using `apply()`?
```javascript
const car = { maker: "Honda" };
function drive(speed) { console.log(this.maker + " at " + speed); }
```
a) `drive.apply(car, 100)`
*b) `drive.apply(car, [100])`
c) `drive.apply([car, 100])`
d) `drive.apply(car)(100)`

20. What does this code log?
```javascript
const person = { name: "Sam", age: 30, city: "Dunedin" };
const { name, city } = person;
console.log(city + " - " + name);
```
a) "Sam - Dunedin"
b) "city - name"
*c) "Dunedin - Sam"
d) undefined

21. What does this code log?
```javascript
const obj = { x: 5 };
function addY(y) {
  return this.x + y;
}
const bound = addY.bind(obj);
console.log(bound(3));
```
a) undefined
b) 5
*c) 8
d) An error because addY is not inside obj
