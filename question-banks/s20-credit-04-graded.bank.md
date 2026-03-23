---
bank_name: "Credit 4: Async JavaScript — Graded Quiz Bank"
---

1. What is a callback function?
*a) A function passed as an argument to another function and called later
b) A function that calls itself recursively
c) A function stored in a variable
d) A function that returns a Promise

2. Why does JavaScript need callbacks for async operations?
*a) JavaScript is single-threaded and cannot block while waiting — callbacks let other code run in the meantime
b) JavaScript runs callbacks on a separate thread to avoid blocking
c) Callbacks are the only way to define functions in JavaScript
d) The browser requires callbacks for all timer functions

3. What does `setTimeout(fn, 3000)` do?
a) Calls `fn` every 3000 milliseconds
*b) Calls `fn` once after 3000 milliseconds
c) Pauses all JavaScript execution for 3000 milliseconds
d) Calls `fn` 3000 times

4. What does `clearInterval(id)` do?
a) Clears the browser console
b) Cancels a pending `setTimeout`
*c) Stops a running `setInterval`
d) Resets the interval timer to zero

5. What is "callback hell"?
*a) Deeply nested callbacks that are hard to read and maintain
b) An error caused by calling too many callbacks in a row
c) A browser warning about slow callback performance
d) When a callback function throws an unhandled error

6. True or False: `setInterval` automatically stops after the callback runs once.
a) True
*b) False

7. Which of these correctly passes a named function as a callback?
```js
function sayHello(msg) { console.log(msg); }
```
*a) `greet("Alex", sayHello);`
b) `greet("Alex", sayHello());`
c) `greet("Alex", callback(sayHello));`
d) `greet("Alex", return sayHello);`

8. What are the three states of a Promise?
a) Loading, success, failure
*b) Pending, fulfilled, rejected
c) Waiting, resolved, errored
d) Idle, running, complete

9. What does calling `resolve(value)` inside a Promise constructor do?
*a) Moves the Promise from pending to fulfilled with the given value
b) Moves the Promise from pending to rejected
c) Cancels the Promise
d) Calls the `.then()` handler immediately

10. Which method runs when a Promise is rejected?
a) `.then()`
*b) `.catch()`
c) `.resolve()`
d) `.error()`

11. True or False: A Promise can be rejected after it has already been fulfilled.
a) True
*b) False

12. What does `.finally()` do on a Promise?
*a) Runs after the Promise settles regardless of whether it was fulfilled or rejected
b) Runs only when the Promise is rejected
c) Cancels the Promise if it has not yet settled
d) Returns the final resolved value

13. What does `Promise.all([p1, p2, p3])` return if p2 rejects?
a) A Promise that fulfills with the results of p1 and p3 only
b) A Promise that fulfills with undefined for p2's position
*c) A rejected Promise with p2's rejection reason
d) It waits for all Promises to finish before deciding

14. What does `Promise.race([p1, p2])` settle with?
*a) The result of whichever Promise settles first
b) The result of both Promises as an array
c) The result of the slowest Promise
d) An error if either Promise rejects

15. In a Promise chain, where should you place `.catch()` to handle errors from any step?
*a) At the end of the chain
b) Before each `.then()`
c) At the beginning of the chain
d) It does not matter where you place it

16. True or False: `.then()` returns a new Promise.
*a) True
b) False

17. What does the `async` keyword do when placed before a function?
*a) Makes the function always return a Promise and allows the use of `await` inside it
b) Makes the function run synchronously
c) Makes the function run in a Web Worker
d) Makes the function return a callback

18. What does `await` do inside an async function?
a) Calls the next function in the queue immediately
*b) Pauses the async function until the awaited Promise settles and returns the resolved value
c) Creates a new Promise from the value
d) Logs the value to the console

19. True or False: You can use `await` inside a regular (non-async) function.
a) True
*b) False

20. What is the correct way to handle errors when using `await`?
*a) Wrap the `await` expression in a `try/catch` block
b) Add `.catch()` directly after the `await` keyword
c) Use `window.onerror` to catch async errors
d) Check the return value of `await` for null

21. Look at this async function. Approximately how long does it take to run?
```js
async function run() {
  await delay(300);
  await delay(300);
  await delay(300);
}
```
a) About 300 ms
b) About 150 ms
*c) About 900 ms
d) It varies randomly

22. Which code runs three async operations in parallel?
*a) `const [a, b, c] = await Promise.all([op1(), op2(), op3()]);`
b) `const a = await op1(); const b = await op2(); const c = await op3();`
c) `await (op1, op2, op3);`
d) `await { op1(), op2(), op3() };`

23. True or False: An async function that throws an error returns a rejected Promise.
*a) True
b) False

24. What does `Math.floor(7.9)` return?
*a) 7
b) 8
c) 7.9
d) 0

25. Which formula generates a random integer between 1 and 10?
*a) `Math.floor(Math.random() * 10) + 1`
b) `Math.round(Math.random() * 10)`
c) `Math.random() * 10`
d) `Math.ceil(Math.random() * 9)`

26. What does `new Date().getMonth()` return for February?
a) 2
*b) 1
c) 0
d) "February"

