---
bank_name: "Session 11: Objects Basics — Practice"
---

1. Which of the following correctly creates a JavaScript object?
*a) `const person = { name: "Alex", age: 28 };`
b) `const person = [ name: "Alex", age: 28 ];`
c) `const person = (name: "Alex", age: 28);`
d) `const person = "name: Alex, age: 28";`

2. Given `const car = { make: "Toyota", year: 2022 };`, which line correctly reads the `make` property?
*a) `car.make`
b) `car[make]`
c) `car.get("make")`
d) `car->make`

3. Which of the following correctly uses bracket notation to access the `city` property of an object called `address`?
*a) `address["city"]`
b) `address.["city"]`
c) `address{city}`
d) `address(city)`

4. You have `const user = { name: "Sam" };`. How do you add a new `email` property with the value `"sam@example.com"`?
*a) `user.email = "sam@example.com";`
b) `user.add("email", "sam@example.com");`
c) `user["email", "sam@example.com"];`
d) `const user.email = "sam@example.com";`

5. What keyword is used to remove a property from an object?
*a) `delete`
b) `remove`
c) `clear`
d) `drop`

6. After running `delete person.city;`, what does `person.city` return?
*a) `undefined`
b) `null`
c) `""` (empty string)
d) A ReferenceError

7. Which expression checks whether a property called `phone` exists in an object called `contact`?
*a) `"phone" in contact`
b) `contact.has("phone")`
c) `contact.includes("phone")`
d) `"phone" === contact`

8. What does "pass by reference" mean for objects?
*a) When you assign an object to a new variable, both variables point to the same object in memory.
b) When you assign an object to a new variable, JavaScript makes a full copy of the object.
c) Objects cannot be assigned to more than one variable.
d) Changing a property in one variable deletes it from the other.

9. Given the code below, what is logged on the last line?
```javascript
const a = { score: 10 };
const b = a;
b.score = 99;
console.log(a.score);
```
*a) 99
b) 10
c) undefined
d) An error is thrown

10. Which loop is used to iterate over all the properties of an object?
*a) `for...in`
b) `for...of`
c) `forEach`
d) `while`

11. Inside a `for...in` loop, if the loop variable is `key` and the object is `product`, how do you log the value of each property?
*a) `console.log(product[key])`
b) `console.log(product.key)`
c) `console.log(key.product)`
d) `console.log(product(key))`

12. What does `Object.keys(person)` return?
*a) An array of all the property names in the object
b) An array of all the property values in the object
c) An array of `[key, value]` pairs
d) The number of properties in the object

13. What does `Object.values(person)` return?
*a) An array of all the property values in the object
b) An array of all the property names in the object
c) An array of `[key, value]` pairs
d) A copy of the object

14. What does `Object.entries(person)` return?
*a) An array of `[key, value]` arrays, one for each property
b) An array of property names only
c) An array of property values only
d) A new object with the same properties

15. You have `const obj = {};` and then `obj.color = "blue";`. Does this cause an error because `obj` is declared with `const`?
*a) No — `const` prevents reassigning the variable, but you can still change the object's properties.
b) Yes — `const` means the object and all its properties are frozen.
c) Yes — you must use `let` to add properties to an object.
d) No — but only because `obj` was created as an empty object.

16. What does this code log?
```javascript
const person = { name: "Alex", age: 28 };
for (const key in person) {
  console.log(key);
}
```
a) "Alex" 28
*b) "name" "age"
c) ["name", "age"]
d) An error

17. What does this code log?
```javascript
const a = { x: 1 };
const b = a;
b.x = 99;
console.log(a.x);
```
a) 1
*b) 99
c) undefined
d) An error

18. What does this code log?
```javascript
const product = { name: "Widget", price: 9.99, stock: 50 };
console.log(Object.keys(product).length);
```
a) 1
b) 2
*c) 3
d) undefined

19. What does this code log?
```javascript
const obj = { a: 1, b: 2, c: 3 };
delete obj.b;
console.log("b" in obj);
```
a) true
*b) false
c) undefined
d) An error

20. What does this code log?
```javascript
const car = { make: "Honda" };
const key = "make";
console.log(car[key]);
```
a) undefined — bracket notation needs a string literal
b) "key"
*c) "Honda"
d) An error
