---
tags:
  - Markup
  - css
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses the override order of css.
Status: Done
Started: 
EditDate: 2024-02-26
Relates: 
Peer Reviewed: 0
dg-publish: false
---
In CSS, the cascade and specificity determine the order in which styles are applied.

### Override Order

1. **`!important` (Avoid Using):**
   - This declaration is applied regardless of specificity and order. However, it's generally discouraged due to its global impact and potential to cause maintenance issues.

2. **Inline Style:**
   - Styles defined directly within the HTML element using the `style` attribute take precedence over other rules.

3. **ID Selector (`#id`):**
   - Styles applied to elements with a specific ID override styles from classes and tags.

4. **Class Selector (`.class`):**
   - Styles applied based on class selectors override styles from tags.

5. **Element (Tag) Selector:**
   - Generic styles applied to all instances of a particular HTML tag.

6. **Order (Top to Bottom):**
   - If multiple rules of the same specificity are defined, the one declared later in the stylesheet takes precedence. Order matters in the cascade.

7. **Inherited Styles:**
   - Child elements inherit styles from their parent, and these inherited styles can be overridden by more specific rules.

8. **Browsers Default Styles:**
   - The default styles applied by browsers serve as the baseline. Any style declarations will override these defaults.

### Notes
- **Multiple Classes for a Tag:**
  - When a tag has multiple classes, the one defined at the bottom of the stylesheet will be applied.

- **Specificity Example (H1 Header):**
  - If you have conflicting styles for an H1 header, e.g., one rule setting color to red and another through a class setting it to green, the red color will be selected because it's more specific (inline styles have the highest specificity).

- **Reference:**
  - You can refer to resources like [this blog](https://blog.webdevsimplified.com/2020-02/css-specificity/) for a deeper understanding of CSS specificity.

Remember, understanding specificity and the cascade is crucial for maintaining a predictable and manageable style system in your web projects.