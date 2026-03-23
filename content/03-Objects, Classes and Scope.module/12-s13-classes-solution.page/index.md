---
indent: 2
name: "Solution: Session 13 — Bank Account Class"
published: false
outcomes:
  - 02-OOP
topics:
  - classes
  - constructor
  - instances
---

# Instructor Solution: Session 13 — Bank Account Class

> alert: warning
>
> This page is for instructor reference only. Keep unpublished until after the assignment deadline. You may share the hint section verbally or reveal this page to individual students as needed.

---

## Student Hint

> alert: tip
>
> The `constructor` method runs automatically when you write `new BankAccount(owner, balance)`. Use `this.owner` and `this.balance` inside the constructor to save those values to the instance. In `withdraw()`, use an `if` statement to check `amount > this.balance` before subtracting — this is where your conditional logic from Credit 1 comes back into play.

---

## Full Solution

```javascript
class BankAccount {
  constructor(owner, balance) {
    this.owner = owner;
    this.balance = balance;
  }

  deposit(amount) {
    this.balance += amount;
    console.log("Deposited " + amount + ". New balance: " + this.balance);
  }

  withdraw(amount) {
    if (amount > this.balance) {
      console.log("Insufficient funds");
    } else {
      this.balance -= amount;
      console.log("Withdrew " + amount + ". New balance: " + this.balance);
    }
  }

  summary() {
    return `Account: ${this.owner} | Balance: $${this.balance}`;
  }
}

// Create three accounts
const account1 = new BankAccount("Jordan Park", 100);
const account2 = new BankAccount("Alex Rivera", 500);
const account3 = new BankAccount("Sam Chen", 0);

// Account 1 — deposit, withdraw, summary
account1.deposit(50);
account1.withdraw(30);
account1.withdraw(200);  // should log "Insufficient funds"
console.log(account1.summary());

// Account 2 — deposit, withdraw, summary
account2.deposit(100);
account2.withdraw(200);
console.log(account2.summary());

// Account 3 — zero balance, try to withdraw
account3.deposit(25);
account3.withdraw(50);   // should log "Insufficient funds"
console.log(account3.summary());
```

---

## Intermediate Stretch Solution

```javascript
class BankAccount {
  constructor(owner, balance) {
    this.owner = owner;
    this.balance = balance;
    this.transactionHistory = [];   // empty array to start
  }

  deposit(amount) {
    this.balance += amount;
    this.transactionHistory.push({ type: "deposit", amount: amount });
    console.log("Deposited " + amount + ". New balance: " + this.balance);
  }

  withdraw(amount) {
    if (amount > this.balance) {
      console.log("Insufficient funds");
    } else {
      this.balance -= amount;
      this.transactionHistory.push({ type: "withdrawal", amount: amount });
      console.log("Withdrew " + amount + ". New balance: " + this.balance);
    }
  }

  summary() {
    return `Account: ${this.owner} | Balance: $${this.balance}`;
  }

  printHistory() {
    console.log("Transaction history for " + this.owner + ":");
    this.transactionHistory.forEach(function(t) {
      console.log("  " + t.type + ": " + t.amount);
    });
  }
}

const account1 = new BankAccount("Jordan Park", 100);
account1.deposit(50);
account1.withdraw(30);
account1.deposit(200);
account1.withdraw(400);  // Insufficient funds
account1.printHistory();
```

---

## Advanced Stretch Solution

```javascript
// transfer method added to the class:
transfer(amount, targetAccount) {
  if (amount > this.balance) {
    console.log("Transfer failed: Insufficient funds");
  } else {
    this.withdraw(amount);
    targetAccount.deposit(amount);
    console.log(`Transferred $${amount} from ${this.owner} to ${targetAccount.owner}`);
  }
}

// External helper function:
function richestAccount(accounts) {
  let richest = accounts[0];
  for (let i = 1; i < accounts.length; i++) {
    if (accounts[i].balance > richest.balance) {
      richest = accounts[i];
    }
  }
  return richest;
}

const a1 = new BankAccount("Jordan", 100);
const a2 = new BankAccount("Alex", 500);
const a3 = new BankAccount("Sam", 50);
const a4 = new BankAccount("Morgan", 350);

a1.transfer(80, a3);    // succeeds
a3.transfer(500, a2);   // fails — insufficient funds

console.log(richestAccount([a1, a2, a3, a4]).summary());
```

---

## Instructor Notes

- **Core:** `BankAccount` class with `constructor(owner, balance)`, `deposit(amount)` that adds to balance, `withdraw(amount)` that checks funds before subtracting, `summary()` returning a template literal string; 3 instances created with at least one "Insufficient funds" case demonstrated
- **Common mistake:** writing `this.balance - amount` in withdraw without reassigning — the balance never actually changes; remind students to use `-=` or `this.balance = this.balance - amount`
- **Common mistake:** forgetting `this.` when accessing properties inside methods — `return owner` throws ReferenceError because `owner` is not a local variable, it is a property on the instance
- **Common mistake:** lowercase class name `class bankAccount` — technically works but violates PascalCase convention; note the standard
- **Intermediate:** `transactionHistory` initialized as `[]` in constructor; each successful transaction pushes an object; `printHistory()` uses `forEach` to log each entry
- **Advanced:** `transfer()` calls `this.withdraw()` and `targetAccount.deposit()` — elegant reuse of existing methods; `richestAccount()` can use a simple loop or `reduce` — either approach is valid
