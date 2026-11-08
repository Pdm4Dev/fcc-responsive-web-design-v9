# CSS `@property` At-Rule & Advanced Custom Properties

The `@property` CSS at-rule (part of the **CSS Houdini API**) provides explicit type checking, default fallback values, inheritance control, and transition capabilities for CSS custom properties.

Unlike standard custom properties (which are parsed as raw string tokens), `@property` registers a variable into the browser's CSSOM with a defined type.

## 🛠️ 1. Basic Syntax

```
@property --property-name {
  syntax: '<type>';
  inherits: true | false;
  initial-value: <value>;
}

```

* **`--property-name`**: The custom property name (must begin with `--`).

* **`syntax`**: Defines the data type (e.g., `<color>`, `<length>`, `<number>`, `<percentage>`, `<angle>`).

* **`inherits`**: Boolean determining if child elements inherit this property from parents.

* **`initial-value`**: Default value used if the property is not explicitly defined or receives an invalid data type.

### Simple Example

```
@property --main-color {
  syntax: '<color>';
  inherits: false;
  initial-value: #3498db;
}

.button {
  background-color: var(--main-color);
}

```

## 🎥 2. Animating Custom Properties & Gradients

Standard custom properties cannot be smoothly animated because browsers treat them as raw strings. `@property` gives custom variables a typed syntax (like `<angle>`), allowing CSS transitions and keyframes to interpolate values smoothly.

### Animating a Linear Gradient Angle

#### HTML

```
<div class="gradient-box"></div>

```

#### CSS

```
@property --gradient-angle {
  syntax: '<angle>';
  inherits: false;
  initial-value: 0deg;
}

.gradient-box {
  width: 100px;
  height: 100px;
  background: linear-gradient(var(--gradient-angle), red, blue);
  transition: --gradient-angle 0.5s ease-in-out;
}

/* Smoothly rotates the gradient angle on hover */
.gradient-box:hover {
  --gradient-angle: 90deg;
}

```

## 🛡️ 3. Strategies for Fallbacks & Type Safety

### Level 1: Legacy Browser Fallbacks

For older browsers that do not support `@property`, declare a standard `:root` custom property alongside the `@property` rule.

```
/* Fallback for legacy browsers */
:root {
  --main-color: #3498db;
}

/* Typed definition for modern browsers */
@property --main-color {
  syntax: '<color>';
  inherits: false;
  initial-value: #3498db;
}

body {
  background-color: var(--main-color);
}

```

### Level 2: `var()` Fallback Values

Use standard `var()` fallback arguments for runtime protection.

```
.button {
  background-color: var(--main-color, #3498db);
}

```

### Level 3: Automatic Type-Safe Fallbacks

Because `@property` validates data types, passing an invalid value automatically triggers the declared `initial-value` instead of breaking the rule.

```
@property --padding {
  syntax: '<length>';
  inherits: false;
  initial-value: 10px;
}

.box {
  width: 100px;
  height: 100px;
  background-color: darkred;
  color: white;
  /* If --padding is assigned an invalid value (e.g. 'red'), it falls back to 10px */
  padding: var(--padding);
}

```

## 🌐 4. Browser Support

* Supported in all major modern browser engines (Chrome, Edge, Opera, Safari, and Firefox).

* Widely available natively across modern browsers.

## 🧠 Quick Review (TL;DR)

| Descriptor | Purpose | Example | 
| ----- | ----- | ----- | 
| **`syntax`** | Restricts the variable to a specific CSS data type. | `'<color>'`, `'<angle>'`, `'<length>'` | 
| **`inherits`** | Controls DOM tree inheritance. | `true` or `false` | 
| **`initial-value`** | Required fallback if value is missing/invalid. | `0deg`, `#ffffff`, `12px` | 
| **Key Capability** | Enables CSS transitions & `@keyframes` on variables. | `transition: --my-color 0.3s;` | 
