---
tags:
  - concurrency
  - methodology
  - Docker
  - 12FactorApp
  - scalability
author:
  - jacgit18
  - chatgpt
Purpose: This documentation Twelve Factor App, factor eight in the context of Docker.
Status: Done
Started: 
EditDate: 2024-03-06
Relates: 
Peer Reviewed: 1
dg-publish:
---
Concurrency: The app should scale out horizontally by adding more processes, rather than increasing the size of individual processes. Docker's orchestration tools (Kubernetes, Nomad, Swarm, etc) can automatically manage the scaling of your app based on defined rules and resource utilization.

In the context of the Springboot app from Cre8tive the [[Eureka Service]] helps with concurrency.

## Relating Topics
[[Vertical vs Horizontal Scaling#Vertical Scaling Relationship with Concurrency |Horizontal Scaling Relationship with Concurrency]]
[[Concurrent programming]]


![[Twelve Factor App Concurrency]]