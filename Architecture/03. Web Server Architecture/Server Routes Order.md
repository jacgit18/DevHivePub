---
tags:
  - routes
  - servers
  - OrderOfOperations
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses the order of operations for server routes.
Status: Done
Started: 
EditDate: 2024-03-06
Relates: 
Peer Reviewed: 0
dg-publish:
---
The order in which you define routes can matter. Express processes routes sequentially, and the first matching route is the one that will be executed. Therefore, the order in which you define your routes determines their priority.  
  
Consider the following example:  
  
```javascript  
const express = require('express');  
const app = express();  
  
app.get('/users/:id', (req, res) => {  
// Handle user details  
});  
  
app.get('/users/admin', (req, res) => {  
// Handle admin details  
});  
  
app.get('/users/:username', (req, res) => {  
// Handle other user details  
});  
  
app.listen(3000, () => {  
console.log('Server is running on port 3000');  
});  
```  
  
In this example, if you request `/users/admin`, it will match the first defined route (`/users/:id`) because Express interprets `admin` as a parameter for `:id`. To avoid this issue, you should define more specific routes before more generic ones:  
  
```javascript  
app.get('/users/admin', (req, res) => {  
// Handle admin details  
});  
  
app.get('/users/:id', (req, res) => {  
// Handle user details  
});  
  
app.get('/users/:username', (req, res) => {  
// Handle other user details  
});  
```  
  
Now, the `/users/admin` route will correctly match the intended handler. So, when working with Express, it's a good practice to order your routes from most specific to least specific to ensure the correct route is matched based on the incoming request.