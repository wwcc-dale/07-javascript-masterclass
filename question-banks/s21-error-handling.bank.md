---
bank_name: "Session 21: Error Handling — Practice"
---

1. Which error type is thrown when you try to use a variable that has not been declared?
a) TypeError
*b) ReferenceError
c) SyntaxError
d) RangeError

2. Which error type is thrown when you call a number like a function, such as `(5)()`?
a) ReferenceError
b) SyntaxError
*c) TypeError
d) RangeError

3. What does the `finally` block in a try/catch/finally statement do?
a) It only runs if no error was thrown
b) It only runs if an error was thrown
*c) It always runs, whether or not an error was thrown
d) It cancels any error that was thrown

4. What is the correct syntax to throw a custom generic error in JavaScript?
a) `error new Error("message")`
b) `raise new Error("message")`
*c) `throw new Error("message")`
d) `catch new Error("message")`

5. Which property of the error object contains a human-readable description of the error?
a) `error.type`
b) `error.name`
*c) `error.message`
d) `error.text`

6. What does the `catch` block receive as its parameter?
*a) The error object that was thrown
b) The return value of the try block
c) A boolean indicating whether the try block succeeded
d) The line number where the error occurred

7. True or false: A try block must always be followed by both a catch block and a finally block.
a) True
*b) False

8. Which error type would be thrown by `new Array(-1)`?
a) TypeError
b) ReferenceError
*c) RangeError
d) SyntaxError

9. What does `error.name` contain?
a) The file name where the error happened
b) The function name that threw the error
*c) The type of the error (e.g., "TypeError")
d) The variable name that caused the error

10. You want to throw an error with a specific message when a function receives the wrong type of input. Which is the most appropriate error to throw?
a) `throw new RangeError("Wrong type")`
b) `throw new ReferenceError("Wrong type")`
*c) `throw new TypeError("Expected a number")`
d) `throw new SyntaxError("Wrong type")`

11. True or false: You can throw any value in JavaScript, not just Error objects — for example, `throw "something went wrong"` is valid.
*a) True
b) False

12. In a nested try/catch, what happens to an error thrown inside the inner try block if the inner catch block re-throws it?
a) It is silently ignored
b) It is automatically logged to the console
*c) The outer catch block receives it
d) It causes an unhandled error that cannot be caught

13. Which of the following correctly checks whether a caught error is a TypeError?
a) `if (error.type === "TypeError")`
b) `if (error.name instanceof TypeError)`
*c) `if (error instanceof TypeError)`
d) `if (typeof error === "TypeError")`

14. What is the purpose of `error.stack`?
a) It lists all the variables that existed when the error happened
b) It contains the error message repeated multiple times
*c) It shows the call stack — the chain of function calls that led to the error
d) It contains the line count of the file where the error occurred

15. True or false: A try block without a catch block is valid JavaScript as long as it has a finally block.
*a) True
b) False

16. What does this code log?
```javascript
try {
  throw new Error("something broke");
} catch (e) {
  console.log(e.message);
}
```
a) "Error"
*b) "something broke"
c) "e"
d) undefined

17. What does this code log?
```javascript
try {
  console.log("a");
  throw new Error("stop");
  console.log("b");
} catch (e) {
  console.log("c");
}
```
a) "a" "b" "c"
b) "a" "b"
*c) "a" "c"
d) "c"

18. What does this code log?
```javascript
function divide(a, b) {
  if (b === 0) throw new RangeError("Cannot divide by zero");
  return a / b;
}
try {
  console.log(divide(10, 0));
} catch (e) {
  console.log(e.constructor.name + ": " + e.message);
}
```
a) "Error: Cannot divide by zero"
b) Infinity
*c) "RangeError: Cannot divide by zero"
d) undefined

19. What does this code log?
```javascript
try {
  JSON.parse("{bad json}");
} catch (e) {
  console.log("Caught");
} finally {
  console.log("Always");
}
```
a) "Always"
b) "Caught"
*c) "Caught" then "Always"
d) An unhandled SyntaxError

20. What does this code log?
```javascript
function getUser(id) {
  if (id <= 0) throw new TypeError("ID must be positive");
  return { id, name: "User" + id };
}
try {
  const u = getUser(-1);
  console.log(u.name);
} catch (e) {
  console.log(e.message);
}
```
a) "User-1"
*b) "ID must be positive"
c) undefined
d) An unhandled TypeError
