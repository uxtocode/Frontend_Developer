# 🎨 CSS (Cascading Style Sheets) – Complete Guide

---

## 1. What is CSS?

**CSS (Cascading Style Sheets)** is a **style sheet language** used to control the **appearance and layout** of HTML elements on a webpage.

* HTML = Structure (the skeleton)
* CSS = Presentation (the design, skin)
* JavaScript = Behavior (the brain, interactivity)

👉 Example:

```html
<h1>Hello World</h1>
```

Without CSS → Just black text.
With CSS →

```css
h1 {
  color: blue;
  font-size: 36px;
  text-align: center;
}
```

---

## 2. Why is CSS Important?

* Separates **content from design** → Clean, maintainable code.
* Makes sites **responsive & accessible**.
* Enables **custom branding & creativity**.
* Reduces duplication → One stylesheet styles multiple pages.

---

## 3. How CSS Works (Cascading & Inheritance)

### 3.1 Cascade (Priority Order)

When multiple CSS rules apply, the **cascade** decides which one wins. Order of priority:

1. **Inline styles** → Inside element (`<p style="color:red">`)
2. **Internal CSS** → Inside `<style>` in `<head>`
3. **External CSS** → Linked via `<link rel="stylesheet">`
4. **Browser default styles**

### 3.2 Specificity (Weight of Selectors)

* Inline styles → Highest
* ID selectors (`#id`) → High
* Class selectors (`.class`) → Medium
* Element selectors (`div, p`) → Low

### 3.3 Inheritance

Some properties **inherit automatically** (color, font-size). Others don’t (margin, border).

---

## 4. Types of CSS

1. **Inline CSS** → Applied directly to element.

   ```html
   <p style="color: red;">Hello</p>
   ```

2. **Internal CSS** → Inside `<style>` tag in `<head>`.

   ```html
   <style>
     p { color: green; }
   </style>
   ```

3. **External CSS** → Linked via separate `.css` file (best practice).

   ```html
   <link rel="stylesheet" href="styles.css">
   ```

---

## 5. CSS Syntax

```css
selector {
  property: value;
}
```

Example:

```css
h1 {
  color: blue;
  font-size: 28px;
  font-weight: bold;
}
```

---

## 6. CSS Selectors (Targeting Elements)

### 6.1 Basic Selectors

* `element` → `p {}` targets all `<p>`
* `.class` → `.btn {}` targets class
* `#id` → `#header {}` targets unique id

### 6.2 Combinators

* `div p` → Descendant selector (all `<p>` inside `<div>`)
* `div > p` → Direct child
* `div + p` → Adjacent sibling
* `div ~ p` → General sibling

### 6.3 Attribute Selectors

* `input[type="text"] {}`
* `a[target="_blank"] {}`

### 6.4 Pseudo-classes

* `a:hover { color: red; }`
* `input:focus { border: 2px solid blue; }`
* `p:first-child {}`

### 6.5 Pseudo-elements

* `p::first-letter { font-size: 30px; }`
* `p::before { content: "👉 "; }`

---

## 7. CSS Properties (The Building Blocks)

### 7.1 Text & Font

* `color`, `font-size`, `font-family`, `font-weight`, `line-height`, `text-align`, `text-transform`

### 7.2 Box Model

Every element is a **box** with:

* `content` → actual text/image
* `padding` → space inside border
* `border` → boundary
* `margin` → space outside border

Example:

```css
div {
  width: 200px;
  padding: 10px;
  border: 2px solid black;
  margin: 20px;
}
```

### 7.3 Backgrounds

* `background-color`, `background-image`, `background-size`, `background-repeat`

### 7.4 Borders & Shadows

* `border: 2px solid red;`
* `border-radius: 10px;`
* `box-shadow: 0 4px 6px rgba(0,0,0,0.2);`

### 7.5 Positioning & Layout

* `position: static | relative | absolute | fixed | sticky`
* `top, left, right, bottom`
* `z-index`

### 7.6 Display & Visibility

* `display: block | inline | inline-block | flex | grid | none`
* `visibility: hidden;` (hides but keeps space)

---

## 8. CSS Layout Techniques

### 8.1 Float (Old method, rarely used now)

```css
img { float: left; }
```

### 8.2 Flexbox (1D Layout)

Used for aligning items horizontally or vertically.

```css
.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
```

### 8.3 Grid (2D Layout)

Perfect for complex layouts.

```css
.container {
  display: grid;
  grid-template-columns: 1fr 2fr 1fr;
  gap: 10px;
}
```

---

## 9. Responsive Design with CSS

### 9.1 Media Queries

```css
@media (max-width: 768px) {
  body {
    font-size: 14px;
  }
}
```

### 9.2 Relative Units

* `%`, `em`, `rem`, `vw`, `vh` → scale with screen size.

### 9.3 Flex & Grid

Both naturally support responsiveness.

---

## 10. Advanced CSS Features

* **Transitions** (smooth property change)

  ```css
  button {
    transition: all 0.3s ease;
  }
  ```

* **Animations** (keyframes)

  ```css
  @keyframes bounce {
    0% { transform: translateY(0); }
    50% { transform: translateY(-20px); }
    100% { transform: translateY(0); }
  }
  div { animation: bounce 2s infinite; }
  ```

* **Transforms** (2D/3D)

  ```css
  div { transform: rotate(45deg) scale(1.2); }
  ```

* **Variables (Custom Properties)**

  ```css
  :root {
    --primary-color: #007bff;
  }
  button {
    background: var(--primary-color);
  }
  ```

* **CSS Functions**

  * `calc()`, `min()`, `max()`, `clamp()`

---

## 11. CSS Best Practices

✔ Keep CSS modular & organized
✔ Use external stylesheets for maintainability
✔ Use semantic class names (`.btn-primary`, `.card-header`)
✔ Don’t overuse IDs for styling → Use classes
✔ Minify CSS for production
✔ Test across devices & browsers
✔ Use variables for consistent colors/fonts
✔ Avoid inline styles except quick tests

---

## 12. Example: Modern Card Component

```html
<div class="card">
  <h2>ClientPanel</h2>
  <p>Manage your freelance clients and projects in one place.</p>
  <button class="btn">Get Started</button>
</div>
```

```css
.card {
  background: #fff;
  border-radius: 12px;
  padding: 20px;
  box-shadow: 0 4px 10px rgba(0,0,0,0.1);
  max-width: 300px;
}

.card h2 {
  font-size: 20px;
  margin-bottom: 10px;
}

.card p {
  font-size: 14px;
  color: #555;
}

.btn {
  display: inline-block;
  padding: 10px 20px;
  background: #007bff;
  color: white;
  border: none;
  border-radius: 8px;
  transition: background 0.3s;
}

.btn:hover {
  background: #0056b3;
}
```

---

## 13. CSS Tools & Frameworks

* **Tailwind CSS** → Utility-first framework
* **Bootstrap** → Prebuilt UI components
* **Sass / SCSS** → CSS preprocessor with nesting, variables, mixins
* **PostCSS** → CSS transformations & optimizations

---

✅ CSS is the **design layer of the web**. Mastering it lets you build **beautiful, responsive, and professional-looking websites**.
