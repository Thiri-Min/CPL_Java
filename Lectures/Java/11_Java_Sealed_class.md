# Java Sealed Classes

## What is a Sealed Class?
A **sealed class** in Java (introduced in Java 15 as a preview, finalized in Java 17) is a class that restricts which other classes can extend or implement it.  
It provides more control over inheritance compared to `final` (no subclassing) or `abstract` (subclassing allowed without restriction).

By declaring a class as `sealed`, you explicitly specify the permitted subclasses using the `permits` clause.

---

## How to Use Sealed Classes
- Use the `sealed` modifier for the base class.
- Use `permits` to list allowed subclasses.
- Subclasses must declare themselves as either:
  - `final` (cannot be extended further),
  - `sealed` (can restrict further subclassing), or
  - `non-sealed` (removes restrictions, allows open inheritance).

---

## Sample Code

```java
// Base sealed class
public sealed class Shape permits Circle, Rectangle, Triangle { }

// Permitted subclasses
public final class Circle extends Shape {
    double radius;
    Circle(double radius) { this.radius = radius; }
}

public final class Rectangle extends Shape {
    double length, width;
    Rectangle(double length, double width) {
        this.length = length;
        this.width = width;
    }
}

public non-sealed class Triangle extends Shape {
    double base, height;
    Triangle(double base, double height) {
        this.base = base;
        this.height = height;
    }
}
```

------

## Pros of Sealed Classes
- Controlled inheritance: Prevents unwanted subclassing, ensuring design integrity.

- Better readability: Makes the hierarchy explicit and clear.

- Improved security: Restricts extension to trusted classes only.

- Pattern matching synergy: Works well with switch expressions and pattern matching, since the compiler knows all possible subclasses.

-----------

## Cons of Sealed Classes
- Reduced flexibility: Limits extensibility, which may be restrictive in evolving systems.

- Maintenance overhead: Adding new subclasses requires modifying the base class permits clause.

- Compatibility issues: Older Java versions (before 17) do not support sealed classes.

- Complexity: May add unnecessary complexity if not used in the right context.

-------

## When to Use
- When you want a controlled class hierarchy (e.g., domain models like Shape, PaymentMethod, EmployeeType).

- When using pattern matching and exhaustive checks.

- When designing APIs where subclassing should be restricted to specific implementations.

