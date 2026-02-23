---
tags:
  - systemDesign
  - distributedSystem
  - scalability
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses what a load balancer purpose.
Status: Refinement
Started: 2024-01-07
EditDate: 2024-03-06
Relates: "[[Dynamic Scaling]]"
Peer Reviewed: 0
dg-publish:
---
![[Load Balancing.gif]]

Load balancing is a crucial aspect of distributed systems and computer networking, aiming to distribute workloads across multiple computing resources for optimal utilization, minimal response time, and high availability. This is especially vital in scenarios where a single server cannot handle all incoming requests, as seen in high-traffic web applications and large-scale systems.

A load balancer, falling under a category rather than a specific technology, is a device or software application that disperses network or application traffic among multiple servers (e.g., proxies and various server types). This ensures no single server is overwhelmed, enhancing the reliability, availability, and scalability of a system.

Horizontal scaling and vertical scaling are two fundamental approaches to achieving load balancing, providing flexibility in adapting to varying workloads and maintaining system efficiency.


 #### Load balancers can operate at different layers of the OSI model, such as:  
  **DNS ->load balancer(also  makes all server appear as one IP) -> server pool -> cache ->DB 
  
- **Layer 4 (Transport Layer):** Distributes traffic based on information in the transport layer, like IP addresses and port numbers. This is known as a TCP/UDP load balancer.  
  
- **Layer 7 (Application Layer):** Makes decisions based on application layer data, such as HTTP header information. This is known as an application or content-aware load balancer.  
  
API gateways and proxy servers, on the other hand, serve different purposes but may include load balancing features as part of their functionality. An API gateway manages, routes, and secures API traffic, while a proxy server acts as an intermediary between clients and servers.  

The term "load balancer" is most commonly associated with managing network traffic by distributing it across multiple servers to ensure optimal utilization and improve performance. However, in a broader sense, the concept of load balancing can be extended beyond network traffic and may apply to other resources or tasks within a system. The key idea is to efficiently distribute workloads to prevent overload on specific components, ensuring a more balanced and reliable system.

In the context of software engineering or system architecture, load balancing can indeed extend to various types of resources or tasks. Here are some examples:

1. **Task Load Balancing:**
   - In parallel computing or distributed systems, load balancing may refer to distributing computational tasks or workloads across multiple processors or nodes to achieve better performance.

2. **Database Load Balancing:**
   - For database systems, load balancing can involve distributing queries or transactions across multiple database servers to prevent overloading a single server and improve overall database performance.

3. **Job Queue Load Balancing:**
   - In job queue systems, load balancing may involve distributing tasks or jobs among multiple worker nodes to ensure efficient processing and reduce queue times.

4. **Application Load Balancing:**
   - Load balancing within an application can refer to distributing workloads or tasks among different components or microservices to optimize resource utilization and enhance overall application performance.

5. **Resource Load Balancing:**
   - Beyond computational tasks, load balancing can extend to managing various resources such as storage, memory, or bandwidth to prevent bottlenecks and ensure optimal utilization.

While the term "load balancer" is commonly associated with network traffic distribution, the underlying principle of distributing workloads to prevent uneven resource utilization can be applied to a broader range of scenarios within a system. It's essential to consider the specific context and the type of load or workload being managed when using the term in a broader sense.

In summary, while load balancers are often associated with network traffic management, the concept of load balancing can be generalized to include the efficient distribution of various types of workloads or tasks within a system to achieve improved performance and resource utilization.

![[load balancer cheet.gif]]

Expanding the server count can introduce challenges, particularly with stateful servers. To mitigate this, separate stateless and stateful concerns by pushing state-related tasks to data cache or databases, relieving the application servers. Additionally, horizontally scaling with more servers may impact the database, prompting consideration for vertical scaling to enhance the database capacity rather than solely relying on horizontal scaling. Balancing server architecture ensures optimal performance and addresses potential issues with increased server count.

![[Load Balance Algo.jpeg]]


![[Load balancer use cases.gif]]