---
tags:
  - javascript
  - typescript
  - parameters
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses different types of parameters.
Status: Done
Started: 
EditDate: 2024-03-02
Relates: 
Peer Reviewed: 0
dg-publish: false
---
### Optional Parameters:

In TypeScript, you can explicitly indicate that a parameter is optional by adding a `?` after its name. This informs TypeScript that the parameter is allowed to be `undefined` and doesn't always need to be provided.

```typescript
function greet(name?: string) {
  console.log(`Hello, ${name || 'Anonymous'}!`);
}

greet(); // Outputs: Hello, Anonymous!
```

In this example, the `name` parameter is marked as optional with `?`, allowing the function to be called without any arguments. If no argument is provided, `name` defaults to `'Anonymous'`.

### Default Parameters:

Default parameters in TypeScript allow you to assign a default value directly in the function signature. TypeScript infers the variable type based on the default value's type.

```typescript
function greet(name: string = 'Anonymous') {
  console.log(`Hello, ${name}!`);
}
```

This function can receive a `string` or `undefined` as its `name` parameter. TypeScript infers the type based on the default value.

```typescript
function proclaim(status = 'not ready...', repeat = 1) {
  for (let i = 0; i < repeat; i += 1) {
    console.log(`I'm ${status}`);
  }
}

proclaim();
proclaim('ready?');
proclaim('ready!', 3);
```

In the `proclaim` function, `status` and `repeat` are optional parameters with default values. TypeScript infers their types based on the default values provided.

### JavaScript Optional Arguments:

JavaScript is lenient with the number of arguments passed to a function. TypeScript inherits this behavior. While it allows flexibility, it may lead to accidental errors when the wrong number of arguments is provided.

```javascript
function minus(a, b) {
  if (b === undefined) return -a;
  else return a - b;
}

console.log(minus(10));       // Outputs: -10
console.log(minus(10, 5));    // Outputs: 5
```

Here, the `minus` function acts on either one or two arguments. If the second argument (`b`) is not provided, it defaults to `undefined`.

### Power Function with Default Parameter:

Default parameters in TypeScript offer a concise way to make function parameters optional.

```typescript
function power(base: number, exponent: number = 2) {
  let result = 1;
  for (let count = 0; count < exponent; count++) {
    result *= base;
  }
  return result;
}

console.log(power(4));   // Outputs: 16
console.log(power(2, 6)); // Outputs: 64
```

In the `power` function, the `exponent` parameter is optional, defaulting to `2` if not provided. This allows the function to behave like a square if only the `base` is given.