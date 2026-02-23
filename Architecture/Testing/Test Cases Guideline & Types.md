---
tags:
  - testing
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses test cases.
Status: Done
Started: 
EditDate: 2024-02-03
Relates: 
Peer Reviewed: 0
dg-publish: true
---
Test cases in programming and coding challenges are scenarios or inputs designed to verify the correctness of a solution. They consist of specific inputs, expected outputs, and sometimes additional conditions. Developers create test cases to ensure that their code works as intended and handles various situations correctly. By running these tests, they can identify and fix errors, ensuring the reliability and robustness of their code.In coding challenges, test cases are crucial for evaluating the correctness and efficiency of a solution against different scenarios.

# Guidelines

1. **Avoid Over-Specificity:**
   - Ensure test cases are not overly specific to allow testing under various conditions.
   - Comprehensive testing should cover a wide range of scenarios and combinations.

2. **Consider Variability:**
   - Test cases should encompass diverse conditions the software may encounter.
   - Emphasize smaller test cases for efficiency while maintaining effectiveness.

3. **Functional Coverage:**
   - Focus on testing broader system functionality instead of isolated functions.
   - Align test cases with user patterns and workflows, transcending technical design boundaries.

4. **Define Scope:**
   - Establish a clear scope for each test case to maintain relevance.
   - Identify and explore 'corner cases' and 'boundary conditions' within the defined scope.

5. **Independence of Test Cases:**
   - Avoid interdependence between test cases to ensure reliable and standalone evaluations.
   - Enhance modularity by isolating test cases from each other.

6. **Truth Tables for Multiple Cases:**
   - Create truth tables for scenarios involving multiple test cases.
   - Evaluate the likelihood of multiple cases being true or false simultaneously.

These guidelines aim to optimize the effectiveness and efficiency of test cases, promoting comprehensive testing while aligning with real-world usage patterns.

#todo/Low/Dev 
- [ ] https://www.softwaretestinghelp.com/login-page-test-cases/
# Types of Cases 

###  Normal Case:
   - Evaluate correctness for typical inputs and anticipate potential issues.
   - Example: Consider sorting algorithms and potential failure on arrays with an odd number of elements due to partitioning. Include such scenarios in your test case.
#### Test Case
- A test case is a specific set of conditions or inputs used to test a particular aspect or functionality of a system or software. Test cases are designed to verify that the system behaves correctly under various conditions

#### Base Case
   - Marks the conclusion of recursion.

### Extremes:
   - Explore scenarios with:
     - Empty arrays or missing parameters.
     - Very small (one element) and very large arrays.
     - Address nulls and handle "illegal" input, defining expected behavior.
   - Example: Test cases for generating the nth Fibonacci number should include situations where n is negative.
#### Boundary Case
   - Occurs at or just beyond maximum or minimum limits.
   - Example: Analyzing current, preceding, and succeeding values to explore boundary conditions.
#### Iron Corner Case Testing
   - Also known as boundary value analysis.
   - Focuses on testing cases just outside and just inside edge cases.
#### Edge Case
   - Errors occurring infrequently, ranging from visual inconsistencies to software crashes.
   - Involves extreme operating parameters, testing the maximum or minimum input for correct output.
   - Important for validating program behavior, often addressed through unit tests.
   - Example: Checking boundary conditions of an algorithm, function, or method.
##### Corner Case
   - A corner case is a specific type of edge case where multiple variables or conditions come together, creating a unique and often challenging scenario.  
   - It involves testing situations where different factors or parameters interact in a way that may not be immediately obvious or common.  
   - For instance, if a system has conditions A, B, and C, a corner case might involve a combination of A and B, where both are simultaneously at their limits.
### Strange Input:
   - Challenge the code with unconventional inputs:
     - Already sorted arrays.
     - Arrays sorted in reverse order.
   - Develop these tests based on your understanding of the function, seeking clarification on constraints if needed.



## Special Case Check:
**Falls under both Normal Case and Strange Input**
   - Addresses non-obvious, non-boundary special values.
   - Example: Handling scenarios like log(1 + the smallest floating-point number), particularly in interviews.


These considerations guide the creation of comprehensive test cases, covering normal, extreme, and unconventional scenarios to ensure robust functionality and identify potential edge cases.






