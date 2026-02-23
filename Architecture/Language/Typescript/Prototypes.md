---
tags:
  - javascript
  - web
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses what are prototypes.
Status: Done
Started: 
EditDate: 2024-02-25
Relates: 
Peer Reviewed: 0
dg-publish:
---
Objects in JavaScript have an internal property known as prototype. It is simply a reference to another object and contains common attributes/properties across all instances of the object. An object’s prototype attribute specifies the object from which it inherits properties.  

The Prototype pattern’s main concern is to ensure that objects being created are not new instances each time. This means if we create an object MathAdd with a method add, we should just reuse add when we created multiple instances of MathAdd since the implementation doesn't change. This is a performance benefit as well.

move somewhere
```javascript
// Method change With "This" keyword goes to prototype 

class User { 

    constructor(email, name){ 

        this.email = email; 
        this.name = name; 
        this.score = 0; 

    } 

    login(){ 

        console.log(this.email, 'just logged in'); 
        return this; 

    } 

    logout(){ 

        console.log(this.email, 'just logged out'); 
        return this; 

    } 

    updateScore(){ 

        this.score++; 
        console.log(
        this.email, 'score is now', this.score); 

        return this; 

    } 

} 

var userOne = new User('ryu@ninjas.com', 'Ryu'); 
var userTwo = new User('yoshi@mariokorp.com', 'Yoshi'); 

userOne.login().updateScore().updateScore().logout(); 

console.log(userOne);
```



Prototypes allows to add functions to existing libraries 
```javascript
libraryName.LibraryClass.prototype.functionNameAdeded = function(){ 

...} 

let numArray = [1,2,-8,3,-4,7]; 

// logs 

[ 
    1, 
    2, 
    -8, 
    3, 
    -4, 
    7 
] 
```


This JavaScript code represents the prototype chain of an empty array object. The object has various built-in array methods and properties, such as `concat`, `forEach`, `length`, etc. Additionally, it inherits methods and properties from the generic Object prototype, like `hasOwnProperty` and `toString`. The `[[Prototype]]` property shows the immediate prototype of the object, and in this case, it points to the generic Object prototype.

```javascript
[[Prototype]]: Array(0) 

at: ƒ at() 

concat: ƒ concat() 

constructor: ƒ Array() 

copyWithin: ƒ copyWithin() 

entries: ƒ entries() 

every: ƒ every() 

fill: ƒ fill() 

filter: ƒ filter() 

find: ƒ find() 

findIndex: ƒ findIndex() 

findLast: ƒ findLast() 

findLastIndex: ƒ findLastIndex() 

flat: ƒ flat() 

flatMap: ƒ flatMap() 

forEach: ƒ forEach() 

includes: ƒ includes() 

indexOf: ƒ indexOf() 

join: ƒ join() 

keys: ƒ keys() 

lastIndexOf: ƒ lastIndexOf() 

length: 0 

map: ƒ map() 

pop: ƒ pop() 

push: ƒ push() 

reduce: ƒ reduce() 

reduceRight: ƒ reduceRight() 

reverse: ƒ reverse() 

shift: ƒ shift() 

slice: ƒ slice() 

some: ƒ some() 

sort: ƒ sort() 

splice: ƒ splice() 

toLocaleString: ƒ toLocaleString() 

toString: ƒ toString() 

unshift: ƒ unshift() 

values: ƒ values() 

Symbol(Symbol.iterator): ƒ values() 

Symbol(Symbol.unscopables): {copyWithin: true, entries: true, fill: true, find: true, findIndex: true, …} 

[[Prototype]]: Object 

constructor: ƒ Object() 

hasOwnProperty: ƒ hasOwnProperty() 

isPrototypeOf: ƒ isPrototypeOf() 

propertyIsEnumerable: ƒ propertyIsEnumerable() 

toLocaleString: ƒ toLocaleString() 

toString: ƒ toString() 

valueOf: ƒ valueOf() 

__defineGetter__: ƒ __defineGetter__() 

__defineSetter__: ƒ __defineSetter__() 

__lookupGetter__: ƒ __lookupGetter__() 

__lookupSetter__: ƒ __lookupSetter__() 

__proto__: (...) 

get __proto__: ƒ __proto__() 

set __proto__: ƒ __proto__()
```