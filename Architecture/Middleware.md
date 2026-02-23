---
tags: 
author:
  - gitUserNamePlaceHolder
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: 
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
Both approaches to handling middleware in Express.js can be valid depending on the context and specific requirements of your application. Let's break down the differences and use cases for each approach.  
  
### Approach 1: Global Middleware in `app.js`  
  
```javascript  
import cors from "cors";  
import express from "express";  
import morgan from "morgan";  
import path from 'path';  
import * as routes from "./routers/index.ts";  
import { authenticateToken } from "./middlewares/index.js"  
  
const app = express()  
  
// Global Middlewares  
app.use(morgan("tiny")); // HTTP request logger  
app.use(cors());  
app.use(express.json());  
app.use(express.urlencoded({ extended: false }));  
app.use(express.static(path.join(__dirname, "static", "about.html")));  
  
// Apply middlewares globally or on specific routes  
app.use("/v1/api", routes.tvShowRouter, authenticateToken);  
  
export default app;  
```  
  
### Approach 2: Middleware at the Router Level  
  
```javascript  
import tvShowController from "../controllers/TvShowController.ts";  
import { RouterEntry, routerFactory } from "./util.ts";  
import { authenticateToken } from "./middlewares/index.js";  
  
const exampleRoutes: RouterEntry[] = [  
{  
method: 'post',  
route: '/add/show',  
middlewares: [authenticateToken],  
controllerFn: tvShowController.createShow  
},  
{  
method: 'get',  
route: '/:id',  
middlewares: [authenticateToken],  
controllerFn: tvShowController.getShowInfo  
},  
{  
method: 'put',  
route: '/:id/episodes',  
middlewares: [],  
controllerFn: tvShowController.updateFullShow  
},  
{  
method: 'patch',  
route: '/:id/ratings',  
middlewares: [],  
controllerFn: tvShowController.updatePartialShow  
},  
{  
method: 'delete',  
route: '/:id',  
middlewares: [],  
controllerFn: tvShowController.deleteShow  
}  
];  
  
export default routerFactory(exampleRoutes);  
```  
  
### Comparison  
  
#### Global Middleware (Approach 1)  
- **Simplicity**: Applying middleware globally makes the code simple and easy to manage. All requests pass through the same set of middlewares.  
- **Consistency**: Ensures all routes are uniformly subjected to the middleware. This is useful for middlewares like logging, CORS, and body parsing.  
- **Performance**: Can be slightly less performant for routes that don't need certain middlewares, as the middleware will still run for every request.  
  
#### Middleware at the Router Level (Approach 2)  
- **Granularity**: Allows you to apply middleware to specific routes only, which can be more efficient and tailored to your application’s needs.  
- **Flexibility**: You can add or remove middleware for individual routes without affecting others. This is useful when different routes have different requirements for authentication, validation, etc.  
- **Complexity**: Can introduce more complexity in managing the routes and their associated middlewares.  
  
### When to Use Each Approach  
  
- **Global Middleware**:  
- Use when the middleware should be applied to all routes (e.g., CORS, logging, body parsers).  
- Suitable for small to medium-sized applications where the routes have uniform requirements.  
  
- **Middleware at the Router Level**:  
- Use when different routes require different middlewares (e.g., some routes need authentication while others do not).  
- Suitable for larger applications where routes have varied requirements and need more control and flexibility over middleware application.  
  
### Conclusion  
  
There is no one-size-fits-all answer. In many applications, a hybrid approach is used where some middlewares are applied globally (e.g., logging, CORS, body parsing), and more specific middlewares (e.g., authentication, validation) are applied at the router or route level.  
  
Given your examples, if you have routes that require different middleware configurations, applying middleware at the router level makes sense. For common middlewares that should be applied universally, global application in `app.js` is appropriate.  
  
Combining both approaches allows you to leverage the strengths of each, ensuring your application remains both flexible and maintainable.