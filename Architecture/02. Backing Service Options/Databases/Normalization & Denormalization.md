---
tags:
  - databases
  - data
  - schema
  - scalability
  - tables
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses database table Normalization & Denormalization.
Status: Refinement
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
Normalization is a crucial technique in database design aimed at improving data integrity by reducing redundancy and inconsistency. It involves organizing data into multiple tables, adhering to specific rules to optimize database performance. Striking the right balance is key, as both over-normalization and under-normalization can lead to issues.

### The Three Rules of Normalization

1. **First Normal Form (1NF):** Eliminates duplicate rows and ensures each column contains atomic (indivisible) values. This sets the foundation for organizing data without redundancy.

2. **Second Normal Form (2NF):** Builds on 1NF by addressing partial dependencies. It involves removing columns that are not fully dependent on the primary key, further streamlining data organization.

3. **Third Normal Form (3NF):** Enhances data integrity by eliminating transitive dependencies. This rule focuses on removing columns that are dependent on non-key columns, promoting a more robust relational structure.

### The Normalization Process

The normalization process involves systematically applying these rules, moving from one normal form to the next. This step-by-step optimization ensures a standardized and efficient structure for business databases. Although there are higher normal forms, such as Boyce-Codd Normal Form (BCNF) and Fourth Normal Form (4NF), they are often deemed unnecessary for basic databases.

### Benefits of Normalization

- **Reduction of Redundancy:** By dividing data into distinct tables, duplication is minimized, saving storage space and ensuring data consistency.
  
- **Improved Data Integrity:** The removal of partial and transitive dependencies enhances the accuracy and reliability of the data.
  
- **Easier Maintenance:** Normalized databases are easier to update and maintain, adapting more seamlessly to changes in schema or structure.

- **Consistency and Concurrency**: Normalized databases can better handle concurrent access to data, as updates are typically isolated to smaller portions of the database.  
  
- **Data Analysis**: If you need to perform complex data analysis and reporting, normalized data can be more flexible and efficient for querying.  

### Denormalization and its Role

On the flip side, denormalization involves combining data into a single table to expedite data retrieval. While it may enhance query performance, it comes at the cost of increased redundancy. Excel, often used as a denormalized SQL table, serves this purpose by simplifying data presentation and analysis.


### Benefits of Denormalization
On the other hand, denormalized databases can be more appropriate in certain scenarios:  
  
1. **Read-Heavy Workloads**: In applications where the majority of operations involve reading data and where query performance is crucial, denormalized databases can reduce the number of joins and potentially improve read performance.  
  
2. **Reduced Complexity**: Denormalized databases can simplify the schema and data retrieval for specific use cases, such as reporting or data warehousing, making development and querying more straightforward.  
  
3. **Data Retrieval**: For certain read patterns, denormalization can lead to faster data retrieval, as you can avoid costly joins by storing related data together.  
  
4. **Caching**: Denormalized data can be beneficial for caching purposes, as it minimizes the amount of data to be cached and speeds up data retrieval for frequently accessed data.  
  
However, there are some trade-offs with denormalized databases, including the risk of data anomalies, increased storage requirements, and complexity when performing updates.  


### Normalization and Denormalization Influence on Data Visualization

The normalization or denormalization of database tables can have a significant effect on the visualization of data in Power BI. Here's how each approach can impact your data visualization:  
  
#### **Normalization:**  
  
1. **Clarity:** Normalized tables can maintain data integrity and reduce redundancy, making your data more logically organized. This can lead to clearer and more structured data models in Power BI.  
  
2. **Flexibility:** Normalization allows for efficient data updates and maintenance. If your data changes frequently, normalized tables can be more adaptable to modifications without affecting the integrity of the data.  
  
3. **Complexity:** Normalized data models may involve multiple related tables and require more complex relationships and `DAX` calculations in Power BI. This can increase the complexity of report development.  
  
#### **Denormalization:**  
  
1. **Performance:** Denormalized tables can improve query performance in Power BI, especially for complex reports with many joins. Flattening the data can make it easier and faster to create visualizations.  
  
2. **Simplicity:** Denormalization can simplify the data model in Power BI, making it more straightforward for report authors to create visuals and calculations.  
  
3. **Storage:** Denormalized tables often require more storage space compared to their normalized counterparts. Consider the trade-off between storage costs and improved performance.  
  
In practice, many Power BI projects find a middle ground. They maintain normalized databases for data integrity and compliance with relational database principles while creating optimized views or data structures for reporting purposes. These optimized structures can be denormalized to improve performance and simplify report development.  
  
Ultimately, the choice between normalization and denormalization should align with your specific reporting requirements, data volume, and performance considerations. Power BI provides tools and features to handle both normalized and denormalized data, allowing you to design your data model according to your needs.

### Continuous Evaluation
Normalization is an ongoing process, requiring periodic reassessment whenever there are changes to the schema or database structure. This ensures that the database remains optimized and aligned with evolving business requirements.

When designing a database schema, it is generally a good idea to aim for a normalization level that is appropriate for the needs of the application.  

It's important to note that aiming for a higher level of normalization may not always be necessary or practical for every application. It depends on the specific needs of the application and the trade-offs between performance, storage efficiency, and maintainability. In some cases, denormalization (i.e. intentionally introducing redundancies) may be appropriate to optimize for certain queries or use cases. 


