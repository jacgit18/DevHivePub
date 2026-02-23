---
tags:
  - Java
  - keywords
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses static keyword.
Status: Done
Started: 
EditDate: 2024-03-04
Relates: 
Peer Reviewed: 0
dg-publish:
---
In Java, the keyword "static" is used to declare members (variables and methods) that belong to the class rather than instances of the class. Here's a brief explanation:

1. **Static Variables (Class Variables):**
   - A static variable is shared among all instances of a class.
   - It's declared using the `static` keyword.
   - Example:
     ```java
     public class MyClass {
         static int staticVariable;
     }
     ```
     Accessed as `MyClass.staticVariable`.

2. **Static Methods:**
   - Similar to static variables, static methods belong to the class rather than an instance.
   - They can be called using the class name, without creating an object.
   - Example:
     ```java
     public class MyClass {
         static void myStaticMethod() {
             // code
         }
     }
     ```
     Called as `MyClass.myStaticMethod()`.

3. **Static Blocks:**
   - A static block is used for static initialization of a class.
   - It runs once when the class is loaded.
   - not available in typescript as of now
   - Example:
     ```java
     public class MyClass {
         static {
             // static block code
         }
     }
     ```

4. **Static Nested Classes:**
   - A nested class that is declared static is called a static nested class.
   - It can be instantiated without the need for an instance of the outer class.
   - Example:
     ```java
     public class OuterClass {
         static class StaticNestedClass {
             // code
         }
     }
     ```
     Instantiated as `OuterClass.StaticNestedClass nestedObject = new OuterClass.StaticNestedClass();`

The use of `static` facilitates memory efficiency and can be helpful in situations where you want certain members to be shared among all instances of a class.


if you want a method or variable to belong to instances of a class rather than the class itself, you should not use the `static` keyword. By default, methods and variables without the `static` keyword are instance members, meaning they are associated with individual instances of the class.

Here's an example:

```java
public class MyClass {
    int instanceVariable;

    void instanceMethod() {
        // code
    }
}
```

In this example, `instanceVariable` and `instanceMethod()` are not declared as static. Therefore, they are instance members, and each instance of `MyClass` will have its own copy of `instanceVariable`, and you can call `instanceMethod()` on individual objects of `MyClass`.

```java
MyClass obj1 = new MyClass();
obj1.instanceVariable = 5;
obj1.instanceMethod();

MyClass obj2 = new MyClass();
obj2.instanceVariable = 10;
obj2.instanceMethod();
```

In this way, each instance of the class can have its own values for instance variables and invoke instance methods independently.