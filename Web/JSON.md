---
tags:
  - web
  - data
  - formats
  - schema
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses JSON.
Status: Done
Started: 
EditDate: 2024-01-30
Relates: 
Peer Reviewed: 0
dg-publish: false
---
### Working with JSON

- **Data Interchange:** JSON is utilized for data interchange, enabling communication between systems that may use different programming languages.

- **Syntax and Exchange:** The syntax of JSON allows for the storage and exchange of data, presented as text in JavaScript Object Notation. This format is universally readable across various programming languages.

- **JSON Methods:** Objects can be encapsulated using the `JSON.parse` or `JSON.stringify` methods. 
  - `JSON.stringify(object)` is used before making requests to servers or databases (via HTTP methods like GET, POST, PUT, or DELETE).
  - Upon receiving data in the browser, `JSON.parse` is applied for processing.

- **Parsing Process:**
  - **Request to Server/DB:** Object is converted to a string using `JSON.stringify` before sending.
  - **Browser Reception:** Upon receiving data, `JSON.parse` is employed to convert the string back to an object.

- **Dealing with JSON Order:**
  - JSON order preservation is inherent; re-parsing may be necessary for specific scenarios, such as reordering keys (`JSON.stringify(JSON.parse(jsonVar))` or `JSON.parse(JSON.stringify(jsonVar))`).

- **Manipulating JSON:**
  - JSON is a protected primitive string; to alter its order, it's converted to an object using `JSON.parse` for mutability. 
  - After manipulation, `JSON.stringify` is used to revert it to a string.

### JSONP

JSONP, or JSON with Padding, addresses cross-domain policy issues when requesting files from external domains. Leveraging the script tag instead of XMLHttpRequest, JSONP facilitates cross-domain data retrieval by embedding the response within a function call, overcoming typical cross-origin limitations.


The difference between **JSON** and a **JSON blob** comes down to context and usage:

1. **JSON (JavaScript Object Notation)**
    
    - A lightweight data format used to store and exchange data between systems.
    - It follows a structured format with key-value pairs, arrays, and nested objects.
    - Example:
        
        ```json
        {
          "name": "Alice",
          "age": 25,
          "hobbies": ["reading", "cycling"]
        }
        ```
        
2. **JSON Blob**
    
    - The term **"blob" (Binary Large Object)** in this context means a **large, unstructured JSON string** stored as a single entity in a database or system.
    - JSON blobs are often stored in **NoSQL databases** (e.g., MongoDB) or relational databases as **TEXT or BLOB** fields.
    - Unlike structured JSON columns (e.g., PostgreSQL’s `jsonb`), JSON blobs are **not easily queryable** without additional parsing.
    - Example (JSON stored as a single text blob in SQL):
        
        ```sql
        INSERT INTO my_table (id, json_data) VALUES 
        (1, '{"name": "Alice", "age": 25, "hobbies": ["reading", "cycling"]}');
        ```
        

### **Key Differences:**

|Feature|JSON|JSON Blob|
|---|---|---|
|**Structure**|Well-structured, key-value format|Stored as a raw string|
|**Queryability**|Can be queried directly in some databases (e.g., PostgreSQL `jsonb`)|Needs parsing to query|
|**Storage**|Typically used in APIs and structured storage|Stored as a large text/blob field in databases|
|**Use Case**|API responses, data interchange|Persisting large JSON documents in databases|

Would you like more details on working with JSON blobs in a specific database?