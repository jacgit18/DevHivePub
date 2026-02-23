---
tags:
  - databases
  - query
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses database transaction.
Status: Done
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish: true
---
A database transaction is  a sequence of operations that is performed on a database that can also be performed as a single unit of work typically through [[Stored Procedure]] or alternative methods.

PostgreSQL ensures that all operations within a transaction either complete entirely or none of them do.

This property prevents incomplete changes in case of a failure during a transaction.

Transactions typically begin with a BEGIN command and end with a COMMIT or ROLLBACK.

#### Commit and Rollback
- **Commit:** Marks the successful end of a transaction, indicating that changes should become permanent.
- **Rollback:** Marks the unsuccessful end, discarding any changes made since the beginning of the transaction.

### [[Distributed Transactions]]
Distributed transactions are transactions that span multiple networked databases or resources. They ensure that a transaction affecting multiple systems can be completed as a single unit of work, maintaining data consistency and integrity across all involved systems.

### [[Transaction Locking]]
Database transaction locking is a mechanism used to ensure data integrity and consistency when multiple transactions occur simultaneously in a database. 


### Atomic Writes

**Atomicity** refers to the principle that a series of operations (typically a transaction) are indivisible and irreducible. This means that a write operation (or a series of write operations within a transaction) must either be fully completed or not executed at all. In other words:

- **All-or-nothing:** If a write operation is atomic, either all of the data is written, or none of it is.
- **No partial writes:** There are no intermediate states visible to other transactions or processes. Other transactions cannot see the data being partially written.
- **Rollback capability:** If something goes wrong during the write operation, the system can roll back to the state before the write operation began.

### Serializable Writes

**Serializability** is a property of transaction schedules (sequences of operations) that ensures the final outcome of executing concurrent transactions is the same as if the transactions were executed serially, one after the other, without any overlap. Specifically:

- **Consistency:** Even though transactions are executed concurrently, the end result should be as if they were executed in some sequential order.
- **Isolation:** Transactions are isolated from each other in such a way that their interleaved execution does not produce results that could not be produced by some serial execution of those transactions.
- **Conflict avoidance:** Operations that could potentially conflict are managed to ensure that their combined effect is consistent with a serial order of execution.

### Key Differences

- **Scope:** Atomicity is about individual operations or transactions, ensuring they are completed fully or not at all. Serializability is about the interleaving of multiple transactions, ensuring that their combined effect is consistent with some serial order.
- **Focus:** Atomicity focuses on the integrity of a single transaction, whereas serializability focuses on the consistency and isolation of multiple transactions.

In practice, both properties are crucial for maintaining data integrity and consistency in concurrent systems, but they address different aspects of transaction management. Atomicity ensures that individual transactions are executed completely, while serializability ensures that the interleaved execution of transactions does not compromise the consistency of the database.


### Indexing
- An index is a data structure reducing the time for certain operations and ensuring no unwanted duplicate values.
- RDM supports hash and b-tree indexing types.
- Indexing allows fast access to a table's rows based on the data values of indexed columns.

### Key Concepts
- **Concurrency:** Two or more processes executing simultaneously.
- **Connection:** Communication means between a client and a server, with a process having multiple connections.
- **Consistency:** Ensures that the database state remains consistent before and after the execution of a transaction.

### Additional Database Concepts
- **Deadlock:** A situation where resources are held by two or more connections needed by each other, causing an infinite wait loop.
- **Distributed Database:** Data distributed among multiple computers or devices, facilitating simultaneous access.
- **DLL (Dynamic Link Library):** Contains related functions not loaded into memory until called, used in RDM APIs.
- **DML (Database Manipulation Language):** Includes SQL statements like UPDATE, INSERT, and DELETE.
- **Durability:** Ensures committed transactions survive system failures.

### More Database Terminology
- **Edge Computing:** Computing infrastructure close to data sources, beneficial for IoT, IIoT, 5G, and AI applications.
- **Embedded Database:** Resides within an application, combining database and controlling software.
- **Encryption:** Encoding data to make it unreadable without the encryption key.
- **Fog Computing:** Distributes computing, storage, and networking closer to users in the Cloud-to-Thing continuum.
- **Geospatial Datatypes:** Optimized for storing geographic coordinate-based data.

### Continued Database Definitions
- **Hash:** Indexing method providing fast retrieval based on matching column values.
- **Hierarchical Model:** Special case of a network model database where each record type can participate in only one set.
- **Hot Spot:** A bottleneck created by a frequently used and updated single shared row in a database.
- **Implicit Locking:** SQL automatically applies locks needed for safe execution in a multiuser environment.
- **IMDB (In-Memory Database):** Keeps the entire database or table contents in computer memory.

### Further Database Concepts
- **Isolation:** Ensures changes made by a transaction are isolated from the rest of the system until after commitment.
- **Little-Endian:** Data storage convention where the least significant bit is stored first.
- **Local Procedure Call:** Software function call to a library function in the same process.
- **Locking:** Safely protects objects from being changed by multiple users simultaneously.
- **Memory Database:** Keeps the entire database or table in computer memory.
- **Mirroring:** Copies transaction changes from a master database to one or more slave databases.

### Additional Database Terminology
- **Multi-version Concurrency Control (MVCC):** Allows multiple types of database access simultaneously.
- **Optimizer:** Estimates the optimum method to access data in response to an SQL statement.
- **Page Size and Page:** Basic unit of database file input/output and associated data in the file.
- **Positioned Update/Delete:** SQL UPDATE or DELETE statement modifying the current row of a cursor.

### Conclusion
- The note covers essential concepts related to transactions, indexing, and various database terminologies.
- It provides a comprehensive overview of key database elements, ensuring a clear understanding of fundamental principles.