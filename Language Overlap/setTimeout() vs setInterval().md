---
tags:
  - asynchronous
  - codeExecution
  - functionCalls
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses setTimeout and setInterval.
Status: Done
Started: 
EditDate: 2024-03-06
Relates: 
Peer Reviewed: 0
dg-publish:
---
Timeout is a delayed call & interval is a continuous call until set time elapses.  

The global setTimeout() method sets a timer which executes a function or specified piece of code once the timer expires. 

```javascript
var timeoutID = setTimeout(function[, delay, arg1, arg2, ...]); 

var timeoutID = setTimeout(function[, delay]); 

var timeoutID = setTimeout(code[, delay]); 
```

**setTimeout()** is an asynchronous function, meaning that the timer function will not pause execution of other functions in the functions stack. In other words, you cannot use **setTimeout()** to create a "pause" before the next function in the function stack fires. 

```javascript

  setTimeout(() => {console.log("this is the first message")}, 5000); 

  setTimeout(() => {console.log("this is the second message")}, 3000); 

  setTimeout(() => {console.log("this is the third message")}, 1000); 

  // Output: 

  // this is the third message 

  // this is the second message 

  // this is the first message 
 ```

The **setInterval()** method, offered on the Window and Worker interfaces, repeatedly calls a function or executes a code snippet, with a fixed time delay between each call. 

This method returns an interval ID which uniquely identifies the interval, so you can remove it later by calling **clearInterval()**. 

```javascript
var intervalID = setInterval(func, [delay, arg1, arg2, ...]); 

var intervalID = setInterval(function[, delay]); 

var intervalID = setInterval(code, [delay]);
```