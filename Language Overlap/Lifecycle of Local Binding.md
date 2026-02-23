---
tags:
  - bindings
  - javascript
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses lifecycle of local bindings.
Status: Done
Started: 
EditDate: 2024-02-17
Relates: "[[Javascript vs TypeScript]]"
Peer Reviewed: 0
dg-publish:
---
Local binding refers to the association of a variable with a value within a specific scope, typically limited to a certain part of a program or function. The variable's existence and value are confined to that particular area, and it doesn't affect variables with the same name in other parts of the program. This helps in organizing and managing data within different sections of code without causing conflicts.

The ability to treat functions as values, combined with the fact that local bindings are re-created every time a function is called, brings up an interesting question. What happens to local bindings when the function call that created them is no longer active? 

The following code shows an example of this. It defines a function, wrapValue, that creates a local binding. It then returns a function that accesses and returns this local binding. 

```javascript
function wrapValue(n) { 

  let local = n; 

  return () => local; 

} 

let wrap1 = wrapValue(1); 

let wrap2 = wrapValue(2); 

console.log(wrap1()); 

// → 1 

console.log(wrap2()); 

// → 2 
```

This is allowed and works as you’d hope—both instances of the binding can still be accessed. This situation is a good demonstration of the fact that local bindings are created anew for every call, and different calls can’t trample on one another’s local bindings. 

This feature—being able to reference a specific instance of a local binding in an enclosing scope—is called closure. A function that references bindings from local scopes around it is called a closure. This behavior not only frees you from having to worry about lifetimes of bindings but also makes it possible to use function values in some creative ways. 

With a slight change, we can turn the previous example into a way to create functions that multiply by an arbitrary amount. 

```javascript
function multiplier(factor) { 

  return number => number * factor; 

} 

let twice = multiplier(2); 

console.log(twice(5)); 

// → 10 
```

The explicit local binding from the wrap value example isn’t really needed since a parameter is itself a local binding. 

Thinking about programs like this takes some practice. A good mental model is to think of function values as containing both the code in their body and the environment in which they are created. When called, the function body sees the environment in which it was created, not the environment in which it is called. 

In the example, multiplier is called and creates an environment in which its factor parameter is bound to 2. The function value it returns, which is stored in twice, remembers this environment. So when that is called, it multiplies its argument by 2.

## Module Pattern

```javascript
function jane() {  
  const name = 'jane';  
  const mid = 'A';  
  const final = 'B+';  
  
  return {  
    midtermScore: () => mid,  
    finaltermScore: () => final,  
  }  
}jane().midtermScore(); // A  
jane().finaltermScore(); // B+
```



## Binding Overall
The concept of local bindings is a programming language feature that can be found in various languages, not exclusive to JavaScript. Many programming languages, especially those that support functions as first-class citizens or have lexical scoping, exhibit similar behavior with local bindings.

Languages like python, ruby, and many functional programming languages share this characteristic. The specifics of scoping rules and the handling of local bindings may vary across languages, but the general idea of local bindings being created and maintained during function execution is a common concept in programming language design.