# 🖼️ Web Accessibility: `alt` Attribute & Best Practices

## 🎯 Primary Purpose of the `alt` Attribute
1. **Accessibility (a11y):** Screen readers pronounce the text for visually impaired users.
2. **Fallback:** Displayed by the browser if the image fails to load (network error, broken URL).
3. **SEO:** Search engine crawlers use `alt` text to index images and understand context.

---

## ⚖️ Bad vs. Good Alt Text

### Example 1: Puppy on a Beach
* ❌ **Bad:** `alt="A cute puppy."` *(Too vague, lacks key details)*
* ✅ **Good:** `alt="A black and white puppy with an orange collar lies on its belly in the sand. A bright orange ball rests near its front paws."`

### Example 2: Tropical Resort
* ❌ **Bad:** `alt="Resort."` *(Too brief)*
* ✅ **Good:** `alt="Tropical resort featuring a swimming pool surrounded by palm trees and bungalows."`

> 💡 **Context Matters:** Tailor the description to the page’s primary purpose. A dog breeding website should focus on physical traits, while a travel website should focus on the resort atmosphere.

---

## ⚡ Alt Text Best Practices Checklist

- [ ] **Be Concise:** Describe essential details without cluttering the user experience.
- [ ] **Avoid Redundancy:** Do NOT start with *"image of"* or *"picture of"* (screen readers automatically announce images).
- [ ] **No Duplicate Info:** Do not repeat text that already exists in nearby headings, captions, or paragraphs.
- [ ] **Punctuation:** End descriptions with a period `.` to trigger a natural pause in screen reader speech.
- [ ] **Functional Images (Image Links):** When an image is wrapped in `<a>`, the `alt` text must describe the **action/destination**, not the visual appearance.
  * ❌ `alt="Right arrow."`
  * ✅ `alt="Go to next page."`

---

## 🎨 Decorative Images

If an image is purely decorative (background graphics, visual spacers) and conveys no meaningful information:

* ✅ **Use empty alt text:** `alt=""` (instructs screen readers to skip the image).
* ❌ **NEVER omit the `alt` attribute completely!** Omitting `alt` causes screen readers to read out the full image file name (`src="decorative_banner_v2.jpg"`), creating unnecessary noise.

```html
<!-- Informational Image -->
<img src="puppy.png" alt="A black and white puppy on the sand." />

<!-- Functional Image (Link) -->
<a href="next.html">
  <img src="arrow.png" alt="Go to next page." />
</a>

<!-- Decorative Image -->
<img src="divider-pattern.png" alt="" />