---
bank_name: "Session 7: Loops — Practice"
---

1. Which loop is best when you know exactly how many times you need to repeat?
*a) for loop
b) while loop
c) do...while loop
d) for...in loop

2. What are the three parts inside the parentheses of a `for` loop, separated by semicolons?
a) condition; update; starting point
*b) starting point; condition; update
c) update; starting point; condition
d) condition; starting point; update

3. What does `i++` mean inside a for loop?
a) Multiply i by itself
b) Subtract 1 from i
*c) Add 1 to i
d) Reset i to 0

4. What is an infinite loop?
a) A loop that runs exactly once
b) A loop that skips every other item
*c) A loop that never stops because the condition never becomes false
d) A loop that uses more than one variable

5. True or False: A `do...while` loop always runs its code block at least once, even if the condition is false from the start.
*True
False

6. Which loop is the cleanest way to visit every item in an array without needing an index variable?
a) for loop
b) while loop
c) do...while loop
*d) for...of loop

7. What does `break` do inside a loop?
*a) Exits the loop immediately
b) Skips the current iteration and moves to the next
c) Restarts the loop from the beginning
d) Pauses the loop for one iteration

8. What does `continue` do inside a loop?
a) Exits the loop immediately
*b) Skips the rest of the current iteration and moves to the next
c) Exits the entire program
d) Continues to the next variable declaration

9. Given `const fruits = ["apple", "banana", "cherry"]`, which loop prints each fruit with its index number?
a) `for (const fruit of fruits) { console.log(fruit); }`
*b) `for (const [index, fruit] of fruits.entries()) { console.log(index, fruit); }`
c) `for (let fruit in fruits) { console.log(fruit); }`
d) `while (fruits.length) { console.log(fruits); }`

10. True or False: `for...in` is the recommended way to loop through an array.
True
*False

11. Short answer: What is the output of this loop? `for (let i = 0; i < 3; i++) { console.log(i); }`
* 0, 1, 2 — one per line

12. Which loop checks its condition AFTER running the code block?
a) for loop
b) while loop
*c) do...while loop
d) for...of loop

13. In a `while` loop, what happens if you forget to update the variable inside the loop?
a) The loop runs exactly once and stops
b) JavaScript throws an error automatically
*c) The condition never changes and the loop runs forever (infinite loop)
d) The loop skips the first iteration

14. True or False: `for...in` is designed to iterate over the keys of an object.
*True
False

15. Short answer: What keyword do you use inside a loop to skip the current item and immediately move to the next iteration?
* continue

16. What does this code log?
```javascript
for (let i = 0; i < 3; i++) {
  if (i === 1) continue;
  console.log(i);
}
```
a) 0 1 2
b) 1 2
*c) 0 2
d) 0 1

17. What does this code log?
```javascript
let count = 0;
while (count < 5) {
  count += 2;
}
console.log(count);
```
a) 4
*b) 6
c) 5
d) 2

18. What does this code log?
```javascript
const animals = ["cat", "dog", "bird"];
for (const animal of animals) {
  if (animal === "dog") break;
  console.log(animal);
}
```
*a) "cat"
b) "cat" "dog"
c) "cat" "dog" "bird"
d) Nothing — break exits before anything logs

19. What does this code log?
```javascript
let result = 1;
for (let i = 1; i <= 4; i++) {
  result *= i;
}
console.log(result);
```
a) 10
b) 16
*c) 24
d) 4

20. What does this code log?
```javascript
const nums = [10, 20, 30, 40];
let total = 0;
for (let i = 0; i < nums.length; i++) {
  total += nums[i];
}
console.log(total);
```
a) 40
b) 4
*c) 100
d) undefined
