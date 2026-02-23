---
tags:
  - MicroCodebaseDecision
  - CodebaseDecision
  - static
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses static methods.
Status: Refinement
Started: 
EditDate: 2024-03-04
Relates: 
Peer Reviewed: 0
dg-publish:
---

```java
class MyClass {
    private static String staticField = "Static field";
    private String instanceField = "Instance field";

    public static void staticMethod() {
        System.out.println("Static method called");
        System.out.println(staticField);  // Accessing static field directly
        System.out.println(instanceField);  // Cannot access instance field directly
    }

    public void instanceMethod() {
        System.out.println("Instance method called");
        System.out.println(staticField);  // Accessing static field directly
        System.out.println(instanceField);  // Accessing instance field directly
    }
}

public class MethodExample {
    public static void main(String[] args) {
        // Accessing a static method
        MyClass.staticMethod();

        // Accessing an instance method
        MyClass obj = new MyClass();
        obj.instanceMethod();
    }
}
```



Explanation:

In the given example, we have a class `MyClass` with two methods: `staticMethod()` and `instanceMethod()`. The class has two fields: a static field `staticField` and an instance field `instanceField`.

1. Static Method:
   - Definition: `public static void staticMethod()`
   - Accessing Fields: Static methods can directly access static fields (`staticField`) but cannot access instance fields (`instanceField`) directly because static methods are not associated with any specific instance of the class.
   - Accessing the Method: Static methods are accessed using the class name (`MyClass.staticMethod()`).
   - Invocation: In the `MethodExample` class, we directly call the static method using `MyClass.staticMethod()`.

2. Instance Method:
   - Definition: `public void instanceMethod()`
   - Accessing Fields: Instance methods can access both static fields (`staticField`) and instance fields (`instanceField`) directly since they are associated with a specific instance of the class.
   - Accessing the Method: Instance methods are accessed through an object or instance of the class (`obj.instanceMethod()`).
   - Invocation: In the `MethodExample` class, we create an instance of `MyClass` using `new MyClass()`, and then we invoke the instance method on that object using `obj.instanceMethod()`.

By running the `MethodExample` class, you will observe the following output:

```
Static method called
Static field
Instance method called
Static field
Instance field
```

This demonstrates that both the static method and the instance method can access the static field (`staticField`), but only the instance method can access the instance field (`instanceField`).



# When to use

You would want to use a static method over an instance method in the following scenarios:

1. Utility Methods: Static methods are commonly used for utility functions that are not tied to a specific instance or object. These methods often perform generic operations that don't require access to instance-specific data.

2. Factory Methods: Static methods can be used as factory methods to create instances of a class. By making the constructor private and providing a static method to create instances, you can control the creation process and provide additional flexibility.

3. Helper Methods: If a method doesn't depend on the state of an object and doesn't need to access any instance-specific fields or methods, it can be declared as static. These methods can be called directly on the class itself, without the need for an instance.

4. Performance Optimization: In certain cases, using static methods can lead to performance improvements. Since static methods are associated with the class rather than individual instances, they don't require object creation, reducing memory overhead and potential object initialization costs.

5. Organization and Clarity: Static methods can help improve code organization and readability. By using static methods for operations that are not specific to a particular instance, you can separate them from instance-specific methods, providing a clearer distinction between the two.

It's important to note that static methods cannot access instance-specific fields or methods directly. They are unable to reference the `this` keyword or use non-static members without an instance reference. Static methods should be stateless and should not rely on instance-specific data.

In general, when deciding whether to use a static method or an instance method, consider the purpose of the method and whether it requires access to instance-specific data. If the method doesn't rely on instance state and can be shared among all instances or doesn't need an instance at all, a static method is a suitable choice. If the method operates on or modifies instance-specific data, an instance method should be used.

## Instantiation

```javascript
class MyClass {
  static add(a, b) {
    return a + b;
  }

  multiply(a, b) {
    return a * b;
  }
}

// Calling a static function without instantiation
const sum = MyClass.add(3, 5);
console.log(sum); // Output: 8

// Using instantiation to call an instance method
const math = new MyClass();
const product = math.multiply(4, 6);
console.log(product); // Output: 24
```
Instantiation is the process of creating an instance or an object based on a class or a blueprint. In object-oriented programming (OOP), classes serve as templates or blueprints for creating objects with specific properties (data) and behaviors (methods).

When you instantiate a class, you create a unique instance of that class, which has its own set of data and can execute the defined methods. Each instance of a class is independent of others and can be modified or accessed separately.