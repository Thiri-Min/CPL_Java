# JavaScript Fundamentals

## 1. Variables & Types
- JavaScript supports dynamic typing, meaning variables can hold values of any type without explicit declaration.
- Common types include:
  - **Primitive types**: `string`, `number`, `boolean`, `null`, `undefined`, `symbol`, `bigint`
  - **Reference types**: `object`, `array`, `function`
- Variables can be declared using:
  - `var` (function-scoped, older usage)
  - `let` (block-scoped, modern usage)
  - `const` (block-scoped, immutable reference)

---

## 2. Functions & Scope
- Functions are reusable blocks of code defined with `function` keyword or arrow syntax (`()=>{}`).
- **Scope** determines variable accessibility:
  - **Global scope**: accessible everywhere
  - **Function scope**: variables declared inside a function are local
  - **Block scope**: variables declared with `let` or `const` inside `{}` are limited to that block
- Functions can return values and accept parameters.

---

## 3. Array & Object Operations
- **Arrays**: ordered collections of values.
  - Common methods: `push()`, `pop()`, `shift()`, `unshift()`, `map()`, `filter()`, `reduce()`
- **Objects**: collections of key-value pairs.
  - Access properties with dot notation (`obj.key`) or bracket notation (`obj["key"]`)
  - Useful methods: `Object.keys()`, `Object.values()`, `Object.entries()`
- Both arrays and objects are reference types, meaning they are stored and passed by reference.

---

## 4. Error Handling Basics
- Errors can occur during runtime; handling them prevents program crashes.
- Use `try...catch` blocks:
  ```js
  try {
    // risky code
  } catch (error) {
    console.error("An error occurred:", error);
  }
