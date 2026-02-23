---
tags:
  - databases
  - data
  - coupling
  - ACID
  - distributedSystem
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses SAGA.
Status: Refinement
Started: 
EditDate: 2024-03-07
Relates: 
Peer Reviewed: 0
dg-publish:
---
SAGA emerges as a robust solution for maintaining data consistency in distributed architectures without strictly adhering to ACID principles. Operating by orchestrating multiple compensatory transactions, SAGA introduces rollback opportunities to ensure consistent and reliable outcomes.

#### Check out & maybe integrate
#todo/Low/Dev 
- [ ] https://medium.com/javarevisited/what-is-saga-pattern-in-microservice-architecture-which-problem-does-it-solve-de45d7d01d2b
- [ ] https://medium.com/design-microservices-architecture-with-patterns/saga-pattern-for-microservices-distributed-transactions-7e95d0613345
- [ ] https://www.java67.com/2022/12/saga-microservice-design-pattern-in-java.html

**Two Approaches to Implementing SAGA:**

1. **Choreography:**
   - In the choreography saga, there is no centralized orchestration. Each service independently executes its transaction and publishes events.
   - Other services respond to these events, carrying out their respective tasks, with the option to publish additional events based on the scenario.

2. **Orchestration:**
   - In the orchestration saga, each participating service executes its transactions and publishes events.
   - Other services respond to these events, completing their tasks in a coordinated manner.

**Advantages of SAGA:**

1. **Consistency Across Multiple Services:**
   - SAGA effectively maintains data consistency across multiple services without imposing tight coupling. This flexibility is instrumental in distributed architectures.

**Disadvantages of SAGA:**

1. **Complexity in Design:**
   - The SAGA design pattern can be perceived as complex from a programmer's perspective. The intricacies of orchestrating and compensating transactions may pose challenges, especially for developers less accustomed to working with sagas compared to traditional transactions.

While SAGA introduces a powerful mechanism for achieving data consistency in distributed systems, its implementation choices of choreography or orchestration bring distinct advantages and challenges, making it essential for developers to carefully consider the suitability of each approach based on specific requirements.