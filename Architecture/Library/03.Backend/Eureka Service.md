---
tags:
  - services
  - microservices
  - Java
  - CodebaseDecision
  - openSource
  - springBoot
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Eureka service and its use.
Status: Done
Started: 2024-02-03
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish: false
---
Eureka is a service discovery(lookup table) tool primarily used in microservices architectures. Developed by Netflix and open-sourced as part of the Netflix OSS (Open Source Software) initiative, Eureka allows services to register themselves dynamically and discover other services within the system.

Key features of Eureka:

1. **Service Registration:**
   - [[Microservices VS Monolithic Architecture |Microservices]] can register themselves with the Eureka server, providing metadata such as hostname, port, and health status.

2. **Service Discovery:**
   - Eureka maintains a registry of all registered services. Other services can query this registry to discover the available services and their locations.

3. **Heartbeat Mechanism:**
   - Eureka includes a heartbeat mechanism where registered services periodically send heartbeats to the server. If a service fails to send heartbeats within a specified time, Eureka marks it as unavailable.

4. **Load Balancing:**
   - Eureka facilitates [[Load Balancer |Load Balancing]] by allowing services to distribute incoming requests among multiple instances of a service.

5. **Client-Side Load Balancing:**
   - Clients, when querying for a service, can use information from Eureka to implement client-side load balancing strategies.

6. **Fault Tolerance:**
   - Eureka is designed with [[Fault Tolerance]] in mind. If one Eureka server goes down, clients can still discover services by querying other available Eureka servers in the system.

7. **Integration with Spring Cloud:**
   - Eureka is commonly used in conjunction with Spring Cloud, a framework for building Java-based microservices. Spring Cloud provides seamless integration with Eureka for service discovery.

In summary, Eureka is a service registry and discovery tool that plays a crucial role in dynamic, distributed systems, allowing microservices to find and communicate with each other efficiently.
  
