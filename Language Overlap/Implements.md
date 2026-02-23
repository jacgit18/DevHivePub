---
tags:
  - keywords
  - languageOverlap
  - OOP
  - interfaces
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses implement keyword.
Status: Refinement
Started: 
EditDate: 2024-03-05
Relates: 
Peer Reviewed: 0
dg-publish:
---
Implements: In Java, the implements keyword is used to implement an interface. An interface is a special type of class which implements a complete abstraction and only contains abstract methods. To access the interface methods, the interface must be “implemented” by another class with the implements keyword and the methods need to be implemented in the class which is inheriting the properties of the interface. Since an interface is not having the implementation of the methods, a class can implement any number of interfaces at a time. 

JavaScript does not have the interface type, it is often times needed. For reasons relating to JavaScript's dynamic nature and use of Prototypical-Inheritance, it is difficult to ensure consistent interfaces across classes -- however, it is possible to do so; and frequently emulated. 

At this point, there are handfuls of particular ways to emulate Interfaces in JavaScript; variance on approaches usually satisfies some needs, while others are left unaddressed. Often times, the most robust approach is overly cumbersome and stymies the implementor (developer). 

Here is an approach to Interfaces / Abstract Classes that is not very cumbersome, is explicative, keeps implementations inside of Abstractions to a minimum, and leaves enough room for dynamic or custom methodologies: 

At this point, there are handfuls of particular ways to emulate Interfaces in JavaScript; variance on approaches usually satisfies some needs, while others are left unaddressed. Often times, the most robust approach is overly cumbersome and stymies the implementor (developer). 

JavaScript inheritance is based on objects, not classes. That's not a big deal until you realize: 

JavaScript is an extremely dynamically typed language -- you can create an object with the proper methods, which would make it conform to the interface, and then undefine all the stuff that made it conform. It'd be so easy to subvert the type system -- even accidentally! -- that it wouldn't be worth it to try and make a type system in the first place. 

Instead, JavaScript uses what's called duck typing. (If it walks like a duck, and quacks like a duck, as far as JS cares, it's a duck.) If your object has quack(), walk(), and fly() methods, code can use it wherever it expects an object that can walk, quack, and fly, without requiring the implementation of some "Duckable" interface. The interface is exactly the set of functions that the code uses (and the return values from those functions), and with duck typing, you get that for free. 

Now, that's not to say your code won't fail halfway through, if you try to call some_dog.quack(); you'll get a TypeError. Frankly, if you're telling dogs to quack, you have slightly bigger problems; duck typing works best when you keep all your ducks in a row, so to speak, and aren't letting dogs and ducks mingle together unless you're treating them as generic animals. In other words, even though the interface is fluid, it's still there; it's often an error to pass a dog to code that expects it to quack and fly in the first place. 

But if you're sure you're doing the right thing, you can work around the quacking-dog problem by testing for the existence of a particular method before trying to use it. Something like 

```javascript
if (typeof(someObject.quack) == "function") { 

    // This thing can quack 

} 
```

So you can check for all the methods you can use before you use them. The syntax is kind of ugly, though. There's a slightly prettier way: 

```javascript
Object.prototype.can = function(methodName) { 

     return ((typeof this[methodName]) == "function"); 

}; 

if (someObject.can("quack")) { 

    someObject.quack(); 

} 
```

This is standard JavaScript, so it should work in any JS interpreter worth using. It has the added benefit of reading like English. 

For modern browsers (that is, pretty much any browser other than IE 6-8), there's even a way to keep the property from showing up in for...in: 

```javascript
Object.defineProperty(Object.prototype, 'can', { 

    enumerable: false, 

    value: function(method) { 

        return (typeof this[method] === 'function'); 

    } 

}) 
```

The problem is that IE7 objects don't have .defineProperty at all, and in IE8, it allegedly only works on host objects (that is, DOM elements and such). If compatibility is an issue, you can't use .defineProperty. (I won't even mention IE6, because it's rather irrelevant anymore outside of China.) 

