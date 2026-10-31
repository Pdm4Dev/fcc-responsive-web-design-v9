# 🔗 Web Accessibility: Link Text Guidelines

## 🎯 Benefits of Good Link Text
- **Faster Information Retrieval:** Descriptive links help all users quickly understand where a link leads, preventing them from feeling lost.
- **Screen Reader Usability:** Assistive technologies announce link text aloud; clear text like `"Read our accessibility guide"` provides immediate value compared to generic phrasing like `"Click here"`.
- **Cognitive Accessibility:** Provides clear, predictable context to assist users with cognitive disabilities.

---

## ⚡ Best Practices Checklist

- [ ] **Visual Distinction:** Make links easy to identify using underlining and other visual cues.
- [ ] **Avoid Generic Text:** Do not use uninformative text such as `"here"`, `"click here"`, or `"more-info"`.
- [ ] **Concise & Purposeful:** Aim for **2–5 descriptive words** that clearly convey the link's purpose.
- [ ] **Plain Language:** Avoid jargon and abbreviations that users may not understand.
- [ ] **Focus on Destination:** Describe the destination rather than the action (e.g., `"user behavior results"` instead of `"click here to read more"`).
- [ ] **Unique Link Text:** Avoid repeating the exact same link text for different destinations on the page.
- [ ] **Natural Integration:** Structure surrounding sentences so the link text flows naturally within context (e.g., `"for more details, visit our events page"` instead of `"Click here for more"`).

---

## ⚖️ Code Examples: Bad vs. Good

### 1. Event Details
* ❌ **Bad:** `<a href="webinar-details-link">Details</a>` *(Vague; doesn't specify if details are for a webinar, product, or policy)*
* ✅ **Good:** `<a href="webinar-details-link">Get details about our upcoming webinar</a>`

### 2. Blog Post
* ❌ **Bad:** `<a href="/blog-post-link">Read more</a>` *(Lacks context when read in isolation)*
* ✅ **Good:** `<a href="/blog-post-link">Read our latest blog post on web accessibility</a>`

### 3. Topic Information
* ❌ **Bad:** `<a href="/link-to-topic">More info</a>` *(Problematic for non-linear screen reader navigation)*
* ✅ **Good:** `<a href="/link-to-topic">Learn more about our accessibility efforts</a>`