# CSS Grid vs. Flexbox

**CSS Grid** is a two-dimensional layout system designed to manage both rows and columns simultaneously. It simplifies creating complex, responsive web page structures by placing elements into a predefined grid matrix.

---

## 📐 Key Differences: CSS Grid vs. Flexbox

| Feature | CSS Grid | Flexbox |
| :--- | :--- | :--- |
| **Dimensionality** | **2D (Two-Dimensional)**: Controls rows and columns at the same time. | **1D (One-Dimensional)**: Controls a single axis (either row *or* column at once). |
| **Design Approach** | **Layout-First**: You define the grid track structure first, then place elements inside it. | **Content-First**: Layout flows dynamically depending on size and size constraints of the individual items. |
| **Best For** | Overall page layout, image galleries, complex multi-column structures. | Navigation bars, form inputs, button groups, aligning items inside components. |

---

## 🧱 1. CSS Grid Implementation

Setting `display: grid` transforms an element into a grid container. The `grid-template-columns` property defines column tracks (using fractional units like `1fr`), while `gap` sets gutter spacing between grid cells.

### HTML

```html
<div class="container">
  <div class="item">Item 1</div>
  <div class="item">Item 2</div>
  <div class="item">Item 3</div>
  <div class="item">Item 4</div>
  <div class="item">Item 5</div>
  <div class="item">Item 6</div>
</div>
```

### CSS (Grid Layout)

```css
.container {
  display: grid;
  /* Creates 3 columns of equal width */
  grid-template-columns: 1fr 1fr 1fr; 
  /* Sets a 20px gap between grid items */
  gap: 20px; 
}

.item {
  background-color: lightgray;
  padding: 20px;
  text-align: center;
  border: 1px solid #ccc;
}
```

---

## 🔀 2. Flexbox Comparison Example

Flexbox arranges elements sequentially along a single main axis.

### CSS (Flexbox Layout)

```css
.container {
  display: flex;
  /* Distributes items along a single horizontal axis */
  justify-content: space-between; 
}
```

---

## 🤝 Using Grid and Flexbox Together

Modern web development frequently combines both tools:

* Use **CSS Grid** to construct the high-level macro structure of the webpage (e.g., header, sidebar, main content area, footer).
* Use **Flexbox** inside specific component elements to align child content (e.g., aligning an icon and text inside a navbar item).

---

## 🧠 Quick Review (TL;DR)

| Concept | Description |
| :--- | :--- |
| **CSS Grid** | Two-dimensional (`rows` + `columns`), Layout-first design model. |
| **Flexbox** | One-dimensional (`row` *or* `column`), Content-first design model. |
| **`grid-template-columns`** | Defines column sizes (e.g., `1fr 1fr 1fr` creates 3 equal columns). |
| **`gap`** | Defines space between grid cells or flex items without using margins. |
