---
tags:
  - databases
  - tables
  - schema
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses different DBMS Keys.
Status: Done
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish: false
---
In the realm of Database Management Systems (DBMS), a database key holds a critical role, representing either a singular attribute or a combination of attributes. Its primary function is to uniquely identify a tuple (row/record) within a relation (table). However, the significance of keys extends beyond mere identification, playing a pivotal role in establishing relationships across various tables and columns within a relational database.

### Understanding Database Management Systems (DBMS)

DBMS stands as the cornerstone for managing data, providing a platform to store, retrieve, and query information. It serves as the intermediary interface between end-users and databases, enabling users to seamlessly create, read, update, and delete data within the database.

A DBMS accommodates diverse data architectures, including relational databases (RDBMS), document stores, key-value stores, column-oriented databases, graph databases, and more. Well-known DBMSs encompass MongoDB, Cassandra, Redis, MySQL, Microsoft SQL Server, PostgreSQL, SQLite, Oracle, and numerous others.

![[ID Generators.gif]]

#### Primary Key
A primary key, such as `ID` or `SSN`, uniquely identifies each record in a table. 

- It may accept null values, but it is generally advisable to enforce uniqueness and non-null constraints.
- Ensures data integrity and uniqueness.
- Used as a reference in foreign keys of other tables.

#### Foreign Key
A foreign key establishes relationships between tables by referencing primary keys in another tabled.

It Enforces referential integrity by ensuring that values in the foreign key match values in the referenced primary key.

#### Foreign Composite Key:
- A foreign key that is composed of multiple columns, referencing a composite primary key in another table.


#### Composite Key
A composite key, unique to a particular table, is formed by combining two or more columns. This amalgamation creates a distinctive identifier, ensuring the unique identification of tuples within the specified table.

While technically a candidate key as the composite key verifies uniqueness, composite keys are only formed when the particular column or columns are used in combination with each other. 

- Comprising multiple columns to achieve a distinctive record identification.
- Involves the amalgamation of two or more attributes to form a singular, unique identifier.

- { Name, Phone }
- In general you may want to avoid using.


#### Compound Key:
- Similar to a composite key, a compound key is composed of multiple columns, but these columns may individually represent partial keys.

#### Unique Key
A unique key ensures uniqueness but allows one null value. Examples include `SSN`, `Email`, or { Name, Phone }.

Often used when a column needs to have unique values but doesn't need to serve as the primary key.

#### Super Key
A super key is a set of attributes that uniquely identifies a tuple.

- A set of one or more keys that, taken collectively, can uniquely identify a record in a table.
- Includes more attributes than necessary for uniqueness.

For instance, in an `Employee` table:

- { ID }
- { SSN }
- { ID, SSN }
- { ID, Name }
- { ID, Phone }
- { Name, Phone }
- { Name, Email }
- { Name, SSN, Phone }
- { ID, SSN, Phone }

#### Candidate Key
A candidate key is the minimal super key without overlaps and null values.

- A minimal set of attributes that can uniquely identify a record.
- Among the super keys, a candidate key is chosen as the primary key.

Examples include:
- { ID }
- { SSN }
- { Email }
- { Name, Phone }


#### Alternate/Secondary Key
Alternate keys are not the primary key, including candidate keys. 

- A candidate key that is not selected as the primary key.
- Often retained as a backup option for uniqueness.

Only one choice for an alternate key is allowed, such as:
- { SSN }


#### Artificial Key
Artificial keys have no business relevance but handle data management challenges. They are often used in complex primary key situations.

#### Surrogate Key
A surrogate key is an auto-generated key used to bring datasets together efficiently, serving as an alternative to a Union, cast, or convert operation.

- A key introduced as an artificial identifier (usually numeric) to serve as the primary key.
- Often used when natural keys are unsuitable or to simplify relationships.

#### Natural Key
A natural key is an alternative key already present in the table and is unique, such as a social security number.

Ensure data integrity by choosing appropriate primary and alternate keys based on the unique characteristics of the data being modeled.
