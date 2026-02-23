---
tags:
  - accessModifier
  - ClassStructure
  - languageOverlap
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses protected keywords.
Status: Done
Started: 
EditDate: 2024-03-04
Relates: 
Peer Reviewed: 0
dg-publish:
---
In Java, the `protected` keyword is an access modifier that can be applied to class members (fields, methods, and nested classes) to control their visibility and accessibility within a class hierarchy. Here's an explanation of the `protected` keyword:

### Scoped at Parent Package Level

1. Access within the Same Package: When a member is declared as `protected`, it can be accessed by other classes within the same package. This allows subclasses and other classes in the package to access the protected member.

2. Access in Subclasses: The `protected` access modifier also grants access to subclasses, even if they are in a different package. Subclasses inherit the protected members of their superclass and can directly access them.

3. Access outside the Package: However, members declared as protected are not accessible to classes that are not subclasses and are not in the same package. They are not accessible to unrelated classes outside the package.

Key Points to Note:
- `protected` provides a balance between accessibility and encapsulation. It allows controlled access to members, preventing unrestricted access from unrelated classes but still allowing access within a class hierarchy.
- Protected members are visible within subclasses, enabling inheritance and overriding of methods or accessing superclass fields and methods.
- It is important to consider the design implications and carefully choose which members should be declared as protected. Making too many members protected may expose more of the internal implementation, reducing encapsulation.
- The `protected` modifier is weaker than `public` but stronger than the default (package-private) access level.

Here's an example to illustrate the use of the `protected` keyword:

```java
package com.example;

public class Animal {
    protected String name;

    protected void makeSound() {
        System.out.println("Animal is making a sound");
    }
}

package com.example;

public class Cat extends Animal {
    public void displayName() {
        System.out.println("Name: " + name);  // Accessing protected member from superclass
    }
}

package com.anotherpackage;

import com.example.Animal;

public class AnotherClass {
    public void accessProtectedMember() {
        Animal animal = new Animal();
        // animal.name;  // Not accessible, protected member of different package
    }
}
```

In the example above, the `name` field and `makeSound()` method in the `Animal` class are declared as protected. The `Cat` class, which extends `Animal`, can access the protected `name` field in its `displayName()` method. However, the `AnotherClass` in a different package cannot access the protected `name` field of the `Animal` class.

In summary, the `protected` keyword provides access to members within the same package and subclasses, enabling controlled visibility within a class hierarchy while maintaining encapsulation.