---
tags:
  - methodology
  - Docker
  - 12FactorApp
  - configuration
author:
  - jacgit18
  - chatgpt
Purpose: This documentation Twelve Factor App, factor three in the context of Docker.
Status: Done
Started: 
EditDate: 2024-03-06
Relates: 
Peer Reviewed: 1
dg-publish:
---
Config: Configuration parameters (such as database connection strings, API keys, etc.) should be stored in the environment. Docker allows you to set environment variables that can be set during container runtime, allowing the banking app to access the necessary configurations.

![[Twelve Factor App Config]]