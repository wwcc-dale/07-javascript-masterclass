---
bank_name: "Session 8: Functions — Practice"
---

1. What is a function in JavaScript?
a) A type of loop that runs automatically
*b) A named block of code you can define once and call many times
c) A special type of variable that holds numbers
d) A built-in command that always runs at the start of a program

2. What keyword is used to send a value back from a function to its caller?
a) send
b) output
*c) return
d) give

3. What is a parameter?
*a) A variable listed in the function definition that receives a value when the function is called
b) The actual value you pass when calling a function
c) A function that calls itself
d) A variable declared outside the function

4. What is an argument?
a) A variable listed in the function definition
*b) The actual value you pass when calling a function
c) A special type of return statement
d) A named block of code

5. True or False: A function declaration is hoisted, meaning you can call it before it appears in the code.
*True
False

6. Which of the following is an arrow function that returns `x * 2`?
a) `function double(x) { return x * 2; }`
b) `const double = function(x) { return x * 2; };`
*c) `const double = x => x * 2;`
d) `double = x => { x * 2 }`

7. What is a default parameter?
*a) A fallback value used when an argument is not provided
b) The first parameter of any function
c) A parameter that cannot be changed
d) A parameter that is required

8. What does a function return if it has no `return` statement?
a) 0
b) null
*c) undefined
d) An empty string

9. True or False: Variables declared inside a function are visible outside the function.
True
*False

10. Which of these is a function expression?
a) `function add(a, b) { return a + b; }`
*b) `const add = function(a, b) { return a + b; };`
c) `const add = a, b => a + b;`
d) `add(a, b) => a + b;`

11. Short answer: What is recursion?
* A function that calls itself — must have a base case to stop

12. What happens if a recursive function has no base case?
a) It returns undefined after one call
b) It throws a syntax error
*c) It calls itself forever until the program crashes with a stack overflow
d) It returns 0 automatically

13. True or False: An arrow function can always be used in place of a regular function expression without any differences.
True
*False

14. Short answer: What is the difference between a function declaration and a function expression?
* A function declaration is hoisted (can be called before it appears in code). A function expression is assigned to a variable and must be defined before it is called.

15. Given `function greet(name = "friend") { return "Hi " + name; }`, what does `greet()` return?
a) "Hi undefined"
b) "Hi "
*c) "Hi friend"
d) An error because no argument was passed

16. What is an IIFE?
a) A function that can only be called once
b) A function that accepts infinite arguments
*c) A function that runs immediately when it is defined
d) A function that calls itself recursively

17. Which of the following is a valid IIFE?
a) `function() { console.log("hi"); }()`
*b) `(function() { console.log("hi"); })()`
c) `function immediately() { console.log("hi"); }`
d) `invoke(function() { console.log("hi"); })`

18. True or False: Variables declared inside an IIFE are accessible from outside it.
True
*False

19. When attaching a function to `onclick`, which is correct?
```javascript
document.getElementById("btn").onclick = _____
```
a) `sayHello()`
*b) `sayHello`
c) `"sayHello"`
d) `call(sayHello)`

20. What does this code log?
```javascript
function double(n) {
  return n * 2;
}
console.log(double(double(3)));
```
a) 3
b) 6
*c) 12
d) undefined

21. What does this code log?
```javascript
const greet = (name) => "Hello, " + name + "!";
console.log(greet("Jordan"));
```
a) Hello, name!
b) greet("Jordan")
*c) Hello, Jordan!
d) undefined

22. What does this code log?
```javascript
(function() {
  const x = 10;
  console.log(x * 3);
})();
```
a) undefined
b) 10
*c) 30
d) An error — IIFE syntax is wrong

23. What does this code log?
```javascript
function countDown(n) {
  if (n === 0) return "done";
  return n + " " + countDown(n - 1);
}
console.log(countDown(3));
```
a) "3 2 1"
b) "0 1 2 3"
*c) "3 2 1 done"
d) An error — countDown never ends
