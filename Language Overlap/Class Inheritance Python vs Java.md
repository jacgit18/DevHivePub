---
tags:
  - languageOverlap
  - Inheritance
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Class inheritance in the context of python and Java.
Status: Done
Started: 2023-11-21
EditDate: 2024-03-04
Relates: "[[Fundamentals of Object-Oriented Concepts]]"
Peer Reviewed: 0
dg-publish:
---
Class inheritance in Python and Java shares some common principles but also has differences in their implementation. Here are some key points to consider:  
  
1. **Inheritance Principle**: In both Python and Java, inheritance allows a new class (subclass or derived class) to inherit properties and behaviors from an existing class (superclass or base class). This promotes code reuse and the creation of a hierarchy of classes.  
  
2. **Syntax**:  
- In Python, you define inheritance by placing the superclass in parentheses when defining the subclass. Python supports single inheritance, which means a class can inherit from only one superclass.  
  
```python  
class Subclass(Superclass):  
```  
  
- In Java, you use the `extends` keyword to establish a subclass that inherits from a superclass. Java supports single inheritance as well.  
  
```java  
class Subclass extends Superclass {  
```  
  
3. **Multiple Inheritance**:  
- Python supports multiple inheritance, which means a class can inherit from multiple superclasses.  
  
```python  
class Subclass(Superclass1, Superclass2):  
```  
  
- Java does not support multiple inheritance through classes. Instead, it uses interfaces for achieving a form of multiple inheritance.  
  
4. **Method Overriding**: Both Python and Java allow subclass methods to override (provide a new implementation for) methods inherited from the superclass.  
  
5. **Access Control**:  
- In Java, you have explicit access control modifiers like `public`, `private`, `protected`, and package-private to control access to class members.  
- In Python, there is no strict access control like in Java. Conventionally, attributes and methods prefixed with an underscore (e.g., `_private_var`) are considered protected, but it's a matter of convention rather than strict enforcement.  
  
6. **Dynamic vs. Static Typing**:  
- Python uses dynamic typing, which means the type of a variable is determined at runtime. This allows more flexibility but can lead to runtime errors if not careful.  
- Java uses static typing, where types are checked at compile time, providing more safety but requiring explicit type declarations.  
  
In summary, while the basic concept of inheritance is similar in Python and Java, there are differences in syntax, support for multiple inheritance, access control, and type systems that you should be aware of when working with classes and inheritance in these languages.