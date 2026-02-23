---
tags:
  - career
  - dev
author:
  - jacgit18
Purpose: This documentation discusses personal features worked on.
Status: Done
Started: 2023-12-14
EditDate:
Relates: "[[Interview Script]]"
dg-publish:
---
**Create Ticket Endpoint**
- No stats available for the old app, making comparisons unfeasible.

**GetAllTickets Endpoint**
- The new app exhibits slower performance at 808.00 ms, potentially due to implementation differences aimed at enhancing security.
- In contrast, the old app demonstrates quicker response times at 576.12 ms.

**GetLetterByID Endpoint**
- Given the structure where letters are collections of change orders, and change orders are collections of tickets, the absence of a setup for change orders indicates that the GetLetterByID functionality may not exist or be implemented yet.
#### **Connected Endpoints to Front-end**

**GetAllMaterial & GetAlEquipment Endpoint**
- New app response time: 4338.2 ms
- Old app response time: 8700.4 ms

**CreateMaterials & CreateEquipment Endpoint**
- New app processing time: 321.542 ms (89), showcasing a 2x faster execution.
- Old app loading time: 812.31 ms (98) due to PHP.

**EditMaterials & EditEquipment Endpoint**
- While the edit endpoint creation was successful, the connection to the front-end didn't materialize.
- The processing time for material edits on the new app was 8222.9 ms, likely similar for equipment due to their resemblance.

### Miscellaneous Things Learned 

### Data Layer
In the data layer, the data model establishes a binding that facilitates seamless interaction within the codebase. This binding ensures a cohesive connection between various components, enabling efficient utilization of the data model throughout the application.

Across layers, asynchronous functions, strategically implemented, create a responsive, non-blocking environment for seamless communication and side effect handling.

Request validation utilities, like `utils.inputPrompt`, enhance code robustness, ensuring systematic input validation for reliability and security.

A nuanced approach involves introducing a dedicated data sub-layer, encapsulating database connectivity and managing interface operations. This enhances clarity and maintainability, streamlining data management complexities within the application architecture.

### Controller
In the Controller, endpoints involve two distinct queries: determining authorization using util companyAccess and retrieving desired data. It's crucial to consider these tasks separately.

Authorization hinges on company type and user role, acquired from companyAccess. Material data queries appear straightforward, possibly not requiring joins.

Regarding date_created & date_modified in post tests, while you can assign them, their values won't match the database output, as the service layer overwrites company_id and created_by. Users cannot specify these fields; they are managed in the service layer for consistency.