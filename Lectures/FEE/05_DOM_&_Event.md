# DOM & Event Handling

## 1. DOM Tree & Manipulation
- The **DOM (Document Object Model)** represents the HTML document as a tree of nodes.
- Each element can be accessed and modified using JavaScript.
- Common methods:
  - `document.getElementById("id")`
  - `document.querySelector(".class")`
  - `element.textContent` / `element.innerHTML`
  - `element.setAttribute("attr", "value")`
- Example:
  ```js
  const heading = document.querySelector("h1");
  heading.textContent = "Updated Title!";
  ```

## 2. Event Bubbling & Delegation
- Event bubbling: when an event triggered on a child element propagates up through its parent elements.

- Event delegation: attaching a single event listener to a parent element to handle events on its children.

- Example:
```
document.querySelector("#list").addEventListener("click", function(e) {
  if (e.target.tagName === "LI") {
    console.log("Item clicked:", e.target.textContent);
  }
});
```

## 3. Form Handling
- Forms collect user input and can be controlled with JavaScript.

- Access values with:

    ` document.forms["formName"].elements["inputName"].value

    - Or directly: document.querySelector("#inputId").value

- Example:
```
const form = document.querySelector("form");
form.addEventListener("submit", function(e) {
  e.preventDefault();
  const name = document.querySelector("#name").value;
  if (!name) {
    alert("Name is required!");
  }
});
```

## 4. Basic State Management
- State refers to the current data or status of an application.

- In vanilla JavaScript, state can be managed using variables or objects.

- Example:
```
let appState = { loggedIn: false };

function login() {
  appState.loggedIn = true;
  render();
}

function render() {
  if (appState.loggedIn) {
    document.body.textContent = "Welcome back!";
  } else {
    document.body.textContent = "Please log in.";
  }
}
```


