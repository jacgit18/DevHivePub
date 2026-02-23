---
tags:
  - javascript
  - typescript
  - interfaces
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses the difference between interfaces and types.
Status: Done
Started: 
EditDate: 2024-03-02
Relates: 
Peer Reviewed: 0
dg-publish:
---
```typescript
// Defining a type
type Student = {
  name: string;
  age: number;
};

// Defining an interface
interface Teacher {
  name: string;
  age: number;
}
```

**Differences between Types and Interfaces in TypeScript:**

1. **Declaration Merging:**
   - **Interface:** Supports declaration merging. Multiple interfaces with the same name are automatically merged into a single interface.
     ```typescript
     interface Teacher {
       name: string;
     }

     interface Teacher {
       age: number;
     }

     interface Teacher {
       subject: string;
     }

     const teacher: Teacher = {
       name: "John",
       age: 30,
       subject: "Mathematics",
     };
     ```
   - **Type:** Does not support declaration merging. Attempting to merge types with the same name results in a compilation error.

2. **Computed Properties:**
   - **Type:** Supports computed properties, allowing for dynamic generation of property names in an object literal. Useful when dealing with data structures like API responses where the exact set of properties is not known beforehand.
     ```typescript
     type Student = {
       name: string;
       age: number;
       [key: string]: unknown; // Computed property
     };

     const student: Student = {
       name: "John",
       age: 30,
       address: "123 ABC", // Computed property
       phone: "111-111-1111", // Computed property
     };
     ```
   - **Interface:** Does not support computed properties. Interfaces require a known set of properties defined at compile time.

3. **Extend and Implement:**
   - **Type:** Can use the `&` operator for intersection types to extend types.
     ```typescript
     type Person = {
       name: string;
       age: number;
     };

     type Employee = Person & {
       role: string;
     };
     ```
   - **Interface:** Uses the `extends` keyword to extend other interfaces and `implements` for class implementation.

4. **Extensibility:**
   - **Type:** More flexible and extensible. Can represent union types, intersection types, and more.
   - **Interface:** Generally used for describing the shape of objects. Well-suited for traditional OOP scenarios.

In summary, while both `type` and `interface` can be used to define object shapes, they have nuanced differences. `type` provides more flexibility, including support for computed properties and union types, whereas `interface` is more suited for traditional OOP scenarios with a focus on defining object structures. The choice between them often depends on the specific use case and coding style preferences.