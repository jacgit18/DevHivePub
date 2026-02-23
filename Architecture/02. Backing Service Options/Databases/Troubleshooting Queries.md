---
tags:
  - debugging
  - troubleshooting
  - query
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses how to debug database queries with built in string methods.
Status: Done
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish: false
---
When debugging Knex.js queries, you may find the following methods helpful to log or inspect the generated SQL queries:  
  
1. **`.toString()` Method:**  
- The `.toString()` method can be called on a Knex query to retrieve the generated SQL as a string. This is useful for logging and debugging.  
```javascript  
const query = db('table').select('*').where({ id: 1 });  
console.log(query.toString());  
```  
  
2. **`.toSQL()` Method:**  
- The `.toSQL()` method provides an object representation of the SQL query along with bindings. This can be useful for inspecting the query and its parameters.  
```javascript  
const query = db('table').select('*').where({ id: 1 });  
console.log(query.toSQL());  
```  
  
3. **`knex.on('query', callback)` Event:**  
- Knex allows you to listen for the `'query'` event, which is triggered whenever a query is executed. You can use this event to log or inspect queries.  
```javascript  
db.on('query', (queryData) => {  
console.log('Executing query:', queryData);  
});  
```  
  
Make sure to add this event listener before executing any queries.  
  
Here's an example combining these techniques:  
  
```javascript  
const query = db('table').select('*').where({ id: 1 });  
  
// Log the SQL string  
console.log(query.toString());  
  
// Log the SQL object  
console.log(query.toSQL());  
  
// Listen for the 'query' event  
db.on('query', (queryData) => {  
console.log('Executing query:', queryData);  
});  
  
// Execute the query  
query.then((result) => {  
console.log('Query result:', result);  
});  
```  
  
These methods allow you to inspect and debug Knex.js queries at different levels of detail. Choose the method that best fits your debugging needs.