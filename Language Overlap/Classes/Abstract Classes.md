---
tags:
  - OOP
  - languageOverlap
  - ClassStructure
  - Inheritance
  - interfaces
  - Abstraction
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses abstract classes.
Status: Done
Started: 2023-10-29
EditDate: 2024-03-04
Relates: "[[Fundamentals of Object-Oriented Concepts]]"
Peer Reviewed: 0
dg-publish:
---
Abstract classes, identified by the `abstract` keyword, are crucial in object-oriented programming. They contain at least one abstract method, devoid of a body, and may feature multiple concrete methods. The inheritance mechanism enforces the implementation of abstract methods, ensuring uniformity among subclasses.

- **Abstraction in Java:**
  - Understanding class function and uses.
  - Hiding implementation details for simplicity.
  - Achieved through abstract classes or interfaces.
  - Deferring object behavior to child classes.

**Key Reasons for Using Abstract Classes:**

1. **Default Functionality for Subclasses:**
   - Offers baseline functionality for subclasses.
   - Establishes standard behavior that can be inherited and modified.

2. **Template for Future Specific Classes:**
   - Guides the creation of specific classes.
   - Provides a structured foundation for future classes.

3. **Common Interface Definition:**
   - Defines a shared interface for subclasses.
   - Ensures consistency in method signatures.

4. **Code Reusability:**
   - Encapsulates common functionality.
   - Promotes code reusability across subclasses.

### **Abstraction in Java:**

Abstraction involves presenting essential information while concealing intricate details. Abstract classes or interfaces, using the "abstract" keyword, achieve this. Abstract classes allow access only through inheritance and consist of a mix of abstract and regular methods.

![[Abstract class Diagram.png]]

**Understanding Abstract Classes and Abstract Methods in Java:**

**Abstract Classes:**
- Cannot be directly instantiated.
- Declared with the `abstract` keyword.
- Contains abstract and non-abstract methods.
- Allows constructors and member variables.
- Permits default implementations for some methods.
- Subclasses must implement all abstract methods.

**Abstract Methods:**
- Method declaration without implementation.
- Declared with the `abstract` keyword.
- Found in abstract classes or interfaces.
- Lacks a method body.
- Defines a contract for subclasses.

**Difference Between Interface and Abstract Method:**
- Abstract classes allow method implementation.
- Interfaces permit only method declaration.
- Abstract class supports single inheritance.
- Interface supports multiple inheritance.
- Neither creates objects directly in Java.

##### Abstract Class vs Interface Distinctions

- **Abstract Class:**
  - Allows defining functionality for subclasses.
  - Permits both method declaration and implementation.
  - Supports single inheritance.
  - Identified by the 'abstract' keyword.

- **Interface:**
  - Permits stating functionality but not implementing it.
  - Supports multiple inheritance.
  - Identified by the 'interface' keyword.

##### Inheritance vs Abstraction: Differentiating Principles

- **Inheritance:**
  - Focuses on sharing and reusing functionality.
  - Enhances code reusability and extensibility.

- **Abstraction:**
  - Focuses on hiding implementation details.
  - Simplifies complex systems for user interaction.

**Summary:**
Abstract classes define shared functionality among subclasses, housing both abstract and non-abstract methods. Understanding abstract classes and abstraction in Java empowers developers to design modular, maintainable, and extensible code structures. Abstract methods, serving as contracts, provide a structural hierarchy, ensuring adherence to specified contracts in Java programming.