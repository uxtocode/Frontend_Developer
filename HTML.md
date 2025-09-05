# 📖 HTML (HyperText Markup Language)

---

## 1. What is HTML?

* **HTML stands for HyperText Markup Language**.
* It’s the **standard language used to create web pages**.
* It describes the **structure of a webpage** (not the styling or behavior).
* HTML uses **elements (tags)** to define parts of content such as:

  * Headings (`<h1>`)
  * Paragraphs (`<p>`)
  * Links (`<a>`)
  * Images (`<img>`)
  * Layout (`<header>`, `<section>`, `<footer>`)

👉 Think of HTML as the **skeleton** of a web page. CSS styles it (appearance), and JavaScript makes it interactive (behavior).

---

## 2. Why is HTML Important?

1. **Foundation of the Web** – Every web page you see is built with HTML.
2. **Cross-platform** – Works across all browsers and devices.
3. **Accessible** – Provides structure for screen readers and assistive technologies.
4. **Search Engine Optimization (SEO)** – Search engines rely on HTML to understand content.
5. **Future-proof** – HTML evolves with standards but always stays backward compatible.

---

## 3. Brief History of HTML

* **1989–1991** → Tim Berners-Lee invented HTML at CERN.
* **HTML 2.0 (1995)** → First official standard.
* **HTML 4.01 (1999)** → Introduced tables, forms, and frames.
* **XHTML (2000s)** → XML-based stricter version.
* **HTML5 (2014)** → Major upgrade: introduced `<header>`, `<nav>`, `<video>`, `<audio>`, `<canvas>`, `<article>`.
* **HTML Living Standard (present)** → Continuously updated by WHATWG (Web Hypertext Application Technology Working Group).

---

## 4. Structure of an HTML Document

Here’s the **basic skeleton**:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My First Page</title>
</head>
<body>
  <h1>Hello, World!</h1>
  <p>This is my first HTML page.</p>
</body>
</html>
```

### Explanation:

* `<!DOCTYPE html>` → Declares the document is HTML5.
* `<html>` → Root element containing everything.
* `<head>` → Metadata (title, charset, styles, scripts).
* `<title>` → Appears in the browser tab.
* `<body>` → The visible content of the page.

---

## 5. Types of HTML Elements

HTML elements can be grouped into categories:

### 5.1 Structural

* Define page layout.
* Examples: `<header>`, `<main>`, `<footer>`, `<section>`, `<article>`.

### 5.2 Text Content

* Define meaning of text.
* Examples: `<h1>`–`<h6>`, `<p>`, `<strong>`, `<em>`, `<blockquote>`.

### 5.3 Hyperlinks

* Allow navigation.
* `<a href="https://example.com">Visit Site</a>`

### 5.4 Multimedia

* Insert images, video, and audio.
* `<img>`, `<video>`, `<audio>`.

### 5.5 Forms

* Collect user input.
* `<form>`, `<input>`, `<textarea>`, `<button>`, `<select>`.

### 5.6 Tables

* Represent tabular data.
* `<table>`, `<tr>`, `<td>`, `<th>`.

### 5.7 Semantic

* Provide meaning beyond layout.
* `<article>`, `<aside>`, `<figure>`, `<time>`.

### 5.8 Metadata & Scripts

* Describe document info or load scripts.
* `<meta>`, `<script>`, `<link>`.

---

## 6. Attributes in HTML

Attributes provide **extra information** about elements.

* Written inside the opening tag.
* Always have a **name** and a **value**.

✅ Examples:

```html
<img src="logo.png" alt="Company Logo" width="200" height="200">
<a href="https://example.com" target="_blank">Visit Example</a>
<input type="text" placeholder="Enter your name">
```

Common attributes:

* `id` → Unique identifier.
* `class` → Grouping for CSS/JS.
* `src` → Source for images, videos, scripts.
* `alt` → Alternative text (important for accessibility).
* `href` → Hyperlink reference.
* `title` → Tooltip text.
* `target="_blank"` → Opens link in new tab.

---

## 7. HTML vs. XHTML vs. HTML5

* **HTML** → Loose rules, forgiving errors.
* **XHTML** → Stricter, XML-based, required closing all tags.
* **HTML5** → Current standard, semantic tags, multimedia support, APIs (e.g., `<canvas>` for graphics, `<video>` for media).

---

## 8. Example: A Mini Web Page

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>My Portfolio</title>
</head>
<body>
  <header>
    <h1>Max’s Portfolio</h1>
    <nav>
      <a href="#about">About</a>
      <a href="#projects">Projects</a>
      <a href="#contact">Contact</a>
    </nav>
  </header>

  <main>
    <section id="about">
      <h2>About Me</h2>
      <p>I am a frontend developer skilled in HTML, CSS, and JavaScript.</p>
    </section>

    <section id="projects">
      <h2>Projects</h2>
      <article>
        <h3>ClientPanel</h3>
        <p>A SaaS platform for freelancers to manage clients and projects.</p>
      </article>
    </section>
  </main>

  <footer>
    <p>&copy; 2025 Max. All rights reserved.</p>
  </footer>
</body>
</html>
```

---

## 9. Best Practices in HTML

* Always declare `<!DOCTYPE html>`.
* Use **semantic tags** instead of `<div>` everywhere.
* Add `alt` text for all images.
* Validate your code (e.g., [W3C Validator](https://validator.w3.org/)).
* Keep indentation clean.
* Organize structure with `<header>`, `<main>`, `<footer>`.
* Use lowercase tags and attributes (consistent convention).

---

## 10. Future of HTML

* HTML is now a **living standard**, constantly updated.
* New features include **Web Components**, **Custom Elements**, and integration with modern APIs.
* Accessibility and semantics are gaining more importance with **WCAG guidelines** and inclusive design.
