# HTML & Semantic Markup

## 📑 HTML Structure
- **DOCTYPE declaration**: Defines the document type (`<!DOCTYPE html>`).
- **HTML element**: Root of the document (`<html>`).
- **Head section**: Metadata, title, links to styles/scripts.
- **Body section**: Visible content (text, images, forms, etc.).

### Example
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Semantic HTML Example</title>
</head>
<body>
  <h1>Welcome to My Page</h1>
  <p>This is a simple HTML structure.</p>
</body>
</html>
```

## Semantic Elements
Semantic elements clearly describe their meaning in the context of the web page:

- <header>: Introductory content or navigation.

- <nav>: Navigation links.

- <main>: Main content of the document.

- <article>: Independent, self-contained content.

- <section>: Thematic grouping of content.

- <aside>: Sidebar or tangential content.

- <footer>: Footer information.

```
<header>
  <h1>My Blog</h1>
  <nav>
    <a href="#home">Home</a>
    <a href="#posts">Posts</a>
  </nav>
</header>

<main>
  <article>
    <h2>First Post</h2>
    <p>This is an article using semantic markup.</p>
  </article>
</main>

<footer>
  <p>&copy; 2026 My Blog</p>
</footer>
```

## Accessibility Basics (ARIA Intro)
- ARIA (Accessible Rich Internet Applications) helps improve accessibility for screen readers.

- Common attributes:

    - role: Defines the role of an element (e.g., role="navigation").

    - aria-label: Provides a label for elements.

    - aria-hidden="true": Hides elements from assistive technologies.

```
<button aria-label="Close Menu">X</button>

<nav role="navigation" aria-label="Main Navigation">
  <ul>
    <li><a href="#home">Home</a></li>
    <li><a href="#about">About</a></li>
  </ul>
</nav>
```

## SEO Fundamentals
- Use semantic HTML for better search engine understanding.

- Include title and meta description tags.

- Use heading hierarchy (<h1> → <h2> → <h3>).

- Provide alt text for images.

- Ensure clean URLs and mobile-friendly design.

Example
```
<head>
  <title>Learn Semantic HTML</title>
  <meta name="description" content="A beginner-friendly guide to semantic HTML, accessibility, and SEO.">
</head>

<img src="semantic.png" alt="Diagram showing semantic HTML structure">
```

