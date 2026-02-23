---
tags:
  - javascript
author:
  - jacgit18
  - chatgpt
Purpose: This documentation explain `this` keyword.
Status: Done
Started: 
EditDate: 2024-02-26
Relates: 
Peer Reviewed: 0
dg-publish:
---
In JavaScript, the `this` keyword is dynamic, depending on its invocation context. Key points include:

- **In Object Methods:**
  - `this` refers to the object calling the method.

- **Alone or in a Function:**
  - In a function alone, `this` points to the global object.
  - In a function within strict mode, `this` is `undefined`.

- **In Events:**
  - In an event handler, `this` refers to the element receiving the event.

- **Methods like `call()`, `apply()`, and `bind()`:**
  - These methods allow explicit setting of `this` to any object.

Understanding these principles is crucial for effective use of the `this` keyword. For instance, in a method, `this` represents the object invoking the method. In contrast, when used in a standalone function, it refers to the global object. Special considerations apply in strict mode and event handlers.

### Code Snippets:

#### 1. Object Methods:
```javascript
const video = {
  title: 'a',
  play() {
    console.log(this); // Refers to the video object
  },
};

video.play(); // Prints the video object
```

#### 2. Function and Global Object:
```javascript
function playvid() {
  console.log(this); // Refers to the global object (window in a browser)
}

playvid(); // Prints the global object

function Video(title) {
  this.title = title;
  console.log(this); // Logs a new empty object called Video with title
}

const v = new Video('b'); // Logs a new object with title
```

#### 3. Event Handler and Arrow Function:
```javascript
const video = {
  title: 'a',
  tag: ['a', 'b', 'c'],
  showTag() {
    this.tag.forEach(function(tag) {
      console.log(this.title); // Prints undefined in strict mode, or window in non-strict
      console.log(this.title, tag);
    }, this); // Sets 'this' to the video object within the forEach callback
  },
};

video.showTag(); // Prints tags with the video title

const vid = video.showTag.bind(video); // Creates a new instance with 'this' set to video
vid(); // Prints tags with the video title
```

These snippets illustrate how the `this` keyword behaves in different contexts, emphasizing its dynamic nature in JavaScript.