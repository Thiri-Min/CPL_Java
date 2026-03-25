# Functional Java Basics

## Lambda Expressions
- Compact way to represent anonymous functions.
- Syntax: `(parameters) -> expression`

### Example
```java
List<String> names = Arrays.asList("Alice", "Bob", "Carol");
names.forEach(n -> System.out.println(n));
```
------

## Functional Interfaces
- Interface with one abstract method.

- Examples: Runnable, Comparator, Function.

```
@FunctionalInterface
interface Payable {
    double calculatePay();
}
```

## Stream Operations
- Declarative way to process collections.

## Common Operations
- map → transform elements

- filter → select elements

- reduce → aggregate values

```
List<Integer> nums = Arrays.asList(1,2,3,4,5);
int sum = nums.stream()
              .filter(n -> n % 2 == 0)
              .map(n -> n * 2)
              .reduce(0, Integer::sum);
System.out.println(sum); // 12
```

## Refactoring Imperative Code

### Imperative
```
int total = 0;
for (int n : nums) {
    if (n % 2 == 0) total += n * 2;
}
```

### Stream-based
```
int total = nums.stream()
                .filter(n -> n % 2 == 0)
                .mapToInt(n -> n * 2)
                .sum();
```
