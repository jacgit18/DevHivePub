---
tags:
  - javascript
  - Framework
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Express.js.
Status: Done
Started: 
EditDate: 2024-02-06
Relates: 
Peer Reviewed: 0
dg-publish: true
---
Express.js is a minimal and flexible [[Node.js]] web application framework that provides a set of robust features to develop web and mobile applications. It simplifies the process of building web servers and handling HTTP requests by offering a straightforward, unopinionated structure.

Key features of Express.js include:

1. **Routing:** Express facilitates the creation of routes, defining how the application responds to specific HTTP requests at designated endpoints.

2. **Middleware:** It allows the use of middleware functions to perform tasks during the request-response cycle, such as logging, authentication, or modifying the request or response objects.

3. **Template Engines:** Express supports various template engines, enabling the dynamic generation of HTML on the server side.

4. **HTTP Utility Methods:** It provides methods to handle various HTTP methods like GET, POST, PUT, and DELETE, making it easier to handle different types of requests.

5. **Static File Serving:** Express can serve static files, such as images, stylesheets, and scripts, simplifying the integration of these assets into the application.

6. **Extensibility:** Express is extensible, allowing developers to integrate additional modules or middleware to enhance functionality.

Overall, Express.js is widely used for building scalable and maintainable web applications, offering developers the flexibility to structure their projects according to their needs.

## Route Handlers
Express route handlers enable the use of multiple callback functions, resembling [middleware](http://expressjs.com/en/guide/using-middleware.html), to manage requests. An exception is the ability to invoke `next('route')`, skipping subsequent route callbacks. This mechanism is valuable for applying pre-conditions to a route, allowing control to pass to subsequent routes if continuing with the current route is unnecessary. Route handlers can take the form of a function, an array of functions, or a combination of both, providing flexibility in implementation, as illustrated in the examples below.

Code snippets for handling routes in Express:

1. Single callback function:
```javascript
app.get('/example/a', (req, res) => {
  res.send('Hello from A!');
});
```

2. Multiple callback functions with `next`:
```javascript
app.get('/example/b', (req, res, next) => {
  console.log('The response will be sent by the next function...');
  next();
}, (req, res) => {
  res.send('Hello from B!');
});
```

3. Array of callback functions:
```javascript
const cb0 = (req, res, next) => {
  console.log('CB0');
  next();
};

const cb1 = (req, res, next) => {
  console.log('CB1');
  next();
};

const cb2 = (req, res) => {
  res.send('Hello from C!');
};

app.get('/example/c', [cb0, cb1, cb2]);
```

4. Combination of independent functions and arrays:
```javascript
const cb0 = (req, res, next) => {
  console.log('CB0');
  next();
};

const cb1 = (req, res, next) => {
  console.log('CB1');
  next();
};

app.get('/example/d', [cb0, cb1], (req, res, next) => {
  console.log('The response will be sent by the next function...');
  next();
}, (req, res) => {
  res.send('Hello from D!');
});
```