---
tags:
  - wrappers
  - languageOverlap
author:
  - jacgit18
  - chatgpt
Status: Done
Purpose: This documentation discusses wrappers.
Started: 
EditDate: 2024-03-06
Relates: "[[Primitive Wrappers Across Languages]]"
Peer Reviewed: 0
dg-publish: false
---

```javascript
const str = 'This is a string';

str.toUpperCase(); 

typeof str; // output: string
```

If `str` is really a primitive, how come there is a method `toUpperCase` accessible to it? Well, JS is doing some magic in the background.

1. When you call a method on a primitive (in this example, a string), JS creates a temporary special object in the background that has primitive-specific methods.
2. The type of object depends on the type of primitive. So, if it’s a number, we have access to number-related methods.
3. The method gets called that returns the result as a new primitive (in this example, a string).
4. The temporary object gets destroyed.

One might think that this is an extra unnecessary overhead, but JS engines highly optimize this process, and the benefits far outweigh the costs.

All the primitive data types except for `null` and `undefined` have their primitive-specific methods available to them.

**Why is this workaround needed?**

It just makes it so much convenient to have methods directly accessible through primitives. Code looks much cleaner as well.

**An alternative? Not recommended:**

```javascript
const str = new String('This is a string');

str.toUpperCase(); // THIS IS A STRING

typeof str; // object
```

As you can see when you create an instance of `String`, the resulting instance has all the string-related methods available like a string primitive does, but it is really an object. Calling `typeof` shows that. This instance would carry the heaviness of an object wherever it goes. It might confuse other developers and might cause issues when `typeof` is used. Hence, it is highly recommended to work with primitives.

**Summary:**

Temporary object creation/deletion was an eye-opener for me. I assumed JS must be managing these primitives internally as objects. These JS quirks always have me on my toes and make me realize even after programming in JS for almost a decade, I have a long way to go! Hope, this was helpful!
