# CSS Style Guide
A comprehensive CSS style guide for maintaining consistency, readability, and scalability in web/application development projects. Ideal for teams and individual developers striving for clean and efficient code.

## Indentation and Formatting

Use 2 spaces or 4 spaces for indentation (no tabs) for consistency.
Each rule should be on its own line.
Keep properties and values on separate lines:

```
selector {
  property: value;
  property: value;
}
```

## Selector Naming Conventions
Use lowercase for all class and ID names.
Use hyphens (-) for naming before element.
Use hyphens (__) for naming before modifier.
Use BEM (Block Element Modifier) methodology for large projects

```
.block { }
.block-element { }
.block-element__modifier { }

```

## CSS Specificity and Structure

Avoid overly specific selectors.
Keep selectors as short as possible to avoid specificity issues.

```
/* Bad */
div.container > ul > li > a { }

/* Good */
.container a { }

```

## Use shorthand properties where possible
Utilize shorthand properties for margin, padding, background, etc., where applicable
```
/* Instead of this */
margin-top: 2rem;
margin-right: 2rem;
margin-bottom: 2rem;
margin-left: 2rem;

/* Use this */
margin: 2rem;

```

## Consistent Units
Use relative units (rem, %) over fixed units (px) to allow for better scalability.
```
.element{
    font-size: 1.6rem;
    padding: 2.4rem 3.2rem
}
```

## Use of Hex, RGB, or HSL for Colors
Prefer using hex codes for colors. For more control (e.g., opacity), use rgba or hsla
```
.element{ 
    color: #ff5733;
    background-color: rgba(255, 87, 51, 0.5);
}
```

## Class Reusability
Avoid using IDs for styling; rely on class selectors for reusability.
Keep classes reusable by not coupling them too tightly to a specific element.

## Avoid Overwriting CSS
Don't use !important unless absolutely necessary, as it makes debugging difficult.

## Use Variables (CSS Custom Properties)
Use CSS variables to maintain consistency for common values (colors, fonts, spacing)
```
:root {
  --font-size: 1.6rem;
  --primary-color: #3498db;
  --secondary-color: #2ecc71;
}

body {
  color: var(--primary-color);
  font-size: var(--font-size);
}
```

## Consistent units
To maintain a clean and consistent design system, use units based on multiples of 2 or 4. This approach ensures logical spacing, alignment, and scalability across your project.

Small Units: 2px, 4px, 8px, 12px
Medium Units: 16px, 20px, 24px // 1.6rem, 2rem, 2.4rem
Large Units: 32px, 40px, 48px // 3.2rem, 4rem, 4.8rem
Extra Large Units: 64px, 128px // 6.4rem 12.8rem


## Proper spacing between Style Blocks
Add one blank line between each CSS rule block.
Keep each style block self-contained, starting with the selector and ending with a closing brace.
Use consistent indentation for readability (typically 2 or 4 spaces).
Follow top down approach or arrow approach
```
/* Default body styles */
body {
  margin: 0;
  padding: 0;
  font-size: 1.6rem;
  font-family: Arial, sans-serif;
}

/* Container styles */
.container {
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto;
  padding: 2rem;
}

/* Header styles */
.header {
  color: #000000;
  font-size: 2rem;
  text-align: center;
}

/* Paragraph styles */
p {
  color: #666666;
  margin: 1rem 0;
  line-height: 1.5;
}
```

## Style Approaches
To maintain consistency and readability in your CSS, it's important to use a uniform "top-down" approach or "arrow approach" for ordering style properties. Mixing these styles within the same codebase can lead to confusion and reduce readability.

### Top-Down Approach
Properties are listed in logical groupings, starting from general (e.g., layout) to specific (e.g., typography or appearance). This approach reads naturally, following a "broad to narrow" hierarchy.
```
body {
  margin: 0;
  padding: 0;
  font-size: 1.6rem;
  font-family: Arial, sans-serif;
}
```

### Arrow Approach
Properties are ordered based on their visual flow, often prioritizing those that define structure (like display, position, etc.) before moving to alignment and aesthetics. This creates a "step-by-step" flow in styling.

```
.container {
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto;
  padding: 2rem;
  z-index: 1;
}
```


## Media Queries
Write media queries as mobile-first, meaning style for small screens first and then larger
```
.element {
  font-size: 1.4rem;
}

@media (min-width: 768px) {
  .element {
    font-size: 1.6rem;
  }
}
```

## Media Queries(Special Case: Desktop-First Approach)
In projects where the majority of visitors are desktop users, or when working on an existing site/application already designed for desktop-first, consider adopting a desktop-first approach for your media queries. This ensures better alignment with the client's existing architecture and optimizes the experience for the primary user base.

```
.element {
  font-size: 1.6rem;
}

@media (max-width: 767px) {
  .element {
    font-size: 1.4rem;
  }
}
```

## Comments for Clarity
Comment your code to provide clarity, especially in complex areas
```
/* Header styling */
.header { }

```

## Avoid Inline Styles

Avoid using inline styles (style=""), and keep all styles in external stylesheets.
Inline styles are acceptable when using CSS variables defined in :root for dynamic or context-specific customization or in html element dynamic variables.

```
/* Define root variables */
:root {
  --border-radius: 0.4rem;

  --button-color: white;
  --button-background: black;
  --button-border-color: black;
}

/* Button Styling */
.button {
  color: var(--button-color);
  border-radius: var(--border-radius);
  background-color: var(--button-background);
  border: 1px solid var(--button-border-color);
}

```

### Inline Style for Element-Specific Overrides

```
<!-- Button using global root variables -->
<button>Default Button</button>

<!-- Button overriding variables with inline style -->
<button style="--button-color: #f1c40f; --button-background: #101010;">
  Custom Button
</button>

```

## Vendor Prefixes

Use vendor prefixes only when necessary

```
.box {
  -webkit-transform: rotate(20deg);
  transform: rotate(20deg);
}
```

## Performance Considerations

Avoid using complex or unnecessary selectors

```
/* Avoid */
.header ul li a {}

/* Prefer */
.header__link {}

```
