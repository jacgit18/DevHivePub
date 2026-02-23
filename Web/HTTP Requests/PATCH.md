---
tags:
  - web
  - HTTP
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Patch request.
Status: Done
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish: false
---
## **PATCH(Update) Method: Partial Modifications**

The PATCH request method is employed for applying partial modifications to a resource.

- PATCH, analogous to the "update(edit/add)" concept in CRUD, provides a set of instructions on how to modify a resource, differing from PUT, which presents a complete representation of the resource.

- Unlike PUT, PATCH is not inherently idempotent, although it can be. Idempotent means that repeated, identical requests will leave the resource in the same state. For instance, if an auto-incrementing counter field is part of the resource, PUT will naturally overwrite it (due to complete overwriting), but PATCH may not.

- **PATCH: Update, Typically Partial:**
  - PATCH is often used for partial updates, offering flexibility in modifying specific aspects of a resource without requiring a full replacement.

