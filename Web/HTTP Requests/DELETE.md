---
tags:
  - web
  - HTTP
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Delete request.
Status: Done
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish: false
---
**DELETE Method: Resource Deletion**

The DELETE request method removes the specified resource.

- **Delete-if-exists:** If the resource doesn't exist, consider the operation a failure. If two valid delete operations occur simultaneously, delete the resource and allow both to proceed.

## How to Use DELETE for Asynchronous Deletion

This recipe outlines using DELETE for asynchronous tasks, ideal for resource deletion requiring substantial time for backend cleanup and archival tasks.

1. Upon receiving a DELETE request, create a new resource, and respond with 202 (Accepted), including a representation of this resource.
  

```http
   HTTP/1.1 202 Accepted
   Content-Type: application/xml;charset=UTF-8
   <status xmlns:atom="http://www.w3.org/2005/Atom">
      <state>pending</state>
      <atom:link href="http://www.example.org/task/1" rel="self"/>
      <message xml:lang="en">Your request has been accepted for processing.</message>
      <created>2009-07-05T03:10:00Z</created>
      <ping-after>2009-07-05T03:15:00Z</ping-after>
   </status>
```
   

2. The client can query the URI http://www.example.org/task/1 to check the status of the request.

This asynchronous deletion approach is straightforward, mirroring a similar strategy for updating a resource asynchronously via the PUT method.