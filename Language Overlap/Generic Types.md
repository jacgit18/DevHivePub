---
tags:
  - Generics
  - languageOverlap
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Generics in typescript.
Status: Done
Started: 
EditDate: 2024-03-04
Relates: 
Peer Reviewed: 0
dg-publish:
---
**Understanding TypeScript Generics:**

In TypeScript, generics offer a way to create collections of types, including typed functions, that share common formal traits. These collections are parameterized by one or more type variables. A practical example of generics is the array type syntax `Array<T>`, allowing substitution of any type (pre-defined or custom) for `T`.

```typescript
type Family<T> = {
  parents: [T, T];
  mate: T;
  children: T[];
};

let aStringFamily: Family<string> = {
  parents: ['stern string', 'nice string'],
  mate: 'string next door',
  children: ['stringy', 'stringo', 'stringina', 'stringolio']
};
```

In this example, `Family<T>` defines a collection of object types, with `T` representing different types. Substituting `T` with `string`, `Family<string>` mirrors the object type `{parents:[string,string], mate:string, children: string[]}`.

**Generic Functions:**

Generics extend to functions, addressing challenges such as specifying the return type for functions that work with various data types. For instance:

```typescript
function getFilledArray<T>(value: T, n: number): T[] {
  return Array(n).fill(value);
}

let stringArray: string[];
let numberArray: number[];
let personArray: { name: string, age: number }[];
let coordinateArray: [number, number][];

stringArray = getFilledArray<string>('hi', 6);
numberArray = getFilledArray<number>(9, 6);
personArray = getFilledArray<{name: string, age: number}>({ name: 'J. Dean', age: 24 }, 6);
coordinateArray = getFilledArray<[number, number]>([3, 4], 6);
```

Here, `getFilledArray<T>` ensures that `value` and the returned array have the same type `T`. This way, the function is correctly typed and less prone to errors.

**Generic Naming Conventions:**

When using generic identifiers like `<T>`, it's common to choose identifiers that provide clarity about their purpose within the code:

- `<T>`: Represents any type.
- `<E>`: Denotes the element type in data structures.
- `<N>`: Refers to the number type, often used in mathematical contexts.
- `<V>`: Stands for value, representing a general value.
- `<K>`: Commonly used for keys in key-value pairs.

This naming convention enhances code readability by offering meaningful hints about the role or purpose of the generic type within the code.