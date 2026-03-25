# String & Collection Framework

## String Immutability
- Strings in Java are **immutable**: once created, their value cannot change.

- Any modification (e.g., concatenation) creates a **new String object**.

- Benefits:
  - Thread safety
  - Efficient memory usage with String Pool

### Example
```java
String s1 = "Hello";
String s2 = s1.concat(" World");
System.out.println(s1); // "Hello"
System.out.println(s2); // "Hello World"
```
-----------------------------------------

## Collections Overview
### List
Ordered, allows duplicates.

Use case: maintaining sequence (e.g., student roll numbers).

### Set
Unordered, no duplicates.

Use case: storing unique values (e.g., email addresses).

### Map
Key-value pairs.

Use case: dictionary lookups (e.g., employee ID → salary).

### Generics in Collections
Provide type safety.

Example:
```
List<String> names = new ArrayList<>();
names.add("Alice");
names.add("Bob");
```

equals() & hashCode()
equals() → logical equality.

hashCode() → used in hashing (e.g., HashMap).

Contract: if two objects are equal, their hashCodes must match.
```
@Override
public boolean equals(Object o) {
    if (this == o) return true;
    if (!(o instanceof Employee)) return false;
    Employee e = (Employee) o;
    return id == e.id;
}

@Override
public int hashCode() {
    return Objects.hash(id);
}
```
-----------------------------------
Practice Websites
GeeksforGeeks - Java Collections ([geeksforgeeks.org](https://www.geeksforgeeks.org/))

Tpoint Tech - Free Online Tutorials: https://www.tpointtech.com/

w3school : https://www.w3schools.com/java/



