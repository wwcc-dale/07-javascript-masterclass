---
bank_name: "Session 16: Callbacks and Timers — Practice"
---

1. What is a callback function?
*a) A function passed as an argument to another function and called later
b) A function that calls itself recursively
c) A function that returns another function
d) A function stored in an array

2. Why does JavaScript use callbacks for async operations?
a) Because JavaScript has multiple threads that need to communicate
b) Because callbacks are faster than regular function calls
*c) Because JavaScript is single-threaded and cannot pause while waiting — callbacks let other code run
d) Because callbacks are required by the browser API

3. What does `setTimeout(fn, 2000)` do?
a) Calls `fn` every 2000 milliseconds
*b) Calls `fn` once after 2000 milliseconds
c) Calls `fn` immediately and then again after 2000 milliseconds
d) Waits 2000 seconds before calling `fn`

4. What is the unit of the delay argument in `setTimeout`?
*a) Milliseconds
b) Seconds
c) Microseconds
d) Ticks

5. What does `setInterval(fn, 1000)` do?
a) Calls `fn` once after 1000 milliseconds
*b) Calls `fn` every 1000 milliseconds until stopped
c) Calls `fn` 1000 times total
d) Runs `fn` 1000 milliseconds in the future and stops automatically

6. What function do you use to stop a running `setInterval`?
a) `stopInterval(id)`
b) `removeInterval(id)`
*c) `clearInterval(id)`
d) `cancelInterval(id)`

7. True or False: `setTimeout` returns a value you can use to cancel the timeout.
*a) True
b) False

8. Look at this code. What order do the three `console.log` lines print?
```js
console.log("A");
setTimeout(() => console.log("B"), 0);
console.log("C");
```
a) A, B, C
b) B, A, C
*c) A, C, B
d) C, A, B

9. What is "callback hell"?
a) A runtime error caused by calling too many callbacks
*b) Deeply nested callbacks that are hard to read and maintain
c) A browser warning about overusing setTimeout
d) When a callback is called before it is defined

10. Which of these correctly passes a callback to a function?
*a) `greet("Alex", msg => console.log(msg));`
b) `greet("Alex", console.log(msg));`
c) `greet("Alex", callback: msg => console.log(msg));`
d) `greet("Alex").callback(msg => console.log(msg));`

11. True or False: You can pass a named function (not just an arrow function) as a callback.
*a) True
b) False

12. What happens if you never call `clearInterval` on an interval that you started?
a) The browser throws an error after 10 seconds
b) The interval automatically stops when the function finishes
*c) The interval keeps running indefinitely until the page is closed or refreshed
d) The interval stops after 60 seconds by default

13. What does this code log to the console?
```js
function run(n, callback) {
  callback(n * 2);
}
run(5, result => console.log(result));
```
a) 5
*b) 10
c) undefined
d) NaN

14. Which problem does callback hell create that Promises solve?
a) Callback hell causes JavaScript to run slower
*b) Callback hell creates deeply nested code that is hard to read and handle errors in
c) Callback hell prevents `setTimeout` from working correctly
d) Callback hell uses too much memory

15. True or False: `clearTimeout` can only be called before the timeout fires. Once the timer runs, there is nothing to cancel.
*a) True
b) False

16. What does this code log first?
```javascript
console.log("start");
setTimeout(() => console.log("timeout"), 0);
console.log("end");
```
a) "timeout" "start" "end"
b) "start" "timeout" "end"
*c) "start" "end" "timeout"
d) "end" "start" "timeout"

17. What does this code log?
```javascript
function greet(name, callback) {
  const message = "Hello, " + name + "!";
  callback(message);
}
greet("Sam", msg => console.log(msg));
```
a) "name"
b) "callback"
*c) "Hello, Sam!"
d) undefined

18. What does this code log?
```javascript
const id = setTimeout(() => console.log("fired"), 1000);
clearTimeout(id);
console.log("cleared");
```
a) "fired" then "cleared"
b) "fired"
*c) "cleared"
d) Nothing

19. What does this code log?
```javascript
[1, 2, 3].forEach(function(n) {
  console.log(n * 10);
});
```
*a) 10 20 30
b) [10, 20, 30]
c) 1 2 3
d) undefined

20. What does this code log?
```javascript
let count = 0;
const id = setInterval(() => {
  count++;
  if (count === 3) clearInterval(id);
}, 100);
```
a) Logs 1, 2, 3, 4 ... forever
*b) Runs 3 times then stops
c) Runs once then stops
d) Never runs — setInterval needs a time > 0
