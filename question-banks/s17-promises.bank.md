---
bank_name: "Session 17: Promises — Practice"
---

1. What is a Promise in JavaScript?
a) A guarantee that a function will never throw an error
*b) An object that represents a value that will be available in the future
c) A built-in timer that resolves after a delay
d) A special kind of callback function

2. A Promise that is still waiting for its result is in which state?
a) Fulfilled
b) Rejected
*c) Pending
d) Resolved

3. A Promise that has completed successfully is in which state?
*a) Fulfilled
b) Rejected
c) Pending
d) Settled

4. What method do you use to handle the successful result of a Promise?
*a) `.then()`
b) `.catch()`
c) `.resolve()`
d) `.success()`

5. What method do you use to handle a Promise that was rejected?
a) `.then()`
*b) `.catch()`
c) `.fail()`
d) `.reject()`

6. What does `.finally()` do on a Promise?
a) Cancels the Promise if it has not resolved yet
b) Runs only if the Promise is rejected
*c) Runs after the Promise settles, whether it was fulfilled or rejected
d) Returns the final value of the Promise chain

7. True or False: `.then()` returns a new Promise, which allows you to chain multiple `.then()` calls.
*a) True
b) False

8. What does `Promise.all([p1, p2, p3])` do?
*a) Returns a new Promise that fulfills when all three Promises fulfill, with their values in an array
b) Returns the first Promise to fulfill
c) Returns a new Promise that fulfills after the slowest Promise finishes, discarding the other results
d) Runs each Promise one at a time and returns the last result

9. What happens to `Promise.all` if one of the Promises rejects?
a) It ignores the rejected Promise and continues with the others
b) It waits for all Promises to settle before deciding what to do
*c) It immediately rejects with the error from the rejected Promise
d) It returns undefined for the rejected Promise's position in the array

10. What does `Promise.race([p1, p2])` return?
a) The Promise that takes the longest
*b) A new Promise that settles as soon as the first Promise in the array settles
c) An array of all fulfilled values
d) The sum of all resolved values

11. In a chained Promise, where should you place `.catch()` to handle errors from any step?
a) Before the first `.then()`
b) After each `.then()`
*c) At the end of the chain
d) It does not matter where you place it

12. True or False: A Promise can move from "fulfilled" back to "pending".
a) True
*b) False

13. What does this code log?
```js
Promise.resolve("hello")
  .then(val => val.toUpperCase())
  .then(val => console.log(val));
```
a) hello
*b) HELLO
c) undefined
d) Error

14. Which of these correctly creates a Promise that rejects with an error message?
a) `new Promise(() => reject("oops"))`
*b) `new Promise((resolve, reject) => reject("oops"))`
c) `Promise.reject = "oops"`
d) `new Promise((resolve) => throw "oops")`

15. True or False: `Promise.race` is useful for implementing a timeout — you can race the real operation against a delay Promise that rejects after a set time.
*a) True
b) False

16. What does this code log?
```javascript
const p = new Promise((resolve) => resolve(42));
p.then(val => console.log(val * 2));
```
a) 42
*b) 84
c) undefined
d) A Promise object

17. What does this code log?
```javascript
Promise.resolve("hello")
  .then(v => v.toUpperCase())
  .then(v => console.log(v));
```
a) "hello"
*b) "HELLO"
c) undefined
d) An error

18. What does this code log?
```javascript
Promise.reject("oops")
  .catch(err => console.log("Caught: " + err));
```
a) "oops"
*b) "Caught: oops"
c) undefined
d) An unhandled rejection error

19. What does this code log?
```javascript
Promise.all([
  Promise.resolve(1),
  Promise.resolve(2),
  Promise.resolve(3)
]).then(values => console.log(values));
```
a) 1 2 3
*b) [1, 2, 3]
c) 6
d) undefined

20. What does this code log?
```javascript
const p1 = new Promise(resolve => setTimeout(() => resolve("slow"), 200));
const p2 = new Promise(resolve => setTimeout(() => resolve("fast"), 50));
Promise.race([p1, p2]).then(v => console.log(v));
```
a) "slow"
*b) "fast"
c) ["slow", "fast"]
d) undefined
