---
tags:
  - testing
  - OrderOfOperations
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses testing hierarchy.
Status: Done
Started: 
EditDate: 2024-02-03
Relates: 
Peer Reviewed: 0
dg-publish: true
---
![[Testing Priority.jpeg]]
To enhance your testing strategy, allot 10% for [[End to End Testing]], the most resource-intensive test, followed by 20% for [[Integration vs System Integration Testing#Integration Tests |integration tests]]. Prioritize 70% for [[Unit Testing]], the most cost-effective and frequently employed test. This balanced approach ensures thorough coverage at the class level through unit testing, emphasizing end-to-end and integration tests for critical user journeys. Additionally, consider both manual and automated testing. It's worth noting that certain tests, like the [[Smoke Test]], span multiple [[Testing Stages Relationship |Test Stages]], such as [[Functional Testing]] and [[Acceptance Testing]], while end-to-end and integration tests align more closely with functional testing.