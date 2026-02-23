---
tags:
  - deployment
  - phases
  - methodology
  - devops
  - Docker
  - 12FactorApp
author:
  - jacgit18
  - chatgpt
Purpose: This documentation Twelve Factor App, factor five in the context of Docker.
Status: Done
Started: 
EditDate: 2024-03-06
Relates: 
Peer Reviewed: 1
dg-publish:
---
The activities of building, releasing, and running an application typically occur within the "Deployment and Maintenance" stage or phase of the application development lifecycle.

[[Build]], [[Release]], [[Run]]: Docker standardizes the build, release, and run stages of your app in language/runtime/OS agnostic manner. The app can be built using a Dockerfile, released as a container image, and then run in any environment that supports Docker, providing consistency and reproducibility. While also improving things like scalability, load balancing, monitoring and alerting.

These activities are tightly connected and usually occur within the Deployment and Maintenance stage because they are related to transitioning the application from the development and testing environment to the production environment. It's also within this stage that ongoing maintenance and support are provided to ensure the application runs smoothly and remains available to users.


![[Twelve Factor App Build, release, run]]

## Flashcard
#deploymentStages
what is the first stages of a application;; Build stage.
what is the second stages of a application;; Release stage.
what is the third stages of a application;; Run stage.


