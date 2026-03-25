# Java Basics Reference

## 1. How to Know Java Version
To check the installed Java version on your system:

```bash
java -version
```

Example output:
```
java version "17.0.2" 2022-01-18 LTS
Java(TM) SE Runtime Environment (build 17.0.2+8-LTS-86)
Java HotSpot(TM) 64-Bit Server VM (build 17.0.2+8-LTS-86, mixed mode)
```

## 2. How to Know Java Compile Version

```
javac -version
```
Example output:
```
javac 17.0.2
```

## 3. What is Bytecode?

- Bytecode is the intermediate representation of Java code after compilation.

- It is platform-independent and executed by the Java Virtual Machine (JVM).

- When you compile a .java file, it produces a .class file containing bytecode.

Example
```
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Bytecode!");
    }
}
```
-------
Compile:
```
javac HelloWorld.java
````
This generates HelloWorld.class containing bytecode, which can be run with:
```
java HelloWorld
```

## 4. Sample Code of Overriding and Overloading

Method Overloading (same method name, different parameters)

```
class Calculator {
    // Overloaded methods
    int add(int a, int b) {
        return a + b;
    }

    double add(double a, double b) {
        return a + b;
    }
}
```
Method Overriding (subclass redefines parent method)

```
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}
```

## 5. Function Definition with No Return Type

A function with no return type uses void.

```
public class Demo {
    void greet() {
        System.out.println("Hello, World!");
    }
}
```

## 6. Function with Return Type

A function that returns a value must specify the return type.

```
public class Demo {
    int square(int x) {
        return x * x;
    }
}
```

Example usage:

```
Demo d = new Demo();
System.out.println(d.square(5)); // Output: 25
```


## 7. Access Modifiers
- **public, private, protected, default**  
- Control visibility and encapsulation of classes, methods, and variables.  
- Example: `private int age;` ensures `age` is only accessible inside the class.

---

## 8. Constructors
- Special methods used to initialize objects.  
- Types: **default constructor**, **parameterized constructor**, **copy constructor**.  
- Example:
```java
class Student {
    String name;
    Student(String n) {
        name = n;
    }
}
```

## 9. Inheritance
Mechanism to acquire properties and behaviors of another class.

Keywords: extends, super.

Example:
```
class Animal {
    void eat() { System.out.println("Eating..."); }
}
class Dog extends Animal {
    void bark() { System.out.println("Barking..."); }
}
```

## 10. Interfaces
Define contracts with abstract methods.

A class implements an interface to provide behavior.

Example:
```
interface Vehicle {
    void drive();
}
class Car implements Vehicle {
    public void drive() { System.out.println("Car is driving"); }
}
```

## 11. Exception Handling
Mechanism to handle runtime errors.

Keywords: try, catch, finally, throw, throws.

Example:
```
try {
    int a = 5 / 0;
} catch (ArithmeticException e) {
    System.out.println("Error: " + e.getMessage());
}
```

## 12. Collections Framework
Provides data structures like ArrayList, HashMap, HashSet.

Example:
```
import java.util.*;
class Demo {
    public static void main(String[] args) {
        ArrayList<String> list = new ArrayList<>();
        list.add("Java");
        list.add("Python");
        System.out.println(list);
    }
}
```

## 13. Multithreading
Allows concurrent execution of tasks.

Example:
```
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread running...");
    }
}
```

## 14. File Handling
Reading and writing files using FileReader, BufferedReader, FileWriter.

Example:
```
import java.io.*;
class Demo {
    public static void main(String[] args) throws IOException {
        FileWriter fw = new FileWriter("output.txt");
        fw.write("Hello Java File Handling");
        fw.close();
    }
}
```