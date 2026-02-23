---
tags:
  - databases
  - schema
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses how to read database table relationships.
Status: Done
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish: false
---
## Simple Relational Model Representation


![[relational model.png]]

1. **Address - Customer:**
   - An Address can have a one-to-one relationship with a Customer.
   - A Customer can have a one-to-one relationship with an Address.

2. **Customer - Order:**
   - A Customer can place one or more Orders.
   - An Order belongs to one Customer.

3. **Order - Order Item:**
   - An Order can have one or more Order Items.
   - An Order Item belongs to one Order.

4. **Product - Order Item:**
   - A Product can be listed in one or many Order Items.
   - An Order Item belongs to one Product.

In terms of database schema:

- **Address Table:**
  - Fields: AddressID (Primary Key), Street, City, State, ZIP, CustomerID (Foreign Key referencing Customer table).

- **Customer Table:**
  - Fields: CustomerID (Primary Key), FirstName, LastName, Email, Phone, AddressID (Foreign Key referencing Address table).

- **Order Table:**
  - Fields: OrderID (Primary Key), OrderDate, CustomerID (Foreign Key referencing Customer table).

- **Order Item Table:**
  - Fields: OrderItemID (Primary Key), OrderID (Foreign Key referencing Order table), ProductID (Foreign Key referencing Product table), Quantity, Price.

- **Product Table:**
  - Fields: ProductID (Primary Key), ProductName, Description, Price.

This structure ensures that each customer can have a unique address and place multiple orders. Each order can contain multiple items, and each item is associated with a specific product. The foreign keys maintain the relationships between the tables, reflecting the defined connections in the relational model.