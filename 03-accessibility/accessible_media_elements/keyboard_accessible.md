# ⌨️ Web Accessibility: Keyboard Navigation

## 🎯 Why Keyboard Accessibility Matters
Many users rely entirely on keyboards (instead of a mouse) due to physical disabilities, repetitive strain injuries (RSI), screen reader usage, or broken hardware.

---

## 🔢 The `tabindex` Attribute
Controls whether elements are focusable and defines their navigation order via the `Tab` key.

### Values & Behavior:
1. **`tabindex="0"`**
   * Adds non-interactive elements (like a `<div>` or `<p>`) into the natural, sequential tab order.
   * ```html
     <button>First</button>
     <div tabindex="0">Second</div>
     <a href="#">Third</a>
     ```

2. **`tabindex="-1"`**
   * Removes an element from the natural tab order, but makes it **programmatically focusable** via JavaScript.
   * *Use case:* Moving focus to dialogs, headings, or error messages dynamically.
   * ```html
     <p tabindex="-1">Sorry, there was an error with your submission.</p>
     ```

3. **`tabindex="1"` (Positive Values)**
   * Sets a **custom tab order** (elements with lower values are focused first, regardless of HTML order).
   * ⚠️ **Anti-pattern / Discouraged:** Can make navigation confusing, non-intuitive, and hard to maintain as pages grow.

---

## 🔤 The `accesskey` Attribute
Allows defining a shortcut key to focus or activate a specific element.

* **Usage:** `<button accesskey="s">Save</button>`
* **Browser Shortcuts:** 
  * Windows: `ALT + [Key]`
  * Mac: `CTRL + Option + [Key]`
* ⚠️ **Best Practice / Warning:** Generally **avoid** using `accesskey`. It frequently conflicts with browser/screen reader shortcuts, varies across operating systems, and is difficult for users to discover.

---

## 👁️ Focus Indicators & Best Practices

- **Visible Focus States:** Never remove focus indicators (`outline: none`) without providing a clear custom alternative.
- **Styling Focus:** Use CSS `:focus` to make focused elements obvious (minimum **3:1 color contrast** ratio with the background).
  ```css
  button:focus {
    outline: 2px solid #005fcc;
  }