---
tags:
  - keywords
  - languageOverlap
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses extends keyword.
Status: Done
Started: 
EditDate: 2024-03-05
Relates: 
Peer Reviewed: 0
dg-publish:
---
In the realm of Java, the `extends` keyword takes center stage, serving as the gateway to inheritance. Its primary role is to signify that the class under definition is an extension or derivation of the base class. In essence, `extends` empowers a subclass by inheriting the functionalities of its parent class, allowing for an augmentation of capabilities.

It's crucial to note that Java imposes a restriction on multiple inheritances to evade ambiguity issues. Consequently, a class can extend only one class, steering clear of potential conflicts.

Let's delve into a simple example to illuminate the prowess of `extends`:

```java
class One { 
    public void methodOne() { 
        // Some Functionality 
    } 
}

class Two extends One { 
    public static void main(String args[]) { 
        Two t = new Two(); 
        // Invokes the methodOne from the parent class 
        t.methodOne(); 
    } 
}
```

In this illustrative snippet, class `Two` extends class `One`, thereby inheriting its `methodOne`. The `main` method demonstrates the invocation of `methodOne` from the parent class within the subclass. This showcases the seamless integration of functionalities through the art of inheritance in Java.