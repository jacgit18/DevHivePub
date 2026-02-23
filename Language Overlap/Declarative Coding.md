---
tags:
  - CodebaseDecision
  - declarative
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses declarative coding.
Status: Done
Started: 
EditDate: 2024-03-05
Relates: 
Peer Reviewed: 0
dg-publish:
---
Declarative programming emphasizes specifying "what should be done" at a high level, focusing on logic, concepts, and the desired end result without detailing specific steps. It encompasses various paradigms, such as Functional, Logic, and Data-Driven programming.

1. **Functional Programming:**
   - **Definition:** Grounded in mathematical principles, it revolves around pure functions—small, composable functions. It often employs recursion and favors immutability.
   - **Characteristics:**
     - **Stored Data:** Typically uses stored data and avoids loops in favor of recursive functions.
     - **Side Effects:** Strongly discourages side effects; functions are expected not to modify external state.
     - **Ease on Abstract Issues:** Easier to work on abstract problems, though might be farther from machine specifics.

2. **Logic Programming:**
   - **Usage:** Limited, primarily in research contexts.
   - **Example:** [Logic Programming Article](https://towardsdatascience.com/logic-programming-rethinking-the-way-we-program-8706b2adc3f1)

3. **Data-Driven Development:**
   - **Focus:** Centered around database schema, emphasizing the importance of data structures.

**Declarative Characteristics:**
- **Complexity:** Declarative programming is complex but excels in handling mathematical and data-related problems. However, it can be challenging to scale.
- **Language Examples:**
  - **SQL:** For database queries.
  - **Prolog:** For logical programming.

**Other Declarative Languages:**
1. **XSLT (Extensible Stylesheet Language Transformations):**
   - **Purpose:** Transforms XML documents into other formats (HTML, PDF, plain text).

2. **CSS (Cascading Style Sheets):**
   - **Purpose:** Describes the presentation of HTML or XML documents (fonts, colors, layout).

3. **Datalog:**
   - **Purpose:** Logic programming language for querying and reasoning about databases and knowledge bases.

4. **YAML (YAML Ain't Markup Language):**
   - **Purpose:** Describes data structures and configurations in a human-readable and machine-friendly format.

5. **GraphQL (Graph Query Language):**
   - **Purpose:** Describes and queries data in a GraphQL API, specifying data requirements and structure in a single request.

#### JavaScript and Declarative Coding
Spread Operator
  ```javascript
  const numbers = [1, 2, 3];
  console.log(...numbers); // Returns the whole array

  let numbersOne = {prop1: 1, prop2: "val2"};
  let numbersTwo = {...numbersOne, prop3: "val3"};
  console.log(numbersTwo);
  ```
**Explanation:** The spread operator in JavaScript, used between two operators, falls under declarative coding. It allows for a concise and declarative way to manipulate arrays or objects by spreading their elements or properties.