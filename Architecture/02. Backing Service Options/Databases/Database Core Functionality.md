---
tags:
  - databases
  - query
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Database Core Functionality.
Status: Done
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish: true
---
A database is a named collection of tables with fields or columns and records or rows. A database can also contain views, indexes, sequences, data types, operators, and functions. 

When establishing a database, SQL serves as the Data Definition Language (DDL) for defining its structure. Once inside the database, SQL transforms into the Data Manipulation Language (DML), enabling operations on the stored data.

MySQL, is a open-source DBMS that includes a few other useful features on top of the SQL standard. SQL allows us to write statements which the DBMS interprets, and that's how we interact with the data in the database, from apps, or even within the DBMS itself. 

Besides that they are also constraints which are the rules enforced on the data columns of a table. These are used to limit the type of data that can go into a table. This ensures the accuracy and reliability of the data in the database. 

Constraints could be either on a column level or a table level. The column level constraints are applied only to one column, whereas the table level constraints are applied to the whole table. 

Constraints can be specified when a table is created with the CREATE TABLE statement or you can use the ALTER TABLE statement to create constraints even after the table is created.

Bridging data accurately is a prime directive. Software integrations and the ability to securely share data between applications are all dependent on data integrity and database relationships. 

This is where constraint comes in. Foreign keys are often constrained to ensure the user cannot take actions that would damage dependency links between tables. This also constrains users from entering invalid data. 

The following syntax allows us to name FOREIGN KEY constraint: 
```SQL
CREATE TABLE Orders (     
OrderID int NOT NULL,     
OrderNumber int NOT NULL,     
PersonID int,     
PRIMARY KEY (OrderID),     
CONSTRAINT FK_PersonOrder FOREIGN KEY (PersonID)     
REFERENCES Persons(PersonID) );
```

We can use foreign key restraints to help maintain referential integrity of our foreign key relationships. There are many referential actions we can use for constraint, including: 

- Cascade: when deleting primary key values, the matching column in the child table are deleted 

- Set null: when a referenced row is deleted/altered, the referencing values in the foreign key are set to null 

- Restrict: Values in the parent table cannot be deleted if they are referred by a foreign key. 

- Set default: The foreign key values in the child table are set to a default value if the parent table is altered/deleted 


![[Database Processes.gif]]
In the context of SQL and relational databases, DCL, DDL, DML, and DQL are the primary sub-languages that cover most of the operations related to database management. However, it's worth noting that there are some additional concepts or features that might be considered separate from these sub-languages:

1. **TCL (Transaction Control Language):**
   - **Purpose:** TCL is used to manage transactions within a database. It includes commands to control the beginning and ending of transactions, as well as to undo or commit changes.
   - **Commands:**
     - `COMMIT`: Saves all changes made during the current transaction.
     - `ROLLBACK`: Undoes changes made during the current transaction.
     - `SAVEPOINT`: Sets a point within a transaction to which you can later roll back.

   Example:
   ```sql
   BEGIN TRANSACTION;
   -- SQL statements
   COMMIT;
   ```

2. **Session Control Statements:**
   - **Purpose:** These statements are used to control the characteristics of a database session.
   - **Commands:**
     - `SET`: Modifies the session-specific settings, such as the isolation level.
     - `USE`: Specifies the default database for a session.

   Example:
   ```sql
   SET TRANSACTION ISOLATION LEVEL READ COMMITTED;
   USE database_name;
   ```

While DCL, DDL, DML, and DQL are fundamental to SQL, TCL and session control statements are additional components that play roles in managing transactions and customizing the behavior of database sessions. The specific features and sub-languages may vary slightly among different database management systems, as some systems may have their own extensions or variations.
![[Sql Exe Order.gif]]
## Triggers
In SQL, a trigger is a set of instructions or a set of actions that are automatically executed, or "triggered," in response to certain events on a particular table or view in a database. Triggers are used to enforce business rules, perform validation, maintain data integrity, or automate complex database operations. The events that can activate a trigger include INSERT, UPDATE, DELETE statements, or a combination of these.

Here are some key points about SQL triggers:

1. **Event Types:**
   - **INSERT Trigger:** Fires when a new record is added to a table.
   - **UPDATE Trigger:** Fires when one or more existing records are modified in a table.
   - **DELETE Trigger:** Fires when a record is deleted from a table.

2. **Timing:**
   - **BEFORE Trigger:** Executes before the triggering event (INSERT, UPDATE, DELETE). It can be used to modify data before it is actually changed in the database.
   - **AFTER Trigger:** Executes after the triggering event. It is commonly used for auditing or logging changes.

3. **Triggering Conditions:**
   - **Row-Level Trigger:** Executes once for each affected row.
   - **Statement-Level Trigger:** Executes once for the entire triggering statement.

4. **Syntax:**
   - The basic syntax for creating a trigger varies slightly between different database management systems, but a generic example might look like this:
   
     ```sql
     CREATE TRIGGER trigger_name
     [BEFORE | AFTER] [INSERT | UPDATE | DELETE]
     ON table_name
     [FOR EACH ROW | FOR EACH STATEMENT]
     [WHEN (condition)]
     BEGIN
         -- Trigger logic here
     END;
     ```

   - The trigger logic within the `BEGIN` and `END` block defines the actions to be taken when the trigger is activated.

5. **Example:**
   - An example of an AFTER INSERT trigger that updates a timestamp column whenever a new record is inserted into a table:
   
     ```sql
     CREATE TRIGGER after_insert_trigger
     AFTER INSERT
     ON your_table
     FOR EACH ROW
     BEGIN
         UPDATE your_table
         SET timestamp_column = CURRENT_TIMESTAMP
         WHERE primary_key_column = NEW.primary_key_column;
     END;
     ```

Triggers should be used judiciously, as they introduce additional complexity to the database schema and operations. Poorly designed triggers can impact performance and maintainability. It's important to understand the specific requirements and implications before implementing triggers in a database system.

![[Execution Order.jpg]]

