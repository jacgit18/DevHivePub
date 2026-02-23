---
tags:
  - pattern
  - languageOverlap
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses design patterns.
Status: Distilling
Started: 
EditDate: 2024-03-06
Relates: 
Peer Reviewed: 0
dg-publish:
---
## Design Patterns — What Are They?

Design patterns are tested solutions to common issues in software development as they act as templates to guide us in structuring our code. With design patterns it’s easier to create code that’s more readable, flexible and maintainable, providing also a common language for developers to communicate more effectively.


## Creational Design Patterns: Constructing Objects

These patterns deal with the process of object creation. They abstract the instantiation process, making it more flexible, reusable, and maintainable. Examples of creational designs include Singleton, Factory Method, Abstract Factory, Builder, and Prototype.


In JavaScript, objects are a core feature and they are often used to represent entities or things with similar characteristics, and we use creational design patterns to organize the creation of these objects.

Creational patterns help to abstract the instantiation process making a system independent of how its objects are created, composed and represented.

**The Factory Pattern**

The Factory Pattern provides a way to create objects, but it allows subclasses to alter the type of objects that will be created.

```javascript
function CarFactory() {  
	this.createCar = function(model) {  
		let car;  
		
		if (model === 'Sedan') {  
		car = new Sedan();  
		} 
		else if (model === 'SUV') {  
			car = new SUV();  
		}  
		return car;  
			
	};  
}
```

**The Singleton Pattern**

The Singleton Pattern restricts a class from instantiating multiple objects and it’s useful when a single object is required to control actions.

```javascript
let Singleton = (function () {  
  let instance;  
   
  function createInstance() {  
    return new Object("I am the instance");  
  }  
   
  return {  
    getInstance: function () {  
      if (!instance) {  
        instance = createInstance();  
      }  
      return instance;  
    }  
  };  
})();
```

**The Builder Pattern**

The Builder Pattern entails a client to construct a complex object with the focus only its type and content, and it takes care of assembling the object.

```javascript

function CarBuilder() {  
this.car = null;  
  
this.step1 = function () {  
this.car = new Car();  
};  
  
this.step2 = function () {  
this.car.addParts();  
};  
  
this.get = function () {  
return this.car;  
};  
}

```

## Structural Design Patterns: Shaping Our Code

Structural patterns are concerned with the composition of classes and objects. They help assemble individual components into a larger structure, making it easiemanaging relationships and dependencies between objects. Struct easierural patterns include Adapter, Bridge, Composite, Decorator, Facade, Flyweight, and Proxy.



Structural patterns are about organizing different classes and objects to form larger structures and when one part of a system changes it ensures that the entire system doesn’t need to change along with it.

**The Adapter Pattern**

The Adapter Pattern allows classes with incompatible interfaces to work together wrapping itself around an object and exposing a standard interface for interacting with that object.

```javascript

class OldCalculator {  
constructor() {  
this.operations = function(term1, term2, operation) {  
switch (operation) {  
case 'add':  
return term1 + term2;  
case 'sub':  
return term1 - term2;  
default:  
return NaN;  
}  
};  
}  
}  
  
class NewCalculator {  
constructor() {  
this.add = function(term1, term2) {  
return term1 + term2;  
};  
this.sub = function(term1, term2) {  
return term1 - term2;  
};  
}  
}  
  
class CalculatorAdapter {  
constructor() {  
const newCalc = new NewCalculator();  
  
this.operations = function(term1, term2, operation) {  
switch (operation) {  
case 'add':  
return newCalc.add(term1, term2);  
case 'sub':  
return newCalc.sub(term1, term2);  
default:  
return NaN;  
}  
};  
}  
}

```

**The Decorator Pattern**

The Decorator Pattern describes the behavior to be added to an individual object, either statically or dynamically, without affecting the behavior of other objects from the same class.

