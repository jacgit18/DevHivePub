---
tags:
  - web
  - HTTP
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses what Out request do and the difference between Put and Post request.
Status: Done
Started: 
EditDate: 2024-01-29
Relates: 
Peer Reviewed: 0
dg-publish: false
---
![[PutVPatch.gif]]
## **PUT(Update) Method: Complete Replacement**
  - The PUT request method creates a new resource or replaces the target resource's representation with the provided payload.
  - Update, in the context of PUT, implies an update-if-exists approach: Overwrite the current value entirely with the new one. If the resource doesn't exist, consider the operation a failure. In case of conflicting updates, accept both but designate the "latest" one for future reads.

- **PUT vs. POST:**
  - The key distinction is that PUT is idempotent, ensuring calling it once or multiple times successively yields the same effect. Conversely, successive identical POST requests may have additional effects, such as placing an order multiple times.

- **When to Use PUT for Creating New Resources:**
  - Both HTTP POST and PUT can create new resources, but use PUT when the client can control part of the URI. For instance, a storage server may allocate a root URI for each client, allowing them to create resources using that root URI as a directory.
  - When using POST to create resources, the server determines the URI. It can manage URI naming policies and network security configurations. Servers can use information in the representation (like the Slug header) when generating URIs for new resources.
  - If supporting PUT for creating new resources, clients must be capable of assigning URIs. Consider explaining the server's URI organization to clients and any security and filtering rules based on URI patterns. Restrict clients to a specific URI range if necessary.