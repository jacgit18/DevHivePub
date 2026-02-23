---
tags:
  - web
  - HTTP
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses HTTP Responses & Common Status Codes
Status: Done
Started: 2023-11-29
EditDate: 2024-01-31
Relates: 
Peer Reviewed: 0
dg-publish: false
---
![[Status Codes.jpg]]

In HTTP responses, the status line includes the HTTP version number, the status code (ranging from 1xx to 5xx), and a reason phrase. HTTP headers, categorized as general, response, and entity headers, provide additional information. They assist the client in understanding the response, caching, and making future requests. An empty line (CRLF) separates headers from the message body.

The message body, or response body, contains the requested resource or status information. It is present in most responses, except for HEAD requests or specific status codes. Message bodies can be single-resource with known or unknown length, indicated by Content-Type and Content-Length or Transfer-Encoding: chunked, respectively. Multiple-resource bodies involve multipart sections, although they are less common.

### Status Codes in HTTP Responses:

- **200: OK** - Signifies a successful request, indicating that it was received and processed without issues.

- **201: Created** - Indicates successful creation of one or more resources on the server, typically a result of an HTTP POST request.

- **301: Moved Permanently** - The requested resource has a new permanent URI, and the server redirects accordingly.

- **302: Found** - The requested resource has a new temporary URI, and the server redirects (with the possibility of using the original location for future requests).

- **401: Unauthorized** - User authentication is required for successful processing, and the request lacked necessary authorization codes.

- **404: Not Found** - The server couldn't find anything matching the requested URI, often used when the reason for refusal isn't disclosed or no other response is applicable.

- **500: Internal Server Error** - A generic message indicating an error in the server itself, preventing the completion of the request.

- **503: Service Unavailable** - The server is temporarily unable to handle the HTTP request, often due to maintenance, overload, or other reasons.

### Handling Missing Parameters in Query String:

When a parameter is missing in the query string, the appropriate status code is **400 - Bad Request**. This signifies that the user failed to provide the required input field. Choosing 400 over 422 is recommended for simplicity and user understanding, avoiding unnecessary complexity in response codes.

### Cases for HTTP 404:

1. The requested URL doesn't exist on the server, typically handled by the server itself.
  
2. If the client is looking for an entity with an ID in a path parameter (e.g., `/students/{id}`), responding with an HTTP 404 when the entity is not found.

### Query Parameter with No Matching Items:

If a user sends a query parameter and no matching items are found, respond with an **HTTP 200** status, indicating success, with an empty array in the body. Avoid using **404** in this case, as it's not an error of resource absence but a successful, albeit empty, response.