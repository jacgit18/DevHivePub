---
tags:
  - testing
  - library
  - example
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses different testing paradigms using jest library.
Status: Done
Started: 2023-11-06
EditDate: 2024-02-02
Relates: 
Peer Reviewed: 0
dg-publish: true
---
Iteration can be useful in unit tests when you need to test a piece of code against multiple inputs or when you want to verify that a function behaves correctly across various scenarios. 
  
Not all the mentioned tests fall under the category of "unit tests." Unit tests have a specific scope and purpose, which is to test individual units or components of code in isolation. These units are typically small and should not have external dependencies. 
  
Here are some scenarios when iteration is commonly used in unit testing along with  a breakdown of how each type of test aligns with different testing categories::  


1. **Parameterized Tests**:  
  
Parameterized tests involve running the same test logic with different input parameters. Iteration can be used to run the same test logic with multiple input values.  
  
```javascript  
test.each([  
[1, 2, 3],  
[0, 0, 0],  
[-1, 1, 0],  
])('Add %i and %i to equal %i', (a, b, expected) => {  
expect(a + b).toBe(expected);  
});  
```  
  
2. **[[Test Cases Guideline & Types#Boundary Case|Boundary Testing]]**:  
  
Testing boundary conditions ensures correct behavior near limits. Boundary testing can be a type of unit testing, but it can also extend to integration testing. It involves testing the behavior of the code at boundary conditions, ensuring it handles edge cases properly. The focus is still on the code's behavior in isolation.
  
```javascript  
test('Square root of zero is zero', () => {  
expect(Math.sqrt(0)).toBe(0);  
});  
  
test('Square root of one is one', () => {  
expect(Math.sqrt(1)).toBe(1);  
});  
```  
  
3. **[[Test Cases Guideline & Types#Edge Case|Edge Cases]]**:  
  
You want to test edge cases and corner cases to ensure that the code handles extreme or uncommon scenarios properly.  Similar to boundary testing, testing edge cases can be part of unit testing, especially when you're examining how the code behaves in specific extreme scenarios.

  
```javascript  
test('Empty array should have length of zero', () => {  
expect([]).toHaveLength(0);  
});  
  
test('Division by zero should throw an error', () => {  
expect(() => {  
const result = 1 / 0;  
}).toThrow();  
});  
```  
  
4. **[[Data Driven Testing]]**:  
  
You have a large dataset, and you want to test your code against various data points. Iteration allows you to run the same test logic with multiple data points.  

Data-driven testing can span multiple levels of testing, including unit, integration, and system testing. In unit testing, you may use data-driven techniques to test a specific unit with various data points.
  
```javascript  
const data = [  
{ input: 2, expected: 4 },  
{ input: 3, expected: 9 },  
{ input: 4, expected: 16 },  
];  
  
test.each(data)('Square of %i is %i', (input, expected) => {  
expect(input * input).toBe(expected);  
});  
```  
  
5. **[[Code Coverage |Test Coverage]]**:  
  
Achieving high test coverage by testing different code paths.  

\You want to achieve high test coverage by systematically testing different scenarios within a function or component.  

Test coverage analysis is a measurement technique rather than a specific type of test. It's often used at the unit testing level to determine how much of the code is covered by your tests. Achieving high test coverage is a goal within unit testing.
  
```javascript  
function add(a, b) {  
return a + b;  
}  
  
test('Add function should cover different code paths', () => {  
expect(add(2, 3)).toBe(5);  
expect(add(-1, 1)).toBe(0);  
});  
```  
  
6. **[[Pre Acceptance Testing#^84bb7e |Regression Testing]]**:  
  
Regression testing can include unit tests, but it often extends to higher testing levels, including integration and system testing, to ensure that code changes or refactor don't introduce new issues.
  
```javascript  
test('Regression test for function foo', () => {  
// Test code for function foo  
expect(foo(1)).toBe(2);  
expect(foo(0)).toBe(1);  
});  
```  
  
7. **Performance Testing**:  
  
For performance testing, Jest provides libraries like `jest-benchmark` that can be used to measure the execution time of functions with different input sizes. and data distributions to identify performance bottlenecks.  

Performance testing typically falls into a different category, such as performance testing or load testing, which focuses on assessing the system's performance under various conditions. While unit testing can involve testing performance-critical functions, comprehensive performance testing usually happens at higher levels.
  
```javascript  
const bench = require('jest-benchmark');  
  
bench('Square root performance', (bench) => {  
bench('sqrt(10000)', () => {  
Math.sqrt(10000);  
});  
bench('sqrt(100000)', () => {  
Math.sqrt(100000);  
});  
});  
```  
  
8. **Concurrency Testing**:  
  
Testing concurrency and thread safety often requires specialized tools and libraries. Jest alone may not cover this type of testing.  
  
These examples demonstrate how to use Jest for different testing scenarios. Jest's flexibility and built-in functions like `test.each` make it a powerful tool for a variety of testing needs. However, some scenarios may require additional libraries or custom approaches.

In summary, not all the mentioned tests are strictly unit tests. Some of these testing types are associated with unit testing, while others are more commonly performed at different testing levels, such as integration, system, or performance testing. The choice of testing level and type depends on the specific goals and requirements of your testing strategy.


## More Examples

Assuming you have a coding challenge function like this:  
  
```typescript  
// codingChallenge.ts
export function sumEvenNumbers(arr: number[]): number {
  return arr.filter(num => isEven(num)).reduce((acc, curr) => acc + curr, 0);
}

export function isEven(num: number): boolean {
  return num % 2 === 0;
}

```  
  
Now, let's create tests for different types of tests:  
  
1. **Unit Tests:**  
  
```typescript  
// unit.test.ts  
import { sumEvenNumbers } from './codingChallenge';  
  
test('sumEvenNumbers unit test', () => {  
const result = sumEvenNumbers([1, 2, 3, 4, 5, 6]);  
expect(result).toBe(12);  
});  
```  
  
2. **Integration Tests:**  
  
```typescript  
// integration.test.ts
import { sumEvenNumbers, isEven } from './codingChallenge';

test('sumEvenNumbers integration test', () => {
  const numbers = [1, 2, 3, 4, 5, 6];
  const result = sumEvenNumbers(numbers);
  
  // You can also test the helper function isEven in the integration test
  expect(isEven(2)).toBe(true);
  
  expect(result).toBe(12);
});

```  
  
3. **Functional Tests:**  
  
```typescript  
// functional.test.ts  
import { sumEvenNumbers } from './codingChallenge';  
  
test('sumEvenNumbers functional test', () => {  
const numbers = [1, 2, 3, 4, 5, 6];  
const result = sumEvenNumbers(numbers);  
expect(result).toBe(12);  
});  
```  
  Same as unit test since dealing with one function to create a true functional test for this scenario, you would typically set up a test environment that simulates how the `sumEvenNumbers` function is used within a larger context, considering factors like input validation, handling of edge cases, and interactions with other parts of the system.
  
4. **Boundary Tests:**  
  
```typescript  
// boundary.test.ts  
import { sumEvenNumbers } from './codingChallenge';  
  
test('sumEvenNumbers boundary test', () => {  
const result = sumEvenNumbers([]);  
expect(result).toBe(0);  
const result2 = sumEvenNumbers([2]);  
expect(result2).toBe(2);  
});  
```  
  
5. **Performance Tests:**  
- Measure execution time using Jest's timer functions.  
  
```typescript  
// performance.test.ts  
import { sumEvenNumbers } from './codingChallenge';  
  
test('sumEvenNumbers performance test', () => {  
const numbers = new Array(1000000).fill(2); // Array with a million 2's  
const start = Date.now();  
const result = sumEvenNumbers(numbers);  
const end = Date.now();  
const duration = end - start;  
expect(result).toBe(2000000);  
expect(duration).toBeLessThan(100); // Check if execution is fast enough  
});  
```  
  
These test examples cover different types of tests, from unit and integration tests to functional and boundary tests, and even performance testing. You can adapt these examples to your specific coding challenges to ensure the correctness and robustness of your code.