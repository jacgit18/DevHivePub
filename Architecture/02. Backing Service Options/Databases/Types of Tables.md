---
tags:
  - databases
  - dataTables
  - Domain
  - models
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses types of tables in logical database models.
Status: Done
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish: true
---
In database design, logical models help define the structure and organization of data without getting into the specifics of how data is physically stored or accessed. Here are some types of tables commonly used in logical database models:  

  
1. **Regular Tables**: These are the most common types of tables used in a database to store data. They consist of rows and columns, where each row represents a record, and each column represents a field or attribute.  
  
2. **Temporary Tables**: Temporary tables are used to store temporary data that is only needed for the duration of a specific database session or task. They are often used in complex queries or stored procedures.  
  
3. **System Tables**: These tables are used by the RDBMS to store metadata and system-related information. Users typically do not interact with these tables directly.

4. **Entity Tables**: These tables represent core entities within the database, such as customers, products, employees, or orders. They store attributes and information related to these entities.  
  
5. **Attribute Tables**: Attribute tables contain detailed information about specific attributes of entities. For example, if you have a "Product" entity, you might have separate attribute tables for product categories, prices, and descriptions.  
  
6. **Relationship Tables**: These tables are used to define many-to-many relationships between entities. They typically consist of foreign keys from two or more entity tables and may include additional attributes describing the relationship.  
  
7. **Lookup Tables**: Lookup tables store reference data used for maintaining data integrity. They often contain lists of values that are used in other tables as foreign keys or for data validation.  
  
8. **Hierarchical Tables**: Hierarchical tables are used to represent hierarchical relationships within the data. They are commonly used in scenarios like organizational structures or category hierarchies.  
  
9. **Mapping Tables**: Mapping tables are used to create many-to-many relationships between entities or attributes. They facilitate the mapping of related items from different tables.  
  
10. **History Tables**: History tables store historical versions of data, allowing you to track changes over time. They are essential for auditing and maintaining historical records.  
  
11. **Intersection Tables**: These tables are used to resolve complex relationships between entities. For example, in a university database, an intersection table might connect students with courses they are enrolled in.  
  
12. **Aggregate Tables**: In data warehousing and business intelligence, aggregate tables summarize and precompute data from lower-level detail tables to improve query performance.  
  
13. **Dimension Tables**: In data warehousing, dimension tables describe the characteristics of data in fact tables. They provide context for analyzing data and often include attributes like time, location, or product dimensions.  
  
14. **Fact Tables**: Fact tables contain quantitative data and metrics, such as sales, revenue, or transaction data. They are central to data warehousing and support business intelligence reporting.  
  
15. **View Tables**: These are virtual tables defined based on one or more underlying tables. Views simplify complex queries and provide a logical layer for data access.  
  
16. **Derived Tables**: Derived tables are created by applying calculations or transformations to existing data. They can be used for specific reporting or analysis purposes.  

17. **Audit Tables**: These tables are used to track changes made to other tables in the database. They capture historical data and are often used for auditing and compliance purposes.  
  
6. **Logging Tables**: Logging tables store logs and events related to database activity. They are useful for monitoring and troubleshooting database performance and issues.  
  
7. **Partitioned Tables**: Large tables can be divided into partitions to improve query performance and manage data more efficiently. Each partition can be stored separately and has its own set of data.  
  
8. **Materialized Views**: Materialized views are pre-computed result sets of queries, stored as tables. They are used to improve query performance by caching the results of complex queries.  
  
9. **Virtual Tables (Views)**: These are not physical tables but virtual representations of data from one or more underlying tables. Views are used to simplify complex queries and control access to data.  
  
10. **Queue Tables**: These tables are used to implement message queues, often in messaging systems. They store messages to be processed asynchronously.  
  
12. **Linking or Junction Tables**: In many-to-many relationships, linking or junction tables are used to connect records from two other tables. They resolve the many-to-many relationship into two one-to-many relationships.  linking tables model pure relationships rather than entities, the rows of an linking table do not represent entities. Instead, they describe the relationships among the entities the table represents. 
  
13. **Blob Tables**: Blob (Binary Large Object) tables store binary data, such as images, documents, or multimedia files. They are used to manage and retrieve large binary data efficiently.