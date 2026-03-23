---
name: "Solution: Session 19 — Built-In Objects"
published: false
outcomes:
  - 04-MOD
topics:
  - built-in-objects
  - math
  - date
  - json
  - set
  - map
---

# Instructor Solution: Session 19 — Built-In Objects

> alert: warning
>
> This page is for instructor reference only. Keep unpublished until after the assignment deadline.

---

## Student Hint

> alert: tip
>
> `Math.random()` gives a number from 0 to less than 1 — multiply by 100 and use `Math.floor()` to get a whole number from 0 to 99, then add 1 to shift the range to 1–100. For word frequency, split the string into an array of words with `.split(" ")`, then loop through the array — for each word, check if the Map has it already and increment, or set it to 1.

---

## Full Solution

Covers all five required sections: `Math` for random integers, `Date` for readable output, `JSON` round-trip serialization, `Set` for deduplication, and `Map` for word frequency counting.

```javascript
// 1. Math — generate 10 random integers from 1 to 100
console.log("=== Math ===");
const randomNumbers = [];
for (let i = 0; i < 10; i++) {
  const num = Math.floor(Math.random() * 100) + 1;
  randomNumbers.push(num);
}
console.log("Random integers:", randomNumbers);
console.log("Max:", Math.max(...randomNumbers));
console.log("Min:", Math.min(...randomNumbers));
console.log("PI:", Math.PI.toFixed(4));

// 2. Date — today in readable format
console.log("\n=== Date ===");
const now = new Date();
console.log("Full date object:", now);
console.log("Locale string:", now.toLocaleDateString("en-US", {
  weekday: "long",
  year:    "numeric",
  month:   "long",
  day:     "numeric"
}));
console.log("Year:", now.getFullYear());
console.log("Month (1-based):", now.getMonth() + 1);  // getMonth() is 0-indexed!
console.log("Day:", now.getDate());
console.log("Day of week:", now.getDay()); // 0=Sunday, 6=Saturday

// 3. JSON — serialize and parse
console.log("\n=== JSON ===");
const user = { name: "Alex", age: 28, hobbies: ["hiking", "coding"], active: true };
const jsonString = JSON.stringify(user, null, 2); // pretty-print with 2-space indent
console.log("Serialized:\n", jsonString);
const parsed = JSON.parse(jsonString);
console.log("Parsed back:", parsed);
console.log("Name from parsed:", parsed.name);
console.log("Are they the same object?", user === parsed); // false — different objects

// 4. Set — remove duplicates
console.log("\n=== Set ===");
const withDuplicates = [1, 2, 3, 2, 4, 3, 5, 1, 6, 2];
const unique = [...new Set(withDuplicates)];
console.log("Original:", withDuplicates);
console.log("Unique:", unique);

const fruitSet = new Set(["apple", "banana", "apple", "cherry", "banana"]);
console.log("Fruit Set size:", fruitSet.size);    // 3
console.log("Has apple?", fruitSet.has("apple")); // true
fruitSet.delete("banana");
console.log("After delete banana:", [...fruitSet]);

// 5. Map — word frequency
console.log("\n=== Map ===");
const sentence = "the quick brown fox jumps over the lazy dog the fox";
const words = sentence.split(" ");
const frequency = new Map();

for (const word of words) {
  frequency.set(word, (frequency.get(word) || 0) + 1);
}

console.log("Word frequency:");
for (const [word, count] of frequency) {
  console.log(`  "${word}": ${count}`);
}

// Sort by frequency
const sorted = [...frequency.entries()].sort((a, b) => b[1] - a[1]);
console.log("\nMost frequent:", sorted[0][0], "×", sorted[0][1]);
```

---

## Instructor Notes

- **Core requirements:** All 5 sections present with visible console output for each.
- **Common mistake:** `Math.random() * 100` without `Math.floor()` — produces decimals instead of integers.
- **Common mistake:** `Math.random() * 100` produces the range 0–99; must add 1 to reach the required 1–100 range.
- **Common mistake:** `now.getMonth()` is 0-indexed — November is returned as `10`, not `11`. This trips up almost every student and is worth highlighting in discussion.
- **Common mistake:** Calling `JSON.parse` on the original object instead of the stringified version — must stringify first.
- **Common mistake:** Map frequency missing the `|| 0` fallback — `frequency.get("unseen-word")` returns `undefined`, and `undefined + 1` evaluates to `NaN`.
- **Intermediate stretch:** Spread `[...new Set(arr)]` to convert a Set back to an array; pretty-printing JSON with `JSON.stringify(obj, null, 2)` (included in solution above).
- **Advanced stretch:** Sorting Map entries by frequency using `[...frequency.entries()].sort()` (included in solution above).
