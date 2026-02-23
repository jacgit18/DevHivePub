---
tags:
  - security
  - javascript
  - CodebaseDecision
  - vulnerability
  - FunctionTypes
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses unsafe function in code.
Status: Done
Started: 2023-11-21
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish: false
---
Unsafe functions in JavaScript can lead to security vulnerabilities and unexpected behavior. Here are some examples of potentially unsafe functions and practices:

1. **eval():**
   ```javascript
   const userInput = 'alert("Unsafe!")';
   eval(userInput); // Executes arbitrary code provided by the user
   ```

   Using `eval()` can introduce security risks by executing code dynamically. It's advisable to avoid its usage, especially with untrusted input. also some libraries may use eval so you need to be careful with what libraries you use. 

2. **innerHTML:**
   ```javascript
   const userContent = '<img src=x onerror=alert("Unsafe!")>';
   document.getElementById('container').innerHTML = userContent; // Injects unescaped HTML
   ```

   Manipulating `innerHTML` with untrusted data can lead to Cross-Site Scripting (XSS) vulnerabilities. Instead, use methods like `textContent` or `createElement` to manipulate content safely.

3. **Function Constructor:**
   ```javascript
   const userInput = 'alert("Unsafe!")';
   const unsafeFunction = new Function(userInput);
   unsafeFunction(); // Dynamically creates a function from user input
   ```

   Creating functions with the `Function` constructor using user input is risky, as it allows execution of arbitrary code. Prefer using named functions and avoiding dynamic function creation.

4. **with Statement:**
   ```javascript
   const userObject = { prop: 'Unsafe!' };
   with (userObject) {
     console.log(prop); // Introduces ambiguity and can lead to unexpected behavior
   }
   ```

   The `with` statement should be avoided as it can make code harder to understand and maintain, and it may lead to unintended variable scope issues.

5. **setTimeout and setInterval with Strings:**
   ```javascript
   const userInput = 'alert("Unsafe!")';
   setTimeout(userInput, 1000); // Executes a string as code
   ```

   Passing a string to `setTimeout` or `setInterval` can lead to code injection. Instead, pass a function to avoid potential security risks.

It's crucial to follow best practices, such as input validation, output encoding, and avoiding the use of insecure functions, to enhance the security of JavaScript applications.