# 📦 CSS Flexbox – The Complete Guide

---

## 1. What is Flexbox?

**Flexbox** = CSS layout model designed to arrange elements in **one dimension** (row or column) with **flexible alignment and spacing**.

* Unlike **block/inline** layouts → rigid, hard to align.
* Unlike **CSS Grid** → 2D layout (rows & columns).
* Flexbox → 1D layout (main axis OR cross axis).

👉 Best for **navbars, cards, buttons, form layouts, vertical centering**.

---

## 2. How Flexbox Works

When you apply:

```css
.container {
  display: flex;
}
```

* The container becomes a **flex container**.
* Its children become **flex items**.

Two main axes are created:

* **Main axis** → depends on `flex-direction` (row by default).
* **Cross axis** → perpendicular to main axis.

---

## 3. Flex Container Properties

These are applied on the **parent container** (`display: flex`).

---

### 3.1 `display: flex | inline-flex`

* `flex` → block-level flex container.
* `inline-flex` → inline-level flex container.

---

### 3.2 `flex-direction` (main axis)

Defines the direction of items.

* `row` (default) → left to right
* `row-reverse` → right to left
* `column` → top to bottom
* `column-reverse` → bottom to top

👉 Example:

```css
.container {
  display: flex;
  flex-direction: row;
}
```

---

### 3.3 `flex-wrap` (line wrapping)

Controls whether items wrap onto multiple lines.

* `nowrap` (default) → all items in one line
* `wrap` → items wrap to next line
* `wrap-reverse` → wrap in reverse order

---

### 3.4 `flex-flow` (shorthand)

Combines `flex-direction` + `flex-wrap`.

```css
flex-flow: row wrap;
```

---

### 3.5 `justify-content` (along main axis)

Aligns items **horizontally (row)** or **vertically (column)**.

* `flex-start` → items at start
* `flex-end` → items at end
* `center` → centered
* `space-between` → equal space between
* `space-around` → equal space around (half at edges)
* `space-evenly` → equal spacing everywhere

---

### 3.6 `align-items` (along cross axis)

Aligns items on the **cross axis**.

* `stretch` (default) → stretch to fill container
* `flex-start` → align to top/left
* `flex-end` → align to bottom/right
* `center` → vertically/horizontally centered
* `baseline` → align text baselines

---

### 3.7 `align-content` (multi-line alignment)

Used **only if wrapping (`flex-wrap`) is on**.

* `stretch` (default)
* `flex-start`
* `flex-end`
* `center`
* `space-between`
* `space-around`

---

## 4. Flex Item Properties

These are applied on the **children (flex items)**.

---

### 4.1 `order`

Controls the order of items (default = 0).

```css
.item1 { order: 2; }
.item2 { order: 1; }
```

---

### 4.2 `flex-grow` (expand)

Defines how much an item **grows relative to siblings**.

```css
.item1 { flex-grow: 1; } /* takes extra space */
.item2 { flex-grow: 2; } /* takes twice more than item1 */
```

---

### 4.3 `flex-shrink` (shrink)

Defines how items **shrink when container is too small**.

```css
.item1 { flex-shrink: 0; } /* won't shrink */
.item2 { flex-shrink: 1; } /* default shrink */
```

---

### 4.4 `flex-basis` (initial size)

Defines **starting size** before grow/shrink.

* Can be px, %, auto.

```css
.item { flex-basis: 200px; }
```

---

### 4.5 `flex` (shorthand)

Shorthand for `flex-grow`, `flex-shrink`, `flex-basis`.

```css
.item { flex: 1; } /* grow=1, shrink=1, basis=0 */
.item { flex: 2 1 150px; } /* grow=2, shrink=1, basis=150px */
```

---

### 4.6 `align-self`

Overrides container’s `align-items` for a single item.

```css
.item { align-self: flex-end; }
```

---

## 5. Practical Flexbox Examples

---

### 5.1 Centering an Element (Classic Use Case)

```css
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
```

---

### 5.2 Navbar with Spaced Items

```css
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
```

---

### 5.3 Equal Height Cards

```css
.cards {
  display: flex;
  gap: 20px;
}
.card {
  flex: 1;
  background: #eee;
  padding: 20px;
}
```

---

### 5.4 Responsive Wrapping Grid

```css
.container {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}
.item {
  flex: 1 1 200px; /* grow, shrink, basis */
  background: lightblue;
}
```

---

### 5.5 Sidebar Layout

```css
.layout {
  display: flex;
}
.sidebar {
  flex: 0 0 250px; /* fixed width */
  background: #ddd;
}
.content {
  flex: 1; /* flexible main area */
  background: #fff;
}
```

---

## 6. Visualizing Flexbox

* **Main Axis** = controlled by `flex-direction`.
* **Cross Axis** = perpendicular to main axis.

👉 Trick: If `flex-direction: row`, then `justify-content` works horizontally, `align-items` works vertically.
👉 If `flex-direction: column`, the roles swap.

---

## 7. Common Flexbox Patterns

* ✅ **Horizontal Navbars**
* ✅ **Vertical Centering**
* ✅ **Responsive Grids without Media Queries**
* ✅ **Sticky Footers**
* ✅ **Sidebar + Content Layout**

---

## 8. Flexbox vs Grid

| Feature   | Flexbox (1D)          | Grid (2D)                  |
| --------- | --------------------- | -------------------------- |
| Layout    | One axis (row/column) | Both rows & columns        |
| Best for  | Navbars, cards, forms | Page layouts, dashboards   |
| Alignment | Strong                | Strong + explicit controls |

Often: **Use Flexbox inside Grid** for inner components.

---

## 9. Flexbox Best Practices

✔ Use `flex: 1` for equal-width columns
✔ Combine `flex-basis` + `flex-grow` for responsiveness
✔ Avoid fixed widths → use `flex` instead
✔ Use `gap` (CSS property) for spacing (instead of margins)
✔ Keep nesting minimal → don’t overcomplicate
✔ For full 2D layouts → prefer Grid

---

## 10. Flexbox Debugging Tools

* Chrome DevTools → Inspect → Layout → Flex overlay
* Websites:

  * **Flexbox Froggy** (game to learn)
  * **CSS Tricks Flexbox Guide** (visual cheatsheet)

---

✅ **Summary:**
Flexbox is **one-dimensional**, highly flexible, and perfect for **aligning and distributing items**. It simplifies layouts that used to require hacks with floats, tables, or absolute positioning.
