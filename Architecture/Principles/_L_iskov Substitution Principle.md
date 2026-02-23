---
tags:
  - SOLID
  - principles
  - ClassStructure
  - languageOverlap
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Liskov substitution in SOLID principles.
Status: Refinement
Started: 
EditDate: 2024-03-06
Relates: 
Peer Reviewed: 0
dg-publish:
---
A super class can be replaced by any of it’s inheriting sub classes at any parts of the system without any change in the code.

It means that the sub classes should extend the functionality of the super class without overriding it.

That’s why we’ve mentioned earlier in [Class Diagram](https://medium.com/omarelgabrys-blog/e7535090824c) that it’s not a good case practice to override the methods of the super class in inheritance.

#todo/BAU/noteRefine 
- [ ] Review and combine with other notes that make sense

>[!note] 
>LSP is closely related **to the Single responsibility principle** and **Interface Segregation Principle**.

> The LSP states that objects of a superclass should be replaceable with objects of a subclass without affecting the correctness of the program.
> If a subclass does not support all the functionality of its superclass, it violates the LSP. In other words, if the subclass overrides or extends the behavior of the superclass in a way that makes it incompatible with the expected functionality, it can lead to issues when substituting the subclass for the superclass. This can result in unexpected behavior and violates the principles of polymorphism and code reusability in object-oriented design.


In order to follow [LSP SOLID design principle](https://click.linksynergy.com/deeplink?id=JVFxdTr9V80&mid=39197&murl=https%3A%2F%2Fwww.udemy.com%2Fsolid-principles-object-oriented-design-architecture%2F), derived class or subclass must enhance functionality, but not reduce them. LSP represents “L” on the SOLID acronym.



1. **Java:**
   ```java
   // Before LSP
   class Bird {
       void fly() {
           // logic to fly
       }
   }
   
   class Penguin extends Bird {
       void fly() {
           // Penguins can't fly
           throw new UnsupportedOperationException("Penguins can't fly");
       }
   }
   
   // After LSP
   interface FlyingBird {
       void fly();
   }
   
   class Bird implements FlyingBird {
       void fly() {
           // logic to fly
       }
   }
   
   class Penguin implements FlyingBird {
       void fly() {
           // Penguins can't fly
           throw new UnsupportedOperationException("Penguins can't fly");
       }
   }
   ```

2. **Python:**
   ```python
   # Before LSP
   class Bird:
       def fly(self):
           # logic to fly
           pass
   
   class Penguin(Bird):
       def fly(self):
           # Penguins can't fly
           raise NotImplementedError("Penguins can't fly")
   
   # After LSP
   from abc import ABC, abstractmethod
   
   class FlyingBird(ABC):
       @abstractmethod
       def fly(self):
           pass
   
   class Bird(FlyingBird):
       def fly(self):
           # logic to fly
           pass
   
   class Penguin(FlyingBird):
       def fly(self):
           # Penguins can't fly
           raise NotImplementedError("Penguins can't fly")
   ```

In these examples, before adhering to LSP, the `Penguin` subclass broke the expectation that all birds can fly. After applying LSP, the code ensures that subclasses (`Penguin`) can be substituted for their base class (`Bird`) without causing unexpected behavior or violating the contract defined by the base class.