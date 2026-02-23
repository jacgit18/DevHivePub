---
tags:
  - cohesion
  - languageOverlap
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses types of Cohesion in software engineering.
Status: Refinement
Started: 
EditDate: 2024-03-06
Relates: "[[Coupling vs Cohesion]]"
Peer Reviewed: 0
dg-publish:
---
Cohesion measures the degree of intra-dependability within elements of a module, indicating how closely related and focused the responsibilities of a module are. The higher the cohesion, the better the program design. There are seven types of cohesion, listed from best to worst:

### 1. Functional Cohesion(Best)
- **Description**: All elements of the module work together to perform a single well-defined task.
- **Examples**: Reading a transaction record, computing the cosine angle, assigning a seat to an airline passenger.
- **Advantages**: High focus, single-minded purpose.

### 2. Sequential Cohesion
- **Description**: Output from one element serves as input for the next.
- **Examples**: Cross-validate records, format modules, use and format raw records.
- **Advantages**: Easy maintenance but limited reusability due to sequential dependency.

### 3. Communicational Cohesion
- **Description**: Elements operate on the same data set or produce the same output.
- **Examples**: Customer detail modules, including account number retrieval, name, and loan balance queries.
- **Advantages**: Focus on shared data, though less flexible than functional cohesion.

### 4. Procedural Cohesion
- **Description**: Elements grouped because they follow a specific sequence of execution.
- **Examples**: Reading, writing, editing records, and zero padding numeric fields.
- **Advantages**: Logical grouping by sequence, found often in main program modules.

### 5. Temporal Cohesion
- **Description**: Elements are related by their timing (e.g., executed at the same time).
- **Examples**: Initialization tasks like setting counters to zero or opening files.
- **Advantages**: Common in initialization and termination modules, though with limited reusability.

### 6. Logical Cohesion
- **Description**: Elements perform related operations, decided at runtime.
- **Examples**: Modules that display records, where the type of record determines the operation.
- **Advantages**: Groups similar operations, but relies on control coupling.

### 7. Coincidental Cohesion(Worst)
- **Description**: Elements are grouped arbitrarily, without a meaningful relationship.
- **Examples**: Miscellaneous functions like customer record usage, sales calculations.
- **Advantages**: Generally considered poor design due to lack of clear relationship, making maintenance difficult.

## Advantages of High Cohesion in Software Engineering
High cohesion within modules offers several benefits:
- **Simplified Complexity**: Modules are easier to understand, develop, and maintain when they focus on a single responsibility.
- **Improved Maintainability**: Changes in one module have minimal impact on others, simplifying updates and bug fixes.
- **Enhanced Reusability**: Well-defined, cohesive modules can be more easily reused across different parts of a project or in new projects.
- **Balanced Design**: Cohesion helps in achieving a balance between module complexity and inter-module coupling, fostering better software architecture.

For more detailed explanations and examples, refer to academic resources such as the [University of Calgary's course materials on software design and cohesion](http://pages.cpsc.ucalgary.ca/~eberly/Courses/CPSC333/Lectures/Design/cohesion.html).