# FE Engineering Basics

## 1. JS Execution Model (Sync/Async Intro)
- JavaScript is **single-threaded**, meaning it executes one task at a time.
- **Synchronous execution**: tasks run sequentially, blocking further execution until complete.
- **Asynchronous execution**: tasks can be deferred, allowing other code to run while waiting (e.g., timers, network requests).
- Key concepts:
  - **Call stack**: keeps track of function execution.
  - **Event loop**: manages asynchronous callbacks.
  - **Promises** and `async/await`: modern ways to handle asynchronous operations.

---

## 2. Fetch API Basics
- The **Fetch API** is used to make network requests.
- Returns a **Promise** that resolves to a `Response` object.
- Example:
```
  fetch("https://api.example.com/data")
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error("Error:", error));
```

- With async/await:
```
async function getData() {
  try {
    const response = await fetch("https://api.example.com/data");
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error("Error:", error);
  }
}
```

## 3. Separation of Concerns
- Principle of organizing code so that each part has a distinct responsibility.

- Benefits:

    - Easier to maintain and scale.

    - Improves readability and collaboration.

- In front-end engineering:

    - HTML → structure/content

    - CSS → styling/presentation

    - JavaScript → behavior/logic

- Example: Avoid mixing inline styles and scripts directly in HTML; instead, use external files.

## 4. FE Folder Structure
- A clean folder structure improves project organization.

Example structure:
```
project/
├── index.html
├── css/
│   └── style.css
├── js/
│   └── app.js
├── assets/
│   ├── images/
│   └── fonts/
└── README.md
```

- Larger projects may include:

    - components/ → reusable UI parts

    - services/ → API calls

    - utils/ → helper functions

    - tests/ → unit/integration tests