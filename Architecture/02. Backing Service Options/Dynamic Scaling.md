---
tags:
  - systemDesign
  - scalability
  - systemComponent
  - distributedSystem
  - automation
  - cloud
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Dynamic scaling.
Status: Refinement
Started: 2024-02-25
EditDate: 2024-03-06
Relates: "[[Vertical vs Horizontal Scaling]]"
Peer Reviewed: 0
dg-publish:
---
Dynamic scaling, the ability to adjust resources based on real-time demand, synergizes effectively with both horizontal and vertical scaling.

#### Dynamic Scaling with Horizontal Scaling
In horizontal scaling, an autoscaling system monitors key metrics and dynamically adds or removes servers to adapt to changing demand. For example, during traffic spikes, additional servers are provisioned, and during lulls, servers are scaled down, optimizing efficiency and costs.

#### Dynamic Scaling with Vertical Scaling
While less common, dynamic scaling can be applied to individual servers in vertical scaling, particularly in cloud environments. Cloud platforms can adjust the computing resources of instances based on demand, optimizing CPU and RAM allocation during peaks and scaling down during lower demand.

In summary, dynamic scaling complements both horizontal and vertical scaling, ensuring adaptability to varying workloads. Horizontal scaling is more commonly associated with dynamic scaling, involving the addition or removal of entire servers, whereas dynamic scaling with vertical scaling is beneficial in cloud environments for adjusting individual instance resources.

### Example

For the Cre8tive springboot code, multiple account services instances are run in the terminal to handle network requests. A load balancer, implemented through business logic or a library, manages these instances. Load balancers typically use a Round Robin approach to distribute traffic across service instances, ensuring efficient utilization.