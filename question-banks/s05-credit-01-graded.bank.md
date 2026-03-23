---
bank_name: "Credit 1: JavaScript Foundations — Graded Quiz Bank"
---

1. Which of the following is a string literal?
a) 42
b) true
*c) "hello"
d) let

2. Which keyword should you use for a variable whose value will NOT change?
a) let
b) var
*c) const
d) fixed

3. Which of the following is a valid JavaScript identifier?
a) 1stPlace
b) my name
*c) firstName
d) let

4. What does `console.log()` do?
a) Creates a new variable
b) Deletes a variable
*c) Prints a value to the browser console
d) Converts a value to a string

5. What is the value of `x` after `let x;` with no assignment?
a) 0
b) null
c) ""
*d) undefined

6. Which naming convention does JavaScript use for multi-word variable names?
a) snake_case
b) PascalCase
*c) camelCase
d) UPPER_CASE

7. True or False: You can reassign a value to a `const` variable.
a) True
*b) False

8. What does `typeof 42` return?
a) "integer"
*b) "number"
c) "float"
d) "digit"

9. What does `typeof "hello"` return?
a) "text"
*b) "string"
c) "word"
d) "char"

10. What does `typeof true` return?
*a) "boolean"
b) "bool"
c) "string"
d) "number"

11. What is the result of `10 % 3`?
a) 3
b) 30
*c) 1
d) 0

12. What does `===` check?
a) Value only
*b) Value AND type
c) Type only
d) It assigns a value

13. What is the result of `2 + 3 * 4`?
a) 20
*b) 14
c) 24
d) 10

14. What is the result of `(2 + 3) * 4`?
*a) 20
b) 14
c) 24
d) 10

15. True or False: `"5" === 5` evaluates to `true`.
a) True
*b) False

16. True or False: `"5" == 5` evaluates to `true`.
*a) True
b) False

17. What does `2 ** 3` evaluate to?
a) 6
*b) 8
c) 9
d) 23

18. What does `x += 5` mean?
a) x is assigned the value 5
*b) x is increased by 5
c) x is multiplied by 5
d) x is compared to 5

19. What does `typeof null` return?
a) "null"
*b) "object"
c) "undefined"
d) "number"

20. Which operator means "strictly not equal"?
a) !=
b) <>
*c) !==
d) =/=

21. What does `"  hello  ".trim()` return?
a) "  hello  "
b) "HELLO"
*c) "hello"
d) ""

22. What does `"hello".toUpperCase()` return?
*a) "HELLO"
b) "Hello"
c) "hello"
d) "HELLO!"

23. What does `"Hello, World!".slice(0, 5)` return?
*a) "Hello"
b) "Hello,"
c) "World"
d) "H"

24. Which of the following correctly uses a template literal?
a) "Hello, " + name + "!"
b) 'Hello, ${name}!'
*c) `Hello, ${name}!`
d) "Hello, {name}!"

25. What does `Math.round(4.6)` return?
a) 4
*b) 5
c) 4.6
d) 6

26. What does `Math.floor(4.9)` return?
*a) 4
b) 5
c) 4.9
d) 3

27. What does `Math.ceil(4.1)` return?
a) 4
*b) 5
c) 4.1
d) 3

28. What does `"JavaScript".includes("Script")` return?
*a) true
b) false
c) "Script"
d) 4

29. True or False: JavaScript is case-sensitive.
*a) True
b) False

30. How do you write a single-line comment in JavaScript?
a) # comment
b) <!-- comment -->
*c) // comment
d) ** comment **

31. What does an `if` statement do?
a) Declares a variable
b) Loops through values
*c) Runs a block of code only if a condition is true
d) Defines a function

32. What does `&&` mean?
a) OR — at least one condition must be true
*b) AND — both conditions must be true
c) NOT — flips the boolean
d) Equals

33. What does `||` mean?
*a) OR — at least one condition must be true
b) AND — both conditions must be true
c) NOT
d) Strictly equal

34. What does `!true` evaluate to?
a) true
*b) false
c) 0
d) undefined

35. What is the purpose of `break` in a `switch` statement?
a) Ends the entire program
b) Skips to the next case
*c) Stops execution after the matching case runs
d) It has no effect

36. What does `default` do in a `switch` statement?
a) Sets the default variable value
b) Runs the first case
*c) Runs when no case matches
d) Ends the switch

37. What will this code log when `score = 75`?
```
if (score >= 90) {
  console.log("A");
} else if (score >= 70) {
  console.log("C");
} else {
  console.log("F");
}
```
a) A
*b) C
c) F
d) Nothing

38. What does this ternary expression return when `age = 20`?
```
age >= 18 ? "adult" : "minor"
```
*a) "adult"
b) "minor"
c) true
d) 20

39. True or False: Once an `else if` condition matches, JavaScript stops checking the remaining conditions.
*a) True
b) False

40. What does `Math.max(3, 7, 2, 9)` return?
a) 3
b) 7
*c) 9
d) 21

41. What does this code log?
```javascript
let score = 0;
score += 10;
score += 5;
score -= 3;
console.log(score);
```
a) 0
b) 10
*c) 12
d) 15

42. What does this code log?
```javascript
const name = "JavaScript";
console.log(name.slice(0, 4));
```
a) "Java"
*b) "Java"
c) "Script"
d) "javascript"

43. What does this code log?
```javascript
const temp = 22;
const weather = temp > 30 ? "hot" : temp > 15 ? "warm" : "cold";
console.log(weather);
```
a) "hot"
*b) "warm"
c) "cold"
d) undefined

44. What does this code log?
```javascript
// let x = 100;
let x = 5;
console.log(x * 2);
```
a) 100
b) 200
*c) 10
d) An error

45. What does this code log?
```javascript
let a = "5";
let b = 5;
console.log(a === b);
console.log(a == b);
```
*a) false / true
b) true / true
c) false / false
d) true / false

46. What does this code log?
```javascript
const nums = [10, 20, 30, 40, 50];
console.log(nums.length);
```
a) 4
*b) 5
c) 50
d) undefined

47. What does this code log?
```javascript
for (let i = 10; i > 0; i -= 3) {
  console.log(i);
}
```
a) 10 7 4 1
*b) 10 7 4 1
c) 10 7 4
d) 10 7

48. What does this code log?
```javascript
function clamp(n, min, max) {
  if (n < min) return min;
  if (n > max) return max;
  return n;
}
console.log(clamp(150, 0, 100));
```
a) 150
b) 0
*c) 100
d) undefined

49. What does this code log?
```javascript
const str = "  Hello World  ";
console.log(str.trim().toLowerCase());
```
a) "  hello world  "
b) "Hello World"
*c) "hello world"
d) "hello world  "

50. What does this code log?
```javascript
let x = 4;
while (x > 0) {
  x--;
}
console.log(x);
```
a) 4
b) 1
*c) 0
d) -1
