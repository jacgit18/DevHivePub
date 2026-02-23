---
tags:
  - javascript
  - web
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Prototype Inheritance.
Status: Capture
Started: 2024-02-04
EditDate: 2024-02-04
Relates: "[[Prototypes]]"
Peer Reviewed: 0
dg-publish:
---
JavaScript's prototype inheritance provides a mechanism for objects to inherit properties and methods from other objects. While JavaScript does not have traditional classes like some other programming languages, it introduces syntax sugar that mimics class-based syntax. This includes the `class`, `extends`, and `super` keywords.

### Prototype Inheritance:

1. **Prototype Chain:**
   JavaScript objects have a prototype, which is another object from which they inherit properties. This creates a prototype chain where objects can inherit from each other.

2. **Object Creation:**
   Objects in JavaScript can be created using constructor functions or object literals. Constructor functions, when invoked with the `new` keyword, create instances with a link to their prototype.

### Class Syntax Sugar

1. **Class Keyword:**
   The `class` keyword was introduced in ECMAScript 2015 (ES6) to provide a more familiar syntax for defining constructor functions and their prototypes.

   ```javascript
   class Animal {
     constructor(name) {
       this.name = name;
     }

     speak() {
	    return this.name
     }
   }
   ```

Is equivalent to the following prototype-based code:  
  
```javascript  
function Animal(name) {  
this.name = name;  
}  
  
MyClass.prototype.speak = function() {  
return this.name;  
};  
```  
  
Both approaches achieve the same result, but the class syntax provides a more concise and readable way to express object-oriented concepts. Under the hood, JavaScript still uses prototypes for managing the inheritance chain and method lookups.


2. **Extends Keyword:**
   The `extends` keyword is used to create a subclass that inherits from a superclass. It simplifies the process of prototype chaining.

   ```javascript
   class Dog extends Animal {
     speak() {
       console.log(`${this.name} barks.`);
     }
   }
   ```

   Here, `Dog` is a subclass extending the `Animal` superclass, inheriting its properties and methods.

3. **Super Keyword:**
   The `super` keyword is used to call the constructor of the superclass within the constructor of the subclass.

   ```javascript
   class Dog extends Animal {
     constructor(name, breed) {
       super(name); // Calls the constructor of the superclass
       this.breed = breed;
     }
   }
   ```

### Syntax Sugar for Class-like Inheritance:

While JavaScript's prototype inheritance is different from classical inheritance, the class syntax sugar provides a more familiar and readable way to work with prototypes. It makes the language feel more like class-based languages, even though it is still based on prototypes.

```javascript
class Shape {
  constructor(color) {
    this.color = color;
  }

  draw() {
    console.log(`Drawing a ${this.color} shape.`);
  }
}

class Circle extends Shape {
  constructor(color, radius) {
    super(color);
    this.radius = radius;
  }

  draw() {
    console.log(`Drawing a ${this.color} circle with radius ${this.radius}.`);
  }
}
```

In this example, the `Circle` class extends the `Shape` class, showcasing the class-based syntax sugar for prototype inheritance in JavaScript.


### Class-like Inheritance with No Syntax Sugar:
The class syntax sugar in JavaScript is essentially a more convenient way of expressing prototype-based inheritance. Here's the equivalent code using prototype-based syntax:

```javascript
// Prototype-based Animal "class"
function Animal(name) {
  this.name = name;
}

Animal.prototype.speak = function () {
  console.log(`${this.name} makes a sound.`);
};

// Prototype-based Dog "subclass" extending Animal
function Dog(name, breed) {
  Animal.call(this, name); // Call the constructor of the superclass
  this.breed = breed;
}

// Inherit from Animal's prototype
Dog.prototype = Object.create(Animal.prototype);

// Set Dog's constructor to itself
Dog.prototype.constructor = Dog;

// Override the speak method
Dog.prototype.speak = function () {
  console.log(`${this.name} barks.`);
};

// Creating instances using the "classes"
const genericAnimal = new Animal('Generic');
genericAnimal.speak(); // Outputs: Generic makes a sound.

const myDog = new Dog('Buddy', 'Labrador');
myDog.speak(); // Outputs: Buddy barks.
```

In this prototype-based version:

- The `Animal` "class" is defined with a constructor function and methods added to its prototype.
- The `Dog` "subclass" is created by calling `Animal.call(this, name)` in its constructor to initialize the superclass properties.
- `Object.create(Animal.prototype)` sets up the prototype chain, linking `Dog`'s prototype to `Animal`'s prototype.
- `Dog.prototype.constructor = Dog;` corrects the constructor property, which is overridden by the previous line.
- Methods like `speak` are added to the `Dog` prototype, allowing method overriding.

While this version is more verbose, it illustrates the underlying prototype inheritance mechanism that the class syntax sugar is built upon in JavaScript.


