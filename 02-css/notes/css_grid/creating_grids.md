# Creating Flexible Grids with the CSS `fr` Unit

The **`fr` (fractional) unit** in CSS Grid represents a fraction of the **remaining available space** in a grid container. Using `fr` units enables dynamic, proportional layout sizing without manual pixel calculations or overflow bugs caused by fixed percentage gaps.

## ❓ Why Use `fr` Over Percentages (`%`)?

When using percentage widths (e.g., `grid-template-columns: 25% 25% 25% 25%`), adding a `gap` (e.g., `gap: 15px`) can cause grid columns to overflow their parent container because `100% width + gaps > 100% total available space`.

The **`fr` unit solves this problem automatically**:
* It first subtracts the total space consumed by explicit pixel gaps (`gap`) or fixed-width columns.
* It then divides whatever space remains proportionally among the `fr` tracks.

---

## 💻 Code Examples & Comparison

### 1. Grid using Percentages (`%`)

Percentage columns do not automatically account for gap space.

#### HTML
```html
<link rel="stylesheet" href="styles.css" />
<div class="grid-container">
  <div class="col"></div>
  <div class="col"></div>
  <div class="col"></div>
  <div class="col"></div>
</div>
```

#### CSS
```css
html,
body {
  width: 90%;
  height: 50%;
}

.grid-container {
  display: grid;
  /* Fixed 25% allocation per column */
  grid-template-columns: 25% 25% 25% 25%;
  gap: 15px; 
  background-color: darkgray;
  height: 100%;
}

.col {
  background-color: darkslateblue;
}
```

---

### 2. Grid Refactored with `fr` Units (Best Practice)

Refactoring to fractional units ensures that all 4 columns take up an equal share of the remaining space *after* accounting for the `15px` gap.

#### CSS
```css
html,
body {
  width: 90%;
  height: 50%;
}

.grid-container {
  display: grid;
  /* Dynamically distributes available space into 4 equal fractions */
  grid-template-columns: 1fr 1fr 1fr 1fr;
  gap: 15px;
  background-color: darkgray;
  height: 100%;
}

.col {
  background-color: darkslateblue;
}
```

---

## ⚖️ Proportional Layout Sizing

`fr` units don't have to be equal. You can mix fractional ratios to create asymmetric column layouts:

```css
/* Column 1 gets 1 share, Column 2 gets 2 shares (double width), Column 3 gets 1 share */
grid-template-columns: 1fr 2fr 1fr;
```

You can also mix `fr` units with fixed pixel sizes:

```css
/* Sidebar is fixed at 250px; main area takes all remaining dynamic space */
grid-template-columns: 250px 1fr;
```

---

## 🧠 Quick Review (TL;DR)

| Concept | Description |
| ----- | ----- |
| **`fr` Definition** | Fractional unit representing a share of available container space. |
| **Space Calculation** | `Available Space = Container Width - (Gap Sizes + Fixed Columns)` |
| **Key Advantage over `%`** | Automatically accounts for `gap` spacing without causing overflow issues. |
| **Proportional Sizing** | `grid-template-columns: 1fr 3fr;` creates a 1:3 width ratio between tracks. |
