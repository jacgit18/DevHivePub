---
tags:
  - methodology
  - Docker
  - 12FactorApp
  - environment
  - devops
  - phases
  - testing
author:
  - jacgit18
  - chatgpt
Purpose: This documentation Twelve Factor App, factor ten in the context of Docker.
Status: Done
Started: 
EditDate: 2024-03-06
Relates: 
Peer Reviewed: 1
dg-publish:
---
>[!note] 
>Parity the state or condition of being equal, example having a environment-specific Configurations like different DB depending on the environment 

Dev/prod parity: The development, staging, and production environments should be as similar as possible. Docker containers help with parity by allowing you to package your codebase and its dependencies improves consistency across different environments and reducing the likelihood of environment-related issues.


When Dev prod parity is setup right like having test which can help parity you can have multiple disposable environments. 

![[Twelve Factor App Dev prod parity]]