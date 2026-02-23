---
tags:
  - accessModifier
  - UML
  - OOP
  - prompt
  - typescript
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses access modifiers in the context of UML and object oriented classes.
Status: Refinement
Started: 
EditDate: 2024-03-03
Relates: 
Peer Reviewed: 0
dg-publish: false
---
## Modifiers 
 Access modifiers are keywords in certain languages that help to restrict the scope of attributes, classes, methods, and constructors (member)

- **no-modifier** - this is `default` to what is known as "*package-private*" making it visible only within its packages (named groups of related classes). 


## Class Diagram 
This product class diagram can repurposed for functions which would increase number of tables.
![[Class Diagram.png]]
### ChatGpt Prompt
#todo/prompts
- [ ] Create a module functional programming structural model for a driving school website
- [ ] Identify util functions in structural model
- [ ] Create a object oriented programming structural model for a driving school website
- [ ] Create a object oriented programming structural model combined with a functional programming structural model
- [ ] try using chatGPT to convert [[User Stories]] into high level object oriented class map breakdown down structure like below 


## Flashcard
**Doesn't show in spaced repetition plugin in probably obsidian reference under UML class sign** 

#accessmod   
which access modifier allows code visible to all classes;; public

What access modifier is limited to classes;; private

what modifier is limited to package;; protected

where can protected classes be accessed;; package and subclass

Which access modifier has more scope private or protected;; protected

What UML sign is for access [[Protected in Depth]] modifier;; hashtag

What UML sign is for access private modifier;; minus

What UML sign is for access public modifier;; plus

What UML sign is for mandatory;; asterisk

What UML sign is for optional;; O

What UML sign is for static member for attributes and methods;; underline or bold and underline

### UML Class Signs

^7de0bf

 ```java
 * Mandidtory  
 O Optional
```
>[!note] Example 
> "astrick sign" function-name
> 0 function-name

-  **public** - code is accessible from everywhere in the program and from outside classes. 
```java
+ public
```

### Private
- The `private` access modifier serves the essential purpose of restricting access to class members, which includes both variables and methods within the same class where they are defined. When a member is declared as `private`, it can only be accessed and modified within the class in which it is defined. This encapsulation effectively hides these members from other classes and objects. 

- Private members play a crucial role in upholding the principle of encapsulation by concealing the internal implementation details of a class. This not only helps in maintaining data integrity but also prevents direct manipulation of the class's internal state by external code, thereby enhancing the overall robustness and security of the program or system.
```java
- private
```

>[!note] 
>Side note to test a private method, create an instance of that class and try to print the output of the variable or method that was private.
>
> You could try to call the private method in a class that should have access and asserts that the call failed.


- [[Protected in Depth |Protected]] - member can only be accessed within its package and by a subclass of its class in another package used a lot with `UUID`.
```java
# protected
```

>[!note] Side Note
>Your access modifier strategy should use the most restrictive access level that makes sense for the specific member.  Also, avoid public fields except for constants.


## Non-Access Modifiers 

**These are the non-access modifiers for classes: 

- **Abstract** - class cannot be used to create objects. 
- **Final** - class cannot be inherited by other classes. 

**These are the non-access modifiers for attributes and methods: 

- **Abstract** - only be used in an abstract class and can only be used on methods. 

- **Final** - both cannot be overridden or modified. 
  
- [[Static methods |Static]]- both belong to the class and not the object. also in uml is represented by being underlined and a little bold. static members are used so, there will be one and only one copy of the member.
 
- **Transient** - both are skipped when serializing the object containing them. 
 
- **Synchronized** - methods can only be accessed by one thread at a time. 

- **Volatile** - the value of an attribute is read from main memory and not cached thread-locally.


## Modifiers in Typescript
In TypeScript, you can use both the `private` keyword and the `#` prefix to define private members of a class. However, they have some differences in their implementation and usage.

### `private` Keyword

The `private` keyword is a TypeScript-specific feature that ensures that the member is only accessible within the class it is declared. It is compiled down to regular JavaScript where private members are not strictly enforced by the language itself but are rather a TypeScript compile-time check.

Example:
```typescript
class Pet {
    private name: string;

    constructor(name: string) {
        this.name = name;
    }

    getName(): string {
        console.log("getName method called");
        return this.name;
    }

    setName(newName: string): void {
        if (typeof newName === "string") {
            this.name = newName;
        }
    }
}

// Example usage:
const myPet = new Pet("Buddy");
console.log(myPet.getName());  // Logs: getName method called
                               //       Buddy
myPet.setName("Max");
console.log(myPet.getName());  // Logs: getName method called
                               //       Max
```

### `#` Prefix (Private Fields)

The `#` prefix is a feature from ECMAScript (JavaScript) for truly private fields. It is enforced by the JavaScript engine itself and ensures that the field is private and not accessible from outside the class, even in plain JavaScript.

Example:
```typescript
class Pet {
    #name: string;

    constructor(name: string) {
        this.#name = name;
    }

    get name(): string {
        console.log("get method called");
        return this.#name;
    }

    set name(newName: string) {
        if (typeof newName === "string") {
            this.#name = newName;
        }
    }
}

// Example usage:
const myPet = new Pet("Buddy");
console.log(myPet.name);  // Logs: get method called
                          //       Buddy
myPet.name = "Max";
console.log(myPet.name);  // Logs: get method called
                          //       Max
```

### Differences and Considerations
- **`private` keyword**: Only enforced by TypeScript at compile-time. Not truly private in the emitted JavaScript code.
- **`#` prefix**: Truly private fields, enforced by the JavaScript engine at runtime. Requires a more recent version of JavaScript (ES2020 and above).

Both approaches are useful, and the choice depends on whether you need true runtime privacy or just compile-time checks provided by TypeScript.