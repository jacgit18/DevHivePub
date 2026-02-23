---
tags:
  - devops
  - scalability
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses development stages.
Status: Refinement
Started: 
EditDate: 2024-02-22
Relates: "[[Deployment Strategies]]"
Peer Reviewed: 0
dg-publish: true
---
![[Software Life Cycle.gif]]

Enhance the software development lifecycle by eliminating obstacles across ideation, implementation, testing, building, deployment, and system observation. This is achieved through the automation and streamlining of processes, optimizing the overall system.

Collaboration between developers and operations managers is pivotal in bridging gaps. Traditionally, developers focus on creating new features, while operations maintain the existing system. DevOps implementation can differ among companies, encompassing continuous integration and delivery, source code and package management, infrastructure treated as code, container orchestration, cloud utilization, and continuous monitoring.

In essence, DevOps aims to harmonize and enhance the entire software development and deployment lifecycle through collaborative efforts and the adoption of streamlined, automated practices.


![[Development Stages to Production.png]]

DevOps facilitates rapid releases, but for stability, the role of a [[Site Reliability Engineer]]is crucial.

**Feedback Loop:**
A feedback loop is exemplified when unit tests within the pipeline identify issues, signaling that the code isn't production-ready.

**Components of an Excellent Pipeline:**
A robust pipeline involves compiling and testing code ([[Continuous Integration]]), producing a [[Deployment Artifacts|deployable artifact]] (Continuous Delivery), and automatic application deployment (Continuous Deployment).

**Automated Trigger:**
The best pipelines automatically trigger upon code commits, either through [[Webhooks vs Polling |Polling or Webhooks]], ensuring seamless and consistent execution.

**Code Checkout:**
The CI server checks out code from the source repository based on the triggered commit, initiating the pipeline.

**Compile the Code:**
In compiled languages like Java, the CI tool compiles the program using appropriate build tools, often in a clean environment, leveraging technologies like Docker.

**Run Unit Tests:**
Unit testing ensures not only that tests pass but also that they evolve with the codebase growth, following the principle that a majority of tests should be unit tests.

**Package the Code:**
After passing tests, the code is packaged into a format suitable for the programming language and target environment, emphasizing building the binary only once.

**Run Acceptance Tests:**
Automated acceptance tests, using tools like Cucumber or Selenium, validate that the software meets requirements, minimizing manual testing efforts.

**Automated Acceptance Testing:**
Tools like Cucumber and Selenium automate acceptance tests, reducing manual testing time and expediting software delivery.

**Delivery or Deployment:**
The application proceeds to the delivery or deployment stage, where an artifact is ready for deployment (Continuous Delivery) or automatically deployed (Continuous Deployment).

**Continuous Deployment:**
To achieve continuous deployment, a production environment is necessary. Public cloud APIs or Kubernetes Helm charts can facilitate automated software deployment.

**Pipeline Conclusion:**
Upon successful deployment, the pipeline concludes, ready to re-run with each subsequent developer commit, emphasizing a continuous and automated development lifecycle.