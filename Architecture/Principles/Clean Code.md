---
tags:
  - CodebaseDecision
  - MacroCodebaseDecision
  - MicroCodebaseDecision
  - bestPractices
  - ClassStructure
  - principles
  - languageOverlap
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses clean code.
Status: Refinement
Started: 
EditDate: 2024-03-06
Relates: 
Peer Reviewed: 0
dg-publish:
---
Clean code is clear, understandable, and maintainable. When you write clean code, you're thinking of the others who may read and interpret it later. Help others understand the purpose of your code so they can change it eventually.

Clean code principles lead to highly modular source code easier to read and test. If you think of these practices as part of a house, clean code is the foundation. Implementing clean code principles is a foundational skill that pays off especially well when refactoring code or testing code under test. 

#todo/High/Dev  
- [ ] Finish Reading [[Clean Code A Handbook of Agile Software Craftsmanship.pdf#page=71&offset=-48,671,1|Clean Code A Handbook of Agile Software Craftsmanship, Function Arguments |Pg 71]]

## General rules
- Follow standard conventions.
- Keep it simple stupid. Simpler is always better. Reduce complexity as much as possible.
- Boy scout rule. Leave the campground cleaner than you found it.
- Always find root cause. Always look for the root cause of a problem.
- Never merge your code or create a pull request with errors or warnings in the terminal from Eslint or otherwise. 
- Your text editor should honor .editorconfig files. Our editor config sets the editor to match Prettier and Eslint rules where possible. Tabs, for example, will be two spaces. This is a common JavaScript development standard.

## Design rules
- Keep configurable data at high levels.
- Prefer polymorphism to if/else or switch/case.
- Separate multi-threading code.
- Prevent over-configurability.
- Use dependency injection.
- Follow Law of Demeter. A class should know only its direct dependencies.

## Understandability tips
- Be consistent. If you do something a certain way, do all similar things in the same way.
- Use explanatory variables.
- Encapsulate boundary conditions. Boundary conditions are hard to keep track of. Put the processing for them in one place.
- Prefer dedicated value objects to primitive type.
- Avoid logical dependency. Don't write methods which works correctly depending on something else in the same class.
- Avoid negative conditionals.



 Code Reusability: Code Reusability is the ability to reuse code in different parts of an application or in different applications. It is an important skill that can help developers save time and effort. However, code reusability is a secondary skill that is dependent on good design patterns and clean code.


### Feature check
- When learning a new feature/technology or library  think about how commonly used and at what stage of the development process or Codebase contribution process will it be used at to decide on the time you give to it in terms of the breath and depth 
	- like if your deciding to go in depth into something you may do it immediately or in the future like with java class loaders or loggers
- or over the long term like learning all the different Java versions in-depth or at least in breath over time in small chunks 


## [[Naming Conventions]]
High level description


## [[Functions rules]]
High level description




Breaking down code into modular functions is a good practice for improving readability, maintainability, and reusability. Besides breaking out conditional logic, here are some other types of functionality that you might consider making modular with helper functions:  
  
1. **Input Validation:**  
- If your code involves user input or external data, create modular functions to validate and sanitize input. This helps ensure that the data your program receives is correct and safe to process.  
  
2. **Data Transformation:**  
- If your code manipulates or transforms data in a specific way, encapsulate that logic into a function. This promotes code reuse and makes it easier to understand and modify the transformation process.  
  
3. **Error Handling:**  
- Create separate functions to handle different types of errors or exceptions. This can make error-handling logic more readable and centralized.  
  
4. **File I/O Operations:**  
- If your code interacts with files, consider breaking out file I/O operations into separate functions. This could include reading from or writing to files, parsing file formats, or managing directories.  
  
5. **Algorithmic Operations:**  
- If your code involves complex algorithms, break them down into smaller, modular functions. This not only makes your code more readable but also allows for easier testing and optimization of specific parts.  
  
6. **Logging and Debugging:**  
- Create modular functions for logging messages or debugging information. This can be particularly useful for enabling or disabling debugging features easily.  
  
7. **Formatting and Display:**  
- If your code involves formatting data for display, consider creating functions responsible for formatting strings, numbers, or other types of output.  
  
8. **Utility Functions:**  
- Identify common operations or computations that are used in multiple places within your code and abstract them into utility functions. These functions can be reused across different parts of your program.  
  
9. **Network Operations:**  
- If your code interacts with network resources, encapsulate networking operations into separate functions. This includes tasks like making HTTP requests, handling sockets, or managing network connections.  
  
10. **Configuration Management:**  
- If your code relies on configuration settings, create modular functions to load and manage configurations. This makes it easier to adapt your code to different environments.  
  
By modularizing your code in this way, you not only improve the organization and readability of your code but also make it easier to maintain, test, and extend in the future. Each modular function should ideally encapsulate a specific piece of functionality, promoting the principles of separation of concerns and modularity.






## Comments rules
![[Eye in the Detail.gif]]
Comments are essentially a type of documentation that requires smart maintenance. Your code should speak for itself through well-chosen conventions. Utilize descriptive verbs in method and function names. Exclude commented-out code in production applications. Steer clear of todo's. Employ concise, one-line comments for crucial legal or explanatory information, such as regular expressions. Comment when there's an issue with a specific line of code.

Comments should explain _Why_

When we're writing code, there are times when we need to pass on more information, like _Why_ a decision was made, _Why_ a piece of code was needed, or some additional context that's relevant to it. These are are the kinds of things that should be commented.

Maybe there's some obscure use-case that needs to be considered when editing a particular chunk of code that isn't immediately obvious. This should be commented clearly so when the next developer returns to this piece of code next week, next month, or even next year, they'll take that information into consideration as well and not re-introduce some bug, or break some other piece of functionality.

Perhaps something out of the "normal" had to be done in a particular area of the code because of how some third party dependency works. Rather than expecting the rest of the team to run into the same issue and have to solve it themselves, a comment explaining the situation would save them time later (potentially hours or even days).

Understanding _Why_ something was done the way it was provides tremendous insight, especially when there were multiple paths to choose from, or if there was indirect context that influenced the decision. In my personal opinion, commenting that _Why_ is not just a "nice to have" in your code, it's vital. It's vital for maintainability, for knowledge sharing, and most importantly for setting other members of the team up for success.

Knowing when the _Why_ should be included can be tough sometimes. Most people, myself included, forget that we have knowledge and understanding of things that others don't. We move through our lives assuming or expecting others to either know that stuff, or to easily figure it out...even if it took _us_ months of collecting different pieces of information to gain that knowledge. So when you're writing that next piece of code, really step back and think to yourself, what information are you assuming the next developer will have in order to understand it? Then, write that stuff down in a comment.

- Always try to explain yourself in code.
- Don't be redundant.
- Don't add obvious noise.
- Don't use closing brace comments.
- Don't comment out code. Just remove.
- Use as explanation of intent.
- Use as clarification of code.
- Use as warning of consequences.


## Source code structure
- Separate concepts vertically.
- Related code should appear vertically dense.
- Declare variables close to their usage.
- Dependent functions should be close.
- Similar functions should be close.
- Place functions in the downward direction.
- Keep lines short.
- Don't use horizontal alignment.
- Use white space to associate related things and disassociate weakly related.
- Don't break indentation.




In TypeScript, it's generally considered best practice to initialize variables when declaring them, and to provide explicit types whenever possible. This contributes to better code readability, maintainability, and helps catch potential errors early in the development process.  
  
Here's why initializing variables is often preferred:  
  
1. **Type Inference:** When you initialize a variable with a value, TypeScript can infer its type based on that value. This allows TypeScript to catch type-related errors during development.  
  
```typescript  
let count = 5; // TypeScript infers that count is of type number  
```  
  
2. **Avoid `undefined`:** Initializing variables helps to avoid unintentional use of `undefined` values. If a variable is not assigned a value initially, its type becomes `any`, and it may lead to runtime errors if not handled properly.  
  
```typescript  
let name: string; // This variable is of type 'any' and can be undefined  
```  
  
3. **Readability:** Initializing variables at the point of declaration makes the code more readable by providing a clear starting point for the variable's value.  
  
```typescript  
let isEnabled = true; // Clear indication of the initial state  
```  
  
However, there are cases where declaring a variable without initializing it might be necessary or preferred. For example, when you want to declare a variable first and assign a value to it later based on some condition.  
  
```typescript  
let result: number;  
  
if (someCondition) {  
result = 42;  
} else {  
result = 0;  
}  
```  
  
In conclusion, prefer initializing variables at the point of declaration to leverage TypeScript's type inference and improve code clarity. Only declare variables without initialization when there's a specific reason to do so.


## Objects and data structures
- Hide internal structure.
- Prefer data structures.
- Avoid hybrids structures (half object and half data).
- Should be small.
- Do one thing.
- Small number of instance variables.
- Base class should know nothing about their derivatives.
- Better to have many functions than to pass some code into a function to select a behavior.
- Prefer non-static methods to static methods.

## Tests
- One assert per test.
- Readable.
- Fast.
- Independent.
- Repeatable.

# Code smells(relates to[[GRASP Design Principles | Grasp]])

Code Smells are a great term for when reading code, the code may be valid, it may work, but there is something about it that just doesn’t smell right.

It’s often a clue, a warning sign of a deeper problem, that there is a part in the code indicates violation of fundamental design principles and negatively impact design quality.

And here are just a few examples of what we mean by a code smell.

## Long Method

One would be the idea of a long method. We open up a method to read it, it has got many lines. This is the kind of thing that really needs to be split up into much smaller methods.

## Identifiers

Working with very short or very long identifiers. Aside from using letters like ‘i’ for indexes and iteration, we shouldn’t be expecting to see variables called A and B and C in real code.


## The God Object

This is where you have one master object that tries to do everything in the program, or at least one object that seems to be doing very different responsibilities that have nothing to do with each other.

It’s a clue that this needs to be revisited and broken apart into the right kind of objects.

## Feature Envy

And then there’s feature envy. If a class seems to do very little except it uses all the methods of one other class, it’s another sign that you need to rethink the roles of one or the other.


- Rigidity. The software is difficult to change. A small change causes a cascade of subsequent changes.
- Fragility. The software breaks in many places due to a single change.
- Immobility. You cannot reuse parts of the code in other projects because of involved risks and high effort.
- Needless Complexity.
- Needless Repetition.
- Opacity. The code is hard to understand.









**Effective Code Reviews:**

Successful code reviews necessitate clear context through comments and descriptions. Engaging in polite and constructive discussions is pivotal for thorough assessments. The role of reviewers, whether managers, tech leads, or engineers, significantly impacts the duration of the review process. Evaluation should encompass aspects like tests, comments, variable/function naming, and the automation of the build pipeline.

Inquiries about deployment procedures, staging environments, and canarying shed light on team dynamics and workflow, enhancing collaboration and understanding.

**Comprehensive Review Considerations:**

Beyond the code structure, it's essential to inquire about authentication, authorization, and data models during code reviews. Assessing test coverage ensures robustness in code functionality.

Identifying clear input and output patterns within the codebase helps maintain orientation and logic comprehension. Regularly revisiting these elements contributes to a deeper understanding of the codebase and the logic being developed.



**Codebase Tips:**

Deprecation in programming involves marking older code as obsolete without immediate removal to prevent regression errors. Understanding the reasons behind new features and their priorities aids comprehension. Keeping track of key information and submitting findings when reassigned to new tasks enhances communication.

**Debugging:**

Debugging is an art that involves reassessment and abstraction. Taking a step back, abstracting problems to a more general level, and examining perspectives contribute to effective debugging. Utilizing the `debugger` statement in code and browser consoles facilitates the process.


**Docker**

Avoid unnecessary Docker builds without recreating the package file. Incrementally adding npm packages and committing changes minimizes the risk of breaking existing functionality.


**Tips to Understand the Codebase:**

Refactoring, creating methods, and adding tests contribute to a clearer understanding of the codebase.

**Use Abstraction to Your Advantage:**

Abstraction, hiding implementation details, focuses on functionality rather than implementation. Interview problem-solving benefits from abstraction by breaking code into smaller, purpose-specific functions. Identifying functions that would simplify the process aids in structuring code effectively.

Breaking down complex problems into manageable components during interviews showcases clarity of thinking. Writing code assuming hypothetical functions and later implementing them allows for a basic working code, clarity, and flexibility in handling minutiae.

This approach promotes clarity in thinking and code organization, making it easier to tackle intricate problems.
