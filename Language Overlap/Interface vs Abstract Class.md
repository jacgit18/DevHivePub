---
tags:
  - interfaces
  - abstraction
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses interfaces vs abstract classes.
Status: Refinement
Started: 
EditDate: 2024-03-05
Relates: 
Peer Reviewed: 0
dg-publish:
---
#### Abstract Class:
- Permits functionality for subclasses to implement or override.
- Defines identity, allowing inheritance of only one abstract class.
- Can have both abstract and concrete methods.
- Allows data fields, constants, constructors, and destructors.
- Can have access modifiers.
- Used to share common behavior among various implementations.
- Suitable for scenarios where multiple implementations share fields and constants.

#### Interface:
- Permits stating functionality without implementation.
- Supports multiple interface implementations.
- Contains only abstract methods and cannot have data fields.
- Abstract to provide code.
- Used for future enhancements and when implementations share only method signatures.
- Defines peripheral abilities of a class.
- No constructors or destructors allowed.
- No access modifiers; everything is assumed public.

### Code Examples:

#### Interface Implementation:
```java
interface Pet {
    public void test();
}

class Dog implements Pet {
    public void test() {
        System.out.println("Interface Method Implemented");
    }

    public static void main(String args[]) {
        Pet p = new Dog();
        p.test();
    }
}
```

#### Abstract Class Implementation:
```java
abstract class Shape {
    int b = 20;

    abstract public void calculateArea();
}

public class Rectangle extends Shape {
    public static void main(String args[]) {
        Rectangle obj = new Rectangle();
        obj.b = 200;
        obj.calculateArea();
    }

    public void calculateArea() {
        System.out.println("Area is " + (b * b));
    }
}
```

These examples illustrate the usage and distinctions between abstract classes and interfaces in Java. Abstract classes allow a mix of abstract and concrete elements, while interfaces focus on defining method signatures without implementation.