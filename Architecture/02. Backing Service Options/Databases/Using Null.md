---
tags:
  - databases
  - schema
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Null in the the context of DBMS.
Status: Done
Started: 2024-01-11
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish: false
---
In SQL, it's crucial to explicitly state whether a column allows NULL values meaning that the value is optional vs not null meaning it is required, rather than relying on defaults. Assuming null-ability based on defaults can lead to confusion, especially when rules governing the omission of this option for a given datatype are complex and not easily explainable. It's essential to avoid assumptions that your team or successors might not comprehend.

Specifying nullability is vital in a relational database designed for efficient data integrity. Constraints, defined through NULL or NOT NULL, act as safeguards against undesirable data. Use NOT NULL for columns that must not contain nulls, creating a constraint to prevent accidental omissions.

Allowing null values in a column complicates aggregation and may yield unexpected results in WHERE clauses. Functions like ISNULL(), IFNULL(), and NULLIF() become necessary for handling nulls effectively.

Never assume a column is nullable if not explicitly specified. This article emphasizes the importance of always indicating whether a column allows null values. While it doesn't delve deeply into the debate on NOT NULL constraints, it underscores the need to express preferences.

Contrary to common belief, omitting the NOT NULL constraint doesn't automatically make a column nullable. The actual nullability depends on factors such as datatype, database settings, and connection settings. Memorizing all these rules and ensuring consistent connection types in DDL scripts can be challenging. To simplify, adhere to the golden rule: always specify whether your columns are NULL or NOT NULL.

The article will now explore the various factors influencing whether a column receives a NOT NULL constraint when not explicitly specified.