---
tags:
  - testing
  - bestPractices
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses test driven development.
Status: Done
Started: 
EditDate: 2024-03-07
Relates: 
Peer Reviewed: 0
dg-publish: true
---
Test-driven development (TDD) is a software development approach where tests are written before the actual code or creating one feature then a test for that feature. The process typically follows these steps:

1. **Write a Test:** Define a test case for a small piece of functionality you want to implement.

2. **Run the Test:** Execute the test and confirm that it fails, as there is no code yet to fulfill the requirements.

3. **Write Code:** Implement the minimum code necessary to make the test pass.

4. **Run All Tests:** Execute all tests to ensure that the new code didn't break existing functionality.

5. **Refactor Code:** Improve the code's structure without changing its behavior.

6. **Repeat:** Repeat the process for the next piece of functionality.

TDD encourages small, incremental development cycles, with the goal of having a comprehensive suite of tests that verify the correctness of the code. This approach helps catch and address issues early in the development process, fostering more robust and maintainable code.

