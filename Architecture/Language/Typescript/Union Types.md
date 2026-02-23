---
tags:
  - typescript
  - types
  - FunctionTypes
  - javascript
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses type narrowing and union types.
Status: Refinement
Started: 
EditDate: 2024-03-02
Relates: 
Peer Reviewed: 0
dg-publish:
---
The pipe symbol (|) in TypeScript is used to create unions, allowing a variable to have multiple possible types. For instance, `number | string | boolean` represents a type that can be a number, a string, or a boolean.

### Variable Typing and Unions

TypeScript provides flexibility in typing variables with different levels of specificity. Forcing a variable to be a specific type, such as `string`, is a highly specific approach, while using `any` allows any type, making it less specific. However, sometimes a balance is needed, as seen in scenarios where a variable can be either a string or a number.

```typescript
let ID: string | number;

ID = 1;       // number
ID = '001';   // string

console.log(`The ID is ${ID}.`);
```

Here, `string | number` defines a union, allowing `ID` to be either a string or a number, providing flexibility without resorting to the overly broad `any` type.

### Type Narrowing with Unions

Type narrowing, or type narrowing, is the ability of TypeScript to infer more specific types based on the surrounding code. For example, within a function, TypeScript can distinguish between a string and a number in a union:

```typescript
function formatValue(value: string | number) {
  if (typeof value === 'string') {
    console.log(value.toLowerCase());
  }
  if (typeof value === 'number') {
    console.log(value.toFixed(2));
  }
}

formatValue('Hiya');
formatValue(42);
```

Here, the `typeof` operator is used for type narrowing, allowing specific operations based on the actual type of the variable. This is known as type guard.

### Type Guards

TypeScript employs type guards to narrow down variable types using conditional statements that check for specific types. One commonly used type guard is `typeof`. For instance:

```typescript
function formatStatistic(stat: string | number) {
  if (typeof stat === 'number') {
    return stat.toFixed(2);
  }
  if (typeof stat === 'string') {
    return stat.toUpperCase();
  }
}
```

Here, TypeScript uses `typeof` as a type guard to determine whether `stat` is a `'number'` or a `'string'` at runtime.

### Using `in` with Type Guards

The `in` operator serves as a type guard when checking for the existence of a property on an object or within its prototype chain. For example:

```typescript
type Tennis = {
  serve: () => void;
}

type Soccer = {
  kick: () => void;
}

function play(sport: Tennis | Soccer) {
  if ('serve' in sport) {
    return sport.serve();
  }
  if ('kick' in sport) {
    return sport.kick();
  }
}
```

Here, TypeScript uses `in` to check for the presence of the `'serve'` property, narrowing down the type within the conditional block.

### Type Narrowing with `else`

TypeScript recognizes the `else` block of an `if/else` statement as the opposite type guard check of the `if` statement's type guard check. For example:

```typescript
function formatPadding(padding: string | number) {
  if (typeof padding === 'string') {
    return padding.toLowerCase();
  } else {
    return `${padding}px`;
  }
}
```

In this case, TypeScript infers that `padding` is a `'number'` within the `else` block since it was determined to be a `'string'` in the preceding `if` statement.

### Type Narrowing After a Type Guard

TypeScript's type inference extends beyond an `else` block. If there's a return statement within a type guard, TypeScript can infer types without needing an `else` statement. For example:

```typescript
type Tea = {
  steep: () => string;
}

type Coffee = {
  pourOver: () => string;
}

function brew(beverage: Coffee | Tea) {
  if ('steep' in beverage) {
    return beverage.steep();
  }
  return beverage.pourOver();
}
```

Here, TypeScript immediately infers that the code following the conditional must be of type `Coffee` after encountering the `return` statement within the `if` block.

These examples illustrate how TypeScript's type narrowing enhances type safety by dynamically inferring specific types based on the actual execution of code.


### Unions and Inferred Return Types

TypeScript can infer return types for functions by examining the function's content. If a function can return multiple types, TypeScript will infer a union of those types.

```typescript
type User = {
  id: number;
  username: string;
};

function createUser(): User | string {
  const randomChance = Math.random() >= 0.5;
  if (randomChance) {
    return { id: 1, username: 'nikko' };
  } else {
    return 'Could not create a user.';
  }
}

const userData: string | User = createUser();
```

Here, `createUser()` can return either a `User` type or a `string` type, and TypeScript automatically infers the union type `User | string` for `userData`.

### Unions with Arrays

Unions become powerful when combined with arrays. For instance, an array can be defined to accept both string and number types:

```typescript
const timesList: (string | number)[] = [dateNumber, dateString];
```

This array can hold values of either string or number types, providing flexibility while maintaining type safety.

### Unions with Literal Types

Literal types can be used in unions to create distinct states within a program. For example, controlling stoplights:

```typescript
type Color = 'green' | 'yellow' | 'red';

function changeLight(color: Color) {
  // ...
}
```

Here, `Color` is a union of literal types, ensuring that only valid stoplight colors are passed to the `changeLight()` function.

### Handling Common Key Value Pairs

When using union types, TypeScript enforces using common methods and properties shared by all members. For instance:

```typescript
const batteryStatus: boolean | number = false;

batteryStatus.toString(); // No TypeScript error
batteryStatus.toFixed(2); // TypeScript error
```

This applies to type objects as well, where only shared properties and methods are allowed.

### Unions with Literal Types for Distinct States

Literal types in unions help create specific states, enhancing code clarity and reducing error-prone scenarios:

```typescript
type Status = 'idle' | 'downloading' | 'complete';

function downloadStatus(status: Status) {
  // ...
}

downloadStatus('complete');
```

In this example, `Status` is a union of literal types, ensuring that only specified states can be used with the `downloadStatus()` function.