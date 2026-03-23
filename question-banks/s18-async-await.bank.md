---
bank_name: "Session 18: Async/Await — Practice"
---

1. What does the `async` keyword do when placed before a function declaration?
*a) It makes the function always return a Promise, and allows the use of `await` inside it
b) It makes the function run immediately without waiting for other code
c) It makes the function run in a separate thread
d) It makes the function synchronous

2. What does `await` do inside an async function?
a) It runs the next line of code immediately without waiting
*b) It pauses execution of the async function until the awaited Promise settles, then gives you the resolved value
c) It creates a new Promise from the expression
d) It throws an error if the Promise rejects

3. True or False: You can use `await` outside of an async function in a regular script.
a) True
*b) False

4. What is the correct syntax to define an async function?
*a) `async function doWork() { ... }`
b) `function async doWork() { ... }`
c) `function doWork() async { ... }`
d) `await function doWork() { ... }`

5. What do you use to handle errors when using `await` inside an async function?
a) `.catch()` on the function call
b) `Promise.catch()` inside the function
*c) A `try/catch` block around the `await` expression
d) An `onerror` event handler

6. What does `finally` do in a try/catch/finally block in an async function?
a) Runs only if an error was caught
b) Runs only if no error occurred
*c) Runs after the try and catch blocks complete, regardless of whether an error occurred
d) Cancels the pending Promise

7. Look at this code. Approximately how long does it take to complete?
```js
async function run() {
  await delay(500);
  await delay(500);
  await delay(500);
}
```
a) About 500 ms
b) About 250 ms
*c) About 1500 ms
d) It depends on the browser

8. How do you run three independent async operations in parallel using async/await?
*a) `const [a, b, c] = await Promise.all([op1(), op2(), op3()]);`
b) `await op1(); await op2(); await op3();`
c) `async { op1(); op2(); op3(); }`
d) `await [op1(), op2(), op3()];`

9. True or False: An `async` function that throws an error returns a rejected Promise.
*a) True
b) False

10. What is the return type of every async function?
*a) A Promise
b) A plain value (number, string, etc.)
c) undefined
d) An array

11. Which approach is faster when the operations do not depend on each other?
a) Sequential `await` calls
*b) `await Promise.all([...])` for parallel execution
c) They always take the same amount of time
d) Nested async functions

12. What does this code log to the console?
```js
async function getValue() {
  return 42;
}
getValue().then(v => console.log(v));
```
a) undefined
b) A Promise object
*c) 42
d) Error — you cannot use .then() on an async function

13. True or False: You can `await` a regular (non-Promise) value inside an async function. It simply gives you the value immediately.
*a) True
b) False

14. In this code, what happens at the `await` line?
```js
async function load() {
  const data = await fetchSomething();
  console.log(data);
}
```
a) `fetchSomething()` is called but the result is ignored
b) JavaScript pauses the entire program until `fetchSomething()` resolves
*c) Execution of `load()` is paused until the Promise returned by `fetchSomething()` resolves; other code can still run
d) An error is thrown because `fetchSomething()` is not defined as async

15. When should you use sequential `await` calls instead of `Promise.all`?
*a) When each step depends on the result of the previous step
b) When you want faster execution
c) When you have more than three Promises
d) When the Promises might reject

16. What does this code log?
```javascript
async function getValue() {
  return 42;
}
getValue().then(v => console.log(v));
```
a) An error — async functions cannot return plain values
b) A Promise object
*c) 42
d) undefined

17. What does this code log?
```javascript
async function run() {
  const result = await Promise.resolve("done");
  console.log(result);
}
run();
```
a) A Promise
b) undefined
*c) "done"
d) An error

18. What does this code log?
```javascript
async function risky() {
  throw new Error("oops");
}
risky().catch(e => console.log(e.message));
```
a) Nothing — you cannot catch async errors with .catch
*b) "oops"
c) "Error: oops"
d) undefined

19. What does this code log?
```javascript
async function main() {
  try {
    const val = await Promise.reject("fail");
  } catch (e) {
    console.log("Caught: " + e);
  }
}
main();
```
a) "fail"
*b) "Caught: fail"
c) Nothing — await cannot reject inside try
d) An unhandled rejection

20. What does this code log?
```javascript
async function double(n) {
  return n * 2;
}
async function main() {
  const a = await double(5);
  const b = await double(a);
  console.log(b);
}
main();
```
a) 5
b) 10
*c) 20
d) undefined
