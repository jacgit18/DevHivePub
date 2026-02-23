---
tags:
  - databases
  - tables
  - query
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Self-joining relationships.
Status: Done
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
A self-join is when a table is joined to itself, typically to compare or relate the data within the same table. For example, in an employee database, a self-join could be used to find pairs of employees who have the same manager. In this case, the table would be joined to itself based on the manager ID column. 

A self-join is a join in which a table is joined with itself (which is also called Unary relationships), especially when the table has a FOREIGN KEY which references its own PRIMARY KEY. To join a table itself means that each row of the table is combined with itself and with every other row of the table. 

The self-join can be viewed as a join of two copies of the same table. The table is not actually copied, but SQL performs the command as though it were. 

The syntax of the command for joining a table to itself is almost same as that for joining two different tables. To distinguish the column names from one another, aliases for the actual the table name are used, since both the tables have the same name. Table name aliases are defined in the 
FROM clause of the SELECT statement. See the syntax : 
```SQL
SELECT a.column_name, b.column_name...  FROM table1 a, table1 b  WHERE a.common_filed = b.common_field; 

```
Joining the table with itself accomplishes a different or smaller dataset with  set from the same table from my understanding and you can have duplicates

https://joins.spathon.com

![[Self-joining.png]]

In the following example, we will use the table EMPLOYEE twice and in order to do this we will use the alias of the table. To get the list of employees and their supervisor the following SQL statement has used: 

```SQL
SELECT a.emp_id AS "Emp_ID",a.emp_name AS "Employee Name", b.emp_id AS "Supervisor ID",b.emp_name AS "Supervisor Name" FROM employee a, employee b WHERE a.emp_supv = b.emp_id;
```


Inner joins returns records with a combination of values where there's overlap between two tables where you have a complete record as opposed to a inconsistent record with missing values on each row  
  
left join includes inconsistent records from the left excluding right  
  
right join is vise versa


![[Types of Joins.png]]

![[4 Type of Joins.gif]]