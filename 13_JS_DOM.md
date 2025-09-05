# 🟨 JavaScript DOM & Events – Complete Guide

---

## 1. What is the DOM?

* **DOM (Document Object Model)** → a **programming interface** for HTML & XML documents.
* Browser converts HTML into a **tree structure** (nodes).
* JavaScript can **read, update, add, or delete elements** in the DOM.

👉 Example of HTML → DOM Tree:

```html
<html>
  <body>
    <h1>Hello</h1>
    <p>World</p>
  </body>
</html>
```

Becomes:

* `document` → root object

  * `html` → element node

    * `body` → element node

      * `h1` → element node → text node (“Hello”)
      * `p` → element node → text node (“World”)

---

## 2. Accessing DOM Elements

### By ID

```js
const title = document.getElementById("main-title");
```

### By Class

```js
const items = document.getElementsByClassName("list-item");
```

### By Tag

```js
const paragraphs = document.getElementsByTagName("p");
```

### Modern Method – Query Selector

```js
const firstItem = document.querySelector(".list-item");   // first match
const allItems = document.querySelectorAll(".list-item"); // all matches
```

---

## 3. Modifying DOM Elements

### Changing Text & HTML

```js
title.textContent = "New Title";   // only text
title.innerHTML = "<span>Styled Title</span>"; // with HTML
```

### Changing Attributes

```js
const link = document.querySelector("a");
link.setAttribute("href", "https://google.com");
console.log(link.getAttribute("href"));
```

### Changing Styles

```js
title.style.color = "blue";
title.style.fontSize = "24px";
```

👉 Better: use `classList` for CSS classes

```js
title.classList.add("highlight");
title.classList.remove("hidden");
title.classList.toggle("active"); // adds/removes
```

---

## 4. Creating & Removing Elements

### Create

```js
const newDiv = document.createElement("div");
newDiv.textContent = "Hello World";
document.body.appendChild(newDiv);
```

### Insert Before/After

```js
const parent = document.querySelector("#container");
const child = document.createElement("p");
child.textContent = "Inserted text";
parent.insertBefore(child, parent.firstChild);
```

### Remove

```js
newDiv.remove(); // modern
parent.removeChild(child); // older
```

---

## 5. Traversing the DOM

```js
const parent = document.querySelector(".parent");
console.log(parent.children);         // child elements
console.log(parent.firstElementChild); // first child
console.log(parent.lastElementChild);  // last child

const child = document.querySelector(".child");
console.log(child.parentElement);     // parent
console.log(child.nextElementSibling); // next sibling
```

---

## 6. DOM Events

Events = user actions (click, keypress, scroll, load, etc.).

### Event Listener

```js
const button = document.querySelector("button");

button.addEventListener("click", () => {
  alert("Button clicked!");
});
```

### Common Events

* **Mouse** → `click`, `dblclick`, `mouseover`, `mouseout`, `contextmenu`
* **Keyboard** → `keydown`, `keyup`, `keypress`
* **Form** → `submit`, `change`, `input`, `focus`, `blur`
* **Window** → `load`, `resize`, `scroll`

---

## 7. Event Object

```js
button.addEventListener("click", (event) => {
  console.log(event.type);   // click
  console.log(event.target); // which element was clicked
});
```

---

## 8. Event Bubbling & Capturing

* **Bubbling (default)** → event travels **from child → parent**.
* **Capturing** → event travels **from parent → child**.

```js
document.querySelector(".parent").addEventListener("click", () => {
  console.log("Parent clicked");
}, true); // true = capturing
```

👉 Use `event.stopPropagation()` to stop bubbling.

---

## 9. Event Delegation

Instead of attaching event listeners to many children, use the **parent**.

```js
document.querySelector("ul").addEventListener("click", (e) => {
  if (e.target.tagName === "LI") {
    console.log("Clicked:", e.target.textContent);
  }
});
```

👉 Useful for dynamic elements.

---

## 10. Forms & Input Events

```js
const form = document.querySelector("form");

form.addEventListener("submit", (e) => {
  e.preventDefault(); // stop reload
  const input = document.querySelector("input").value;
  console.log("Input value:", input);
});
```

👉 Other input events: `input`, `change`, `focus`, `blur`.

---

## 11. Real-World Example (ClientPanel Dashboard)

Dynamic **Add Project Button**:

```html
<button id="addProjectBtn">Add Project</button>
<ul id="projectList"></ul>
```

```js
const button = document.getElementById("addProjectBtn");
const list = document.getElementById("projectList");

button.addEventListener("click", () => {
  const li = document.createElement("li");
  li.textContent = "New Project " + (list.children.length + 1);
  list.appendChild(li);
});
```

👉 Every time you click, a new project is added to the list.

---

## 12. Best Practices

✔ Use `querySelector` & `querySelectorAll` (modern & flexible).
✔ Use `classList` for styling instead of inline `style`.
✔ Always use `addEventListener` (not `onclick` → overwrites handlers).
✔ Use **event delegation** for efficiency.
✔ Prevent default form reload with `e.preventDefault()`.
✔ Keep DOM manipulation minimal (batch changes if possible).

---

✅ **Summary**

* DOM = structure of HTML in memory.
* You can **select, modify, create, delete, traverse** elements.
* Events = user actions → handled with `addEventListener`.
* Important concepts: **event bubbling, delegation, event object**.
* Crucial for **interactive UIs, forms, dashboards, and real apps**.
