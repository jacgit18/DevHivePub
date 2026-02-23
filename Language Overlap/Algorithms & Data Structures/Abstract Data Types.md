---
tags:
  - dataType
  - abstraction
  - dataStructure
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Abstract Data Types
Status: Refinement
Started: 
EditDate: 2024-02-29
Relates: 
Peer Reviewed: 0
dg-publish:
---
![[Abstract Data.gif]]

#todo/BAU/noteRefine 
- [ ] combine with other notes that make sense, or delete 

Abstract Data Types (ADTs) are conceptual entities in computer science that define a set of data and the operations that can be performed on that data without specifying the details of how these operations will be implemented. This approach allows for the separation of the 'what' from the 'how,' enabling the focus on what operations are to be performed without getting entangled in the specifics of how these operations are executed in any particular programming language.

### Understanding ADTs Through Analogies:

Imagine a smartphone: At an abstract level, you're aware of its specifications—RAM, processor, screen size, etc. You also know about the operations it can perform, such as calling, texting, and video streaming. The abstract view doesn't delve into the specifics of how these operations are executed; it just specifies that these operations are possible.

Similarly, consider an array: Abstractly, you understand it as a collection of elements that can be accessed via indexes. You know you can perform operations like reading, modifying, and sorting the elements. However, the abstract view doesn't concern itself with how these operations are implemented—this varies with programming languages.

### ADTs in Data Structures:

Many data structures are considered Concrete Data Types (CDTs) because they come with specific implementations. However, some data structures, conceptualized as ADTs, can be implemented in numerous ways, with the specifics varying across different programming environments.

ADTs provide a framework for understanding the behavior of data structures without locking into any one implementation. For example, a stack ADT defines behavior (like push and pop operations) without specifying how these behaviors are to be achieved. This conceptual framework allows for flexibility in implementation across different programming languages.

### Examples of ADTs:

- **Array, List, Map, Queue, Set, Stack, Table, Tree, and Vector:** These are all examples of ADTs, each with a range of possible implementations or CDTs. A container could be seen as a higher-level ADT encompassing these.
  
- **Linked List:** This ADT represents a sequence of nodes connected in a linear fashion. The abstract definition includes operations for inserting and removing nodes but does not detail how these operations are implemented.

### ADT Operations:

- **Traversal:** For instance, traversing a linked list involves moving from node to node, an operation defined at the abstract level without specifying how traversal is to be programmed.

### Interface vs. Implementation:

- ADTs are about the interface—the set of operations that can be performed. Since ADTs don't specify implementation, discussing the time complexity of an ADT operation in abstract terms is not meaningful; time complexity is a property of a specific implementation.

In essence, ADTs serve as a blueprint for data structures, outlining the required operations and behaviors without confining to any specific programming language or implementation details. This abstraction fosters versatility and innovation in how data structures are implemented and used across different software projects.