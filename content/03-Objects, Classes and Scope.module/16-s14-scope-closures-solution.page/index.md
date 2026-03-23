---
indent: 2
name: "Solution: Session 14 — Scope and Closures"
published: false
outcomes:
  - 02-OOP
topics:
  - scope-closures
---

# Instructor Solution: Session 14 — Scope and Closures

> alert: warning
>
> This page is for instructor reference only. Keep unpublished until after the assignment deadline. You may share the hint section verbally or reveal this page to individual students as needed.

---

## Student Hint

> alert: tip
>
> For the closure, write a function that declares a variable AND returns an object with two methods — the returned methods can "see" that inner variable because they close over it. For shadowing, declare a variable with one name in the outer scope, then declare another variable with the exact same name inside a block or function — the inner one shadows the outer one within that scope.

---

## Full Solution

Three separate demonstrations: `let` block scope vs. `var` leakage, variable shadowing at both function and block level, and a closure-based private counter with increment and reset.

```javascript
// ============================================================
// 1. Global vs Block Scope with let
// ============================================================
let globalMessage = "I am global";

{
  let blockMessage = "I am only inside this block";
  console.log("Inside block — global:", globalMessage);  // accessible
  console.log("Inside block — block:", blockMessage);    // accessible
}

console.log("Outside block — global:", globalMessage);   // accessible
// console.log(blockMessage);  // would throw ReferenceError — blockMessage is gone

// var does NOT have block scope — it leaks out:
{
  var leakyVar = "I leaked out of the block!";
}
console.log("var after block:", leakyVar); // accessible (bad!)

// ============================================================
// 2. Variable Shadowing
// ============================================================
let color = "blue";  // outer scope

function paintRoom() {
  let color = "red";  // shadows the outer `color` inside this function
  console.log("Inside paintRoom:", color);  // "red" — inner shadows outer
}

paintRoom();
console.log("Outside paintRoom:", color);  // "blue" — outer unchanged

// Block-level shadowing
let score = 100;
{
  let score = 50;  // shadows in this block only
  console.log("Inner score:", score);   // 50
}
console.log("Outer score:", score);     // 100 — unchanged

// ============================================================
// 3. Closure — private counter
// ============================================================
function makeCounter(startValue = 0) {
  let count = startValue;  // private — not accessible from outside

  return {
    increment() {
      count++;
      return count;
    },
    decrement() {
      count--;
      return count;
    },
    reset() {
      count = startValue;
      return count;
    },
    value() {
      return count;
    }
  };
}

const counter = makeCounter();
console.log("Initial:", counter.value());  // 0
console.log("After increment:", counter.increment()); // 1
console.log("After increment:", counter.increment()); // 2
console.log("After increment:", counter.increment()); // 3
console.log("After reset:", counter.reset());         // 0

const counter2 = makeCounter(10);  // starts at 10
console.log("Counter2 initial:", counter2.value()); // 10
counter2.increment();
console.log("Counter2 after increment:", counter2.value()); // 11

// The two counters are independent — each has its own private `count`
console.log("Counter1 after counter2 increment:", counter.value()); // still 0
```

---

## Instructor Notes

- Core: three clear demonstrations — block scope, shadowing, closure counter — all with console output that proves the behavior
- Common mistake: shadow demo that does not log the outer variable *after* the function returns — without that final log, the student has not proven the outer variable was unchanged
- Common mistake: closure that `console.log`s `count` directly inside `increment` instead of returning it — the return value is what allows callers to observe the encapsulated state cleanly
- Common mistake: using `var` instead of `let` for the closure's private variable — `var` declared inside a function is function-scoped and still works, but using `let` is idiomatic and reinforces the lesson
- Intermediate: `decrement()` method and a `startValue` parameter for `makeCounter` that also resets to the original start value
- Advanced: two independent counters (`counter` and `counter2`) with console output proving their state is truly private from each other; also accepting a `step` parameter to increment by more than 1
