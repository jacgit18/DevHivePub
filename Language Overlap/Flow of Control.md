---
tags:
  - CodebaseDecision
  - codeFlow
  - languageOverlap
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses flow of control for business logic.
Status: Refinement
Started: 
EditDate: 2024-03-05
Relates: 
Peer Reviewed: 0
dg-publish:
---
![[Flow of control.gif]]

The "flow of control" in computer programming refers to the order in which a program's instructions or statements are executed. It determines how a program progresses from one statement to another, making decisions, looping, and branching as necessary. Understanding the flow of control is fundamental to writing and understanding computer programs. Here are some key concepts related to the flow of control in programming:

1. **Sequential Execution**: In a simple, sequential program, statements are executed one after another in the order they appear in the code. The flow of control moves sequentially from the first statement to the last.

2. **Selection or Conditional Statements**: Conditional statements, like "if," "else if," and "else," allow the program to make decisions based on certain conditions. Depending on whether a condition is true or false, the flow of control may follow different paths.

```typescript
if (condition) {
    // Code to execute if the condition is true
} else {
    // Code to execute if the condition is false
}
```


3. **Looping or Iteration**: Looping constructs, such as "for" and "while" loops, allow a program to repeat a set of instructions multiple times until a specified condition is met. The flow of control cycles back to the beginning of the loop until the condition becomes false.

```typescript
// For loop
for (let i = 0; i < 5; i++) {
    // Code to execute in each iteration
}

// While loop
while (condition) {
    // Code to execute while the condition is true
}
```

4. **Function Calls**: When a function is called, control is transferred to the function's code. After the function completes its execution, control returns to the point in the program from which the function was called.

```typescript
function myFunction(): void {
    // Function code
}

myFunction(); // Calling the function
// Control returns here after the function finishes
```


5. **Execution Control**: Some programming languages provide ***jump/label statements*** like "break" and "continue" within loops to modify the flow of control. "Break" exits a loop prematurely, while "continue" skips the current iteration and moves to the next.

>[!note] The break statement terminates the current loop, switch, or label statement and transfers program control to the statement following the terminated statement. 

```typescript
let text = '';

for (let i = 0; i < 10; i++) {
  if (i === 3) {
    break; // Exit the loop when i is 3
  }
  text = text + i;
}

console.log(text); // output: "012
// As a result, the loop will not continue to iterate through the remaining values (4 to 9)
```

>[!note] The continue statement terminates execution of the statements in the current iteration of the current or labeled loop, and continues execution of the loop with the next iteration. 

```typescript
let text = ''; 
//continue skips code at current code iteration in loop so when we hit 3 we dont get to add it  

for (let i = 0; i < 10; i++) { 
  if (i === 3) { 
    continue; 
  } 
  text = text + i; 
} 

console.log(text); // output: "012 4 56789"
// 3 is not appended because we skip action on that iteration


```

6. **Recursion**: In recursive functions, control flows by calling the same function within itself. Each recursive call creates a new level of control flow until a base case is reached, at which point the control flows back up through the stack of recursive calls.

```typescript
function factorial(n: number): number {
    if (n === 0) {
        return 1;
    } else {
        return n * factorial(n - 1);
    }
}
```

7. [[Exception Handling|Exception Handling]]: In cases of errors or exceptional situations, the flow of control can be redirected to an exception handling block to handle the error gracefully instead of terminating the program.

8. **Throwing Exception**: Execution of the current function will stop (the statements after throw won't be executed), and control will be passed to the first catch block in the call stack. If no catch block exists among caller functions, the program will terminate. 

```typescript
try {
    willGiveErrorSometime();
} catch (error) {
    if (error instanceof RangeError) {
        throw new RangeError('Custom RangeError Message');
    } else if (error instanceof ReferenceError) {
        throw new ReferenceError('Custom ReferenceError Message');
    } else {
        throw new Error('Custom Error Message');
    }
} finally {
    // Any cleanup or finalization code can be placed here
}
```

Understanding and managing the flow of control is essential for writing correct and efficient programs. It allows programmers to create logic that responds to different conditions, loops through data, and handles errors gracefully, enabling the execution of complex and meaningful tasks in computer programs.












