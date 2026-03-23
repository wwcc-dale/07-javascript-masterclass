---
bank_name: "Session 4: Conditional Logic — Practice"
---

1. What does an `if` statement do?
a) Declares a new variable
b) Loops through a list of values
*c) Runs a block of code only if a condition is true
d) Defines a reusable function

2. What runs when an `if` condition is false and an `else` is present?
a) The if block runs anyway
b) Nothing runs
*c) The else block runs
d) JavaScript throws an error

3. What is the correct syntax for an `if` statement?
a) if [score > 90] { ... }
b) if score > 90 { ... }
*c) if (score > 90) { ... }
d) if: score > 90 { ... }

4. What does `&&` mean?
a) OR — at least one condition must be true
*b) AND — both conditions must be true
c) NOT — flips the boolean
d) Equals — checks if two values are the same

5. What does `||` mean?
*a) OR — at least one condition must be true
b) AND — both conditions must be true
c) NOT — flips the boolean
d) Strictly equal

6. What does `!true` evaluate to?
a) true
*b) false
c) 0
d) undefined

7. What is the purpose of `break` in a `switch` statement?
a) It ends the entire program
b) It skips to the next case
*c) It stops execution after the matching case runs
d) It is optional and has no effect

8. What is the ternary operator syntax?
a) value1 : value2 ? condition
b) if condition then value1 else value2
*c) condition ? valueIfTrue : valueIfFalse
d) condition -> value1 | value2

9. What does `default` do in a `switch` statement?
a) Sets the default variable value
b) Runs the first case every time
*c) Runs when no case matches
d) Ends the switch statement

10. True or False: `else if` allows you to check multiple conditions in sequence.
*a) True
b) False

11. What will this code log?
```
let score = 75;
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

12. What does this ternary expression return when `age = 20`?
```
age >= 18 ? "adult" : "minor"
```
*a) "adult"
b) "minor"
c) true
d) 20

13. True or False: Once an `else if` condition matches, JavaScript will continue checking the remaining conditions.
a) True
*b) False

14. Which logical operator flips a boolean value?
a) &&
b) ||
*c) !
d) ==

15. How many blocks will run in an if/else if/else chain?
a) All of them
b) None of them
*c) Exactly one — the first matching block
d) It depends on the number of conditions

16. What does this code log?
```javascript
const x = 15;
if (x > 10 && x < 20) {
  console.log("in range");
} else {
  console.log("out of range");
}
```
*a) "in range"
b) "out of range"
c) true
d) false

17. What does this code log?
```javascript
const score = 72;
const grade = score >= 90 ? "A" : score >= 60 ? "B" : "C";
console.log(grade);
```
a) "A"
*b) "B"
c) "C"
d) undefined

18. What does this code log?
```javascript
const car = { color: "green" };
const color = car && car.color;
console.log(color);
```
a) true
b) false
*c) "green"
d) undefined

19. What does this code log?
```javascript
const val = null || "default";
console.log(val);
```
a) null
b) false
*c) "default"
d) undefined

20. What does this code log?
```javascript
let day = "Monday";
switch(day) {
  case "Monday":
  case "Tuesday":
    console.log("Early week");
    break;
  case "Friday":
    console.log("End of week");
    break;
  default:
    console.log("Midweek");
}
```
*a) "Early week"
b) "End of week"
c) "Midweek"
d) Nothing — Monday has no break before Tuesday
