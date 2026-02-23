---
tags:
  - databases
  - tables
  - schema
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Functional Dependencies.
Status: Refinement
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---


![[Functional Dependencies.png]]

A **functional dependency (FD)** defines a relationship between two sets of attributes in a relational database. Specifically, for any two tuples `t1` and `t2` in relation `r`, if `t1[X] = t2[X]`, then it follows that `t1[Y] = t2[Y]`. In essence, this implies that the value of the X component of a tuple uniquely determines the value of the Y component.

The notation for a functional dependency is X → Y, where X is termed the **determinant** and Y is the **dependent**.

## Closure of a Set of Attributes

A **closure** is the complete set of all possible functional dependencies derived from a given set of FDs. It is denoted as F+, where F represents the set of FDs for relation R.

Understanding the closure is crucial for identifying the super key of the relationship and determining whether an FD can be inferred or if it is redundant. After establishing a set of functional dependencies on a relation, the subsequent step involves finding the Super Key for that relation (table).

The closure of a set of attributes is pivotal in deciding whether an attribute (or set of attributes) in any table can function as a key for that table. The set of attributes functionally dependent on attribute X is termed the **Attribute Closure of X**, denoted as X+.

Several rules guide the determination of F+:

1. **Reflexivity:** If X is a superset of Y or Y is a subset of X, then X → Y.

2. **Augmentation:** If X → Y, then XZ → YZ. Additionally, if Z ⊆ W and X → Y, then XW → YZ.

3. **Transitivity:** If X → Y and Y → Z, then X → Z.

4. **Union:** If X → Y and X → Z, then X → YZ.

5. **Decomposition:** If X → YZ, then X → Y and X → Z.

6. **Pseudo-Transitivity:** If X → Y and YW → Z, then XW → Z.

Ensuring adherence to these rules facilitates a comprehensive understanding of functional dependencies and their implications on the structure of a relational database.