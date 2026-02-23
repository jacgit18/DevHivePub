---
tags:
  - databases
  - tables
  - schema
author:
  - jacgit18
Purpose: This documentation discusses Foreign Key Referential Actions.
Status: Refinement
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
[[Database Table Relationship Types#Referential Integrity |Referential integrity]]  is constrained by foreign keys, ensuring that values in a particular table match values that are found in a different table. 

These referential actions reinforce the integrity of the table structure, reducing the possibility of error by ensuring that referenced columns only contain unique sets of values. 

Foreign keys can also accept null values, but it’s important to note that this may restrict their ability to protect the integrity of the referenced column, as null values are not checked. 

***Tip***: Best practices indicate using a <mark style="background: #FF5582A6;">NOT NULL</mark> constraint when creating foreign keys to maintain the structural integrity of the database. 

Creating a data structure that is flexible and extensible enough for long-term use can become increasingly difficult as data complexity and volume soars. The addition of unstructured data can easily result in errors. 

Foreign keys are an extremely valuable component, helping ensure that your database is clear, consistent, and able to rapidly deliver accurate results. 

  