Another issue is that some coding styles like to assume that everyone writes bad code, and prohibit modifying Object.prototype in case someone wants to blindly use for...in. If you care about that, or are using (IMO broken) code that does, try a slightly different version: 

```javascript
function can(obj, methodName) { 

     return ((typeof obj[methodName]) == "function"); 

} 

if (can(someObject, "quack")) 

{ 

    someObject.quack(); 

} 
```



Here is an approach to Interfaces / Abstract Classes that is not very cumbersome, is explicative, keeps implementations inside of Abstractions to a minimum, and leaves enough room for dynamic or custom methodologies: 

```javascript
function resolvePrecept(interfaceName) { 

    var interfaceName = interfaceName; 

    return function curry(value) { 

        /*      throw new Error(interfaceName + ' requires an implementation for ...');     */ 

        console.warn('%s requires an implementation for ...', interfaceName); 

        return value; 

    }; 

} 

var iAbstractClass = function AbstractClass() { 

    var defaultTo = resolvePrecept('iAbstractClass'); 

    this.datum1 = this.datum1 || defaultTo(new Number()); 

    this.datum2 = this.datum2 || defaultTo(new String()); 

    this.method1 = this.method1 || defaultTo(new Function('return new Boolean();')); 

    this.method2 = this.method2 || defaultTo(new Function('return new Object();')); 

}; 

var ConcreteImplementation = function ConcreteImplementation() { 

    this.datum1 = 1; 

    this.datum2 = 'str'; 

    this.method1 = function method1() { 

        return true; 

    }; 

    this.method2 = function method2() { 

        return {}; 

    }; 

    //Applies Interface (Implement iAbstractClass Interface) 

    iAbstractClass.apply(this);  // .call / .apply after precept definitions 

}; 
```

## Participants 

### Precept Resolver

The `resolvePrecept` function serves as a utility and helper function within your Abstract Class, facilitating customized implementation-handling of encapsulated Precepts. It can throw errors or warnings and assign default values to the Implementor class.

### iAbstractClass

The `iAbstractClass` defines the interface, establishing a tacit agreement with its Implementor class. The interface assigns each precept to the same namespace or whatever the Precept Resolver function returns. The agreement is contextual, providing a provision for the Implementor.

### Implementor

The Implementor agrees with the Interface (`iAbstractClass`) and applies it through Constructor-Hijacking: `iAbstractClass.apply(this)`. By defining data and behavior, then hijacking the Interface's constructor, we ensure Implementor's overrides are added, and Interface explicates warnings and default values.

While non-cumbersome, this approach has served well with some drawbacks:

### Drawbacks

- It emulates true interfaces but doesn't enforce them.
- Definitions, defaults, warnings, or errors are explicated but rely on developer adherence.
- Missing assertions for return types, signatures, object freeze, and other specifics within the JavaScript community.

This method, while the best approach to "Interfaces in JavaScript" for now, awaits improvements such as:

- Assertions for return types.
- Assertions for signatures.
- Object freeze to prevent deletions.
- Assertions for other prevalent JavaScript-specific needs.

Despite these considerations, it has proven beneficial for our team and projects, providing consistency in software development.


### Example 1

```java
interface One { 
    // Abstract method 
    void methodOne(); 
} 

class Two { 
    public void methodTwo() { 
    } 
}

// Class extending the Two class 
// and implementing the One interface 
class Three extends Two implements One { 
    public void methodOne() { 
        // Implementation of the method 
    } 
}
```

### Example 2

```java
// Defining the interface One 
interface One { 
    public void methodOne(); 
} 

// Defining the second interface Two 
interface Two { 
    public void methodTwo(); 
} 

// Class implementing both interfaces 
class Three implements One, Two { 
    public void methodOne() { 
        // Implementation of the method 
    } 
    public void methodTwo() { 
        // Implementation of the method 
    } 
}
```

### Example 3

```java
// Defining the interface One 
interface One { 
    void methodOne(); 
} 

// Defining the interface Two 
interface Two { 
    void methodTwo(); 
} 

// Interface extending both defined interfaces 
interface Three extends One, Two { 
}
```
