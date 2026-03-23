---
bank_name: "Session 14: Scope and Closures — Practice"
---

1. What is scope in JavaScript?
*a) The region of code where a variable can be accessed
b) The amount of memory a variable uses
c) The order in which statements run
d) The type of a variable

2. A variable declared outside all functions and blocks is in which scope?
*a) Global scope
b) Function scope
c) Block scope
d) Module scope

3. Which keyword(s) create a variable with block scope?
*a) `let` and `const`
b) `var`
c) `function`
d) `class`

4. What happens if you try to access a `let` variable outside the block where it was declared?
*a) A ReferenceError is thrown
b) The value is `undefined`
c) The value is `null`
d) JavaScript searches the outer scope automatically

5. A variable declared with `var` inside a `for` loop is accessible:
*a) Outside the loop, in the surrounding function or global scope
b) Only inside the loop body
c) Only on the iteration it was declared
d) Nowhere — `var` in a loop creates a constant

6. What is variable shadowing?
*a) When an inner scope variable has the same name as an outer scope variable, hiding the outer one
b) When two variables hold the same value
c) When a variable is declared but never used
d) When a function parameter overwrites a global variable permanently

7. Given this code, what is logged by `console.log(color)` inside the function?
```javascript
const color = "blue";
function paintIt() {
  const color = "red";
  console.log(color);
}
paintIt();
```
*a) "red" — the inner `color` shadows the outer one
b) "blue" — functions always use the global value
c) undefined — the inner declaration hides both values
d) An error — you cannot use the same name twice

8. What is hoisting?
*a) JavaScript's behavior of moving variable declarations to the top of their scope before code runs
b) The process of copying variables from one scope to another
c) The way `const` prevents variable reassignment
d) How JavaScript handles errors in nested functions

9. A `var` variable is hoisted and initialized to what value?
*a) `undefined`
b) `null`
c) `0`
d) It is not initialized — accessing it throws an error

10. What is the Temporal Dead Zone (TDZ)?
*a) The period before a `let` or `const` variable's declaration where it cannot be accessed
b) The time it takes JavaScript to hoist a `var` variable
c) A zone where `var` variables are stored before being used
d) An area of memory used for deleted variables

11. Which type of function declaration is fully hoisted (name and body)?
*a) `function greet() { }` (a function declaration)
b) `const greet = function() { }` (a function expression)
c) `const greet = () => { }` (an arrow function expression)
d) All three are hoisted equally

12. What is a closure?
*a) A function that remembers variables from its surrounding scope, even after that outer scope has finished
b) A function that cannot be called more than once
c) A variable that cannot be changed after it is declared
d) A block of code that runs immediately when the script loads

13. In the code below, what is logged after calling `counter()` three times?
```javascript
function makeCounter() {
  let count = 0;
  return function() {
    count++;
    return count;
  };
}
const counter = makeCounter();
counter();
counter();
console.log(counter());
```
*a) 3
b) 1
c) undefined
d) An error is thrown

14. Why does the `count` variable in a closure not reset to 0 every time the returned function is called?
*a) Because the closure keeps a reference to the outer function's variable, not a new copy each time
b) Because `let` variables never reset
c) Because closures always share a global variable
d) Because the `count` variable is stored in the class

15. What is a practical benefit of using a closure?
*a) It creates private state — variables that outside code cannot directly read or change
b) It makes code run faster than regular functions
c) It automatically saves data to the browser
d) It allows a function to run before it is defined

16. What does this code log?
```javascript
let x = 10;
function show() {
  let x = 20;
  console.log(x);
}
show();
```
a) 10
*b) 20
c) undefined
d) An error — you cannot declare x twice

17. What does this code log?
```javascript
var a = 1;
if (true) {
  var a = 2;
}
console.log(a);
```
a) 1
*b) 2
c) undefined
d) An error — a is declared twice

18. What does this code log?
```javascript
let b = 1;
if (true) {
  let b = 2;
}
console.log(b);
```
*a) 1
b) 2
c) undefined
d) An error

19. What does this code log?
```javascript
const ops = [];
for (var i = 0; i < 3; i++) {
  ops.push(() => i);
}
console.log(ops[0]());
```
a) 0
b) 1
*c) 3
d) undefined

20. What does this code log? (Same as above but with let)
```javascript
const ops = [];
for (let i = 0; i < 3; i++) {
  ops.push(() => i);
}
console.log(ops[0]());
```
*a) 0
b) 1
c) 3
d) undefined

21. What does this code log?
```javascript
function outer() {
  let count = 0;
  return function() {
    count++;
    return count;
  };
}
const inc = outer();
inc();
inc();
console.log(inc());
```
a) 1
b) 2
*c) 3
d) 0 — count resets each time
