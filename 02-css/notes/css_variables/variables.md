# CSS Custom Properties (CSS Variables)

**CSS Custom Properties** (commonly called **CSS Variables**) allow developers to store specific values in named entities and reuse them throughout a stylesheet. They improve code maintainability, facilitate dynamic layout updates, and simplify theme implementation.

---

## 🛠️ 1. Basic Declaration and Usage

Custom properties begin with a double hyphen (`--`). They are accessed using the `var()` function.

### Global Scope with `:root`

Declaring custom properties inside `:root` makes them accessible everywhere in the document (the top-level DOM node).

```css
/* Declaration */
:root {
  --main-color: #3498db;
}

/* Usage */
.button {
  background-color: var(--main-color);
}
```

---

## 🌊 2. Cascading and Scope Overrides

Custom properties follow standard CSS cascade and inheritance rules. You can override a global property locally within a specific class or component context.

```css
:root {
  --main-color: #3498db; /* Default global color */
}

.alert {
  --main-color: #e74c3c; /* Local override for alerts */
  background-color: var(--main-color);
}
```

---

## 🛡️ 3. Fallback Values

The `var()` function accepts a second parameter as a **fallback value** in case the variable is undefined or invalid.

```css
:root {
  --text-color: green;
}

.text {
  /* Uses --text-color if defined, otherwise falls back to 'green' */
  color: var(--text-color, green);
}
```

---

## 🎨 4. Theme Management

Custom properties simplify switching light/dark themes or sub-brand themes by reassigning values under a specific theme class or attribute.

```css
:root {
  --bg-color: black;
  --text-color: white;
}

body {
  background-color: var(--bg-color);
  color: var(--text-color);
}

/* Light Theme Override */
.light-theme {
  --bg-color: white;
  --text-color: black;
}
```

---

## 📐 5. Responsive Design with Media Queries

Updating variables within media queries changes responsive layout parameters site-wide without needing to re-target individual elements.

```html
<div class="card">
  <h2>Responsive Design</h2>
  <p>Resize the window to see the card adapt!</p>
</div>
```

```css
/* Default Mobile Values */
:root {
  --card-width: 90%;
  --card-bg: #f0f0f0;
  --card-padding: 1rem;
  --text-color: #333;
}

/* Tablet Screens */
@media (min-width: 600px) {
  :root {
    --card-width: 70%;
    --card-bg: #e8f5e9;
    --card-padding: 1.5rem;
  }
}

/* Desktop Screens */
@media (min-width: 1024px) {
  :root {
    --card-width: 50%;
    --card-bg: #d0f0ff;
    --card-padding: 2rem;
  }
}

.card {
  width: var(--card-width);
  background-color: var(--card-bg);
  padding: var(--card-padding);
  color: var(--text-color);
  border-radius: 8px;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.1);
  text-align: center;
  transition: all 0.3s ease;
}
```

---

## 🔗 6. Referencing Other Custom Properties

A custom property can be set to the value of another custom property, creating design system relationships (e.g., alias tokens).

```css
:root {
  --primary-color: #3498db;
  --button-bg: var(--primary-color); /* Alias assignment */
}

button {
  background-color: var(--button-bg);
}
```

---

## 🧠 Quick Review (TL;DR)

| Feature | Syntax / Concept | Description |
| :--- | :--- | :--- |
| **Declaration** | `--name: value;` | Must start with `--`. Declared in CSS selectors (e.g., `:root`). |
| **Usage** | `var(--name, fallback)` | Pulls the value of the custom property with an optional fallback. |
| **Scope** | Cascading & Inherited | Local declarations override `:root` values for target elements and their children. |
| **Responsive Use** | `@media { :root { --var: ... } }` | Simplifies media queries by changing variable values in one central place. |
| **Chaining** | `--b: var(--a);` | Custom properties can reference other custom properties. |
