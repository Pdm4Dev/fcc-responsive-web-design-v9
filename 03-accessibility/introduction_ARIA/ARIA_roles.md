# 🏷️ ARIA Roles: Types & Best Practices

## 🎯 What are ARIA Roles?
* **Definition:** Attributes (`role="..."`) that specify the semantic meaning and purpose of HTML elements for assistive technologies (like screen readers).
* **Key Limitation:** Roles **only** inform assistive technology of an element's purpose; they **do not** add underlying behavior, styling, or native functionality (e.g., adding `role="button"` to a `<div>` does not make it focusable or clickable without custom JavaScript and CSS).

---

## 📂 6 Categories of ARIA Roles

### 1. Document Structure Roles
* **Purpose:** Define overall document structure to help screen readers navigate sections.
* **Best Practice:** **Prioritize native HTML elements** (like headings, paragraphs, lists). Use ARIA roles *only* for elements without semantic HTML equivalents (e.g., `math`, `tooltip`, `feed`, `note`, `presentation`, `none`).
* *Example:* `<div role="math" aria-label="x squared + y squared = 3">x<sup>2</sup> + y<sup>2</sup> = 3</div>`

### 2. Widget Roles
* **Purpose:** Define interactive components and UI widgets.
* **Examples:** `searchbox`, `slider`, `switch`, `tab`, `tabpanel`, `scrollbar`, `treeitem`.
* **Best Practice:** Always prefer native interactive HTML elements over custom widgets with roles whenever possible.

### 3. Landmark Roles
* **Purpose:** Classify and label primary page sections for fast screen-reader navigation.
* **Examples:** `banner`, `navigation`, `main`, `contentinfo` (footer), `complementary` (aside), `form`, `search`.
* **Best Practice:** Modern HTML has native equivalents (`<header>`, `<nav>`, `<main>`, `<footer>`, `<aside>`, `<form>`, `<search>`). **If you use correct semantic HTML, explicit landmark roles are redundant and unnecessary.**

### 4. Live Region Roles
* **Purpose:** Notify screen readers when dynamic content changes in real-time.
* **Examples:** `alert`, `status`, `log`, `timer`, `marquee`.
* *Example:* `<div id="status-msg" role="status">No updates yet.</div>`

### 5. Window Roles
* **Purpose:** Define sub-windows, overlays, and popup dialogs.
* **Examples:** `dialog`, `alertdialog`.
* **Best Practice:** Modern development standard dictates using the native HTML `<dialog>` element and its built-in JavaScript methods instead of manually building accessible custom dialogs with ARIA roles.

### 6. Abstract Roles
* **Purpose:** Internal roles used strictly by the browser specification to organize the ARIA taxonomy.
* **Rule:** **Never use abstract roles** in your custom code.

---

## ⚡ Golden Rule of ARIA Roles
* **Native HTML First:** Always use native semantic HTML elements (`<button>`, `<nav>`, `<dialog>`) before reaching for ARIA roles. 
* *"No ARIA is better than bad ARIA."* Overuse or misuse of roles confuses assistive tech and degrades user experience.