# 🟨 Functional Programming (FP) in JavaScript – Complete Guide

---

## 1. What is Functional Programming?

* **Definition:** Functional Programming is a **programming paradigm** that treats computation as the **evaluation of pure functions** and avoids **shared state** and **side effects**.
* Emphasis on **immutability**, **pure functions**, and **higher-order functions**.
* Benefits:

  * Predictable code
  * Easier testing & debugging
  * Reusable logic
  * Better handling of async workflows

---

## 2. Key Principles of FP

1. **Pure Functions**

   * Output depends only on input.
   * No side effects (don’t change external state).

```js
// Pure function
function add(a, b) {
  return a + b;
}

// Impure function
let x = 0;
function impureAdd(y) {
  x += y; // modifies external state
  return x;
}
```

---

2. **Immutability**

   * Data cannot be changed once created.
   * Use **new variables/objects** instead of modifying originals.

```js
const user = { name: "Max", age: 25 };
const updatedUser = { ...user, age: 26 }; // new object
console.log(user.age); // 25
console.log(updatedUser.age); // 26
```

---

3. **First-Class Functions**

   * Functions are **values** → can be assigned, passed, or returned.

```js
const greet = function(name) { return `Hello ${name}`; };
const greetFn = greet;
console.log(greetFn("Max")); // Hello Max
```

---

4. **Higher-Order Functions (HOFs)**

   * Functions that **take functions as arguments** or **return functions**.

```js
function multiplyBy(factor) {
  return function(x) {
    return x * factor;
  };
}

const double = multiplyBy(2);
console.log(double(5)); // 10
```

---

5. **Avoid Side Effects**

   * Functions shouldn’t change external variables, DOM, or input data.

```js
// Avoid this
const arr = [1,2,3];
function addItem(value) {
  arr.push(value);
}

// Better (pure)
function addItemImmutable(arr, value) {
  return [...arr, value];
}
```

---

## 3. Functional Array Methods

1. **map()** → transform array

```js
const nums = [1,2,3];
const doubled = nums.map(n => n * 2);
console.log(doubled); // [2,4,6]
```

2. **filter()** → select elements

```js
const even = nums.filter(n => n % 2 === 0);
console.log(even); // [2]
```

3. **reduce()** → accumulate a value

```js
const sum = nums.reduce((acc, n) => acc + n, 0);
console.log(sum); // 6
```

4. **forEach()** → iterate (side-effect allowed)

```js
nums.forEach(n => console.log(n));
```

5. **find() / findIndex()** → search

```js
const firstEven = nums.find(n => n % 2 === 0);
console.log(firstEven); // 2
```

6. **some() / every()** → boolean checks

```js
const hasEven = nums.some(n => n % 2 === 0);
const allEven = nums.every(n => n % 2 === 0);
```

---

## 4. Function Composition

* Combine small functions to build **complex operations**.

```js
const add2 = x => x + 2;
const double = x => x * 2;

const addThenDouble = x => double(add2(x));
console.log(addThenDouble(3)); // 10
```

* Libraries like **Ramda / Lodash FP** provide `compose` and `pipe`.

---

## 5. Currying

* Transform a function that takes multiple arguments → **series of unary functions**.

```js
const multiply = x => y => x * y;

const double = multiply(2);
console.log(double(5)); // 10
```

* Useful for **partial application**.

---

## 6. Recursion (instead of loops)

* FP prefers **recursion** over **for/while loops**.

```js
function factorial(n) {
  if (n === 0) return 1;
  return n * factorial(n - 1);
}

console.log(factorial(5)); // 120
```

---

## 7. Immutable Data Structures

* Avoid direct mutation:

```js
const arr = [1,2,3];
const newArr = [...arr, 4]; // new array
console.log(arr); // [1,2,3]
console.log(newArr); // [1,2,3,4]
```

* For objects:

```js
const obj = { a: 1, b: 2 };
const newObj = { ...obj, b: 3 };
```

---

## 8. Real-World Example (ClientPanel)

Functional way to **filter active projects**:

```js
const projects = [
  { name: "Website", status: "In Progress" },
  { name: "SEO", status: "Completed" },
  { name: "App", status: "In Progress" },
];

const activeProjects = projects.filter(p => p.status === "In Progress")
                               .map(p => p.name);

console.log(activeProjects); // ["Website", "App"]
```

* No mutation.
* Composable, readable, and predictable.

---

## 9. Advantages of Functional JS

* **Predictable & pure code** → easier debugging.
* **Reusable logic** → small, composable functions.
* **Better for async workflows** → works well with Promises and async/await.
* Avoids **global state & side effects** → less bugs.

---

## 10. Key Takeaways

* FP = write **pure, immutable, composable** functions.
* **map, filter, reduce** → core functional methods for arrays.
* **Currying, composition, recursion** → functional patterns.
* Ideal for **state transformations, pipelines, and SaaS dashboards**.

---

✅ **Summary**
Functional Programming in JS allows you to:

* Transform data **without side effects**.
* Write **clean, reusable, testable code**.
* Combine small functions to handle **complex workflows**.
* Works perfectly with **Promises, async/await, and modern frameworks**.
