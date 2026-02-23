---
tags:
  - CodebaseDecision
  - MacroCodebaseDecision
  - MicroCodebaseDecision
  - OOP
  - Inheritance
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Polymorphism.
Status: Refinement
Started: 
EditDate: 2023-10-29
Relates: 
Peer Reviewed: 0
dg-publish:
---
## Understanding Polymorphism in Java

**Polymorphism**, derived from "poly" (many) and "morph" (variance of form), is a fundamental concept in programming. In Java, it allows objects to take on different forms, enabling developers to use inherited attributes and methods to perform various tasks. This versatility allows the execution of a single action in multiple ways.

### Key Concepts

**1. "Many Forms" Concept:**
   - Polymorphism means "many forms," enabling methods with similar signatures to accomplish different tasks.

**2. Types of Polymorphism:**
   - Polymorphism in Java can be categorized into two types:
   
   - **Compile-Time Polymorphism:**
     - This type of polymorphism involves method overloading. It occurs when two methods share the same name but have different required parameters. The compiler determines which method to call based on the parameters provided.

   - **Run-Time Polymorphism:**
     - Run-time polymorphism is resolved through method overriding. In this case, a method in a subclass with the same name and signature as a method in the superclass replaces the superclass method. Method calls are determined at runtime, based on the reference variable of a superclass or parent class.
## Shapes and Methods
Consider a program calculating area and perimeter of shapes. We define methods `area()` and `perimeter()`. Different shapes require distinct calculations, leading to subclasses like circle, square, trapezium, and polygon. This represents polymorphism, where the base class "shapes" takes on various forms.

## JavaScript's Polymorphism Handling
Programming languages implement polymorphism differently. Java and JavaScript, both object-oriented, differ in their approaches. Some data-oriented languages use Entity Component System (ECS) pattern. Polymorphism also works with inheritance and encapsulation.

### Types of Polymorphism

The three major types are:
- [[#Ad-hoc Polymorphism]]
- [[#Subtype Polymorphism]]
- [[#Parametric Polymorphism]]

### Ad-hoc Polymorphism

Ad-hoc polymorphism enables a value to display varied behaviors when examined through different types. This often involves function overloading, such as operator overloading, where a function can take on different forms but shares the same name, adapting to the types of its arguments.

### Subtype Polymorphism

Subtype polymorphism involves a subtype and a supertype data type. It's about implementing an interface and substituting different implementations. Inheritance is commonly used with subtype polymorphism.


This type of polymorphism shouldn’t be confused with inheritance as it doesn’t involve the creation of new objects from existing objects — even though inheritance is used most times with this type of polymorphism in JavaScript. Rather, this type of polymorphism is about implementing an interface and substituting different implementations. 

For example, if a relative unfortunately died and left you his bookstore. You can read all the books there, sell off the books if you like, you can look at the deceased accounts, the deceased customer list, etc. This is inheritance; you have everything the relative had. Inheritance is a form of code reuse. 

If your relative doesn’t leave the bookstore for you in his will, you can reopen the bookstore yourself, taking on all of the relative’s roles and responsibilities, add even some changes of your own — this is subtyping; you are now a bookstore owner, just like your relative used to be. 

### Parametric Polymorphism

Parametric polymorphism, also known as generics, is a programming language feature that allows you to write code without specifying the data types of certain elements. Instead, you can use placeholders or type parameters that represent a range of possible types. This enables you to create generic functions, classes, or data structures that can work with different types.

### Examples 

```javascript
function Animal() {}

let cat = new Cat("Kitty");
let dog = new Dog("Puppy");
let goat = new Goat("Billy");

// Cat, dog, and goat are subtypes of Animal.
// You can substitute different implementations for these animals.
```

we have a superclass named Technologist with a method **study()**.  We also have a subclass called **SRE** and create a **DevOps** subclass.  SRE and DevOps could use the same **study()** method with different results. 

```java
public class Technologist { 

public void study() { 

System.out.println("Technologist study generic things"); 

	} 

} 



public class SRE extends Technologist { 

public void study() { 

System.out.println("SRE study chaos engineering"); 

	} 

} 


public class DevOps extends Technologist { 

public void study() { 

System.out.println("DevOps study Terraform"); 

	} 

}
```


### Common Gotchas with Polymorphism
1. Polymorphic functions affect the performance of your code, i.e. how fast your program runs. For instance, a monomorphic function will run faster compared to a polymorphic function. In some cases, this difference in performance may be insignificant if they’re frequently run. 

**Monomorphic Function :**
   In this case, `addIntegers` is a monomorphic function as it specifically works with integers.
   ```java
   public class MonomorphicExample {
       public static int addIntegers(int a, int b) {
           return a + b;
       }
   }
   ```

>[!note] *Monomorphism* is the opposite of polymorphism meaning a function is works only for one type. while with polymorphism or polymorphic functions works with many types.


**Polymorphic Function:**
   Here, `addValues` is polymorphic as it uses Java's generics (`<T>`) to allow the function to work with different types, adapting its behavior based on the provided types that support the "+" operator.
   ```java
   public class PolymorphicExample {
       public static <T> T addValues(T x, T y) {
           // This function can work with different types (polymorphism)
           // as long as those types support the "+" operator.
           return x + y;
       }
   }
   ```

2. Sometimes, polymorphism reduces the readability of a program. To solve this problem, it is important to comment on your code so that people can identify the runtime behavior of the program. 

3. To implement polymorphism easily in JavaScript, one needs to understand inheritance. This is because polymorphism in JavaScript is centered around inheritance. 



### Why do monomorphic and polymorphic matter in JavaScript? 

The answer lies in the fact that VMs can do heuristic detection of "hot functions", meaning code that is executed hundreds or even thousands of times. If a function's execution count exceeds a predetermined limit, the VMs optimizer might pick up that bit of code and attempt to compile an optimized version based on the arguments passed to the function. In this case, it presumes your function will always be called with the same type of arguments (not necessarily the same objects). 

The reason for this is well-documented in this v8-specific guideline document where an integer vs. general number optimization is explained. Say you have: 

```javascript
function add(a, b) { return a + b; } 
```

...and you're always calling this function with integers, this method might be optimized by compiling a function that does integer summation on the CPU, which is fast. If after optimization you feed it a non-integer value, then the VM deoptimizes the function and falls back to the unoptimized version, since it cannot perform integer summation on non-integers and the function would return erroneous results. 

In languages where you specify overloaded monomorphic methods you can get around this problem by simply compiling multiple versions like [[Dynamic & Static Polymorphism#^4a17f7| here]]  of the same method name with different argument signatures which are then optimized on their own. This means that you call different optimized methods because using differently typed arguments requires you to use a different overloaded method, so there's no question of which method you're using. 

You might think that you could keep multiple copies of optimized functions in the VM and check types to determine which optimized compiled function to use. In theory, that would work, if type checking before method invocation were free or very inexpensive. In practice, that usually doesn't turn out to be the case, and you'd probably want to balance things against real-world code to determine the best trade-off threshold. 

