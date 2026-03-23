---
indent: 2
name: "Assignment: Bank Account Class"
published: false
points_possible: 100
grading_type: points
submission_types:
  - online_upload
allowed_extensions:
  - html
  - js
  - txt
due_at: null
outcomes:
  - 02-OOP
topics:
  - classes
  - constructor
  - instances
---

[lead]You have learned how classes work — now you build one from scratch, create multiple instances, and see the power of writing a template once and using it many times.

# Assignment: Bank Account Class

In this assignment you will define a `BankAccount` class, create several account instances, and use each instance's methods to deposit, withdraw, and display account information. This puts the class pattern to work in a realistic scenario.

- stats
- 100 | Points | success
- online_upload | Submission | accent

---

## Why This Matters

The class pattern appears everywhere in real-world JavaScript. Every time you model data in an application — a user account, a product, a game character — you use a class. Understanding constructors, `this`, instances, and methods is a skill every developer needs.

---

## Skills You Need

Before you start, make sure you can answer these from Session 13:

- What does the `constructor` method do?
- How do you create an instance using `new`?
- What does `this` refer to inside a class method?
- What is the naming convention for class names?
- How do you call a method on an instance?

If any of these are unclear, re-read the Key Concepts section of the Session 13 page.

---

## What You Will Build

You will create a file called `bank-account.html`. Inside it, you will write a `<script>` tag with JavaScript that:

1. Defines a `BankAccount` class with three properties
2. Adds three methods: `deposit()`, `withdraw()`, and `summary()`
3. Creates 3 different account instances
4. Calls methods on each instance and logs the results

---

## Step-by-Step Instructions

- steps: Step-by-Step Instructions
- Step 1 — Create `bank-account.html` using the HTML skeleton below.
- Step 2 — Define a class called `BankAccount`. The `constructor` should accept two parameters: `owner` (a string — the account holder's name) and `balance` (a number — the starting balance). Store both as `this.owner` and `this.balance`.
- Step 3 — Add a `deposit(amount)` method. It should add `amount` to `this.balance`. The method does not need to return anything — just update the balance and log a confirmation like: `"Deposited 50. New balance: 150"`.
- Step 4 — Add a `withdraw(amount)` method. If `amount` is greater than `this.balance`, log `"Insufficient funds"` and do NOT change the balance. Otherwise subtract `amount` from `this.balance` and log: `"Withdrew 30. New balance: 70"`.
- Step 5 — Add a `summary()` method that uses a template literal to return a string like: `"Account: Jordan Park | Balance: $120"`.
- Step 6 — Create three `BankAccount` instances with different owners and starting balances. For example: `new BankAccount("Jordan Park", 100)`, `new BankAccount("Alex Rivera", 500)`, and `new BankAccount("Sam Chen", 0)`.
- Step 7 — For each account: call `deposit()` at least once, call `withdraw()` at least once (including one attempt that should result in "Insufficient funds"), and call `summary()` and log the result with a label.
- Step 8 — Save the file, open it in a browser, check the console output, and upload to Canvas.

**HTML skeleton:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Bank Account Class</title>
</head>
<body>
  <h1>Bank Account Class</h1>
  <p>Open the console to see the output.</p>

  <script>
    // Your JavaScript goes here

  </script>
</body>
</html>
```

---

## Success Criteria

- checklist: Success Criteria
- The file is named `bank-account.html` and opens in a browser without errors
- A `BankAccount` class is defined with a correct `constructor` accepting `owner` and `balance`
- `deposit(amount)` adds to the balance and logs a confirmation
- `withdraw(amount)` checks for sufficient funds before subtracting; logs "Insufficient funds" if not enough
- `summary()` returns a formatted string using a template literal
- Three `BankAccount` instances are created with different owners and starting balances
- Methods are called on each instance and results are logged with labels
- Class name starts with a capital letter (PascalCase)
- Code is neatly indented and easy to read

---

- flow-accordion: Stretch Levels

###### Base — Required for everyone
Complete all steps as described. Define the BankAccount class with all three methods, create 3 instances, and demonstrate deposit, withdraw (including an "Insufficient funds" case), and summary.

###### Intermediate — More challenge
Add a `transactionHistory` property (an empty array in the constructor). Each time `deposit()` or `withdraw()` is called successfully, push a record into `transactionHistory` — an object with `type` ("deposit" or "withdrawal") and `amount`. Add a `printHistory()` method that loops through `transactionHistory` and logs each transaction. Call `printHistory()` on one of your accounts after several transactions.

###### Advanced — Push yourself
Add a `transfer(amount, targetAccount)` method. It should withdraw `amount` from `this` account and deposit it into `targetAccount` — only if `this` has sufficient funds. If not, log "Transfer failed: Insufficient funds". Demonstrate a successful transfer and a failed one. Then write a regular function (outside the class) called `richestAccount(accounts)` that takes an array of BankAccount instances and returns the one with the highest balance. Create 4 accounts, put them in an array, and log `richestAccount(accounts).summary()`.

---

{{include:session-footer}}

{{include:completion-checklist}}
