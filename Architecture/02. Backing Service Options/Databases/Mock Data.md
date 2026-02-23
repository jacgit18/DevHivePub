---
tags:
  - databases
  - data
  - testing
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses mock data.
Status: Done
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
#todo/Low/Dev 
- [ ] https://dev.to/omermorad/unit-test-like-a-pro-automock-my-open-source-answer-to-mocking-frustration-31p4
- [ ] https://dev.to/iainfreestone/20-resources-for-generating-fake-and-mock-data-55g1

### Fixtures and Database Objects
- A fixture is a database object that helps in testing.
- When using mock data and adding, it's essential to check the fixture for previous data. If existing data is found, it should be flushed within the fixture method.
- If a database table, such as the roles table, is not changing, there's no need to create fixtures for it.

### Mocking in Testing
- Mocking is primarily used in unit testing to isolate the behavior of the object under test with dependencies on other complex objects.
- Mocks simulate the behavior of real objects, replacing them in tests where incorporating real objects is impractical.

### Mocking vs. Stubbing
- Mocking simulates the behavior of real objects and verifies that the object under test calls the mock as expected.
- Stubbing is a minimal simulated object that implements just enough behavior to allow the object under test to execute the test.
- A stub is "minimal," while a mock involves verifying that the object under test uses the mock correctly.

### Distinguishing Between Mocking and Stubbing
- You may want to distinguish between mocking and stubbing.
- A stub is minimal and helps the object under test execute the test.
- A mock verifies that the object under test calls it correctly, and part of the test is confirming the correct usage of the mock.

### Example and Clarification
- For example, stubbing a database involves implementing a simple in-memory structure for storing records.
- Mocking a database is necessary when you want to verify specific data interactions, incorporating assertions about what was written to the database mock.
- The distinction lies in whether you want to test behavior related to the database (stub) or verify specific interactions (mock).

### Generalization of Mocking
- The concept of mocking is not restricted to objects; it can be applied more generally to units.
- Replacing "object" with "unit" makes the concept more general and applicable beyond traditional objects.

### Verification in Stubbing
- While testing with a stub, if it passes, one might conclude that the stub is being used. However, verification becomes essential when ensuring that the code goes through the desired function and not another.
- The use of a bool check is the distinction between stubs and mocks, where mocks involve verifying specific interactions.

### Conclusion
- The decision to use a stub or a mock depends on the testing scenario, with mocks being more suitable for verifying specific interactions and stubs for minimal behavior to execute tests.