# Exceptions & Error Handling

## Checked vs Unchecked Exceptions
- **Checked**: must be declared or handled (`IOException`, `SQLException`).
- **Unchecked**: runtime errors (`NullPointerException`, `IllegalArgumentException`).

---

## try–catch–finally
- `try` → code that may throw exception.
- `catch` → handle exception.
- `finally` → always executes (cleanup).

### Example
```java
try {
    int result = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Error: " + e.getMessage());
} finally {
    System.out.println("Cleanup done.");
}
```

## Custom Exception Design
- Extend Exception (checked) or RuntimeException (unchecked).

```
class InvalidSalaryException extends Exception {
    public InvalidSalaryException(String msg) {
        super(msg);
    }
}

public void setSalary(double salary) throws InvalidSalaryException {
    if (salary < 0) throw new InvalidSalaryException("Salary cannot be negative");
}
```
## Use Cases
- Checked: file handling, database operations.

- Unchecked: programming errors, invalid arguments.
