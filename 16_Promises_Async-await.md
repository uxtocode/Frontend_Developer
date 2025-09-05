# 🟨 Promises & Async/Await – Complete Guide

---

## 1. Why Do We Need Promises?

Before Promises, async tasks were handled with **callbacks**, which often caused:

* **Callback hell** → nested callbacks.
* Hard to **read** & **debug**.
* Error handling was messy.

👉 Promises solve this by providing a **cleaner way to handle async operations**.

---

## 2. What is a Promise?

* A **Promise** is an object representing the eventual **completion or failure** of an asynchronous operation.
* States of a Promise:

  1. **Pending** → operation not finished.
  2. **Fulfilled** → operation completed successfully (`.then()` runs).
  3. **Rejected** → operation failed (`.catch()` runs).

---

## 3. Creating a Promise

```js
const myPromise = new Promise((resolve, reject) => {
  let success = true;

  if (success) {
    resolve("Operation successful!");
  } else {
    reject("Something went wrong.");
  }
});

myPromise
  .then(result => console.log(result)) // Operation successful!
  .catch(error => console.error(error));
```

---

## 4. Chaining Promises

```js
const fetchData = () => {
  return new Promise((resolve) => {
    setTimeout(() => resolve("Data loaded"), 1000);
  });
};

fetchData()
  .then(result => {
    console.log(result); // Data loaded
    return "Next step";
  })
  .then(step => console.log(step)) // Next step
  .catch(err => console.error(err));
```

👉 Each `.then()` returns a new Promise → allows chaining.

---

## 5. Error Handling

```js
Promise.reject("Error happened")
  .then(data => console.log(data))  // skipped
  .catch(err => console.error("Caught:", err))
  .finally(() => console.log("Always runs"));
```

✔ `.finally()` always executes, regardless of success or failure.

---

## 6. Promise Combinators

### `Promise.all()` – Run in parallel, wait for all

```js
Promise.all([
  fetch("/api/users"),
  fetch("/api/projects"),
])
.then(responses => console.log("All done:", responses))
.catch(err => console.error("One failed:", err));
```

👉 If one fails → whole Promise fails.

### `Promise.race()` – First result wins

```js
Promise.race([
  fetch("/api/slow"),
  fetch("/api/fast")
]).then(res => console.log("First response:", res));
```

### `Promise.allSettled()` – Returns results of all (success/failure)

```js
Promise.allSettled([
  Promise.resolve("A"),
  Promise.reject("B")
]).then(results => console.log(results));
```

### `Promise.any()` – Returns the first fulfilled promise

```js
Promise.any([
  Promise.reject("Fail 1"),
  Promise.resolve("Success"),
  Promise.reject("Fail 2"),
]).then(result => console.log(result)); // Success
```

---

## 7. Async/Await

* Introduced in **ES2017 (ES8)**.
* Built on top of Promises.
* Allows writing async code like **synchronous code**.

### Example

```js
async function fetchData() {
  try {
    let response = await fetch("https://jsonplaceholder.typicode.com/posts/1");
    let data = await response.json();
    console.log(data);
  } catch (error) {
    console.error("Error:", error);
  }
}
fetchData();
```

✔ `await` pauses function execution until the Promise resolves.
✔ Must be inside an `async` function.

---

## 8. Sequential vs Parallel Execution

### Sequential (one by one)

```js
async function loadSequential() {
  const res1 = await fetch("/api/one");
  const res2 = await fetch("/api/two");
  console.log("Done");
}
```

👉 Slow, waits for each fetch.

### Parallel (faster)

```js
async function loadParallel() {
  const [res1, res2] = await Promise.all([
    fetch("/api/one"),
    fetch("/api/two")
  ]);
  console.log("Done faster");
}
```

---

## 9. Converting Callbacks → Promises

Old callback:

```js
setTimeout(() => {
  console.log("Done");
}, 1000);
```

Promise version:

```js
function wait(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}

async function run() {
  console.log("Wait...");
  await wait(1000);
  console.log("Done");
}
run();
```

---

## 10. Real-World Example (ClientPanel SaaS)

Fetching client projects:

```js
async function loadProjects() {
  try {
    const res = await fetch("/api/projects");
    if (!res.ok) throw new Error("Failed to fetch");

    const projects = await res.json();
    projects.forEach(p => {
      console.log(`${p.id}: ${p.name} (${p.status})`);
    });
  } catch (err) {
    console.error("Error loading projects:", err);
  } finally {
    console.log("Projects fetch attempt finished");
  }
}

loadProjects();
```

✔ Handles **API fetch, error handling, and cleanup** in a clean, readable way.

---

## 11. Key Takeaways

* **Promises** represent async operations → `then`, `catch`, `finally`.
* **Promise combinators** allow handling multiple Promises.
* **Async/await** makes async code look synchronous.
* **Error handling** → use `try/catch` with `async/await`.
* For **parallel tasks** → use `Promise.all`.
* Promises & async/await are **the backbone of modern apps** → APIs, databases, real-time updates.

---

✅ **Summary**

* Promises → cleaner alternative to callbacks.
* Async/await → modern, readable async code.
* Both essential for **fetching data, handling APIs, and building SaaS dashboards**.
