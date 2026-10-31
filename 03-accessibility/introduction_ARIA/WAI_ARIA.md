# ♿ WAI-ARIA: Purpose, Roles & Best Practices

## 🎯 What is WAI-ARIA?
* **Definition:** Web Accessibility Initiative - Accessible Rich Internet Applications. A specification that enhances accessibility for **dynamic content and complex UI components**.
* **Difference from WCAG:** 
  * *WCAG* provides general accessibility guidelines.
  * *WAI-ARIA* offers specific rules for making dynamic and interactive content accessible to assistive technologies.

---

## ⚙️ How WAI-ARIA Works
WAI-ARIA introduces special attributes categorized into **Roles**, **States**, and **Properties** to provide additional semantic information.

### 1. ARIA Roles
* Defines the purpose/behavior of an element within a web app.
* *Example:* `<div role="button">Click Me</div>`
* ⚠️ **Important:** ARIA roles **do not** provide native functionality. If you use a custom element (like a `<div>`), you must manually add CSS and JavaScript (such as handling keyboard events for `Enter` or `Space`) to make it fully functional.

### 2. ARIA Properties
* Provide additional details and relationships between elements.
* *Example (`aria-labelledby`):* Connects an element to a specific label text.
  ```html
  <h2 id="header-id">About freeCodeCamp</h2>
  <button id="button-id" aria-labelledby="header-id button-id">Learn More</button>