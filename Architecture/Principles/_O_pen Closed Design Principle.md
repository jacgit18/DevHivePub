---
tags:
  - SOLID
  - OOP
  - mutability
  - principles
  - languageOverlap
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Open Close design in SOLID principles.
Status: Refinement
Started: 
EditDate: 2024-03-06
Relates: 
Peer Reviewed: 0
dg-publish:
---
According to tho this OOP design principle, software entities like (“Classes, modules, methods, functions, etc...) should be Open for extension (new functionality) and Closed for modification.”

Whenever you need to add additional behaviors, or methods, you don’t have to modify the existing one, instead, you start writing new methods.

Because, _What if you changed a behavior of an object, where some other parts of the system depends on it?_. So, you need to change also every single part in the software that has a dependency with that object, and check the logic, and do some extra testing.

> _The key benefit of this design principle is that already tried and tested code is not touched which means they won’t break._


#todo/BAU/noteRefine 
- [ ] Review and combine with other notes that make sense


1. **Java:**
   ```java
   // Before OCP
   class Shape {
       String type;
       
       void draw() {
           if (type.equals("circle")) {
               // draw circle
           } else if (type.equals("square")) {
               // draw square
           }
           // more shapes...
       }
   }
   
   // After OCP
   interface Shape {
       void draw();
   }
   
   class Circle implements Shape {
       void draw() {
           // draw circle
       }
   }
   
   class Square implements Shape {
       void draw() {
           // draw square
       }
   }
   ```

2. **Python:**
   ```python
   # Before OCP
   class Shape:
       def __init__(self, type):
           self.type = type
       
       def draw(self):
           if self.type == "circle":
               # draw circle
           elif self.type == "square":
               # draw square
           # more shapes...
   
   # After OCP
   from abc import ABC, abstractmethod
   
   class Shape(ABC):
       @abstractmethod
       def draw(self):
           pass
   
   class Circle(Shape):
       def draw(self):
           # draw circle
           
   class Square(Shape):
       def draw(self):
           # draw square
   ```

In the examples, before adhering to OCP, the `Shape` class had conditional statements to handle different shapes. After applying OCP, the code is open for extension by introducing new shape classes (`Circle`, `Square`) without modifying the existing `Shape` class, thus adhering to the Open/Closed Principle.