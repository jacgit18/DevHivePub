---
tags:
  - testing
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses smoke test.
Status: Done
Started: 
EditDate: 2024-03-07
Relates: 
Peer Reviewed: 0
dg-publish: true
---
![[Smoke Banner.gif]]
A smoke test is a type of software testing that is designed to quickly assess the basic functionality of a software application or system. The primary purpose of a smoke test is to verify that the most critical and fundamental features of the software are working as expected and that the application can start and run without major issues. It's often performed at the early stages of development or after significant changes to ensure that the system is not "broken."  
  
Key characteristics of a smoke test include:  
  
1. **High-Level Testing**: Smoke tests focus on high-level functionality rather than detailed testing of every feature. They ensure that the core features are operational.  
  
2. **Quick and Simple**: Smoke tests are usually simple and quick to execute, making them an efficient way to catch severe issues early in the development or integration process.  
  
3. **Pass or Fail**: Smoke tests have a binary outcome: pass or fail. If any critical functionality fails during the smoke test, it indicates a serious problem, and further testing is often halted until the issue is resolved.  
  
4. **Limited Test Cases**: Smoke tests typically include a small set of test cases that cover the most critical paths through the application, such as launching the software, basic user interactions, and key functionality.  
  
5. **Non-Exhaustive**: Smoke tests do not aim to cover all possible scenarios or edge cases. They are not exhaustive tests; instead, they provide a "smoke check" to ensure the system's basic integrity.  
  
6. **Rapid Feedback**: The quick execution of smoke tests provides rapid feedback to developers, allowing them to address significant issues early in the development cycle.  
  
Smoke tests are often a part of continuous integration and continuous delivery (CI/CD) pipelines, where they are executed automatically after each code commit to ensure that the software remains in a usable state. They are a valuable tool for quickly identifying show-stopping issues before more comprehensive testing is performed. 