# Creating Gaps Between Tracks in CSS Grid

In CSS Grid, a **track** is the space between two neighboring grid lines (referring to either rows or columns). The `column-gap`, `row-gap`, and `gap` properties allow you to set spacing (gutters) between grid tracks without adding unwanted outer margins.

## 📏 1. Column Gaps (`column-gap`)

The `column-gap` property sets horizontal spacing between grid columns.

### HTML

```
<link rel="stylesheet" href="styles.css">
<div class="grid-container">
  <div></div>
  <div></div>
  <div></div>
  <div></div>
</div>

```

### CSS

```
.grid-container {
  display: grid;
  height: 100px;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  column-gap: 10px; /* 10px horizontal gap between 4 columns */
}

.grid-container div {
  background-color: darkblue;
}

```

> **Note on `normal`**: Setting `column-gap: normal` defaults to `0` in standard CSS Grid layouts.

---

## ↕️ 2. Row Gaps (`row-gap`)

The `row-gap` property sets vertical spacing between grid rows.

### CSS Example (2 Rows, 2 Columns)

```
.grid-container {
  display: grid;
  grid-template-columns: 1fr 1fr; /* 2 columns create 2 implicit rows */
  column-gap: 10px;
  row-gap: 30px;   /* 30px vertical gap between rows */
}

.grid-container div {
  height: 100px;
  background-color: darkblue;
}

```

---

## ⚡ 3. The `gap` Shorthand Property

Instead of writing `row-gap` and `column-gap` separately, use the `gap` shorthand.

### Basic Syntax

```
/* Two values: gap: <row-gap> <column-gap>; */
gap: 30px 10px;

/* One value: gap: <row-and-column-gap>; */
gap: 20px; /* Sets both row-gap and column-gap to 20px */

```

### CSS Example using `gap` Shorthand

```
.grid-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 30px 10px; /* row-gap = 30px, column-gap = 10px */
}

.grid-container div {
  height: 100px;
  background-color: darkblue;
}

```

---

## ⚠️ Acceptable Units & Restrictions

* **Supported Units**: `px`, `em`, `rem`, `%`, `vh`/`vw`, and `calc()`.

* **Forbidden Units**: You **cannot** use `fr` units for `gap`, `row-gap`, or `column-gap`.

---

## 🧠 Quick Review (TL;DR)

| Property | Description | Example Syntax | 
| ----- | ----- | ----- | 
| **`column-gap`** | Spacing between vertical grid columns. | `column-gap: 15px;` | 
| **`row-gap`** | Spacing between horizontal grid rows. | `row-gap: 20px;` | 
| **`gap` Shorthand** | Combines row and column gaps (`<row> <column>`). | `gap: 20px 10px;` | 
| **Single-Value `gap`** | Applies identical spacing to both rows and columns. | `gap: 16px;` | 
| **Invalid Units** | Fractional (`fr`) units are **not allowed**. | `gap: 1fr;` ❌ | 
