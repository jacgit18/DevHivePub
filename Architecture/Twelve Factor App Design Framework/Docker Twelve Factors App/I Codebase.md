---
tags:
  - methodology
  - environment
  - devops
  - Docker
  - 12FactorApp
author:
  - jacgit18
  - chatgpt
Purpose: This documentation Twelve Factor App, factor one in the context of Docker.
Status: Done
Started: 
EditDate: 2024-03-06
Relates: 
Peer Reviewed: 1
dg-publish:
---
A twelve-factor app most important factor is the codebase which is the glue that connects all the other factors. Lets say you have a banking app and you have it stored in a version control system (such as Git). Now the code is available to run in different environments but the environments can very and require additional setup. In order to bypass this we decide to use Docker. Docker enables us to build the app into a image once and consistently deploy container instances for local development, QE(Quality Engineering), [[Integration vs System Integration Testing|SIT]], [[Pre Acceptance Testing | PAT]] and Production environments eliminating extra setup.




![[Twelve Factor App Codebase]]

