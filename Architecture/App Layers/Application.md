---
tags:
  - systemDesign
  - systemComponent
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses application layer of a web app.
Status: Done
Started: 
EditDate: 2024-03-06
Relates: "[[_Web App Architecture.canvas|_Web App Architecture]]"
Peer Reviewed: 0
dg-publish:
---
The application layer which **focuses on use case** uses a controller in the presentation layer to manage the flow of data and interactions between the user interface and the underlying business logic. The controller acts as an intermediary, receiving input from the user interface components and translating it into actions that trigger specific business logic or application processes. This separation helps maintain a clear distinction between the presentation layer (UI) and the application logic, promoting modularity and easier maintenance of the software system.