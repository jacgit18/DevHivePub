---
tags:
  - security
  - javascript
  - web
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses prototype pollution.
Status: Refinement
Started: 2023-11-21
EditDate: 
Relates: "[[Prototypes]]"
Peer Reviewed: 0
dg-publish: false
---
Prototype pollution is a security vulnerability in JavaScript that occurs when an attacker manipulates the prototype of an object to introduce or modify properties and methods. This can have unintended consequences, leading to security risks. Here's an explanation of prototype pollution:

### Understanding Prototype Pollution:

1. **Prototypes in JavaScript:**
   JavaScript is a prototype-based language, meaning objects can inherit properties and methods from other objects through their prototypes. Each object, including functions, has a prototype from which it inherits. You also should watch out for libraries because they could have prototype pollution and [[Unit Testing]] is good for detecting pollution.

2. **Object Prototype Manipulation:**
   Attackers exploit the ability to manipulate an object's prototype to inject or modify properties at a broader scope. If an object's prototype is altered, the changes affect all instances derived from that prototype.

### Example of Prototype Pollution:

Consider the following example:

```javascript
// Initial object
const baseObject = {};

// User input with potential pollution
const userInput = '{"__proto__": {"polluted": true}}';
const userObject = JSON.parse(userInput);

// Extending the base object with user input
Object.assign(baseObject, userObject);

// Now baseObject inherits the polluted property
console.log(baseObject.polluted); // Outputs: true
```

In this example, the user manipulates the prototype using the `__proto__` property, introducing a `polluted` property to all objects derived from `baseObject`.

### Risks and Consequences:

1. **Unintended Property Overwrites:**
   Prototype pollution can lead to unintended overwrites of existing properties or the introduction of malicious properties. This can result in unexpected behavior and security vulnerabilities.

2. **Security Implications:**
   If sensitive properties or methods are affected, an attacker could compromise the integrity and security of the application. This is particularly dangerous in environments where user input is not properly validated.

### Mitigating Prototype Pollution:

1. **Input Validation:**
   Ensure that user inputs, especially those derived from external sources, are properly validated and sanitized to prevent malicious input.

2. **Immutable Objects:**
   Use immutable objects where possible to avoid unintentional modifications. Libraries like `Object.freeze` can help make objects immutable.

3. **Property Whitelisting:**
   Explicitly define the properties that an object can have, preventing unexpected additions through prototype pollution.

4. **Security Tooling:**
   Employ security tools and static analysis to detect and prevent prototype pollution vulnerabilities in the codebase.

Understanding and mitigating prototype pollution is crucial for building secure JavaScript applications. Developers should be vigilant in validating and sanitizing user inputs to prevent such vulnerabilities.
