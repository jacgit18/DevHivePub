---
tags:
  - CodingProblem
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses leetcode 20 checking for valid parentheses.
Status: Done
Started: 
EditDate: 2024-02-29
Relates: "[[Map]]"
Peer Reviewed: 0
dg-publish:
---
```javascript
function isWellFormed(expression) {
  const stack = [];

  const openingSymbols = { '(': ')', '[': ']', '{': '}' };

  for (const char of expression) {
    if (char in openingSymbols) {
      // It's an opening symbol, push onto the stack
      stack.push(char);
    } else {
      // It's a closing symbol
      const lastOpeningSymbol = stack.pop();

      // Check if the last opening symbol matches the current closing symbol
      if (openingSymbols[lastOpeningSymbol] !== char) {
        return false; // Mismatch
      }
    }
  }

  // The expression is well-formed if the stack is empty at the end
  return stack.length === 0;
}

// Example usage:
console.log(isWellFormed("()")); // Output: true
console.log(isWellFormed("()[]{}")); // Output: true
console.log(isWellFormed("(]")); // Output: false
console.log(isWellFormed("([)]")); // Output: false
console.log(isWellFormed("{[]}")); // Output: true
```

Alt
```javascript
// Creating a bracket map using Map
const bracketMap = new Map([
  ['(', ')'],
  ['[', ']'],
  ['{', '}'],
  // Add more brackets as needed
]);

// Example usage for matching brackets
function isBracketMatch(str) {
  const stack = [];
  for (const char of str) {
    if (bracketMap.has(char)) {
      stack.push(char);
    } else if (bracketMap.values().includes(char) && bracketMap.get(stack.pop()) !== char) {
      return false;
    }
  }
  return stack.length === 0;
}
```


This function takes a string `expression` as input and checks if the parentheses or brackets in the expression are well-formed. It uses a stack to keep track of opening symbols and pops from the stack when encountering closing symbols, ensuring proper nesting.





**Undo Mechanism Example:**
- In a coding challenge scenario, implementing an Undo Mechanism using a stack can be a powerful solution. Consider a scenario where you need to manage a sequence of operations, and the ability to undo each operation is crucial. This is where a stack comes into play.

**Example Scenario:**
- Imagine you are tasked with creating a text editor application in a coding challenge. Users can perform various operations like editing text, inserting images, or deleting paragraphs. To implement an efficient Undo Mechanism, you can use a stack to keep track of each operation. For instance, you might push each operation onto the stack as it occurs (e.g., editing text or inserting an image), and undoing an action involves popping the last operation from the stack.

**Coding Approach:**
- Utilizing a stack, you can easily implement undo functionality by popping the last operation from the stack. For instance, in JavaScript, you might use the `pop` method to undo the last action or `unshift` to redo the action.

**Example Code Snippet:**
```javascript
const simplifyPath = (path) => {
  const parts = path.split('/').filter(part => part !== ''); // Remove empty parts
  const stack = [];

  for (let part of parts) {
    if (part === '.') {
      continue; // Skip current directory markers
    } else if (part === '..') {
      stack.pop(); // Move one level up if encountering '..'
    } else {
      stack.push(part); // Push valid directory names to stack
    }
  }

  return '/' + stack.join('/');
};
```


In this example, the stack-based Undo Mechanism provides an elegant solution for managing and reverting operations, a common requirement in various coding challenges.


