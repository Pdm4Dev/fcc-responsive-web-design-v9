# CSS Grid Placement: `grid-column` & `grid-row`

The **`grid-column`** and **`grid-row`** properties allow you to control the exact position and size of individual grid items inside a CSS Grid container. They work by referencing **grid lines**—the numbered lines dividing tracks horizontally and vertically.

---

## 📐 1. Syntax & Understanding Grid Lines

Grid lines are **1-indexed** (counting starts at 1, not 0). For instance, a 4-column grid has **5 grid lines** (lines 1 through 5).

### Syntax

```css
/* Shorthand syntax using start and end line numbers */
grid-column: <start-line> / <end-line>;
grid-row: <start-line> / <end-line>;
```

* **`<start-line>`**: The grid line where the item begins.
* **`<end-line>`**: The grid line where the item stops (the item fills up to, but does not include, this line).

---

## 💻 2. Basic Positioning Examples

### Base HTML & CSS Setup

```html
<link rel="stylesheet" href="styles.css">
<div class="grid">
  <div class="item1">1</div>
  <div class="item2">2</div>
  <div class="item3">3</div>
  <div class="item4">4</div>
  <div class="item5">5</div>
  <div class="item6">6</div>
</div>
```

```css
.grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr); /* 4 equal columns -> Lines 1 to 5 */
  grid-template-rows: repeat(3, 100px);   /* 3 equal rows -> Lines 1 to 4 */
  gap: 10px;
}

.grid > div {
  display: grid;
  place-items: center;
  background: crimson;
  color: white;
  font-size: 4rem;
}
```

---

### Example A: Spanning Columns

To make the first item span across the first 2 columns (from Line 1 to Line 3):

```css
.item1 {
  grid-column: 1 / 3; /* Starts at Column Line 1, ends at Line 3 */
}
```

### Example B: Spanning Both Columns and Rows

To make the first item occupy 2 columns and 2 rows simultaneously:

```css
.item1 {
  grid-column: 1 / 3; /* Spans columns 1 and 2 */
  grid-row: 1 / 3;    /* Spans rows 1 and 2 */
}
```

---

## 🔄 3. Using the `span` Keyword

Instead of specifying precise end-line numbers, you can use the **`span`** keyword to state how many track cells an item should cover from its starting line.

```css
/* Equivalent to grid-column: 1 / 3; */
.item1 {
  grid-column: 1 / span 2;
  grid-row: 1 / span 2;
}
```

---

## 🧱 4. Practical Layout Example (Masonry / Asymmetric Grid)

By using different column spans across multiple elements, you can easily compose dynamic dashboard tiles or masonry-style gallery layouts.

### HTML

```html
<link rel="stylesheet" href="styles.css">
<div class="grid">
  <div class="item1">1</div>
  <div class="item2">2</div>
  <div class="item3">3</div>
  <div class="item4">4</div>
  <div class="item5">5</div>
  <div class="item6">6</div>
  <div class="item7">7</div>
</div>
```

### CSS

```css
.grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(4, 100px);
  gap: 10px;
}

.grid > div {
  display: grid;
  place-items: center;
  background: crimson;
  color: white;
  font-size: 4rem;
}

/* Custom Item Spans */
.item1 {
  grid-column: 1 / span 2; /* Occupies 2 columns */
}

.item4 {
  grid-column: 1 / span 3; /* Occupies 3 columns */
}

.item6 {
  grid-column: 1 / span 2; /* Occupies 2 columns */
}

.item7 {
  grid-column: 3 / span 2; /* Starts at line 3 and spans 2 columns */
}
```

---

## 🧠 Quick Review (TL;DR)

| Property | Purpose | Example |
| ----- | ----- | ----- |
| **`grid-column`** | Sets column start and end lines (or span count). | `grid-column: 1 / 4;` |
| **`grid-row`** | Sets row start and end lines (or span count). | `grid-row: 2 / span 3;` |
| **`span` Keyword** | Tells an item how many tracks to occupy. | `grid-column: 2 / span 2;` |
| **Indexing** | Grid line counting starts at `1` (not `0`). | 4 columns = 5 total lines |
