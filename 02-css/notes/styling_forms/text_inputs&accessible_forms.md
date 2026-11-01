# Best Practices for Styling Text Inputs & Accessible Forms

This document covers key best practices for styling text inputs (`<input>`, `<textarea>`) with a primary focus on **Accessibility (a11y)**, User Experience (UX), and state management.

---

## 📌 Core Principles

1. **Sufficient Contrast & Font Sizing**: Text elements must be legible. Always maintain high contrast between text colors and the background.
2. **Accessible Placeholders (`::placeholder`)**: Placeholders are text elements too. Override default browser opacity (`opacity: 1`) and ensure adequate visual contrast.
3. **Clear Focus Indicators (`:focus`)**: Provide an obvious visual cue when an element receives focus (for keyboard navigation and accessibility).
4. **User Control & Resizing**: Avoid disabling native accessibility controls like `<textarea>` resizing. Ensure inputs scale smoothly when zoomed.
5. **Distinct Error States (`.error`)**: The error state must be visually distinct from both normal and standard focus states.

---

## 🛠 1. Accessible Placeholder Styling

By default, many browsers render input placeholders with low opacity. Ensure placeholders are readable:

```css
input::placeholder {
  color: #555;        /* High contrast color */
  opacity: 1;         /* Override browser default fading */
  font-style: italic; /* Additional visual distinction */
}
```

---

## 🔍 2. Focus State Management

Never remove the default `outline` without providing a prominent, high-contrast replacement such as a custom `border-color` combined with `box-shadow`.

```css
input[type="text"],
input[type="email"] {
  width: 100%;
  padding: 0.6rem 0.8rem;
  font-size: 1rem;
  border: 2px solid #666;
  border-radius: 4px;
  background-color: #fff;
  color: #111;
  transition: border-color 0.2s, box-shadow 0.2s;
}

/* Noticeable focus ring */
input:focus {
  outline: none; /* Remove default outline ONLY when replaced by box-shadow */
  border-color: #1e90ff;      
  box-shadow: 0 0 0 3px rgba(30, 144, 255, 0.4); 
}
```

---

## 📐 3. Textarea & Resizability

Allow users to adjust form controls to their needs. Avoid setting `resize: none`.

### HTML
```html
<label for="message">Your message</label>
<textarea id="message" name="message" placeholder="Type your message here..."></textarea>
```

### CSS
```css
textarea {
  width: 100%;
  min-height: 120px;
  padding: 0.8rem;
  font-size: 1rem;
  border: 2px solid #555;
  border-radius: 4px;
  resize: both; /* Preserve the user's ability to resize */
  box-sizing: border-box; /* Include padding & border in width */
}
```

---

## ⚠️ 4. Styling Error States & Accessibility

Use `aria-describedby` to programmatically link error messages to input fields for screen reader accessibility.

### HTML
```html
<form class="accessible-form">
  <label for="email">Email address</label>
  <input 
    type="email" 
    id="email" 
    name="email" 
    placeholder="you@example.com" 
    aria-describedby="email-error"
    class="error"
  >
  <p id="email-error" class="error-message">
    Please enter a valid email address.
  </p>

  <button type="submit">Submit</button>
</form>
```

### CSS
```css
/* Input with validation error */
input.error {
  border-color: #d93025;
  background-color: #fff5f5;
}

/* Focus state on an erroneous field */
input.error:focus {
  border-color: #d93025;
  box-shadow: 0 0 0 3px rgba(217, 48, 37, 0.4);
}

/* Text style for the error message */
.error-message {
  color: #d93025;
  font-size: 0.95rem;
  margin-top: 0.4rem;
}
```

---

## 🧠 Quick Review (TL;DR)

| Feature / State | Key Requirement | CSS / HTML Implementation |
| :--- | :--- | :--- |
| **`::placeholder`** | Sufficient visual contrast | `color: #555; opacity: 1;` |
| **`:focus`** | High-contrast keyboard focus indicator | `border-color` + `box-shadow` |
| **`<textarea>`** | Keep resizing enabled | `resize: vertical;` or `resize: both;` |
| **`input.error`** | Visually distinct from standard focus | Red `border-color` and light tint background |
| **Screen Readers** | Link inputs to error feedback | Attribute `aria-describedby="[error-id]"` |