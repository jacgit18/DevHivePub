---
tags:
  - MacroCodebaseDecision
  - architecturalPatterns
  - microservices
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses the different combinations of architecture to use together.
Status: Refinement
Started: 
EditDate: 2024-03-07
Relates: "[[Event Driven Architecture]]"
Peer Reviewed: 0
dg-publish:
---
The appropriate combination depends on the specific use case, scalability needs, and architectural goals. Here are some common combinations when it comes :  
  
1. **Microservices with Event-Driven Architecture:**  
   - Microservices often work well with an event-driven architecture. Each microservice can emit events when state changes occur, allowing other microservices to react accordingly. This promotes loose coupling between services.  
  
2. **Microservices with CQRS:**  
   - CQRS is often used in conjunction with microservices to separate the read and write concerns. Each microservice might have separate components or services for handling commands (write) and queries (read), providing flexibility in scaling and optimizing for specific operations.  
  
3. **Microservices with Event Sourcing:**  
   - Event sourcing can be employed in a microservices architecture to store the state changes of a system as a sequence of events. This can enhance auditability and enable replaying events to rebuild state.  
  
4. **Serverless with Event-Driven Architecture:**  
   - Serverless architectures often leverage an event-driven model where functions ([[Cloud Service Model#FAAS|FaaS]]  ) are triggered by events. Events could be changes in state, external triggers, or scheduled events. This can lead to a more scalable and cost-efficient system.  
  
5. **Serverless with Microservices:**  
   - Serverless functions can be used within a microservices architecture to handle specific functionalities or tasks. For example, a serverless function might process uploaded files, sending events to other microservices for further processing.  
  
6. **Streaming with Microservices:**  
   - Streaming platforms (e.g., Apache Kafka) can be used with microservices to facilitate real-time data processing and communication between services. Streaming enables the handling of large volumes of data with low latency.  
  
7. **Streaming with Event Sourcing:**  
   - Streaming can be used as the underlying infrastructure for event sourcing. Events are streamed to an event store, providing a real-time log of state changes.  
  
8. **Event-Driven with CQRS:**  
   - Event-driven architectures often align well with CQRS. Commands and events can be used to represent state changes and trigger actions in a system, while separate query components handle read operations.  
  
9. **Microservices with Streaming and CQRS:**  
   - A combination of microservices, streaming platforms, and CQRS can provide a scalable and responsive architecture. Events are used for communication, a streaming platform handles real-time data flow, and CQRS separates read and write concerns.  
  
10. **Microservices with Serverless and Streaming:**  
    - Combining microservices with serverless functions and a streaming platform can provide a flexible and scalable architecture. Serverless functions handle specific tasks, while streaming enables real-time communication and coordination between microservices.  


It's important to note that while these combinations offer flexibility, the choice should align with the specific requirements of the system, the team's expertise, and the operational constraints of the environment. Each combination has its own trade-offs and considerations.