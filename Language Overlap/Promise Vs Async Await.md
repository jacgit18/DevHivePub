---
tags:
  - asynchronous
  - promises
  - FunctionTypes
  - codeExecution
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses promises and async functions.
Status: Refinement
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
A Promise in NodeJS mirrors the concept of a promise in real life, providing an assurance that a specific task will be completed. It serves to track the execution status of asynchronous events and dictates the course of action post-event completion. A promise object encompasses three states:

- **PENDING:** The initial state before the event has occurred.
- **RESOLVED:** The state after a successful operation.
- **REJECTED:** The state when an error occurs during execution, causing the promise to fail.

Async functions return promises, allowing the use of chaining methods like `.then()` and `.catch()` for error handling.

When handling promises, `.then()` is used for successfully resolved promises, `.catch()` for rejected promises, and `.finally()` for code execution regardless of the promise's state.

```javascript
const promise = new Promise(function (resolve, reject) {
  const string1 = "geeksforgeeks";
  const string2 = "geeksforgeeks";
  if (string1 === string2) resolve();
  else reject();
});

promise
  .then(function () {
    console.log("Promise resolved successfully");
  })
  .catch(function () {
    console.log("Promise is rejected");
  });
```

The Promise API facilitates promise chaining for handling multiple asynchronous functions in sequence. `Promise.all()` is used when all promises need to be fulfilled, and `Promise.any()` is employed when any one of a set of promises should be fulfilled.

```javascript
// Example using Promise.all()
Promise.all([fetchPromise1, fetchPromise2, fetchPromise3])
  .then(responses => {
    for (const response of responses) {
      console.log(`${response.url}: ${response.status}`);
    }
  });

// Example using Promise.any()
Promise.any([fetchPromise1, fetchPromise2, fetchPromise3])
  .then(response => {
    console.log(`${response.url}: ${response.status}`);
  })
  .catch(error => {
    console.error(`Failed to fetch: ${error}`);
  });
```


## Alt Example 
```javascript
// Create a promise with resolve and reject functions
var porm = new Promise((resolve, reject) => {
    setTimeout(() => {
        // Uncomment either resolve() or reject() to test
        // resolve();
        reject();
    }, 2000);
});

// Function to be executed on success
function succ() {
    console.log('Success!');
}

// Function to be executed on error
function err() {
    console.log('Error!');
}

// Handle promise using .then() for success and .catch() for error
porm.then(succ).catch(err);

// Using async function with await to handle promise
async function handlePromise() {
    try {
        await porm;
        succ();
    } catch (error) {
        err();
    }
}

// Uncomment the line below to test async/await
// handlePromise();
```

In this example, a promise (`porm`) is created with `resolve` and `reject` functions. Depending on whether `resolve` or `reject` is called, the promise will either be fulfilled (success) or rejected (error). The `.then()` method is used to handle success, and the `.catch()` method is used to handle errors. Additionally, the code includes an async function (`handlePromise`) using `async/await` to demonstrate an alternative way of handling promises with error handling.



For more detailed information on promises, async/await, and fetch in modern JavaScript, refer to the following resources:

- [Promises, Async/Await, and Fetch: Network Requests in Modern JavaScript](https://medium.com/swlh/promises-async-await-and-fetch-network-requests-in-modern-javascript-fd0b2b384f3e)
- [MDN Web Docs: Async/await](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Async_await)
- [MDN Web Docs: Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)