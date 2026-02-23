---
tags:
  - typescript
author:
  - gitUserNamePlaceHolder
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: 
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
WeakMap and WeakSet are collections in JavaScript that are similar to Map and Set but with some key differences, primarily related to how they handle references to objects and garbage collection.

### WeakMap

A `WeakMap` is a collection of key/value pairs where the keys are objects and the values can be arbitrary values. The main features and differences from `Map` are:

1. **Keys must be objects**: Unlike a `Map`, where keys can be any value (primitives or objects), keys in a `WeakMap` must be objects.
2. **Weak references**: A `WeakMap` holds "weak" references to the keys. This means that if there are no other references to the key object, it can be garbage collected. This is not possible with `Map`, where keys are strongly referenced.
3. **Not enumerable**: A `WeakMap` does not have methods to iterate over its elements (like `forEach`, `keys`, `values`, or `entries`). You can't get a list of keys or values from a `WeakMap`.
4. **Use cases**: `WeakMap` is useful for associating data with objects in a way that doesn't prevent the garbage collector from reclaiming the memory. For example, it's often used in cases where you want to attach metadata to objects without risking memory leaks.

Example:

```javascript
let weakMap = new WeakMap();

let obj = {};
weakMap.set(obj, "value");

console.log(weakMap.get(obj)); // "value"

obj = null; // Now the object is eligible for garbage collection
```

In the above example, once `obj` is set to `null`, the entry in the `WeakMap` is automatically removed since `WeakMap` does not prevent the garbage collector from reclaiming the object.

### WeakSet

A `WeakSet` is a collection of unique objects, similar to `Set`, but with some key differences:

1. **Only objects**: Unlike `Set`, which can hold any value, `WeakSet` can only contain objects.
2. **Weak references**: The objects in a `WeakSet` are held weakly. If there are no other references to an object stored in a `WeakSet`, it can be garbage collected.
3. **Not enumerable**: A `WeakSet` does not have methods to iterate over its elements (like `forEach`, `values`, or `entries`). You can't get a list of its elements.

Example:

```javascript
let weakSet = new WeakSet();

let obj = {};
weakSet.add(obj);

console.log(weakSet.has(obj)); // true

obj = null; // Now the object is eligible for garbage collection
```

In the above example, once `obj` is set to `null`, the entry in the `WeakSet` is automatically removed because `WeakSet` does not prevent the garbage collector from reclaiming the object.

### Summary

- **WeakMap** and **WeakSet** hold weak references to their keys or values, allowing those objects to be garbage collected if there are no other references.
- **WeakMap** keys must be objects, and it is used for key/value pairs.
- **WeakSet** values must be objects, and it is used for storing unique objects.
- They do not support iteration methods and do not expose their contents, making them useful for scenarios where you need to manage object lifecycles without preventing garbage collection.