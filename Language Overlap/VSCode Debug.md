---
tags:
  - tool
  - debugging
author:
  - gitUserNamePlaceHolder
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: 
Started: 2024-11-11
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
# Debugging a Full-Stack Application in VS Code

When debugging a full-stack application in VS Code, there are several complementary approaches that can work together:

## 1. Direct Debugging with VS Code

You can set up separate debugging configurations for both the front end and back end, allowing you to debug each part directly. For example, you might configure two launch configurations in your `launch.json`:

- One to start and attach to your backend server (e.g., a Node.js server).
- Another to launch and debug the front end (often via Chrome Debugging for web apps).

With this setup, you can set breakpoints, inspect variables, and step through the code directly. This approach is ideal for debugging issues that occur at runtime but may require initial configuration.

## 2. Debugging with Console Logs

Many developers, even those with a debugger set up, add `console.log` statements, especially for quick insights or to trace function calls and variables. Logs can be particularly useful when dealing with asynchronous operations or callbacks that might be harder to inspect with a debugger alone.

## 3. Using Testing Infrastructure for Debugging

If you have tests set up (e.g., Jest for unit and integration testing on the front end, or Mocha for backend testing), you can debug those tests directly.

- In VS Code, you can attach the debugger to your test runner by setting breakpoints in your tests or in the code that your tests execute. 
- This helps you test isolated parts of the application and is often easier to set up than debugging the whole stack at once.

Running tests while debugging provides repeatable conditions to identify and fix issues without manually reproducing scenarios.

## 4. Connecting Front-End and Back-End Debugging

For debugging issues where front-end and back-end interactions are involved, you might want to launch both the front-end and back-end debuggers simultaneously. This setup allows you to see how front-end requests are handled by the back end and step through code on both sides.

## 5. Test Debugging vs. Application Debugging

Testing frameworks (like Jest, Mocha) let you simulate and check different parts of the application in isolation, which is often helpful for validating functionality in specific, isolated parts.

- **Test Debugging**: Useful for validating specific units or isolated functionality.
- **Application Debugging**: More suitable when investigating issues that involve multiple components working together.

## Summary

Generally, using a combination of the debugger, console logs, and test debugging gives you flexibility and more visibility across the stack. The approach you choose can depend on the issue—console logs for quick traces, test debugging for isolated unit issues, and direct debugging for runtime behavior across the stack.


# Debugging and Testing a Full-Stack Application in VS Code

Testing a full-stack application in VS Code is more complex than testing isolated functions, but there are effective ways to debug both the front-end and back-end parts of your application in a controlled manner. Here’s a step-by-step approach:

## 1. Setting Up the Debugger for Both Front and Back End

### Backend Debugging:
1. Ensure your backend server (e.g., Node.js) is running.
2. In VS Code, go to the **Debug** tab (or hit `Ctrl + Shift + D`) and open the `launch.json` file.
3. Add a new debug configuration for the backend:

```json
{
  "type": "node",
  "request": "launch",
  "name": "Launch Backend",
  "program": "${workspaceFolder}/path/to/server.js",
  "outFiles": ["${workspaceFolder}/**/*.js"]
}
```

With this setup, you can set breakpoints in your backend code, start the debugger, and inspect how requests and responses are processed.

### Frontend Debugging:
If you're working with a JavaScript front end (e.g., React, Vue, or Angular), add another configuration for **Chrome Debugging** in the same `launch.json` file:

```json
{
  "type": "chrome",
  "request": "launch",
  "name": "Launch Frontend",
  "url": "http://localhost:3000", // replace with your front-end's local dev URL
  "webRoot": "${workspaceFolder}/path/to/frontend/src"
}
```

This will open a Chrome instance and attach the debugger. You can now set breakpoints in your front-end code and inspect state, variables, and function calls.

## 2. Running Integration Tests in VS Code

### Setting Up a Test Runner:
Use a test framework like **Jest** for JavaScript projects (or Mocha for the backend). In your test files, set up integration tests that simulate real-world interactions, such as making HTTP requests from the front end to the back end.

VS Code has extensions for Jest and Mocha, allowing you to view test results and debug tests by setting breakpoints within the test files.

### Debugging Tests:
Create another debug configuration to launch the test runner with breakpoints. For Jest, this would look like:

```json
{
  "type": "node",
  "request": "launch",
  "name": "Debug Jest Tests",
  "program": "${workspaceFolder}/node_modules/.bin/jest",
  "args": ["--runInBand"],
  "console": "integratedTerminal",
  "internalConsoleOptions": "neverOpen"
}
```

This setup allows you to run tests and pause execution at breakpoints in your code, helping you isolate issues in specific parts of your full-stack application without running the entire stack.

## 3. Testing Full Application Flow (E2E Testing)

### End-to-End (E2E) Testing:
For full application flow, consider using tools like **Cypress** or **Playwright** for E2E testing. These tools simulate real user actions by opening a browser and interacting with the application as a user would.

You can configure VS Code to debug Cypress tests by using a Cypress VS Code extension or setting up a `launch.json` configuration.

Set up your E2E tests to cover critical paths like logging in, navigating to specific pages, or submitting a form. E2E tests verify that both the frontend and backend communicate correctly under real usage scenarios.

## 4. Running and Debugging the Full Stack Together

Once you have debugging configurations for both the front end and back end, you can run them simultaneously in VS Code:

1. Open the **Debug** panel.
2. Instead of running a single debug configuration, select **Add Configuration...** to run multiple configurations.
3. Run both the front-end and back-end debuggers side by side. Start with your backend debugger, and once it’s running, start the frontend debugger.

This approach allows you to trace the full flow between the front end and back end, automatically processing actions triggered from the front end by the backend.

## 5. Using Console Logs as a Supplement

Console logs are often useful for tracking variable values or quick tests, especially in asynchronous functions or areas where the debugger can be tricky to use.

Add logs to both your front-end and back-end code for additional visibility. This helps track data flow or inspect requests and responses at each step of the application.

---

By combining direct debugging configurations, test frameworks, and E2E tests, you can cover a wide range of debugging needs in VS Code for your full-stack application.


# The `debugger` Command

You can pause the execution of your code using the `debugger` command. Here's an example:

```javascript
function hello(name) {
  let phrase = `Hello, ${name}!`;

  debugger;  // <-- the debugger stops here

  say(phrase);
}
```

The `debugger` command works only when the development tools (DevTools) are open. If they are closed, the browser will ignore the command.

---

# How to Get the Query String in Vanilla JavaScript

### Example 1: Basic Query String

Given a URL like `index.php?keyword=Search Text&click=Submit`, you can extract the `keyword` parameter like this:

```javascript
var objUrlParams = new URLSearchParams(window.location.search);
console.log(objUrlParams.get('keyword')); // “Search Text”
```

### Example 2: Checking for Parameters

You can check whether certain query parameters exist with `has`:

```javascript
var objUrlParams = new URLSearchParams(window.location.search);
console.log(objUrlParams.has('order')); // “false” 
console.log(objUrlParams.has('click')); // “true”
```

### Example 3: Getting All Values for a Parameter

If there are multiple values for the same parameter (e.g., `filter`), you can get them using `getAll`:

```javascript
var objUrlParams = new URLSearchParams(window.location.search);
console.log(objUrlParams.getAll('filter')); // [“value1”, “value2”]
```