```javascript

function Car(name) {  
this.name = name;  
}  
  
Car.prototype.getName = function () {  
return this.name;  
};  
  
function DecoratedCar(car, color, price) {  
this.car = car;  
this.color = color;  
this.price = price;  
}  
  
DecoratedCar.prototype.getName = function () {  
return this.car.getName() + ' has color ' + this.color + ' and price ' + this.price;  
};

```

**The Proxy Pattern**

The Proxy Pattern provides a surrogate or placeholder object to control access to the original object.

```javascript

function NetworkAccess() {  
this.connect = function () {  
console.log('Connected to the network.');  
};  
}  
  
function NetworkProxy() {  
this.network = new NetworkAccess();  
this.connect = function () {  
console.log('Using network proxy.');  
this.network.connect();  
};  
}

```

## Behavioral Design Patterns: Managing Object Collaboration

Behavioural patterns define how objects communicate and interact with each other. They help streamline complex communication flows and improve the flexibility and reusability of code by encapsulating behaviour. Examples of behavioural patterns include Observer, Iterator, Strategy, Command, Chain of Responsibility, State, Template Method, Mediator, and Memento.




Behavioral design patterns are concerned with communication between objects, how objects operate and carry out their responsibilities most of the times increasing flexibility in carrying out communication between objects.

**The Observer Pattern**

The Observer Pattern defines a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.

```javascript
class Subject {  
constructor() {  
this.observers = [];  
}  
  
subscribe(observer) {  
this.observers.push(observer);  
}  
  
unsubscribe(observer) {  
const index = this.observers.indexOf(observer);  
if (index > -1) {  
this.observers.splice(index, 1);  
}  
}  
  
notifyAll(data) {  
for (let i = 0; i < this.observers.length; i++) {  
this.observers[i].notify(data);  
}  
}  
}  
  
class Observer {  
notify(data) {  
console.log(`Observer received: ${data}`);  
}  
}
```

**The Strategy Pattern**

The Strategy Pattern allows a method to be swapped out at runtime by any other method (strategy) without the client realizing it and essentially it’s a group of algorithms that are interchangeable.

```javascript

class Shipping {  
setStrategy(strategy) {  
this.strategy = strategy;  
}  
  
calculate(parcel) {  
return this.strategy.calculate(parcel);  
}  
}  
  
class UPS {  
calculate(parcel) {  
return `$${parcel.weight * 1.75}`;  
}  
}  
  
class FedEx {  
calculate(parcel) {  
return `$${parcel.weight * 2.45}`;  
}  
}  
  
class USPS {  
calculate(parcel) {  
return `$${parcel.weight * 1.25}`;  
}  
}
```

## The Command Pattern

The Command Pattern grants the encapsulation of operations in objects without knowing the request’s specifics.

```javascript
class Switch {  
execute(command) {  
command.execute();  
}  
}  
  
class TurnOnCommand {  
constructor(light) {  
this.light = light;  
}  
  
execute() {  
this.light.turnOn();  
}  
}  
  
class Light {  
turnOn() {  
console.log('Light is on');  
}  
  
turnOff() {  
console.log('Light is off');  
}  
}
```

In the next section we’ll see how these patterns are used in practical JavaScript applications and how they lead to clean and scalable code.

## Practical Applications of JavaScript Design Patterns

Design patterns are powerful tools but it’s through their application in real-world scenarios that we truly appreciate their power, and to show this let’s explore how some of the patterns we’ve discussed can be utilized in practical situations.

## User Profile Creation

Suppose you’re tasked with creating a user profile system for a social media site: with the Factory Pattern you can streamline this process creating profiles with predefined templates.

```javascript
function UserFactory() {  
this.createUser = function(type) {  
let user;  
  
if (type === 'Personal') {  
user = new PersonalUser();  
} else if (type === 'Business') {  
user = new BusinessUser();  
}  
  
user.type = type;  
user.say = function() {  
console.log(this.type + ": profile created");  
}  
return user;  
}  
}
```

## Integrating with a Third-party API

In another situation imagine you need to integrate a third-party API into your application but this API’s interface doesn’t match your application’s existing system: The Adapter Pattern will aid you to make the API compatible with your application without changing your existing codebase.

