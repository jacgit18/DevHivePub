---
tags:
  - ClassStructure
  - languageOverlap
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Nested Classes.
Status: Refinement
Started: 
EditDate: 2024-03-04
Relates: 
Peer Reviewed: 0
dg-publish:
---
### Nested Classes in Java:

In Java, nested classes enable the logical grouping of classes used exclusively in one place, promoting encapsulation and enhancing code readability and maintainability.

#### Key Points:

- **Scope and Independence:**
  - The scope of a nested class is bound by the scope of its enclosing class.
  - In the example, `NestedClass` does not exist independently of `OuterClass`.
  
- **Access to Members:**
  - A nested class has access to the members, including private ones, of its enclosing class.
  - The enclosing class does not have direct access to members of the nested class.
  
- **Membership:**
  - A nested class is also considered a member of its enclosing class.
  
- **Categories:**
  - **Static Nested Class:** Declared as static, it is a nested class that can be accessed without creating an instance of the outer class.
  - **Inner Class:** A non-static nested class.

#### Example:

```java
class OuterClass {
    // ...

    class InnerClass {
        // ...
    }
}
```

In this example, `InnerClass` is a non-static nested class of `OuterClass`. Nested classes provide a structured way to organize and group related functionality within a class.
![[classes.png]]

### Inner Classes and Packages in Java:

#### Inner Classes:
In regular inner classes, an object of the inner class is strongly associated with an outer class object. However, in the case of a static nested class, there may be a static nested class object without a corresponding outer class object. A static nested class is associated with its outer class, similar to class methods and variables. It cannot directly refer to instance variables or methods in the enclosing class but can use them through an object reference, accessed using the enclosing class name.

[More about Inner Classes](https://docs.oracle.com/javase/tutorial/java/javaOO/nested.html)

#### Packages in Java:
Java has two types of packages: built-in (part of the Java API) and user-defined (created by developers). To use a package in a class, use the `import` keyword followed by the package name using dot notation.

#### Java Enums:
Java Enums represent a group of constants and are declared using the `enum` keyword. Enum constants are in uppercase letters.

[More about Java Enums](https://docs.oracle.com/javase/tutorial/java/javaOO/enum.html)

#### Java User Input:
Java User Input is captured using the `Scanner` class, which can parse primitive types and strings, breaking down input into tokens using a delimiter pattern.

[Scanner Class Documentation](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Scanner.html)

### Multiple Classes in a Java File:

While each Java file needs at least one class, it can have multiple classes. However, only one class can be declared as public, and the file must be named after the public class. If there are multiple public classes in the same file, the code will not compile. Accessing methods and instances of other classes is possible by creating their respective objects in the public class.

Example:
```java
public class Test {
    public static void main(String... s) {
        System.out.println("Hello Guys");
    }
}

class Test1 {}

class Test2 {}
```

In this example, the file is named `Test.java`, and the public class is `Test` containing the `main` method. Classes `Test1` and `Test2` can be accessed within the same file.