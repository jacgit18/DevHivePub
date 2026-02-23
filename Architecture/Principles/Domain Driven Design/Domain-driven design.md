---
tags:
  - Domain
author:
  - jacgit18
Purpose: This documentation discusses
Status: Done
Started: 
EditDate: 2024-03-06
Relates: 
Peer Reviewed: 0
dg-publish:
---
![[Domain Driven.gif]]
Domain-driven design (DDD) is an approach to software development that focuses on understanding and modeling the core domain of a business or application. It aims to align software design with the complexities and nuances of the domain, resulting in more maintainable, flexible, and scalable systems.



Domain driven design is used when there's a lot of complexity in the domain that you're trying to build for


Here are some key concepts and principles of Domain-driven design:

1. Ubiquitous Language: DDD promotes the use of a common, shared language between developers and domain experts. This language, known as the "ubiquitous language," is used in communication, code, and documentation. By using a consistent language, misunderstandings and gaps in communication can be minimized, fostering a deeper understanding of the domain.

2. Bounded Context: A bounded context defines a specific area or boundary within a larger system where a certain model or language is applicable. It helps manage the complexity of large domains by breaking them down into smaller, self-contained contexts. Each bounded context has its own domain model and explicitly defines the context in which its concepts, terms, and rules apply.

3. Aggregates: Aggregates are clusters of related objects treated as a single unit. They encapsulate the behavior and enforce the consistency rules within the boundaries of the aggregate. Aggregates protect the integrity of the domain by ensuring that all changes to its internal objects are made through well-defined entry points.

4. Domain Events: Domain events represent significant occurrences or facts within the domain. They capture something important that has happened and can trigger changes in other parts of the system. Domain events are often used to communicate between bounded contexts and maintain consistency across different models.

5. Domain Services: Domain services encapsulate complex domain logic that doesn't naturally belong to a specific entity or value object. They provide operations and behavior that are significant to the domain but cannot be attributed to a single object. Domain services help maintain the cohesion and encapsulation of domain concepts.

6. Strategic Design: DDD emphasizes the importance of strategic design, which involves analyzing the business context, defining bounded contexts, establishing relationships between contexts, and identifying core domain concepts. Strategic design decisions shape the overall structure and organization of the software system.

7. Tactical Design: Tactical design focuses on modeling individual domain concepts within a bounded context. It involves designing entities, value objects, aggregates, services, repositories, and other building blocks of the domain model. Tactical design ensures that the domain model reflects the business rules and processes accurately.

By applying Domain-driven design principles and practices, developers can gain a deep understanding of the business domain and create software systems that closely align with the real-world requirements. DDD encourages collaboration between domain experts and software developers, enabling the creation of more effective and maintainable solutions.



**Relationship:**

- Event storming is a technique that can be employed within the context of DDD to facilitate the exploration and understanding of the domain. It often serves as a collaborative workshop where stakeholders come together to uncover domain events and their relationships.
- DDD provides the foundational concepts and patterns for designing the actual software based on the insights gained through techniques like event storming.
- The events identified during an event storming session often become the building blocks for defining aggregates, entities, and the overall domain model in a DDD-driven development process.

In summary, event storming is a practical, collaborative activity that aligns well with the principles of DDD. It helps teams discover and model the intricacies of a domain, providing valuable insights that can be directly translated into the design and implementation of a software system using DDD principles.




In Domain-Driven Design (DDD), conversations play a crucial role in understanding and defining the problem domain. Here are some essential conversations that need to be had:

1. **Domain Experts Interview:**
   - Engage with domain experts to understand their perspectives, insights, and knowledge about the business domain. This helps in capturing the domain's intricacies.

2. **Ubiquitous Language Definition:**
   - Establish a shared vocabulary (Ubiquitous Language) between technical and non-technical team members. Discuss and define key terms to ensure a common understanding.

3. **Context Mapping:**
   - Discuss the relationships and boundaries between different Bounded Contexts. Clarify how different parts of the system interact and share information.

4. **Bounded Context Exploration:**
   - Identify and define Bounded Contexts within the system. Discuss the scope and responsibilities of each Bounded Context and how they collaborate.

5. **Event Storming:**
   - Conduct an Event Storming session to model complex business processes. Collaborate with stakeholders to identify events, commands, aggregates, and policies.

6. **Aggregate Design:**
   - Discuss and design Aggregates that represent consistency boundaries within the system. Clarify which entities and value objects belong to each aggregate.

7. **Value Object Identification:**
   - Identify and define Value Objects in collaboration with domain experts. Discuss the immutability and behavior of these objects.

8. **Entity Identification:**
   - Define Entities based on discussions with domain experts. Identify objects with a distinct identity and lifecycle.

9. **Repository Design:**
   - Discuss the design of Repositories to access and persist Aggregates. Clarify the data access requirements and how Repositories fit into the overall architecture.

10. **Anti-corruption Layer Strategies:**
    - Discuss strategies for implementing anti-corruption layers to ensure communication between Bounded Contexts without corrupting their models.

11. **Consistency Models:**
    - Discuss and define consistency models for different parts of the system. Clarify how eventual consistency or strong consistency is achieved.

12. **Domain-Driven Design Patterns:**
    - Discuss and apply DDD patterns such as the Specification Pattern, Factory Pattern, and others based on the specific needs of the domain.

13. **Feedback Loops:**
    - Establish feedback loops with domain experts to continuously refine the model as the understanding of the domain evolves.

These conversations help create a shared understanding of the business domain, leading to the development of a well-modeled and effective software system.