```javascript
class ThirdPartyAPI {  
constructor() {  
this.specificRequest = function() {  
return "Third-party API response";  
};  
}  
}  
  
class Adapter {  
constructor(thirdPartyAPI) {  
this.request = function() {  
return thirdPartyAPI.specificRequest();  
};  
}  
}  
  
// Using the Adapter  
const thirdPartyAPI = new ThirdPartyAPI();  
const adapter = new Adapter(thirdPartyAPI);  
adapter.request();
```

## Adding Features to User Profiles

The Decorator Pattern can be applied when you want to add new features to your user profiles like premium badges or customized themes without altering your original User object.

```javascript

function User(name) {  
this.name = name;  
}  
  
User.prototype.getName = function () {  
return this.name;  
};  
  
function DecoratedUser(user, badge, theme) {  
this.user = user;  
this.badge = badge;  
this.theme = theme;  
}  
  
DecoratedUser.prototype.getName = function () {  
return `${this.user.getName()}, Badge: ${this.badge}, Theme: ${this.theme}`;  
};

```

## User Interactions with Posts

The Observer Pattern comes in handy when you need to implement a system where users can interact with posts such as liking or commenting on them, where each post could act as a subject with other users as observers that are notified of any interactions.

```javascript
class Post {  
constructor() {  
this.observers = [];  
}  
  
like(user) {  
this.notifyAll(`Post liked by ${user}`);  
}  
  
subscribe(observer) {  
this.observers.push(observer);  
}  
  
notifyAll(message) {  
for (let observer of this.observers) {  
observer.notify(message);  
}  
}  
}  
  
class User {  
notify(message) {  
console.log(`User notified: ${message}`);  
}  
}
```

## Different Shipping Methods

Now suppose your e-commerce application needs to support different shipping methods: the Strategy Pattern is a perfect fit for this case because each shipping method can be implemented as a separate strategy.

```javascript
class Shipping {  
setStrategy(strategy) {  
this.strategy = strategy;  
}  
  
calculate(parcel) {  
return this.strategy.calculate(parcel);  
}  
}  
  
class UPS {  
calculate(parcel) {  
return `$${parcel.weight * 1.75}`;  
}  
}  
  
class FedEx {  
calculate(parcel) {  
return `$${parcel.weight * 2.45}`;  
}  
}  
  
class USPS {  
calculate(parcel) {  
return `$${parcel.weight * 1.25}`;  
}  
}
```

## Website Theme Customization

Imagine you have a website that allows users to customize their themes so you can use the Factory Pattern to create different theme objects and then use the Decorator Pattern to add additional features to those themes.

```javascript
// Factory Pattern  
function ThemeFactory() {  
this.createTheme = function(type) {  
let theme;  
  
if (type === 'Dark') {  
theme = new DarkTheme();  
} else if (type === 'Light') {  
theme = new LightTheme();  
}  
  
theme.type = type;  
return theme;  
}  
}  
  
// Decorator Pattern  
function DecoratedTheme(theme, color) {  
this.theme = theme;  
this.color = color;  
}  
  
DecoratedTheme.prototype.getName = function () {  
return this.theme.getName() + ' in ' + this.color + ' color';  
};
```

## E-commerce Site with Special Offers

Imagine an e-commerce site and you want to implement a system that applies special offers to products where you could use the Strategy Pattern to represent different types of special offers and the Observer Pattern to notify customers whenever a special offer is applied to a product they’re interested in.

```javascript
// Strategy Pattern  
class SpecialOffer {  
apply(product) {  
// abstract method  
}  
}  
  
class BlackFridayOffer extends SpecialOffer {  
apply(product) {  
product.price *= 0.8; // 20% discount  
}  
}  
  
class ChristmasOffer extends SpecialOffer {  
apply(product) {  
product.price *= 0.85; // 15% discount  
}  
}  
  
// Observer Pattern  
class Product {  
constructor(price) {  
this.price = price;  
this.observers = [];  
}  
  
setPrice(price) {  
this.price = price;  
this.notifyAll();  
}  
  
subscribe(observer) {  
this.observers.push(observer);  
}  
  
notifyAll() {  
for (let observer of this.observers) {  
observer.notify(this);  
}  
}  
}  
  
class Customer {  
notify(product) {  
console.log(`Product price has been updated to $${product.price}`);  
}  
}
```