27. You want to display the month as a number from 1 to 12. What code is correct?
*a) `new Date().getMonth() + 1`
b) `new Date().getMonth()`
c) `new Date().getDate()`
d) `new Date().getFullYear()`

28. What does `JSON.stringify({ x: 1, y: 2 })` produce?
*a) `'{"x":1,"y":2}'`
b) `{ x: 1, y: 2 }`
c) `"x=1, y=2"`
d) `[1, 2]`

29. What does `JSON.parse('{"name":"Lee"}')` return?
*a) A JavaScript object: `{ name: "Lee" }`
b) The string `'{"name":"Lee"}'`
c) An array: `["name", "Lee"]`
d) An error because the quotes are wrong

30. What does `"abc".repeat(3)` return?
a) `"abc 3"`
b) `"abcabc"`
*c) `"abcabcabc"`
d) `["abc", "abc", "abc"]`

31. What does `"hello".startsWith("he")` return?
*a) `true`
b) `false`
c) `"he"`
d) 2

32. What does `new Set([5, 5, 5, 6, 7])` contain?
a) `[5, 5, 5, 6, 7]`
*b) `{5, 6, 7}` — only unique values
c) `{6, 7}` — the duplicate value is removed entirely
d) An error

33. How do you add a value to a Set?
*a) `mySet.add(value)`
b) `mySet.push(value)`
c) `mySet[value] = true`
d) `mySet.insert(value)`

34. What does `mySet.has(value)` return?
a) The index of the value in the Set
*b) `true` if the value is in the Set, `false` if not
c) The number of times the value appears
d) The value itself

35. What is the main advantage of `Map` over a plain object?
*a) Map keys can be any type — numbers, booleans, objects — not just strings
b) Maps are always faster than objects
c) Maps allow the same key to appear more than once
d) Maps automatically convert all keys to strings

36. How do you retrieve a value from a Map?
a) `myMap[key]`
*b) `myMap.get(key)`
c) `myMap.value(key)`
d) `myMap.retrieve(key)`

37. What does `parseInt("100px")` return?
*a) 100
b) `"100"`
c) NaN
d) 0

38. What does `(9.999).toFixed(1)` return?
*a) `"10.0"` (a string)
b) `9.9`
c) `10`
d) `"9.999"`

39. You need to run two async tasks where task B must use the result of task A. Which approach is correct?
*a) Sequential: `const a = await taskA(); const b = await taskB(a);`
b) Parallel: `const [a, b] = await Promise.all([taskA(), taskB()]);`
c) They are equivalent; it does not matter
d) You must use callbacks for this pattern

40. True or False: `Date.now()` returns the current time as a number of milliseconds since January 1, 1970. You can subtract two `Date.now()` calls to measure elapsed time.
*a) True
b) False

41. What does this code log first?
```javascript
console.log("A");
setTimeout(() => console.log("B"), 0);
Promise.resolve().then(() => console.log("C"));
console.log("D");
```
a) A B C D
b) A D B C
*c) A D C B
d) A C D B

42. What does this code log?
```javascript
async function run() {
  const a = await Promise.resolve(3);
  const b = await Promise.resolve(4);
  return a + b;
}
run().then(v => console.log(v));
```
a) A Promise
b) 3
*c) 7
d) undefined

43. What does this code log?
```javascript
const s = new Set([1, 1, 2, 3, 3, 4]);
console.log([...s]);
```
a) [1, 1, 2, 3, 3, 4]
*b) [1, 2, 3, 4]
c) 4
d) undefined

44. What does this code log?
```javascript
const m = new Map([["x", 10], ["y", 20]]);
m.set("z", 30);
console.log(m.size);
```
a) 2
*b) 3
c) 30
d) undefined

45. What does this code log?
```javascript
let count = 0;
const id = setInterval(() => {
  count++;
  if (count === 3) {
    clearInterval(id);
    console.log("stopped at " + count);
  }
}, 100);
```
a) "stopped at 1"
b) "stopped at 2"
*c) "stopped at 3"
d) Nothing — setInterval needs a longer interval to work

46. What does this code log?
```javascript
function delay(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}
async function run() {
  await delay(0);
  console.log("after delay");
}
run();
console.log("before await");
```
*a) "before await" then "after delay"
b) "after delay" then "before await"
c) "before await" only
d) "after delay" only

47. What does this code log?
```javascript
const d = new Date(2024, 0, 15);
console.log(d.getMonth());
```
*a) 0
b) 1
c) 15
d) 2024

48. What does this code log?
```javascript
async function fail() {
  throw new Error("broken");
}
async function run() {
  try {
    await fail();
  } catch (e) {
    console.log("handled: " + e.message);
  }
}
run();
```
a) "broken"
*b) "handled: broken"
c) An unhandled rejection
d) Nothing

49. What does this code log?
```javascript
const arr = [1, 2, 3];
arr.forEach((n, i) => {
  if (i === 1) return;
  console.log(n);
});
```
a) 1 2 3
*b) 1 3
c) 2
d) 1

50. What does this code log?
```javascript
Promise.all([
  Promise.resolve(10),
  Promise.resolve(20),
  Promise.resolve(30)
]).then(vals => console.log(vals.reduce((a, b) => a + b)));
```
a) [10, 20, 30]
b) 30
*c) 60
d) undefined
