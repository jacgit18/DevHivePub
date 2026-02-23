---
tags:
  - languageOverlap
  - instance
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Instantiation.
Status: Done
Started: 
EditDate: 2024-03-05
Relates: "[[Class Instance]]"
Peer Reviewed: 0
dg-publish:
---
In programming, instantiation typically refers to the process of creating an instance of a class, which can represent an object or, in the context of servers and microservices, an independent unit or occurrence. It involves allocating memory and setting up the initial state of the instance based on the blueprint provided by the class or template.

```typescript
class MyClass {
  private myProperty: string;

  constructor(initialValue: string) {
    this.myProperty = initialValue;
  }

  public displayProperty(): void {
    console.log(this.myProperty);
  }
}

// Instantiating an object of MyClass
const myObject = new MyClass("Hello, TypeScript!");

// Calling a method on the instantiated object
myObject.displayProperty();
```

This example defines a class `MyClass` with a private property `myProperty` and a method `displayProperty()`. It then creates an instance of `MyClass` called `myObject` and calls the `displayProperty` method, printing the initialized property to the console.

## Constructors 
A constructor is employed to instantiate a class, but unlike properties and methods, a superclass's constructors aren't inherited by subclasses. Invocation occurs within subclasses using the "super" keyword, following syntax such as super() or super(parameters).


In the realm of static methods, object creation is limited to constructors. A static method doesn't allow object creation unless it's a constructor; otherwise, object instantiation is precluded.

The use of "static" ensures direct access to the main method by a class without necessitating the creation of a main class object in Java.

When contemplating Java constructors, having a constructor with an empty or coded body offers flexibility over multiple overloaded constructors.

In the context of classes and objects, System.out.print exemplifies the system as the class, "out" as the object, and "print" as the method. Various classes feature distinct objects with diverse methods.

However, the use of this.color = color and this.filled = filled is illegal with super and subclasses, limited to one class with private variables and methods. Access or mutation is feasible through public accessors/mutators if defined in the superclass.