## Performance Monitoring System

Ok, and what if you’re building a system to monitor the performance of different modules in an application? The modules could be represented using the Factory Pattern and to observe the performance of these modules and report any issues, you can use the Proxy Pattern.

```javascript
// Factory Pattern  
function ModuleFactory() {  
this.createModule = function(type) {  
let module;  
  
if (type === 'Database') {  
module = new DatabaseModule();  
} else if (type === 'Network') {  
module = new NetworkModule();  
}  
  
module.type = type;  
return module;  
}  
}  
  
// Proxy Pattern  
class PerformanceProxy {  
constructor(module) {  
this.module = module;  
}  
  
monitor() {  
console.log('Monitoring performance...');  
// Delegate the call to the original object  
this.module.monitor();  
}  
}

```

## Chat Application

In a very common chat application you might use the Singleton Pattern to ensure that there’s only one instance of the ChatRoom class and each User could be an Observer receiving messages whenever another user sends one.

```javascript
// Singleton Pattern  
let ChatRoom = (function() {  
let instance;  
  
function createInstance() {  
let object = new Object("ChatRoom");  
return object;  
}  
  
return {  
getInstance: function() {  
if (!instance) {  
instance = createInstance();  
}  
return instance;  
}  
};  
})();  
  
// Observer Pattern  
class User {  
notify(message) {  
console.log(`Received message: ${message}`);  
}  
}

```

## Online Gaming System

In an other example like an online gaming system you can use the Factory Pattern to create different types of game characters, the Observer Pattern can be used to inform other players when a character has been hit and the Decorator Pattern can be used to add special abilities to a character.

```javascript
// Factory Pattern  
function CharacterFactory() {  
  this.createCharacter = function(type) {  
    let character;  
  
    if (type === 'Warrior') {  
      character = new Warrior();  
    } else if (type === 'Mage') {  
      character = new Mage();  
    }  
  
    character.type = type;  
    return character;  
  }  
}  
  
// Observer Pattern  
class Character {  
  hit() {  
    // Notify all observers  
  }  
}  
  
// Decorator Pattern  
function EnhancedCharacter(character, ability) {  
  this.character = character;  
  this.ability = ability;  
}  
  
EnhancedCharacter.prototype.useAbility = function() {  
  console.log(`Using ability: ${this.ability}`);  
};
```

These examples demonstrate the power of combining different design patterns to create a flexible and scalable solution, but remember: the key is not to force the use of patterns, it’s to identify when a pattern can improve code quality and maintainability.

## Pitfalls to Avoid When Using Design Patterns

Design patterns can make a significant difference in your software development process, but like any tool they must be used judiciously.

Here are a few common pitfalls to avoid:

## Overusing Design Patterns

Design patterns are solutions to common problems, but they are not a panacea for all software development woes, thus using them in places where they aren’t needed can lead to unnecessarily complex and convoluted code.

## Misapplying Design Patterns

Each design pattern has a specific scenario where it shines and using it in a context where it doesn’t fit can lead to confusing and hard-to-maintain code.

## Not Understanding the Pattern Fully

Before using a design pattern it’s fundamental to fully understand its structure, purpose and implications, because without understanding it can lead to incorrect implementation and bugs that are hard to debug.

## Ignoring the Principle of Simplicity

The KISS (Keep It Simple, Stupid) principle is key in software development and I always prefer to mention it: sometimes a simple procedural solution may be more suitable than a sophisticated design pattern.

> If a pattern introduces complexity without a proportional benefit, it may not be the best solution.

## Recap and Recommendations

In essence design patterns offer efficient solutions to recurring coding problems, but it’s important not to misuse them because as said overusing or applying them without understanding can lead to unnecessary complexity in your code.


