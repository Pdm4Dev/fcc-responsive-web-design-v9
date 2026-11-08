# CSS Grid Template Areas: `grid-template-areas` & `grid-area`

The **`grid-template-areas`** property provides an intuitive, ASCII-art-like syntax to define visual grid layouts using named regions. Child items are then assigned to these regions using the **`grid-area`** property.

## 📐 1. Syntax Breakdown

```css
grid-template-areas:
  'header header header'
  'sidebar-left main sidebar-right'
  'footer footer footer';
```

* **Strings represent Rows**: Each string in quotes (e.g., `'header header header'`) represents a single grid row.
* **Words represent Columns**: Each space-separated name within a string represents a grid column cell.
* **Matrix Size**: The example above creates a **3-row by 3-column** grid container.
* **Empty Cells**: A period (`.`) can be used as a placeholder to represent an empty grid cell without a name.

---

## 🏛️ 2. Practical Example: The Holy Grail Layout

The **Holy Grail Layout** consists of a header, main content region, two flanking sidebars, and a footer. Using named grid areas is the cleanest way to construct this structure.

### HTML

```html
<link rel="stylesheet" href="styles.css">
<div class="grid-container">
  <div class="header">
    <h2>Header</h2>
  </div>
  <div class="sidebar-left">
    <h2>Left Sidebar</h2>
  </div>
  <div class="main">
    <h2>Main Content</h2>
  </div>
  <div class="sidebar-right">
    <h2>Right Sidebar</h2>
  </div>
  <div class="footer">
    <h2>Footer</h2>
  </div>
</div>
```

### CSS

```css
/* Container Layout Definition */
.grid-container {
  display: grid;
  grid-template-areas:
    'header header header'
    'sidebar-left main sidebar-right'
    'footer footer footer';
  gap: 10px;
  background-color: #2196F3;
  padding: 10px;
}

/* Mapping Child Elements to Named Areas */
.header {
  grid-area: header;
  background-color: rgba(255, 255, 255, 0.8);
  padding: 20px;
  text-align: center;
}

.sidebar-left {
  grid-area: sidebar-left;
  background-color: rgba(255, 255, 255, 0.8);
  padding: 20px;
  text-align: center;
}

.main {
  grid-area: main;
  background-color: rgba(255, 255, 255, 0.8);
  padding: 20px;
  text-align: center;
}

.sidebar-right {
  grid-area: sidebar-right;
  background-color: rgba(255, 255, 255, 0.8);
  padding: 20px;
  text-align: center;
}

.footer {
  grid-area: footer;
  background-color: rgba(255, 255, 255, 0.8);
  padding: 20px;
  text-align: center;
}
```

---

## 🔑 3. Key Distinctions Between `grid-template-areas` & `grid-area`

While frequently used together, both properties serve distinct functions:

| Property | Applied To | Role & Functionality |
| :--- | :--- | :--- |
| **`grid-template-areas`** | Grid **Container** | Defines the macro structural template by mapping out named regions in row/column strings. |
| **`grid-area`** | Grid **Item** | Assigns a child element to a specific named region (or can be used as shorthand for numeric grid lines: `row-start / col-start / row-end / col-end`). |

---

## 📱 4. Responsive Layout Redefinition

One major advantage of `grid-template-areas` is how easily layouts can be altered for mobile viewports using media queries—without touching child element styles:

```css
/* Mobile Viewport: Stack everything in 1 single column */
@media (max-width: 768px) {
  .grid-container {
    grid-template-areas:
      'header'
      'main'
      'sidebar-left'
      'sidebar-right'
      'footer';
  }
}
```

---

## 🧠 Quick Review (TL;DR)

| Concept | Key Point |
| :--- | :--- |
| **Syntax** | Each quoted string = **Row**, each name within quotes = **Column**. |
| **Placeholder** | Use `.` to leave a cell empty (e.g., `'header . header'`). |
| **Holy Grail Pattern** | Easily built by assigning `grid-area` labels to main elements. |
| **RWD Benefit** | Reorder the entire page layout on mobile screens by simply changing the `grid-template-areas` string inside a media query. |