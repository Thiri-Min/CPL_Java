# CSS Fundamentals

## 📦 Box Model
Every element in CSS is a rectangular box consisting of:
- **Content**: Text or image inside the element.
- **Padding**: Space between content and border.
- **Border**: Surrounds padding and content.
- **Margin**: Space outside the border.

### Example
```css
div {
  width: 200px;
  padding: 20px;
  border: 5px solid black;
  margin: 10px;
}
```

## Display, Position, Flexbox
- Display:

    - block: Takes full width.

    - inline: Fits content width.

    - inline-block: Inline but allows width/height.

    - none: Hides element.

- Position:

    - static: Default.

    - relative: Positioned relative to itself.

    - absolute: Positioned relative to nearest positioned ancestor.

    - fixed: Stays fixed relative to viewport.

    - sticky: Switches between relative and fixed depending on scroll.

- Flexbox:

    - Provides flexible layout.

    - Key properties: display: flex;, justify-content, align-items.

```
.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
```

## Responsive Design Basics
- Use media queries to adapt layout.

- Use relative units (%, em, rem, vh, vw).

- Ensure mobile-first design.

```
body {
  font-size: 16px;
}

@media (max-width: 600px) {
  body {
    font-size: 14px;
  }
}
```


## CSS Specificity & Cascade
- Specificity hierarchy:

    1. Inline styles (style="...")

    2. IDs (#id)

    3. Classes, attributes, pseudo-classes (.class, [attr], :hover)

    4. Elements (div, p)

- Cascade: Last rule wins if specificity is equal.

- Best practice: Avoid overusing !important.

```
/* Element selector */
p { color: blue; }

/* Class selector overrides element */
.text { color: green; }

/* ID selector overrides class */
#highlight { color: red; }
```

## UI Framework Introduction
- Bootstrap: Popular responsive framework.

- Tailwind CSS: Utility-first CSS framework.

- Material UI: Based on Google’s Material Design.

```
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap/dist/css/bootstrap.min.css">

<div class="container">
  <button class="btn btn-primary">Click Me</button>
</div>
```