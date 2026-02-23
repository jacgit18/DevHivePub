---
tags:
  - services
  - methodology
  - Docker
  - 12FactorApp
  - systemDesign
  - MacroCodebaseDecision
  - databases
  - caches
author:
  - jacgit18
  - chatgpt
Purpose: This documentation Twelve Factor App, factor four in the context of Docker.
Status: Done
Started: 
EditDate: 2024-03-06
Relates: 
Peer Reviewed: 1
dg-publish:
---
Backing services: External services (such as databases, message queues, or caching systems) should be treated as attached resources. Docker's container networking capabilities enables your code to connect to and utilize these services as needed while maintaining modularity which can help with deployment strategies. ^558d6a

![[Twelve Factor App Backing services]]