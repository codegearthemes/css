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
Use hyphens (\_\_) for naming before modifier.
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

## Avoid Inline Styles

Avoid using inline styles (style=""), and keep all styles in external stylesheets.
Inline styles are acceptable when using CSS variables defined in :root for dynamic or context-specific customization or in html element dynamic variables.

```
/* Define root variables */
:root {
  --border-radius: 4px;
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
