---
tags:
  - web
  - query
  - HTTP
  - URL
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses URI a super-set of  URL, talking about query design.
Status: Done
Started: 
EditDate: 2024-01-30
Relates: "[[Structuring URL]]"
Peer Reviewed: 0
dg-publish: false
---
A Query String assigns values to specified Query Parameters and is typically encoded. It is initiated by the "?" within the URL and includes parameters and their corresponding values, such as "id" and "123". Parameters are occasionally employed for session IDs.

In the context of web and database queries, data transmission can occur through various means, including Query Strings/Params within the URL, URL Route Params, or Request Body Params. For example:

- Query String/Param within URL:
  - `https://example.com/api/data?category=tech&type=article`

- URL Route Param:
  - `https://example.com/api/data/category/tech/type/article`

- Request Body Param:
  - Included in the body of an HTTP request during data submission.

Query Params play a crucial role in specifying conditions or filters when querying a database through a web application, allowing for dynamic and targeted retrieval of information.


The query component in a URI plays a crucial role in uniquely identifying a resource. For instance:

- `http://api.college.restapi.org/students/morgan/send-sms`
- `http://api.college.restapi.org/students/morgan/send-sms?text=hello`

**Rule:** The query component can be used to filter collections or stores:

- `GET /users`
- `GET /users?role=admin`

**Rule:** Use the query component for paginating collection or store results:

A REST API client should employ the query component for pagination, specifying parameters like `pageSize` and `pageStartIndex`. For example:

- `GET /users?pageSize=25&pageStartIndex=50`

When client pagination requirements become complex, consider designing a special controller resource. For instance:

- `POST /users/search`

This design allows more intricate inputs via the request's entity body. However, ensure cacheable results are marked accordingly, as detailed in Chapter 4.

###  Query Parameters:
- `limit`: Includes only the first N items of a resource collection in the first page of a response.
- `offset`: Excludes the first N items of a resource collection from a response or you can rephrase this a say the number of resources skipped, adjustable with this parameter.
- `sort`: Sorts items in a resource collection returned in a response.
- `filter`: Filters items in a resource collection to return a subset based on parameter values.
- `total`: Total number of resources returned.
- `count`: Number of resources on the current page, modifiable using the `limit` parameter (default is 100).


Reference: [Ember.js Guide on Query Parameters](https://guides.emberjs.com/release/routing/query-params/)