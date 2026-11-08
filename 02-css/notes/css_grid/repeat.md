# Repeating Track Listings in CSS Grid (`repeat()`)

The CSS **`repeat()` function** provides a concise syntax for defining repetitive grid track listings (for both `grid-template-columns` and `grid-template-rows`). Instead of manually listing individual track measurements, `repeat()` automatically duplicates specified track sizing patterns.

## 🛠️ Basic Syntax

```
repeat(count, track-size(s))
```

* **`count`**: The number of times to repeat the track pattern (e.g., `4`, `12`).
* **`track-size(s)`**: The track measurement or pattern of measurements to repeat (e.g., `1fr`, `100px`, `20px 1fr`).

---

## 💻 1. Simple Repetition vs. Manual Listing

Instead of explicitly repeating values multiple times:

```css
/* Manual syntax */
grid-template-columns: 1fr 1fr 1fr 1fr;
```

You can write cleaner, refactored code using `repeat()`:

```css
/* Equivalent repeat syntax */
grid-template-columns: repeat(4, 1fr);
```

### Complete Code Example

#### HTML
```html
<link rel="stylesheet" href="styles.css">
<div class="grid-container">
  <div class="box"></div>
  <div class="box"></div>
  <div class="box"></div>
  <div class="box"></div>
</div>
```

#### CSS
```css
.grid-container {
  display: grid;
  grid-template-columns: repeat(4, 1fr); /* 4 equal columns */
  column-gap: 10px;
}

.box {
  width: 100px;
  height: 100px;
  background-color: darkblue;
}
```

---

## 🔄 2. Repeating Multi-Track Patterns

The `repeat()` function can duplicate complex, alternating patterns of multiple values.

### Pattern Example: Alternating Fixed & Fractional Columns

```css
/* Repeats the pair (20px 1fr) twice -> [20px, 1fr, 20px, 1fr] */
grid-template-columns: repeat(2, 20px 1fr);
```

#### CSS Implementation
```css
.grid-container {
  display: grid;
  grid-template-columns: repeat(2, 20px 1fr);
  column-gap: 10px;
}

.grid-container div {
  height: 100px;
  background-color: darkblue;
}
```

* **Column 1**: `20px`
* **Column 2**: `1fr`
* **Column 3**: `20px`
* **Column 4**: `1fr`

---

## 🔀 3. Combining `repeat()` with Explicit Tracks

`repeat()` can be combined with other individual track definitions within the same rule:

```css
/* 1 fixed 200px sidebar + 3 equal remaining fractional columns */
grid-template-columns: 200px repeat(3, 1fr);
```

---

## 🧠 Quick Review (TL;DR)

| Feature | Code Example | Output |
| --- | --- | --- |
| **Basic `repeat()`** | `repeat(3, 1fr)` | `1fr 1fr 1fr` |
| **Fixed Sizes** | `repeat(4, 100px)` | `100px 100px 100px 100px` |
| **Multi-Track Pattern** | `repeat(2, 50px 1fr)` | `50px 1fr 50px 1fr` |
| **Mixed Layout** | `150px repeat(2, 1fr)` | `150px 1fr 1fr` |
| **Primary Advantage** | Clean, readable syntax for grid track definitions. | Reduces code duplication. |
