---
tags:
  - Domain
  - OOP
  - Inheritance
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses OO Thought process
Status: Refinement
Started: 
EditDate: 2024-03-05
Relates: 
Peer Reviewed: 0
dg-publish:
---
# Object Oriented Program explained 

The way I like to describe them is a class is like a template or definition of what it means to be something let's say we have an animal class and a dog variable that stores a new instance of an animal and that dog has access to all the properties Encapsulated in the animal class so it can swim fetch bark maybe even fly but a dog can fly so we might want to exclude that somewhere so that is where interfaces come in were we can define abstract methods or properties we can extend to that truly define what a dog is and what it can do and what it can inherit through inheritance or polymorphism like some type of new trick like having the dog alternate between flipping or walking on back legs . 

JavaScript doesn't have interface and sticks to duck typing and but has implement reserved as a keyword for future use but Typescript does have interfaces 

Polymorphism describes situations in which something occurs in several different forms. In computer science, it describes the concept that you can access objects of different types through the same interface. it lets transform a class or object behavior  

The basic difference between inheritance and polymorphism is that inheritance allows the already existing code to be reused again in a program, and polymorphism provides a mechanism to dynamically decide what form of a function to be invoked. 

Seems like it also establishes new forms 





At a system design level, storing new instances of classes in different objects and object types involves determining the appropriate data structures and design patterns to represent and manage the instances effectively. Here are some considerations:

1. Object-Oriented Design: Before thinking about storage, it's important to design the classes and their relationships based on the problem [[Domain-driven design | Domain]]. Identify the entities, their attributes, and behaviors. Define appropriate classes and establish inheritance and composition relationships as needed.

2. Data Structures:
   - Arrays: If the number of instances is fixed or known in advance, an array can be used to store the instances. Arrays provide fast access to elements but have a fixed size.
   - Lists: If the number of instances is dynamic or can grow/shrink, lists such as ArrayList or LinkedList can be used. Lists provide flexibility in adding, removing, and accessing elements.
   - Maps: If instances need to be stored and retrieved based on keys, maps like HashMap or TreeMap can be used. Maps provide efficient key-value lookups.
   - Sets: If instances need to be stored in an unordered collection without duplicates, sets like HashSet or TreeSet can be used.

3. [[Polymorphism]] and Inheritance:
   - Polymorphism allows instances of different classes to be treated as instances of a common superclass or interface. This allows flexibility in storing and manipulating instances of different types in a uniform way.
   - Inheritance enables objects of derived classes to be stored and manipulated as objects of their superclass. This allows for a more generalized approach to handling different object types.

4. Design Patterns:
   - Factory Pattern: The Factory pattern can be used to create instances of different classes based on a common interface or superclass. The factory method can return instances of different types based on the input or configuration.
   - Abstract Factory Pattern: The Abstract Factory pattern provides an interface for creating families of related or dependent objects. It allows for the creation of objects belonging to different classes but having a common theme.
   - Builder Pattern: The Builder pattern can be used when the process of creating objects involves multiple steps or complex configurations. It provides a step-by-step approach to create objects and allows for different object types to be created based on the builder implementation.

5. Serialization and Persistence:
   - If the instances need to be stored persistently, serialization can be used to convert objects into a byte stream that can be saved to disk or transferred over a network. The objects can then be deserialized back into instances when needed.
   - Various serialization frameworks and formats like JSON or XML can be used to store and retrieve object instances.

Overall, designing the storage and handling of instances of different classes and object types involves considering the problem domain, selecting appropriate data structures and design patterns, and leveraging concepts like polymorphism and inheritance to ensure flexibility and maintainability in the system design.