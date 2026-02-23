---
tags:
  - javascript
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses __proto__.
Status: Done
Started: 
EditDate: 2024-03-02
Relates: 
Peer Reviewed: 0
dg-publish:
---
**1. Rules of Prototypal Delegation:**

   - **No Circular Reference Allowed:**
     - Explanation: An object's prototype (`__proto__`) should not create a circular reference, meaning it cannot refer back to itself or create a loop in the prototype chain.
     - Example:
       ```javascript
       // Incorrect (Circular Reference)
       person.__proto__ = guitarist; // This creates a circular reference

       // Correct
       person.__proto__ = instrument; // Avoids circular reference
       ```

   - **`__proto__` Must Be Object or Null:**
     - Explanation: The `__proto__` property should be either an object or `null`. It should not be another type.
     - Example:
       ```javascript
       // Correct
       person.__proto__ = instrument; // Object

       // Incorrect
       person.__proto__ = 'someString'; // Not an object or null
       ```

   - **Object Can Only Directly Inherit From One Object:**
     - Explanation: An object can have only one prototype in its prototype chain. However, it can indirectly inherit from multiple objects through delegation.
     - Example:
       ```javascript
       // Correct
       person.__proto__ = instrument; // Single direct inheritance

       // Incorrect
       person.__proto__ = [guitar, piano]; // Multiple direct inheritance (not allowed)
       ```

**2. Object Delegation in JavaScript:**
   - Explanation: Object delegation in JavaScript leverages the prototype chain to enable objects to delegate behavior to each other without a strict class hierarchy. This is more about sharing behavior than traditional class-based inheritance.
   - Example:
     ```javascript
     youObj = {
       paper: ""
     }

     friendWithPen = {
       tool: pen()
     }

     friendObj = {
       otherFriend: friendWithPen.tool
     }

     Object.setPrototypeOf(friendWithPen, friendObj);

     console.log(youObj.paper);
     console.log(youObj.otherFriend.tool.pen());
     ```

**3. Prototypal Delegation vs. Inheritance:**
   - Explanation: JavaScript uses prototypal delegation, which is often mistakenly referred to as inheritance. This mechanism is more about delegation and sharing behavior among objects rather than true class-based inheritance.
   - Example:
     ```javascript
     function Dog() {}

     Dog.prototype.breed = "bulldog";

     let myDoggie = new Dog();

     // myDoggie doesn't have a "prototype" property, but it inherits from Dog.prototype
     console.log(myDoggie.breed);

     function Cat() {}
     let bear = {};

     // "prototype" is a property on a function, not on instances
     console.log(Cat.prototype);

     // "__proto__" is a property on instances that points to their prototype
     console.log(bear.__proto__);
     ```

This refined explanation aims to clarify the concepts of prototypal delegation, circular references, and the nature of object-oriented behavior in JavaScript.