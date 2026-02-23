---
tags:
  - Java
  - static
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses static method reference.
Status: Done
Started: 
EditDate: 2024-03-04
Relates: "[[Back Pressure]]"
Peer Reviewed: 0
dg-publish:
---
In Java, the `::` operator is used to create method references or reference to a method. It's also known as the method reference operator. Method references are a shorthand notation for defining a method that can be used as a functional interface (such as a lambda expression).

There are four main types of method references in Java:

1. **Static Method Reference:** It refers to a static method. The syntax is `ClassName::staticMethodName`.

   Example:
   ```java
   // Using a static method reference
   Function<Integer, Integer> square = Math::square;
   ```

2. **Instance Method Reference of a Particular Object:** It refers to an instance method of a specific object. The syntax is `objectReference::instanceMethodName`.

   Example:
   ```java
   // Using an instance method reference on a specific object
   String str = "Hello, World!";
   Consumer<String> printer = str::println;
   ```

3. **Instance Method Reference of an Arbitrary Object of a Particular Type:** It refers to an instance method of an arbitrary object of a particular type. The syntax is `ClassName::instanceMethodName`.

   Example:
   ```java
   // Using an instance method reference on an arbitrary object
   List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
   names.forEach(System.out::println);
   ```

4. **Constructor Reference:** It refers to a constructor. The syntax is `ClassName::new`.

   Example:
   ```java
   // Using a constructor reference to create an instance
   Supplier<List<String>> listSupplier = ArrayList::new;
   List<String> list = listSupplier.get();
   ```

Method references are often used with functional interfaces, which allow them to be used in contexts where a single abstract method needs to be implemented. This provides a more concise and readable alternative to using explicit lambda expressions.

Method references are a powerful feature in Java, particularly in functional programming and stream processing. They make the code more expressive and reduce boilerplate code when working with functional interfaces.