For further details on database normalization, you can explore additional resources at [Guru99](https://www.guru99.com/database-normalization.html).

In summary, normalization is a foundational concept in database design, essential for maintaining data integrity and optimizing performance. Balancing the rules of normalization with practical considerations is key to creating an efficient and effective database structure.
## 1NF (First Normal Form) Rules 
-   Each table cell should contain a single value. 
-   Each record needs to be unique.     

**Pros**: Ensures that each column in a table contains only atomic values, and each row in the table is unique. 

**Cons**: May result in duplicate data and require more storage space. 

**Trade-offs**: Choosing a higher level of normalization may improve data integrity and reduce data inconsistencies but may also impact performance due to additional joins required.

![[1NF.png]]

## 2NF (Second Normal Form) Rules 
-   Rule 1- Be in 1NF 
-   Rule 2- Single Column ***Primary Key*** that does not functionally dependent on any subset of candidate key relation     

**Pros**: Helps ensure that all non-key columns are dependent on the table's primary key. 

**Cons**: May still result in duplicate data and require more storage space. 

**Trade-offs**: Choosing a higher level of normalization may result in slower performance and more complex queries.

![[2NF.png]]

![[Dependencies.png]]

![[Column Relatioships.png]]
## 3NF (Third Normal Form) Rules 
*You can also break teacher out into its own table
-   Rule 1- Be in 2NF 
-   Rule 2- Has no transitive functional dependencies     

To move our 2NF table into 3NF, we again need to again divide our table. 

**Pros**: Helps ensure that non-key columns are dependent only on the table's primary key, and reduces the risk of data inconsistencies. 

**Cons**: May still result in duplicate data and require more storage space, and may require more complex queries. 

**Trade-offs**: Choosing a higher level of normalization may result in slower performance and more complex queries.


![[3NF.png]]

![[Trans dependencies.png]]


![[Employee relationship.png]]

![[Exam relationship.png]]


## BCNF (Boyce-Codd Normal Form) 
Even when a database is in 3rd Normal Form, still there would be anomalies resulted if it has more than one ***Candidate*** Key. 

Sometimes is BCNF is also referred as ***3.5 Normal Form***. 

**Pros**: Helps ensure that the table is fully normalized and reduces the risk of data inconsistencies. 

**Cons**: May require more complex queries and result in slower performance. 

**Trade-offs**: Choosing a higher level of normalization may result in slower performance and more complex queries.

![[3.5NF.jpeg]]

## 4NF (Fourth Normal Form) Rules 
If ***no*** database table instance contains(***we don’t want anywhere***) two or more, independent and ***multivalued(bad)*** data describing the relevant entity, then it is in 4th Normal Form. 

**Pros**: Helps ensure that the table is fully normalized and reduces the risk of data inconsistencies and redundancies. 

**Cons**: May require more complex queries and result in slower performance. 

**Trade-offs**: Choosing a higher level of normalization may result in slower performance and more complex queries, and may require additional maintenance to ensure that the data remains consistent.


![[4NF.png]]

Don’t want this it is better if separated  

also to be considered multi value you need at <mark style="background: #FFF3A3A6;">least 3 columns</mark> the reason why is because with two columns you can fix the issue  in this example A1 is multivalued but we fixed by making independent rows the <mark style="background: #FFF3A3A6;">2nd rule to be multi value is column A have multiple relationships like how A1 maps to B1 and B2</mark>

![[4NF part 1.png]]

The last requirement to be considered multi valued after meeting 3 coulmn minimum is no <mark style="background: #FFF3A3A6;">relationship between b and c in this example</mark>

![[4NF part 2.png]]

![[4NF part 3.png]]

## 5NF (Fifth Normal Form) Rules 
A table is in 5th Normal Form only if it is in 4NF and <mark style="background: #FFB86CA6;">it cannot be decomposed into any number of smaller tables without loss of data and no join dependencies. </mark>

**Pros**: 5NF is the highest level of normalization and provides the most complete normalization of data, which helps to ensure data consistency and eliminates redundancies. 

Reduces data anomalies and inconsistencies, which can help to improve the quality of the data. 

Helps to simplify data maintenance and updates, by reducing the number of tables and dependencies. 

**Cons**: Implementing 5NF can be complex and time-consuming, requiring a deep understanding of the relationships between tables and dependencies. 

It can result in more complex queries, which may impact query performance. 

It may also lead to increased storage requirements, as it may require additional tables to store data. 

**Trade-offs**:  The decision to implement 5NF should be based on the specific needs and requirements of the application. While 5NF provides the most complete normalization of data, it may not be necessary or practical for all applications. 

Implementing 5NF can help to improve the quality and consistency of data, but it may also lead to more complex queries and slower query performance. 

Choosing a higher level of normalization can help to improve data integrity but may result in additional storage requirements and more complex database schema. 

In summary, 5NF is a powerful tool for ensuring the consistency and quality of data. However, it can be complex to implement, and may have trade-offs in terms of query performance and storage requirements. Therefore, it is important to carefully consider the specific needs of the application and work with stakeholders to find the right balance between normalization, performance, and maintenance.

![[5NF part 1.jpeg]]

![[5NF part 2.jpeg]]

![[5NF part 3.jpeg]]

<mark style="background: #FFB8EBA6;">Ford could have different supplier or you might be sold a different product the way things are separated on this table </mark>

Since table is broken down and loss of data happened this isn't 5th form but if it could be broken down without loss of data then it would be 5th form also known as join dependency  

## 6NF (Sixth Normal Form) Proposed 

6th Normal Form is not standardized, yet however, it is being discussed by database experts for some time. Hopefully, we would have a clear & standardized definition for 6th Normal Form in the near future… 

That’s all to SQL Normalization!!! 

Ultimately, the choice of normalization level should be driven by the specific needs of the application and the trade-offs between data integrity, query performance, storage efficiency, and maintenance complexity. It's important to carefully consider these factors and work with stakeholders to find the right balance for your specific use case.