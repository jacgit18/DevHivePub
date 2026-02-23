---
tags:
  - pattern
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Software Architectural Patterns
Status: Refinement
Started: 
EditDate: 2024-03-07
Relates: 
Peer Reviewed: 0
dg-publish:
---
1. Model-View-Controller (MVC): Separates the application into three interconnected components: the model (data and logic), the view (user interface), and the controller (handles user input and updates the model and view).
2. MVVM stands for Model-View-ViewModel, and it is often used in the context of graphical user interfaces (GUIs) and applications with rich user interactions.

3. Layered Architecture: Organizes the application into horizontal layers, such as presentation layer, business logic layer, and data access layer, each responsible for specific tasks. Higher layers depend on lower layers.

4. Client-Server: Divides the system into client (user interface) and server (centralized logic and data), with communication happening over a network. The server provides services to multiple clients.

5. Microservices: Splits the application into small, loosely coupled, and independently deployable services that communicate over a network. Each service focuses on a specific business capability.

6. Event-Driven Architecture (EDA): Emphasizes the production, detection, and consumption of events. Components communicate by producing and consuming events asynchronously.

7. Service-Oriented Architecture (SOA): Organizes the application as a collection of services that communicate with each other through well-defined interfaces. Services can be independently developed and deployed.

8. Domain-Driven Design (DDD): Focuses on modeling the problem domain in software by defining domain objects, entities, aggregates, and their relationships.

9. Repository Pattern: Provides a layer of abstraction between the data access logic and the business logic, allowing the business logic to work with objects instead of directly interacting with the database.

10. Pipe and Filter: Divides the processing of data into a series of self-contained filters connected by pipes. Each filter transforms the data as it passes through.

11. Publish-Subscribe: Allows components to communicate through a message broker. Publishers send messages to specific topics, and subscribers receive messages based on their subscriptions.

12. Blackboard Pattern: Consists of a shared knowledge base (blackboard) and multiple specialized components (knowledge sources) that read from and write to the blackboard, collaborating to solve a problem.

13. Peer-to-Peer (P2P): Distributes the application's workload across a network of equal peers, where each peer can act as a client and a server.

These are just a few examples, and there are many other software architectural patterns available depending on the specific requirements and goals of the application.