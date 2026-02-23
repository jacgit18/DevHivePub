---
tags:
  - MicroCodebaseDecision
  - MacroCodebaseDecision
  - CodebaseDecision
  - polymorphism
  - static
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Dynamic and Static Polymorphism.
Status: Done
Started: 
EditDate: 2024-03-05
Relates: 
Peer Reviewed: 0
dg-publish:
---
Dynamic polymorphism and static polymorphism are two forms of polymorphism in programming, and they differ in the timing of binding between the method call and the method implementation.

## Dynamic Polymorphism (Run-time Polymorphism):
   - **Binding Time:** Occurs at runtime.
   - **Example:** Involves method overriding, where a method in a subclass provides a specific implementation for a method that is already defined in its superclass.
   - **How it Works:** The decision about which method to call is made during runtime based on the actual type of the object.
   - **Implementation:** Achieved through method overriding and the use of the `virtual` keyword in languages like C++ or the `@Override` annotation in Java.

## Static Polymorphism (Compile-time Polymorphism):
   - **Binding Time:** Occurs at compile time.
   - **Example:** Involves method overloading, where multiple methods with the same name are defined in the same class but with different parameter types or a different number of parameters.
   - **How it Works:** The decision about which method to call is made by the compiler based on the method signature, and it is known at compile time.
   - **Implementation:** Achieved through method overloading.


dynamic polymorphism with a simple example in Java using method overriding:

```java
class Animal {
    void makeSound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    // Method overriding
    void makeSound() {
        System.out.println("Dog barks");
    }
}

class Cat extends Animal {
    // Method overriding
    void makeSound() {
        System.out.println("Cat meows");
    }
}

public class PolymorphismExample {
    public static void main(String[] args) {
        Animal animal1 = new Dog();
        Animal animal2 = new Cat();

        // Calls the overridden methods at runtime
        animal1.makeSound(); // Output: Dog barks
        animal2.makeSound(); // Output: Cat meows
    }
}
```

In this example, the `Animal` class has a method `makeSound()`. Both `Dog` and `Cat` classes extend `Animal` and override the `makeSound()` method. At runtime, the actual type of the objects (`Dog` and `Cat`) is considered, and the appropriate overridden method is called.

Now, let's look at static polymorphism with method overloading in Java: ^4a17f7

```java
class Calculator {
    // Method overloading
    int add(int a, int b) {
        return a + b;
    }

    // Overloaded method with a different parameter type
    double add(double a, double b) {
        return a + b;
    }
}

public class StaticPolymorphismExample {
    public static void main(String[] args) {
        Calculator calculator = new Calculator();

        // Calls the appropriate overloaded method at compile time
        int result1 = calculator.add(5, 7);         // Calls the int version
        double result2 = calculator.add(3.5, 2.5);  // Calls the double version

        System.out.println("Result 1: " + result1); // Output: Result 1: 12
        System.out.println("Result 2: " + result2); // Output: Result 2: 6.0
    }
}
```

Here, the `Calculator` class has two overloaded `add` methods. The decision about which method to call is made by the compiler based on the method signature and is known at compile time.


The decision between method overloading and method overriding depends on the specific requirements of your program and the behavior you want to achieve. Here are some considerations for choosing between method overloading and method overriding:

### Method Overloading:

1. **Same Functionality, Different Parameters:**
   - **Use Case:** When you want to provide different ways to call a method with varying parameters, but the functionality remains similar.
   - **Example:** Calculating the sum of integers and doubles using the same method name (`add` in the previous example) but with different parameter types.

2. **Compile-time Binding:**
   - **Use Case:** When you want the decision about which method to call to be made at compile time.
   - **Example:** If the determination of the method to be called can be resolved based on the number or types of arguments during compilation.

3. **Independent Methods:**
   - **Use Case:** When the methods are logically independent and provide different functionalities.
   - **Example:** Having multiple `print` methods for different data types, each printing in a format suitable for that type.

### Method Overriding:

1. **Polymorphism and Extensibility:**
   - **Use Case:** When you want to achieve polymorphic behavior, allowing subclasses to provide specific implementations for methods defined in their superclass.
   - **Example:** Overriding the `makeSound` method in animal subclasses to have specific sounds for each type of animal.

2. **Run-time Binding:**
   - **Use Case:** When you want the decision about which method to call to be deferred until runtime.
   - **Example:** If the determination of the method to be called depends on the actual type of the object (dynamic polymorphism).

3. **Inheritance and Code Reuse:**
   - **Use Case:** When you have a common behavior in a superclass that you want to be shared by all subclasses, but each subclass may provide its own implementation.
   - **Example:** A `Vehicle` class with a method `startEngine`, and subclasses like `Car` and `Motorcycle` override this method with their specific start-up procedures.

### General Tips:

- **Both Can Coexist:**
  - It's important to note that method overloading and method overriding can coexist in the same program.

- **Consider the Context:**
  - Consider the context of your application, the relationships between classes, and the desired behavior.

- **Follow Naming Conventions:**
  - Follow consistent and meaningful naming conventions for methods to enhance code readability.

Ultimately, the choice between method overloading and method overriding is driven by the design goals and requirements of your software.



### Runtime Binding (Dynamic Polymorphism):

**Pros:**

1. **Flexibility and Extensibility:**
    
    - Allows for flexibility and extensibility in the code by enabling the selection of the appropriate method at runtime based on the actual type of the object.
2. **Polymorphic Behavior:**
    
    - Enables polymorphic behavior, where a single interface can represent different types, and the appropriate method is called based on the runtime type of the object.

**Cons:**

1. **Runtime Overhead:**
    
    - The decision-making process occurs at runtime, which can introduce some overhead compared to compile-time decisions.
2. **Late Discovery of Errors:**
    
    - Errors related to method calls might only be discovered at runtime, which makes debugging potentially more challenging.

### Compile-time Binding (Static Polymorphism):

**Pros:**

1. **Performance:**
    
    - Generally results in faster performance because the decision about which method to call is made at compile time, reducing the need for runtime checks.
2. **Early Error Detection:**
    
    - Errors related to method calls are detected at compile time, providing early feedback and making debugging easier.

**Cons:**

1. **Less Flexibility:**
    
    - Offers less flexibility compared to runtime binding. Once the code is compiled, the decision about method calls is fixed.
2. **Limited Polymorphism:**
    
    - May not support certain forms of polymorphism as effectively as runtime binding, especially in scenarios where dynamic behavior is required.