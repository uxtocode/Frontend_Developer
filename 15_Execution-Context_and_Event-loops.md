# 🟨 JavaScript Execution Context & Event Loop – Complete Guide

---

## 1. What is Execution Context?

Execution Context = **the environment where JS code runs**.

Every time JavaScript executes code, it creates an **Execution Context (EC)** that keeps track of:

* **Variable Environment** → variables, functions.
* **Scope Chain** → access to outer scopes.
* **this binding** → value of `this`.

---

## 2. Types of Execution Context

1. **Global Execution Context (GEC)**

   * Created when script starts.
   * Contains global objects (`window` in browser, `global` in Node.js).
   * Only one per program.

2. **Function Execution Context (FEC)**

   * Created when a function is called.
   * Each function has its own local variables, arguments, and scope.

3. **Eval Execution Context** (rarely used, discouraged).

---

## 3. Phases of Execution Context

Every EC goes through **two phases**:

### a) Creation Phase

* JS engine scans code.
* Memory is allocated for variables & functions.
* Variables declared with `var` → initialized as `undefined`.
* Functions → stored in memory fully.

### b) Execution Phase

* Code runs line by line.
* Variables assigned actual values.

---

### Example

```js
console.log(x); // undefined (hoisted)
var x = 10;

function greet() {
  console.log("Hello");
}
greet(); // Hello
```

✔ During **Creation Phase**:

* `x` is hoisted → `undefined`.
* `greet` is fully hoisted.

✔ During **Execution Phase**:

* `x = 10`
* `greet()` runs.

---

## 4. Call Stack

* **Call Stack** = stack data structure to keep track of ECs.
* Global EC is at the bottom.
* Each function call → new EC pushed on top.
* Function return → EC popped.

### Example

```js
function a() {
  console.log("A");
  b();
}

function b() {
  console.log("B");
}

a();
console.log("Done");
```

Call Stack order:

1. GEC created.
2. `a()` pushed → runs.
3. `b()` pushed → runs.
4. `b()` popped.
5. `a()` popped.
6. GEC remains.

Output:

```
A
B
Done
```

---

## 5. Synchronous vs Asynchronous Execution

* **Synchronous** → one task at a time (default in JS).
* **Asynchronous** → tasks that wait (e.g., API calls, timers) don’t block the main thread.

---

## 6. The Event Loop

Since JS is **single-threaded**, how does it handle async tasks?
👉 With the **Event Loop**.

Components:

1. **Call Stack** → runs functions.
2. **Web APIs** → provided by browser (setTimeout, DOM events, fetch).
3. **Callback Queue (Task Queue)** → holds completed async callbacks.
4. **Microtask Queue** → holds promises/callbacks (`.then`, `catch`).
5. **Event Loop** → checks if stack is empty → pushes tasks from queues.

---

### Example with setTimeout

```js
console.log("Start");

setTimeout(() => {
  console.log("Timeout done");
}, 2000);

console.log("End");
```

Flow:

1. "Start" logged.
2. `setTimeout` goes to Web API → after 2s → callback placed in Callback Queue.
3. "End" logged.
4. Event Loop checks → pushes callback to Call Stack.
5. "Timeout done" logged.

Output:

```
Start
End
Timeout done
```

---

## 7. Microtasks vs Macrotasks

* **Macrotask Queue** → setTimeout, setInterval, events.
* **Microtask Queue** → promises, MutationObserver.

👉 Microtasks have **higher priority** than macrotasks.

### Example

```js
console.log("Start");

setTimeout(() => console.log("setTimeout"), 0);

Promise.resolve().then(() => console.log("Promise"));

console.log("End");
```

Output:

```
Start
End
Promise
setTimeout
```

✔ Promise runs before setTimeout, even with 0ms delay.

---

## 8. Real-World Example (ClientPanel)

```js
console.log("Fetching clients...");

fetch("/api/clients")
  .then(res => res.json())
  .then(data => console.log("Clients loaded:", data))
  .catch(err => console.error(err));

console.log("Continuing UI render...");
```

Flow:

1. "Fetching clients..." logged.
2. `fetch` sent to Web API.
3. "Continuing UI render..." logged.
4. Once response arrives → `.then()` callback goes to **microtask queue**.
5. Event Loop pushes it when stack is free.

---

## 9. Key Takeaways

✔ Execution Context = environment for running code.
✔ Call Stack = keeps track of execution order.
✔ JS is **single-threaded** but handles async with Event Loop.
✔ **Microtasks (promises)** always run before **macrotasks (timeouts, events)**.
✔ Event Loop ensures non-blocking, smooth execution → vital for APIs, UI updates, SaaS apps.

---

## 10. Diagram (Mental Model)

```
[ Call Stack ]  <— Executes functions
[ Web APIs ]   <— Timers, fetch, DOM
[ Task Queue ] <— setTimeout, events
[ Microtasks ] <— promises
[ Event Loop ] <— Moves tasks when stack is empty
```

---

✅ **Summary**

* Execution Context = how JS runs functions.
* Call Stack manages sync execution.
* Event Loop + Queues handle async tasks.
* Microtasks (Promises) > Macrotasks (Timers).
* This model powers modern apps → from API fetching to real-time updates.
