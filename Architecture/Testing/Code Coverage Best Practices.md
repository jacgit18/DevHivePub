---
tags:
  - career
  - CapitalOne
  - bestPractices
  - testing
  - systemDesign
author:
  - gitUserNamePlaceHolder
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: 
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
For decades, we have driven software testing initiatives across large software companies, consistently advocating for the use of **code coverage data** to assess risk and identify gaps in testing. However, the topic of code coverage is polarizing. Discussions around it often derail into unproductive debates, with people entrenched in opposing views. This document provides tools to guide these discussions towards productive, pragmatic use of coverage data to improve code health.

## The Value of Code Coverage

**Code coverage** offers significant benefits to the developer workflow. While it’s not a perfect measure of test quality, it provides a reasonable, objective, industry-standard metric with actionable insights:

- Minimal human interaction is required.
- It applies universally across products.
- Numerous tools are available for most programming languages.

That said, code coverage should not be your sole metric. It compresses a lot of information into a single number, and its lossy nature means it must be used alongside other techniques to get a more complete view of your testing efforts.

---

## Benefits Beyond the Metric

Though it’s unclear if code coverage alone reduces defects, **our experience shows** that focusing on it can bring long-term benefits:

- **Cultural Shift**: Teams that prioritize code coverage tend to treat testing as essential and often build better testability into their product designs.
- **Better Code Quality**: Coverage-focused teams tend to write more modular, cleaner code, making it easier to test and review.
- **Engineering Excellence**: Prioritizing coverage can foster a focus on overall code health and engineering excellence.

---

## The Limitations of High Coverage

Achieving high code coverage does not guarantee quality in tests:

- **False Sense of Security**: Chasing 100% coverage can be misleading and wasteful, often leading to technical debt.
- **Coverage ≠ Quality**: Code coverage only ensures that lines of code were executed by tests, not that they were tested correctly. Edge cases may still be missed.
  
A more valuable approach is using **[mutation testing](https://research.google/pubs/state-of-mutation-testing-at-google/)** to assess whether tests are effectively exercising the code.

---

## Low Coverage: A Clear Warning

On the flip side, **low code coverage** guarantees that large areas of your product are untested, which increases the risk of pushing bad code to production. A lot of the value in code coverage comes from highlighting **what’s not covered**, directing attention to areas that need testing.

---

## There Is No Universal “Ideal” Code Coverage Number

The "ideal" level of code coverage depends on various factors:

- **Business impact and criticality** of the code
- **Frequency of changes** to the code
- **Code complexity and expected lifespan**

While broad mandates like "every team should have X% coverage" aren’t practical, coverage goals should be set by **product owners** with deep domain knowledge.

At Google, we suggest the following guidelines:

- **60%** coverage: acceptable
- **75%** coverage: commendable
- **90%** coverage: exemplary

---

## Focus on Improving Low Coverage, Not Maximizing High Coverage

Rather than obsessing over moving from **90% to 95% coverage**, focus on more impactful changes, like moving from **30% to 70%**. Prioritize improving the **coverage of newly written code**.

### Human Judgment Matters

What’s *not covered* is often more meaningful than what is. Focus on the **specific code lines and behaviors not covered** and decide if the risks are acceptable. Embedding this discussion into the **code review process** makes reviews faster and more effective.

---

## Incremental Steps to Improve Coverage

If you inherit a legacy system with poor coverage, improving it can seem daunting. But by adopting the **"boy scout rule"** (leave the code cleaner than you found it), you can make incremental improvements over time. Focus especially on covering frequently changing code.

---

## Unit Tests Aren’t Everything

**Unit test coverage** is only one part of the picture. **Integration** and **system tests** are just as important. Combining coverage data from all sources gives you a more comprehensive view of your testing efforts.

Be mindful that integration and end-to-end test coverage can sometimes be **incidental** rather than deliberate. Nonetheless, incorporating it into your analysis will help identify untested areas that might not be covered in unit tests.

---

## Using Code Coverage as a Gating Mechanism

To ensure test quality, you can gate deployments based on code coverage standards. There are many approaches you can use, such as:

- Gating on overall code coverage
- Gating on **new code** coverage
- Gating on **coverage deltas**

It’s important to guard against turning these gates into **checklist exercises**, as that can lead to unintended outcomes. Drops in code coverage that violate agreed-upon standards should block code from being merged or deployed to production.

---

## Conclusion

Code coverage is a valuable tool, but it should be used pragmatically. **Combine it with other testing strategies**, focus on what’s not covered, and cultivate a culture of engineering excellence that treats testing as an essential part of development.

By fostering **thoughtful discussions** around code coverage, setting appropriate goals, and embedding coverage analysis into the development process, teams can improve testing effectiveness and overall code health.

---

In programming, especially within QA testing, testing alternative business logic flows often means ensuring that different branches in code (like if, else if, else, and catch blocks) handle both expected and unexpected conditions correctly.  
  
For instance:  
  
1. If/Else If/Else Blocks: These conditionals allow you to specify different behaviors based on specific conditions. In testing, you'd check each possible path to make sure that each branch behaves as expected and covers all cases.  
  
  
2. Error Handling (Catch Blocks): This is essential for testing how your application handles exceptions or errors. It’s important to verify that, when unexpected issues arise, the catch block gracefully handles them without crashing the system or exposing vulnerabilities.  
  
  
3. Edge Cases and Business Logic Variants: You’d want to make sure that all possible logical paths are covered, including edge cases that may trigger specific business logic flows.  
  
In QA, you might create test cases for each logical branch, covering normal scenarios and edge cases, to ensure that your code’s logic is robust and that alternative flows handle each condition correctly.