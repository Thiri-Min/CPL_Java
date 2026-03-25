# Validation & Exception Handling in Spring
## 1. Bean Validation Basics
- Spring integrates with Jakarta Bean Validation (JSR 380).

- Common constraints:

    - @NotNull, @NotBlank, @Size, @Email, @Min, @Max.

- Automatically applied when using @Valid in controllers.
```
public class UserRequest {
    @NotBlank(message = "Name is required")
    private String name;

    @Email(message = "Invalid email format")
    private String email;
}
```

## 2. @Valid & Constraints
- @Valid triggers validation on request DTOs.

- If validation fails, Spring throws MethodArgumentNotValidException.
```
@PostMapping("/users")
public ResponseEntity<String> createUser(@Valid @RequestBody UserRequest request) {
    return ResponseEntity.ok("User created: " + request.getName());
}
```

## 3. @ExceptionHandler
- Handles exceptions at the controller level.

- Useful for customizing error responses.
```
@RestController
@RequestMapping("/api")
public class UserController {

    @PostMapping("/users")
    public ResponseEntity<String> createUser(@Valid @RequestBody UserRequest request) {
        return ResponseEntity.ok("User created");
    }

    @ExceptionHandler(MethodArgumentNotValidException.class)
    public ResponseEntity<String> handleValidationException(MethodArgumentNotValidException ex) {
        return ResponseEntity.badRequest().body("Validation error: " + ex.getMessage());
    }
}
```

## 4. @ControllerAdvice
- Global exception handling across controllers.

- Centralizes error response logic.
```
@ControllerAdvice
public class GlobalExceptionHandler {

    @ExceptionHandler(MethodArgumentNotValidException.class)
    public ResponseEntity<Map<String, String>> handleValidationErrors(MethodArgumentNotValidException ex) {
        Map<String, String> errors = new HashMap<>();
        ex.getBindingResult().getFieldErrors().forEach(error ->
            errors.put(error.getField(), error.getDefaultMessage())
        );
        return ResponseEntity.badRequest().body(errors);
    }
}
```

## 5. Error Response Design
- Use a consistent error response format.

- Include fields like timestamp, status, error, message, path.
```
public class ErrorResponse {
    private LocalDateTime timestamp;
    private int status;
    private String error;
    private String message;
    private String path;

    public ErrorResponse(HttpStatus status, String message, String path) {
        this.timestamp = LocalDateTime.now();
        this.status = status.value();
        this.error = status.getReasonPhrase();
        this.message = message;
        this.path = path;
    }
}
```
Example JSON response:
```
{
  "timestamp": "2026-02-10T10:15:30",
  "status": 400,
  "error": "Bad Request",
  "message": "Email is invalid",
  "path": "/api/users"
}
```