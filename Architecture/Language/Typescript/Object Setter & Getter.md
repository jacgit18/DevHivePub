---
tags:
  - javascript
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Object Setter & Getter.
Status: Done
Started: 
EditDate: 2024-03-02
Relates: 
Peer Reviewed: 0
dg-publish:
---
### Harnessing the Power of Getters and Setters in JavaScript

In JavaScript, getters and setters provide a powerful mechanism to control access to object properties. They enable you to customize the behavior of reading and writing properties, introducing flexibility and encapsulation in your code.

#### **Reading with Getters:**

```javascript
const obj = {
  log: ['a', 'b', 'c'],
  get latest() {
    if (this.log.length === 0) {
      return undefined;
    }
    return this.log[this.log.length - 1];
  }
};

console.log(obj.latest);
// Expected output: "c"
```

In this example, the `latest` property is a getter. When accessed, it returns the last element of the `log` array. If the array is empty, it gracefully returns `undefined`.

#### **Writing with Setters:**

```javascript
const language = {
  set current(name) {
    this.log.push(name);
  },
  log: []
};

language.current = 'EN';
language.current = 'FA';

console.log(language.log);
// Expected output: Array ["EN", "FA"]
```

The `current` property is a setter in this case. When a value is assigned to `language.current`, the setter function is invoked, pushing the provided value into the `log` array. This allows you to perform actions or validations when setting a property.

#### **Understanding Getters and Setters:**

- **Getters:**
  - Used to retrieve the value of an object property.
  - Defined using the `get` keyword followed by the property name.
  - Executed when the property is accessed.

- **Setters:**
  - Used to set the value of an object property.
  - Defined using the `set` keyword followed by the property name.
  - Executed when a value is assigned to the property.

#### **Practical Applications:**

- **Validation in Setters:**
  - Setters provide an opportunity to validate incoming values before setting them.

- **Computed Properties with Getters:**
  - Getters allow the creation of computed properties based on existing ones.

#### **Example: Computed Property with Getter:**

```javascript
const rectangle = {
  width: 5,
  height: 10,
  get area() {
    return this.width * this.height;
  }
};

console.log(rectangle.area);
// Expected output: 50
```

In this example, the `area` property is a getter that computes and returns the area of the rectangle based on its `width` and `height`.

#### **Conclusion:**

Getters and setters bring a new level of control and customization to object properties in JavaScript. Whether you need to perform actions when reading or writing properties, validate values, or create computed properties, getters and setters empower you to write more expressive and robust code.