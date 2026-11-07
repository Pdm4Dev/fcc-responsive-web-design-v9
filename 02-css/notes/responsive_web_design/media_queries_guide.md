# CSS Media Queries: Types, Features & Logic

**Media queries** are a foundational CSS feature in Responsive Web Design. They allow developers to conditionally apply styles depending on the user's device characteristics, screen dimensions, resolution, input mechanisms, or user system preferences.

---

## 🛠️ Basic Syntax

```css
@media mediatype and (feature: value) {
  /* CSS rules apply only if conditions are met */
}
```

* **`mediatype`**: The target category of device (optional, defaults to `all`).
* **`feature: value`**: The specific condition/property to check.

---

## 📺 Common Media Types

| Media Type | Target Devices / Environments | Status |
| :--- | :--- | :--- |
| **`all`** | Suitable for all devices (default if omitted). | Active |
| **`screen`** | Primary target for desktop screens, smartphones, tablets. | Active |
| **`print`** | Intended for printed physical output and print-preview mode. | Active |
| *`handheld`, `tv`* | Older legacy target types. | **Deprecated** |

---

## 🔍 Popular Media Features & Examples

### 1. Viewport Dimensions (`width` / `height`)
Used with `min-` or `max-` prefixes for range checks.

```css
@media screen and (min-width: 768px) {
  /* Screens at least 768px wide */
}
```

### 2. Aspect Ratio (`aspect-ratio`)
Tests the ratio of viewport width to height.

```css
@media screen and (aspect-ratio: 16/9) {
  /* Viewports with exact 16:9 aspect ratio */
}
```

### 3. Screen Orientation (`orientation`)
Checks whether the device is held vertically or horizontally.

```css
@media screen and (orientation: landscape) {
  /* Horizontal/Landscape viewports */
}
```

### 4. Display Resolution (`resolution`)
Checks device pixel density in `dpi` (dots per inch) or `dpcm`.

```css
@media screen and (min-resolution: 300dpi) {
  /* High-density (Retina / HDPI) displays */
}
```

### 5. Input Capabilities (`hover`)
Checks if the primary input mechanism supports hovering (e.g., mouse cursor vs. touch screen).

```css
@media (hover: hover) {
  /* Rules for devices with mouse/pointer input */
}
```

### 6. User Preferences (`prefers-color-scheme`)
Detects if the user selected Light or Dark mode in system preferences.

```css
@media (prefers-color-scheme: dark) {
  body {
    background-color: #121212;
    color: #ffffff;
  }
}
```

---

## 🔀 Combining Multiple Conditions (Logical Operators)

### `and` Operator (ALL conditions must be true)
```css
@media screen and (min-width: 768px) and (orientation: landscape) {
  /* Landscape screens AT LEAST 768px wide */
}
```

### Comma `,` Operator (OR logic - ANY condition can be true)
```css
@media screen and (min-width: 768px), print {
  /* Screens AT LEAST 768px wide OR printed media */
}
```

### `not` Operator (Negates the query)
```css
@media not screen and (color) {
  /* Reverses the condition evaluation */
}
```

---

## ⚠️ Cascade & Specificity Rule

* Media queries **do not increase CSS specificity**.
* Rules inside media queries still follow standard **CSS Cascade** rules (order of appearance matters).
* **Best Practice:** Place media queries **after** base styles in your stylesheet to properly override default values.

---

## 📱 Mobile-First Implementation Example

### HTML
```html
<link rel="stylesheet" href="styles.css">
<div class="container">
  <p>Responsive text content block.</p>
</div>
```

### CSS
```css
/* 1. Base Styles (Default for Mobile Devices) */
.container {
  width: 100%;
  padding: 15px;
}

/* 2. Tablet Progressive Enhancement */
@media screen and (min-width: 768px) {
  .container {
    width: 750px;
    margin: 0 auto;
  }
}

/* 3. Desktop Progressive Enhancement */
@media screen and (min-width: 1024px) {
  .container {
    width: 960px;
  }
}
```

---

## 🧠 Quick Review (TL;DR)

| Concept | Key Takeaway |
| :--- | :--- |
| **Basic Syntax** | `@media type and (feature: value) { ... }` |
| **Default Type** | `all` (if omitted) |
| **Logic** | `and` = BOTH true \| `,` (comma) = EITHER true |
| **Input Detection** | Use `(hover: hover)` for mouse devices vs. touchscreens |
| **Cascade Behavior** | Media queries do not boost specificity; standard source order applies |
