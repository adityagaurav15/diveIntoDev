### 1. What is the difference between `null` and `undefined`?

**Answer:**
While both represent "no value," they are used in different contexts:

* **`undefined`**: Means a variable has been declared but has not yet been assigned a value. It is the default return value of functions that don't explicitly return anything.
* **`null`**: Is an assignment value. It is used by developers to explicitly indicate that a variable is empty or has no value.

> **Note:** `typeof undefined` is `"undefined"`, but `typeof null` is `"object"` (this is a long-standing bug in JavaScript).

---

### 2. Explain "Hoisting" in JavaScript.

**Answer:**
Hoisting is JavaScript's default behavior of moving declarations to the top of the current scope before code execution.

* **Function declarations** are fully hoisted, meaning you can call a function before it is defined in the code.
* **`var` variables** are hoisted but initialized with `undefined`.
* **`let` and `const` variables** are hoisted but placed in a "Temporal Dead Zone" (TDZ). You cannot access them until the line of code where they are defined is executed.

---

### 3. What are Closures and why are they useful?

**Answer:**
A closure is the combination of a function bundled together with references to its surrounding state (the lexical environment). In simpler terms, a closure gives an inner function access to an outer function's scope even after the outer function has finished executing.

**Example:**

```javascript
function counter() {
  let count = 0;
  return function() {
    count++;
    return count;
  };
}
const increment = counter();
console.log(increment()); // 1
console.log(increment()); // 2

```

**Use cases:** Data privacy (emulating private variables) and partial application/currying.

---

### 4. What is the "Event Loop" and how does it handle Asynchronous code?

**Answer:**
JavaScript is single-threaded, meaning it can only do one thing at a time. The Event Loop is the mechanism that allows JS to perform non-blocking operations by offloading tasks (like API calls or timers) to the browser (Web APIs).

1. **Call Stack:** Executes synchronous code.
2. **Web APIs:** Handles async tasks (setTimeout, fetch).
3. **Task Queue:** Where callback functions wait to be executed.
4. **Event Loop:** Continuously checks if the Call Stack is empty. If it is, it pushes the first task from the queue to the stack.

---

### 5. What is the difference between `.call()`, `.apply()`, and `.bind()`?

**Answer:**
All three methods are used to set the `this` context of a function manually.

* **`.call()`**: Invokes the function immediately. Arguments are passed **individually** (comma-separated).
* **`.apply()`**: Invokes the function immediately. Arguments are passed as an **array**.
* **`.bind()`**: Does **not** invoke the function immediately. Instead, it returns a new function with the `this` context permanently bound to it, which can be executed later.

| Method | Immediate Execution? | Argument Format |
| --- | --- | --- |
| `.call()` | Yes | `arg1, arg2` |
| `.apply()` | Yes | `[arg1, arg2]` |
| `.bind()` | No | `arg1, arg2` |
