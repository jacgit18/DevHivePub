---
tags:
  - MicroCodebaseDecision
  - casting
  - wrappers
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses boxing and unboxing.
Status: Done
Started: 
EditDate: 2024-03-04
Relates: 
Peer Reviewed: 0
dg-publish:
---
1. Unboxing: is the process of converting a wrapper class object to its corresponding primitive type. In Java, automatic unboxing is performed when a wrapper object is assigned to a primitive variable. Here's an example:

```java
Integer wrapperObj = 10; // Autoboxing - Integer wrapper object
int primitiveVar = wrapperObj; // Unboxing - converting to primitive int

System.out.println(primitiveVar); // Output: 10
```

In the above example, the `Integer` wrapper object `wrapperObj` is automatically unboxed to the primitive `int` type when assigning it to the variable `primitiveVar`.

2. Boxing Casting: involves explicitly converting a primitive type to its corresponding wrapper class object. Here's an example:

```java
int primitiveVar = 20; // Primitive int variable
Integer wrapperObj = Integer.valueOf(primitiveVar); // Boxing - explicit conversion

System.out.println(wrapperObj); // Output: 20
```

In the above example, the primitive `int` variable `primitiveVar` is explicitly boxed to the `Integer` wrapper object using the `valueOf()` method.

3. Casting between wrapper classes: can also be performed between different wrapper classes. Here's an example:

```java
Integer wrapperObj1 = 30; // Integer wrapper object
Double wrapperObj2 = (Double) wrapperObj1; // Boxing casting - casting to Double

System.out.println(wrapperObj2); // Output: 30.0
```

In the above example, the `Integer` wrapper object `wrapperObj1` is casted to the `Double` wrapper object `wrapperObj2` using explicit casting.

Note that casting between incompatible types can result in a `ClassCastException` at runtime if the types are not compatible. It is important to ensure compatibility when performing casting operations.


## Reference Type Casting Example
```java
class Animal {
    public void sound() {
        System.out.println("Animal is making a sound.");
    }
}

class Dog extends Animal {
    public void sound() {
        System.out.println("Dog is barking.");
    }
    
    public void fetch() {
        System.out.println("Dog is fetching.");
    }
}

public class Main {
    public static void main(String[] args) {
    // Upcasting - reference of Dog to Animal
        Animal animal = new Dog(); 
		
		// alt upcast
		Dog dog = new Dog();
		Animal animal = dog;


        animal.sound(); // Output: Dog is barking.
        // poloymorphism example
        
	if (animal instanceof Dog) { 
	
	// can use `instanceof` operator to check the object's compatibility before performing the cast.
	
        // Reference type casting from Animal to Dog
        Dog dog = (Dog) animal; // Downcasting
	    // Access dog-specific members and methods
        
        dog.sound(); // Output: Dog is barking.
        dog.fetch(); // Output: Dog is fetching.
        }
	
	Animal animal = new Animal();
	Dog dog = (Dog) animal; // ClassCastException - Invalid downcasting
	// if dog doesnt extend to animal class


    }
}
```

In the above example, we have an `Animal` class and a `Dog` class, where `Dog` is a subclass of `Animal`. Initially, we create an instance of `Dog` and assign it to a variable of type `Animal`, which is an example of upcasting. We can call the `sound()` method on the `animal` object, and it executes the overridden method from the `Dog` class.

Later in the code, we perform reference type casting by explicitly casting the `animal` object to the `Dog` class using `(Dog) animal`. This is possible because the `animal` object is actually an instance of `Dog`. After casting, we can access both the overridden `sound()` method and the `fetch()` method specific to the `Dog` class.

It's important to note that reference type casting should be used with caution. If the object being casted is not compatible with the target class, a `ClassCastException` will occur at runtime. It is advisable to check the compatibility of classes before performing casting operations.
