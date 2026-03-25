# Spring Web & REST API Notes

## 🌐 Spring Web Architecture Overview
- **DispatcherServlet role**
  - Central dispatcher for HTTP requests.
  - Routes requests to appropriate controllers.
  - Handles view resolution and response rendering.

- **Controller → Service → Repository flow**
  - **Controller**: Handles HTTP requests, maps endpoints.
  - **Service**: Contains business logic.
  - **Repository**: Interacts with the database (usually via JPA).

- **Request mapping & handler resolution**
  - `@RequestMapping`, `@GetMapping`, `@PostMapping`, etc.
  - DispatcherServlet resolves handler methods based on URL, HTTP method, and parameters.

---

## 📌 @RestController & Mappings
- `@RestController` combines `@Controller` + `@ResponseBody`.
- Used for REST APIs returning JSON/XML directly.
- Common mappings:
  - `@GetMapping("/resource")`
  - `@PostMapping("/resource")`
  - `@PutMapping("/resource/{id}")`
  - `@DeleteMapping("/resource/{id}")`

---

## 🔑 Path vs Query Parameters
- **Path parameters**: Part of the URL (e.g., `/users/{id}`).
- **Query parameters**: Key-value pairs in URL (e.g., `/users?active=true`).

---

## 📦 Request/Response DTOs
- **DTO (Data Transfer Object)**: Encapsulates request/response payloads.
- Keeps API contracts clean and decoupled from entity models.
- Example:
```
  public class UserRequest {
      private String name;
      private String email;
  }
```

## Service Responsibility
- Encapsulates business logic.

- Ensures controllers remain lightweight.

- Promotes reusability and testability.

## Controller–Service Separation
- Controller: Handles HTTP layer (requests/responses).

- Service: Handles application logic.

- Clear separation improves maintainability.

## REST Principles
- Statelessness: Each request contains all necessary info.

- Resource-oriented: APIs expose resources, not actions.

- Uniform interface: Consistent use of HTTP methods.

- Representation: Resources represented in JSON/XML.

## HTTP Methods & Status Codes
- GET → Retrieve resource → 200 OK

- POST → Create resource → 201 Created

- PUT → Update resource → 200 OK / 204 No Content

- DELETE → Remove resource → 204 No Content

## Error codes:

- 400 Bad Request

- 404 Not Found

- 500 Internal Server Error

## Resource-Oriented API Design
- Resources identified by URIs.

- Example: /users/{id}/orders

- Hierarchical and intuitive structure.

## Request vs Response Model
- Request model: Defines input structure (DTO for incoming data).

- Response model: Defines output structure (DTO for outgoing data).

- Separation ensures flexibility and avoids exposing internal entities.