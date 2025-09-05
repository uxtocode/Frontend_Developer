# 🗂️ CSS Grid – Complete Guide

---

## 1. What is CSS Grid?

**CSS Grid** = A powerful **2D layout system** in CSS that allows you to arrange items in **rows and columns** with full control.

* **Flexbox** → One dimension (row **or** column).
* **Grid** → Two dimensions (row **and** column).

👉 Perfect for **page layouts, dashboards, galleries, landing pages, product grids**.

---

## 2. How CSS Grid Works

When you apply:

```css
.container {
  display: grid;
}
```

* The container becomes a **grid container**.
* Its direct children become **grid items**.
* A grid is defined by **rows + columns**.

---

## 3. Grid Container Properties

These control the grid **structure** (applied on the parent).

---

### 3.1 `display: grid | inline-grid`

* `grid` → block-level grid.
* `inline-grid` → inline-level grid.

---

### 3.2 `grid-template-columns` & `grid-template-rows`

Define number and size of rows/columns.

```css
.container {
  display: grid;
  grid-template-columns: 200px 1fr 2fr;
  grid-template-rows: 100px auto 50px;
}
```

Units:

* `px` → fixed
* `%` → relative to container
* `fr` → **fractional unit** (flexible space)
* `auto` → adjusts to content
* `min-content`, `max-content` → based on content size

👉 Example:

```css
grid-template-columns: 1fr 1fr 1fr; /* 3 equal columns */
grid-template-rows: auto 200px auto; /* flexible rows */
```

---

### 3.3 `gap` (spacing)

Sets space between rows & columns.

```css
.container {
  gap: 20px; /* row + column gap */
  row-gap: 10px;
  column-gap: 15px;
}
```

---

### 3.4 `grid-template-areas` (named layout)

Lets you create visual layouts with **names**.

```css
.container {
  display: grid;
  grid-template-areas: 
    "header header"
    "sidebar main"
    "footer footer";
  grid-template-columns: 200px 1fr;
  grid-template-rows: 60px auto 40px;
}
```

Assign items:

```css
.header { grid-area: header; }
.sidebar { grid-area: sidebar; }
.main { grid-area: main; }
.footer { grid-area: footer; }
```

---

### 3.5 `justify-items` (align horizontally in cells)

* `start` | `end` | `center` | `stretch` (default)

### 3.6 `align-items` (align vertically in cells)

* `start` | `end` | `center` | `stretch`

### 3.7 `place-items` (shorthand)

```css
place-items: center; /* align + justify */
```

---

### 3.8 `justify-content` & `align-content`

Align the **whole grid** inside container (if grid smaller than container).

* `start`, `end`, `center`, `stretch`
* `space-between`, `space-around`, `space-evenly`

---

### 3.9 `repeat()` function

Shortcut for repeating columns/rows.

```css
grid-template-columns: repeat(3, 1fr); /* 3 equal columns */
```

---

### 3.10 `minmax()` function

Set min/max sizes.

```css
grid-template-columns: repeat(3, minmax(150px, 1fr));
```

---

### 3.11 `auto-fit` & `auto-fill` (responsive grids)

Automatically fill space with as many columns as possible.

```css
grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
```

👉 Perfect for **responsive card grids**.

---

## 4. Grid Item Properties

Applied on **children (items)**.

---

### 4.1 `grid-column` & `grid-row`

Define where an item starts/ends.

```css
.item {
  grid-column: 1 / 3; /* spans from col 1 to 2 */
  grid-row: 2 / 4;    /* spans rows 2-3 */
}
```

---

### 4.2 `grid-area`

Shorthand for `grid-row-start / grid-column-start / grid-row-end / grid-column-end`.

```css
.item {
  grid-area: 1 / 1 / 3 / 3;
}
```

---

### 4.3 `justify-self` & `align-self`

Align individual items in their cell.

```css
.item {
  justify-self: center;
  align-self: end;
}
```

---

### 4.4 `place-self` (shorthand)

```css
.item {
  place-self: center;
}
```

---

## 5. Practical Grid Examples

---

### 5.1 Basic 3-Column Layout

```css
.container {
  display: grid;
  grid-template-columns: 1fr 2fr 1fr;
  gap: 20px;
}
```

---

### 5.2 Responsive Card Grid

```css
.container {
  display: grid;
  gap: 15px;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
}
```

---

### 5.3 Page Layout with Grid Areas

```css
.container {
  display: grid;
  grid-template-areas: 
    "header header"
    "sidebar main"
    "footer footer";
  grid-template-columns: 250px 1fr;
  grid-template-rows: 80px auto 60px;
  height: 100vh;
}
.header { grid-area: header; background: #444; }
.sidebar { grid-area: sidebar; background: #ddd; }
.main { grid-area: main; background: #fff; }
.footer { grid-area: footer; background: #444; }
```

---

### 5.4 Dashboard Example

```css
.container {
  display: grid;
  grid-template-columns: 200px 1fr 1fr;
  grid-template-rows: 100px auto;
  gap: 20px;
}
.header { grid-column: 1 / 4; }
.sidebar { grid-row: 2 / 3; }
.main { grid-column: 2 / 4; }
```

---

## 6. Grid vs Flexbox

| Feature        | Flexbox (1D)             | Grid (2D)                   |
| -------------- | ------------------------ | --------------------------- |
| Layout Type    | One axis (row OR column) | Two axes (rows AND columns) |
| Best For       | Navbars, forms, cards    | Page layouts, dashboards    |
| Alignment      | Powerful                 | Even more powerful          |
| Learning Curve | Easier                   | A bit harder but versatile  |

👉 Use **Flexbox for components**, **Grid for overall page layout**.

---

## 7. Advanced Grid Features

* **Subgrid** → Allow nested grids to inherit parent tracks (modern browsers).
* **Implicit vs Explicit Grids** → Extra items create implicit rows/columns.
* **Layering** → Items can overlap (like absolute positioning).

---

## 8. Grid Best Practices

✔ Use `fr` units instead of fixed px for flexibility
✔ Use `minmax()` + `auto-fit` for responsive grids
✔ Prefer `gap` instead of margins for spacing
✔ Use named areas for readability
✔ Combine Grid (layout) + Flexbox (components)
✔ Test across different screen sizes

---

## 9. Example: Complete Page Layout with Grid

```html
<div class="grid-container">
  <header class="header">Header</header>
  <aside class="sidebar">Sidebar</aside>
  <main class="main">Main Content</main>
  <footer class="footer">Footer</footer>
</div>
```

```css
.grid-container {
  display: grid;
  grid-template-areas: 
    "header header"
    "sidebar main"
    "footer footer";
  grid-template-columns: 200px 1fr;
  grid-template-rows: 60px auto 40px;
  height: 100vh;
}

.header { grid-area: header; background: #333; color: white; }
.sidebar { grid-area: sidebar; background: #f4f4f4; }
.main { grid-area: main; background: white; }
.footer { grid-area: footer; background: #333; color: white; }
```

---

✅ **Summary:**
CSS Grid is a **powerful 2D system** that lets you create full-page layouts with precision. Combined with **Flexbox** for inner alignment, you can build **modern, responsive, and scalable UIs** without relying on hacks.
