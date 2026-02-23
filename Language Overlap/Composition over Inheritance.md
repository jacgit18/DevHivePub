---
tags:
  - ClassStructure
  - Inheritance
  - languageOverlap
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses using Composition over Inheritance.
Status: Done
Started: 
EditDate: 2024-03-04
Relates: 
Peer Reviewed: 0
dg-publish:
---
### Composition Example:

```java
class Animal {
    void eat() {
        System.out.println("Animal is eating");
    }
}

class Dog {
    private Animal animal;

    Dog(Animal animal) {
        this.animal = animal;
    }

    void eat() {
        animal.eat();
    }

    void bark() {
        System.out.println("Dog is barking");
    }
}

public class CompositionExample {
    public static void main(String[] args) {
        Animal myAnimal = new Animal();
        Dog myDog = new Dog(myAnimal);

        myDog.eat();  // Using composition
        myDog.bark(); // Own method
    }
}
```

#### Function composition calling function in specific order 

```javascript
const addCus = func => (...args) => {
    console.log('Save Info');
    return func(...args);
};

const processOrder = func => (...args) => {
    console.log(`Processing order #${args[0]}`);
    return func(...args);
};

let completeOrder = (...args) => {
    console.log(`Order #${[...args].toString()} completed`);
};

completeOrder = processOrder(completeOrder);
completeOrder = addCus(completeOrder);
completeOrder('1000');

// Explanation
// function addCus(...args) {
//     return function processOrder(...args) {
//         return function completeOrder(...args) {
//             // goes up to the other function
//         }
//     }
// }

const curry = func => {
    const curried = (...args) => {
        if (func.length !== args.length) {
            return curried.bind(null, ...args);
        }
        return func(...args);
    };
    return curried;
};

const total = (x, y, z) => x + y + z;
const currTotal = curry(total);
console.log(currTotal(10)(20)(30));

```


### Inheritance Example:

```java
class Animal {
    void eat() {
        System.out.println("Animal is eating");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Dog is barking");
    }
}

public class InheritanceExample {
    public static void main(String[] args) {
        Dog myDog = new Dog();
        myDog.eat();  // Inherited method
        myDog.bark(); // Own method
    }
}
```


#### Function inheritance
In JavaScript, functions can participate in a form of inheritance through [[Prototypes]]. Every JavaScript object has a prototype, which is essentially a reference to another object. When you call a method or property on an object and it's not found on the object itself, JavaScript looks for it in the object's prototype chain.

Functions in JavaScript are also objects, and they have prototypes. You can use the prototype property of a constructor function to add properties or methods that will be shared by all instances created with that constructor. This is often referred to as prototype-based inheritance.

Here's a simple example:

```javascript
// Constructor function
function Animal(name) {
    this.name = name;
}

// Adding a method to the prototype
Animal.prototype.sound = function() {
    console.log('Some generic sound');
};

// Creating instances
const dog = new Animal('Dog');
const cat = new Animal('Cat');

// Both instances share the 'sound' method
dog.sound(); // Output: Some generic sound
cat.sound(); // Output: Some generic sound
```

In modern JavaScript, the class syntax is often used to achieve the same result in a more structured way. Under the hood, classes are just syntactic sugar over prototype-based inheritance.

```javascript
class Animal {
    constructor(name) {
        this.name = name;
    }

    sound() {
        console.log('Some generic sound');
    }
}

const dog = new Animal('Dog');
const cat = new Animal('Cat');

dog.sound(); // Output: Some generic sound
cat.sound(); // Output: Some generic sound
```

So, while functions themselves don't inherit from each other, they can be used as constructors to create objects that inherit properties and methods through the prototype chain.

### When to Choose:
- **Composition:**
  - Use when a class represents a "has-a or has to" relationship with another class.
	  -  Like a dog *has to eat which you can think of as a external action all animals do so we have base animal class with function that all animals do.
	  - Then a dog class use that animal class and its own internal functions
  - Greater flexibility, as you can switch the composed object dynamically.
  - Helps to avoid the issues like the diamond problem in multiple inheritance.


- **Inheritance:**
  - Use when a class represents an "is-a" relationship with the base class (e.g., Dog "is-a" Animal).
  - Reuse of code is a primary concern.

Choose based on your specific needs and design principles.


## more examples 
```Javascript
// Class with methods 

class Pizza { 

  constructor(size, crust, sauce) { 

      this.size = size; 

      this.crust = crust; 

      this.sauce = sauce; 

      this.toppings = []; 

  } 

  prepare() { console.log('Preparing...') } 

  bake() { console.log('Baking...') } 

  ready() { console.log('Ready!') } 

} 

// Lines 16 through 43 are examples WITHOUT composition  

// Problem: Repeats methods from above - Not D.R.Y. 

class Salad { 

  constructor(size, dressing) { 

      this.size = size; 

      this.dressing = dressing 

  } 

  prepare() { console.log('Preparing...') } 

  toss() { console.log('Tossing...') } 

  ready() { console.log('Ready!') } 

} 

class stuffedCrustPizza extends Pizza { 

  stuff() { console.log('Stuffing the crust...') } 

} 

class butteredCrustPizza extends Pizza { 

  butter() { console.log('Buttering the crust...') } 

} 

// Problem: Repeats methods from above - Not D.R.Y. 

class stuffedButteredCrustPizza extends Pizza { 

  stuff() { console.log('Stuffing the crust...') } 

  butter() { console.log('Buttering the crust...') } 

} 

const myPizza = new stuffedButteredCrustPizza(); 

myPizza.stuff(); 

myPizza.butter(); 

// And now here's a BETTER way with composition below:  

// Create all of the methods as separate functions 

const prepare = () => { 

  return { 

      prepare: () => console.log('Preparing...') 

  } 

} 

const bake = () => { 

  return { 

      bake: () => { console.log('Baking...'); return [1, 2, 3] } 

  } 

} 

const toss = () => { 

  return { 

      toss: () => console.log('Tossing...') 

  } 

} 

const ready = () => { 

  return { 

      ready: () => console.log('Ready!') 

  } 

} 

const stuff = () => { 

  return { 

      stuff() { console.log('Stuffing the crust...') } 

  } 

} 

const butter = () => { 

  return { 

      butter() { console.log('Buttering the crust...') } 

  } 

} 
```

```Javascript
// Use composition to add the methods to the objects  

// You are never defining the same method twice! 

const createPizza = (size, crust, sauce) => { 

  const pizza = { 

      size: size, 

      crust: crust, 

      sauce: sauce, 

      toppings: [] 

  } 

  return { 

      ...pizza, 

      ...prepare(), 

      ...bake(), 

      ...ready() 

  } 

} 

const createSalad = (size, dressing) => { 

  return { 

      size: size, 

      dressing: dressing, 

      ...prepare(), 

      ...toss(), 

      ...ready() 

  } 

} 

// Compare to ES6 Class syntax with extends and super() 

const createStuffedButteredCrustPizza = (pizza) => { 

  return { 

      ...pizza, 

      ...stuff(), 

      ...butter() 

  } 

} 

const anotherPizza = createPizza("medium", "thin", "original"); 

const somebodysPizza = createStuffedButteredCrustPizza(anotherPizza); 

// OR 

const davesPizza = 

  createStuffedButteredCrustPizza(createPizza("medium", "thin", "original")); 

const davesSalad = createSalad("side", "ranch"); 

davesPizza.bake(); 

console.log(davesPizza.bake().reverse()); //chaining 

davesPizza.stuff(); 

davesSalad.prepare(); 

console.log(davesPizza); 

console.log(davesSalad);
```