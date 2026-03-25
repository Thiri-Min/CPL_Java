# Web & Browser Fundamentals

## 🌐 How the Web Works
- **Client/Server model**:  
  - The **client** (browser) sends a request to a **server**.  
  - The **server** processes the request and sends back a response (HTML, JSON, etc.).  
- **HTTP request/response cycle**:  
  - Request: `GET /index.html HTTP/1.1`  
  - Response: `200 OK` with content.

### Example
```
GET /home HTTP/1.1
Host: example.com

HTTP/1.1 200 OK
Content-Type: text/html

<html>
  <body>Hello World!</body>
</html>
```

### Browser Architecture
- DOM (Document Object Model): Tree structure of HTML elements.

- CSSOM (CSS Object Model): Tree structure of CSS styles.

- JavaScript Engine: Parses and executes JS code (e.g., V8 in Chrome).

- Rendering Engine: Combines DOM + CSSOM → Render Tree → Layout → Paint.

## Critical Rendering Path
Steps the browser takes to display a page:

1. Parse HTML → Build DOM.

2. Parse CSS → Build CSSOM.

3. Combine → Render Tree.

4. Layout → Calculate positions & sizes.

5. Paint → Draw pixels on screen.

## Roles of HTML, CSS, JS
- HTML: Structure & content.

- CSS: Presentation & styling.

- JavaScript: Interactivity & logic.

```
<!DOCTYPE html>
<html>
<head>
  <title>Web Fundamentals</title>
  <style>
    body { font-family: Arial; background: #f0f0f0; }
    h1 { color: blue; }
  </style>
</head>
<body>
  <h1>Hello Web!</h1>
  <button onclick="alert('Button clicked!')">Click Me</button>
</body>
</html>
```
## Reference Websites to Practice

- MDN Web Docs — Comprehensive web standards documentation.
https://developer.mozilla.org/

- W3Schools — Beginner-friendly tutorials.
https://www.w3schools.com/

- Frontend Mentor — Hands-on coding challenges.
https://www.frontendmentor.io/

- CodePen — Online editor to experiment with HTML/CSS/JS.
https://codepen.io/