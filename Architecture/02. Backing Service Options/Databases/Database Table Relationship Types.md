---
tags:
  - databases
  - tables
  - schema
  - UML
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses database table relationships.
Status: Done
Started: 
EditDate: 2024-02-06
Relates: 
Peer Reviewed: 0
dg-publish: false
---
![[DB UML relationship types.jpeg]]

Database relationships are associations between tables that are created using join statements to retrieve data. [[Self-joining relationships|Join]] statements are then used to retrieve data from multiple tables based on these relationships. There are different types of joins, such as INNER JOIN, LEFT JOIN, RIGHT JOIN, and FULL JOIN, which determine how data from related tables is combined.

## Most Common Relationships
The most prevalent relationships are many-to-one or vice versa, as well as one-to-many. In one-to-one relationships, both sides hold unique values, while in many-to-many relationships, both sides can contain duplicates.

For simplicity and clarity, it's advisable to focus on one-to-one, many-to-one, and one-to-many relationships. This approach helps maintain a straightforward understanding of unique and duplicate values on each side of the relationship.

### One-to-One Relationships
One-to-one relationships are less common because, typically, if there's only one row associated with another row, they could be merged into a single table. An example involves separating customer information into two tables: one with name and ID, and another with personal details. This creates a one-to-one relationship, allowing restricted access to sensitive data while using the common elements for other relationships. Another example is the assignment of resources like equipment. In a one-to-one relationship, each item is assigned to one person, ensuring exclusivity. Although one-to-one relationships may not be frequently used, they can be relevant in scenarios where data protection or resource allocation requires such specificity. Some DBMS tools permit securing individual columns, potentially eliminating the need for one-to-one relationships.


### One-to-Many Relationship
In a one-to-many relationship, one record from one table is connected to one or more records in another table. This relationship is depicted by a line with one endpoint representing the "one" side and a symbol like a crow's foot indicating the "many" side. For instance, a Customers table may be linked to a Dishes table, where each customer can have a favorite dish. The Foreign Key, in this case, is placed on the "many" side, representing the connection from many customers to one dish.

### Many-to-One Relationship
While the term "many-to-one" is often used colloquially, in reality, it is still a one-to-many relationship. Whether viewed from the "one" side or the "many" side, the underlying structure of the relationship remains the same. For example, when modeling a connection between a Customers table and a Reservations table, a one-to-many relationship exists, as one customer can have many reservations.

### Flexibility in One-to-Many Relationships
One-to-many relationships provide flexibility by allowing one record to be associated with many records in another table. This flexibility is useful for modeling various connections, such as tracking reservations, where each reservation is linked to a customer using a Foreign Key. This approach simplifies data maintenance and ensures the integrity of the database.

![[Relationship Example.png]]

### Many-to-Many Relationships
In the scenario where many orders could have many dishes, and vice versa, a many-to-many relationship is represented by a line with a crow's foot on each end. However, most Database Management System (DBMS) tools do not directly support modeling many-to-many relationships. To address this, a linking table, such as "orders_dishes," is created. This linking table establishes one-to-many relationships with both the "orders" and "dishes" tables. It contains two columns, an order ID and a dish ID, with each row representing a specific dish included in a particular order. This approach keeps the "orders" table clean while allowing detailed recording of order contents. Many-to-many relationships can be applied to various scenarios, such as tracking customer preferences, managing ingredients, or associating customers with events.


### Referential Integrity
Maintaining referential integrity in a database ensures that relationships between tables are preserved and prevents data modifications that would violate these relationships. The DBMS becomes aware of the relationships, preventing users from making changes that could compromise consistency. This practice contributes to the overall reliability and accuracy of the database. While designing a database with Entity-Relationship (ER) diagrams, it's important to recognize that the process is iterative, allowing for adjustments and improvements over time.


![[Relationship Example Two.png]]

## Junction Table
A junction table encompasses multiple foreign keys, exemplified by, for instance, a movie rental table linking a rental table's primary key and a movie table's primary key.

Commonly associated with many-to-many relationships, junction tables are employed when records in both entities may reference multiple records in each other's entities, necessitating an intermediary entity—known as a junction table—to consolidate these multiple connections.

An entity, defined as something with distinct and independent existence, is integral to understanding the structure of these relationships. Junction tables optimize data normalization, bringing it to its lowest normalized level. This approach is especially useful when dealing with elements that could be duplicated across multiple entries, such as dates or times.

Consider the example of doctors and patients: a junction table might contain primary keys for both doctor and patient IDs. This setup allows for the creation of additional table relationships, such as those between doctors and appointments, as well as patients and procedures.


![[Relationship Example Three.png]]

