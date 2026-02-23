---
tags:
  - SOLID
  - interfaces
  - principles
  - languageOverlap
author:
  - jacgit18
  - chatgpt
Comments: Need to clean up
Purpose: This documentation discusses interface segregation in SOLID principles.
Status: Refinement
Started: 
EditDate: 2024-03-06
Relates: 
Peer Reviewed: 0
dg-publish:
---
![[Circle Implements Shape Interface.png]]

#todo/BAU/noteRefine 
- [ ] Clean up and combine or backlinks to other notes that discuss interface getting rid of repeating information.

**The Interface Segregation Principle** states that a client should not implement an [interface](http://javarevisited.blogspot.com/2012/04/10-points-on-interface-in-java-with.html) if it doesn't use all of its functionality. This often occurs when an interface contains multiple features, but the client only requires one of them. Interfaces should be specific, focusing on individual tasks rather than trying to do many different things.

The reasoning behind this principle is to ensure that implementing classes only include the specific interfaces they need, rather than being forced to implement methods they have no use for. Therefore, it's advisable to break down large interfaces into smaller, more specialized ones.

Developing interfaces requires careful consideration since once an interface is released, it cannot be modified without potentially breaking existing implementations. Java 8 introduced [default or defender methods](https://javarevisited.blogspot.com/2014/07/default-defender-or-extension-method-of-Java8-example-tutorial.html#axzz5kO8vmDxy) to facilitate interface evolution, but not all programming languages support such features.

One notable benefit of adhering to this design principle in Java is that having single-function interfaces results in fewer methods that need to be implemented. This keeps code more concise and focused.

**Key Points about Interfaces:**

- An interface serves as a blueprint for implementing a class. It does not contain concrete methods with code; all methods are abstract.
- You cannot instantiate an interface, but classes implementing interfaces can be instantiated.
- Interfaces do not have instance variables but can include public static final variables (constant class variables).
- Interfaces are essential for achieving abstraction, dynamic method resolution at runtime, loose coupling, and separating method definitions from the inheritance hierarchy.
- When you anticipate multiple implementations of something, using interfaces is a good practice.

In Java, it's recommended to **program for the interface, not the implementation.** This approach leads to flexible code that can work with any new implementation of the interface. In practical terms, use interface types for variables, return types of methods, or argument types. For example, use:

```java
List numbers = getNumbers();
```

instead of:

```java
ArrayList numbers = getNumbers();
```

This practice allows for greater flexibility in your code and makes it easier to adapt to changes or new implementations.

### Java:

```java
// Interface
interface Worker {
    void work();
    void eat();
}

// Violation of ISP
class SuperWorker implements Worker {
    @Override
    public void work() {
        // ... doing super work
    }

    @Override
    public void eat() {
        // ... eating in a super way
    }
}

// Adhering to ISP
interface Workable {
    void work();
}

interface Eatable {
    void eat();
}

class NormalWorker implements Workable, Eatable {
    @Override
    public void work() {
        // ... doing normal work
    }

    @Override
    public void eat() {
        // ... eating in a normal way
    }
}
```

### Python:

```python
# Interface
class Worker:
    def work(self):
        pass

    def eat(self):
        pass

# Violation of ISP
class SuperWorker(Worker):
    def work(self):
        # ... doing super work

    def eat(self):
        # ... eating in a super way

# Adhering to ISP
class Workable:
    def work(self):
        pass

class Eatable:
    def eat(self):
        pass

class NormalWorker(Workable, Eatable):
    def work(self):
        # ... doing normal work

    def eat(self):
        # ... eating in a normal way
```

### C#:

```csharp
// Interface
interface IWorker
{
    void Work();
    void Eat();
}

// Violation of ISP
class SuperWorker : IWorker
{
    public void Work()
    {
        // ... doing super work
    }

    public void Eat()
    {
        // ... eating in a super way
    }
}

// Adhering to ISP
interface IWorkable
{
    void Work();
}

interface IEatable
{
    void Eat();
}

class NormalWorker : IWorkable, IEatable
{
    public void Work()
    {
        // ... doing normal work
    }

    public void Eat()
    {
        // ... eating in a normal way
    }
}
```

In the examples adhering to the Interface Segregation Principle, I've split the original `Worker` interface into smaller interfaces (`Workable` and `Eatable`) to avoid forcing classes to implement methods they don't need. This way, classes can implement only the interfaces that are relevant to them, promoting a more modular and maintainable design.


# Java Diamond Problem

using interfaces solves this problem 

In Java, the Diamond Problem occurs in the context of multiple inheritance when a class inherits from two classes that have a common ancestor. If both parent classes have a method with the same name, and the child class doesn't override that method, it becomes ambiguous for the compiler to decide which method to call.

Here's a simple example to illustrate the Diamond Problem:

```java
class A {
    void method() {
        System.out.println("Method from class A");
    }
}

class B extends A {
}

class C extends A {
}

class D extends B, C { // This would cause a compilation error in Java
}
```

In the example above, if a class `D` tries to extend both `B` and `C`, it would result in a compilation error because Java doesn't support multiple inheritance through classes.

One way to solve the Diamond Problem in Java is by using interfaces. Here's an example:

```java
interface A {
    void method();
}

class B implements A {
    public void method() {
        System.out.println("Method from class B");
    }
}

class C implements A {
    public void method() {
        System.out.println("Method from class C");
    }
}

class D implements B, C {
    // Here, D needs to provide its own implementation of the 'method' to resolve ambiguity.
    public void method() {
        System.out.println("Method from class D");
    }
}
```

In this solution, interfaces are used instead of classes, and the class `D` implements both interfaces `B` and `C`. This way, the compiler doesn't face the ambiguity of conflicting method names, and the class `D` provides its own implementation of the method to resolve the issue.




"interfaces expose operations and not data" is generally true when discussing software design principles, particularly in the context of programming interfaces such as those in object-oriented programming. Let's delve into this concept a bit further:  
  
1. **Exposing Operations:**  
- Interfaces define a contract specifying what operations or behaviors a class or module should provide. They declare a set of methods or functions that an implementing class or module must support. These methods represent the actions or operations that can be performed on or by an object.  
  
2. **Hiding Implementation Details:**  
- By focusing on operations, interfaces abstract away the internal details and state of an object. This encapsulation ensures that the user of the interface is concerned only with what an object can do (its behavior) rather than how it achieves those actions (its implementation). This separation promotes a clear and concise design.  
  
3. **Encapsulation:**  
- The principle of encapsulation involves bundling data and methods that operate on that data into a single unit, typically a class. Interfaces contribute to encapsulation by exposing only the necessary operations, shielding the internal data and implementation details from external entities.  
  
4. **Flexibility and Abstraction:**  
- Designing interfaces around operations enhances flexibility. Implementing classes can provide different ways to achieve the specified operations, as long as they adhere to the contract defined by the interface. This allows for interchangeable components and promotes a high level of abstraction.  
  
5. **Reducing Coupling:**  
- When interfaces expose operations rather than data, it reduces the dependency between different parts of a system. Components that rely on the interface only need to know how to interact with the exposed operations, not the internal structure or representation of the data.  
  
6. **Security and Access Control:**  
- Exposing operations rather than raw data helps in controlling access to sensitive information. By limiting the exposure of data and allowing controlled access through well-defined operations, interfaces contribute to security and privacy considerations.  
  
Consider an example in an object-oriented context:  
  
```java  
// Interface defining operations  
public interface Shape {  
double calculateArea();  
double calculatePerimeter();  
}  
  
// Implementing class  
public class Circle implements Shape {  
private double radius;  
  
public Circle(double radius) {  
this.radius = radius;  
}  
  
@Override  
public double calculateArea() {  
return Math.PI * radius * radius;  
}  
  
@Override  
public double calculatePerimeter() {  
return 2 * Math.PI * radius;  
}  
}  
```  
  
In this example, the `Shape` interface exposes operations (`calculateArea` and `calculatePerimeter`) that define the behavior expected from any class implementing the interface. The internal data (radius) and the implementation details are hidden from the interface user.  
  
By emphasizing operations in interfaces, software design becomes more modular, adaptable, and maintainable, contributing to the principles of abstraction, encapsulation, and reduced coupling.