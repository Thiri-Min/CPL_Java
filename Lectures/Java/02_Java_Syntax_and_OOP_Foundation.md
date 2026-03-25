# Core Java Concepts Explained

## Variables & Data Types
- **Variables:** Containers for storing data values.
- **Data Types:** Primitive (int, double, char, boolean) and reference types (objects, arrays).
- **Note:** Choosing the right data type improves memory efficiency and readability.
- **Practice Website:** [W3Schools Java Variables](https://www.w3schools.com/java/java_variables.asp)
- **Real-world Example:** A payroll system uses `double` for salary calculations and `String` for employee names.

## Control Flow (if/loop)
- **If Statements:** Used for decision-making.
- **Loops:** `for`, `while`, `do-while` for repetitive tasks.
- **Note:** Control flow structures help manage program logic.
- **Practice Website:** [Java Control Statements](https://www.javatpoint.com/control-statements-in-java)
- **Real-world Example:** Online shopping cart uses loops to calculate total price of items.

## Methods & Parameters
- **Methods:** Blocks of code that perform tasks.
- **Parameters:** Inputs passed to methods for dynamic behavior.
- **Note:** Methods promote code reuse and modularity.
- **Practice Website:** [Java Methods](https://www.w3schools.com/java/java_methods.asp)
- **Real-world Example:** A `calculateTax(double amount)` method in an e-commerce system.

## Naming Conventions
- **Classes:** PascalCase (e.g., `CustomerAccount`).
- **Methods/Variables:** camelCase (e.g., `calculateTotal`).
- **Constants:** UPPER_CASE (e.g., `MAX_VALUE`).
- **Note:** Consistent naming improves readability and collaboration.
- **Practice Website:** [Java Naming Conventions](https://www.geeksforgeeks.org/java-naming-conventions/)
- **Real-world Example:** Google’s Java style guide enforces naming conventions across teams.

## Method Length & Readability
- **Best Practice:** Keep methods short (20–30 lines max).
- **Note:** Long methods reduce readability and increase complexity.
- **Practice Website:** [Clean Code Principles](https://www.baeldung.com/java-clean-code)
- **Real-world Example:** Refactoring a `processOrder()` method into smaller helper methods like `validateOrder()`, `calculateDiscount()`, `generateInvoice()`.

---

## Class & Object Concepts
- **Class:** Blueprint for objects.
- **Object:** Instance of a class with state and behavior.
- **Note:** Classes and objects are the foundation of OOP.
- **Practice Website:** [Java Classes and Objects](https://www.w3schools.com/java/java_classes.asp)
- **Real-world Example:** A `Car` class with objects like `myCar` and `yourCar`.

## Encapsulation, Inheritance, Polymorphism
- **Encapsulation:** Hiding data with private fields and public getters/setters.
- **Inheritance:** Reusing code by extending classes.
- **Polymorphism:** Same method name, different implementations.
- **Note:** These principles make code modular and reusable.
- **Practice Website:** [OOP Concepts in Java](https://www.javatpoint.com/object-oriented-programming-in-java)
- **Real-world Example:** A `Vehicle` superclass with `Car` and `Bike` subclasses.

## Interface vs Abstract Class
- **Interface:** Defines contract (methods without implementation).
- **Abstract Class:** Can have both abstract and concrete methods.
- **Note:** Interfaces are for capabilities; abstract classes are for shared base functionality.
- **Practice Website:** [Interface vs Abstract Class](https://www.geeksforgeeks.org/difference-between-abstract-class-and-interface-in-java/)
- **Real-world Example:** `Comparable` interface vs `AbstractList` class in Java Collections.

## Composition over Inheritance
- **Composition:** Building classes using references to other classes.
- **Note:** Preferred over inheritance to reduce tight coupling.
- **Practice Website:** [Composition in Java](https://www.baeldung.com/java-composition)
- **Real-world Example:** A `Car` class has an `Engine` object instead of inheriting from `Engine`.

## SOLID Principles (Overview)
- **S – Single Responsibility:** One reason to change per class.
- **O – Open/Closed:** Open for extension, closed for modification.
- **L – Liskov Substitution:** Subclasses should be substitutable for base classes.
- **I – Interface Segregation:** Many small interfaces are better than one large one.
- **D – Dependency Inversion:** Depend on abstractions, not concrete implementations.
- **Note:** SOLID principles exist to make software maintainable, scalable, and flexible.
- **Practice Website:** [SOLID Principles in Java](https://www.baeldung.com/solid-principles)
- **Real-world Example:** Spring Framework follows SOLID principles to ensure extensibility and maintainability.
