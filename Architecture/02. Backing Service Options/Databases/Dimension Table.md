---
tags:
  - databases
  - dataTables
  - descriptive
  - dataEngineering
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses dimension table.
Status: Refinement
Started: 2024-01-07
EditDate: 2024-03-06
Relates: 
Peer Reviewed: 0
dg-publish:
---
A dimension table is a fundamental concept in data warehousing and relational database design. It is a type of table that contains descriptive information about the entities in a business or analytical context, providing context and details for the measurements stored in fact tables. Dimension tables are a crucial component of the star schema and snowflake schema, common data warehouse modeling techniques.

Here are key characteristics and components of a dimension table:

1. **Descriptive Attributes:**
   - A dimension table holds descriptive attributes or characteristics related to specific entities. These entities can represent people, products, locations, time periods, or any other business-related concepts.

2. **Primary Key:**
   - The dimension table typically has a primary key that uniquely identifies each record or row. This key is often used as a foreign key in fact tables to establish relationships between the dimension and fact tables.

3. **Surrogate Key:**
   - In some cases, a surrogate key may be used as the primary key in a dimension table. This is a system-generated key that serves as a unique identifier, especially when the natural key (original business key) is not suitable for indexing or when changes to the natural key are anticipated.

4. **Descriptive Attributes:**
   - The primary purpose of a dimension table is to store descriptive attributes or characteristics related to the entities it represents. For example, a "Time" dimension table may include attributes like day, month, quarter, and year.

5. **Hierarchical Structure:**
   - Dimension tables may have a hierarchical structure, allowing the organization of attributes in levels. For example, a "Location" dimension might have levels such as country, region, and city.

6. **Slowly Changing Dimensions (SCDs):**
   - Dimension tables often deal with changes in data over time. Slowly Changing Dimensions (SCDs) are a concept used to manage historical changes in dimension attributes. SCD techniques include Type 1 (overwrite), Type 2 (add new row), and Type 3 (add new attribute).

7. **Foreign Key Relationships:**
   - Dimension tables are linked to fact tables through foreign key relationships. The foreign key in the fact table corresponds to the primary key or surrogate key in the dimension table.

8. **Examples of Dimension Tables:**
   - Common examples of dimension tables include:
     - **Time Dimension:** Contains attributes like day, month, quarter, year, etc.
     - **Product Dimension:** Contains attributes such as product name, category, and manufacturer.
     - **Customer Dimension:** Contains attributes like customer name, address, and segment.

9. **Star Schema and Snowflake Schema:**
   - Dimension tables play a central role in star schema and snowflake schema designs, which are widely used in data warehousing. In a star schema, dimension tables are directly connected to a central fact table. In a snowflake schema, dimension tables may be normalized into sub-dimensions, creating a more normalized structure.

In summary, dimension tables provide descriptive context for measurements stored in fact tables in the context of data warehousing and business intelligence. They help organize and categorize data, enabling analysts and decision-makers to perform meaningful analyses and gain insights into various business aspects.



### Unveiling Common Dimension Table Types

**Time Dimension Table:**
- Stores date and time-related information for analyzing trends and patterns over time (year, quarter, month, week, day, hour, minute, second).

**Geography Dimension Table:**
- Contains geographical details like country, state, city, postal code, longitude, and latitude for analyzing data based on geography.

**Product Dimension Table:**
- Houses product information such as name, category, brand, size, and color for analyzing sales and inventory data.

**Customer Dimension Table:**
- Stores customer details like name, age, gender, address, email, and loyalty status for analyzing behavior and preferences.

**Salesperson Dimension Table:**
- Captures salesperson information including name, department, territory, and commission rate for analyzing sales performance.

**Promotion Dimension Table:**
- Records promotion details such as name, start date, end date, discount rate, and coupon code for analyzing marketing campaign effectiveness.

**Supplier Dimension Table:**
- Contains supplier information like name, address, contact details, and supplied products for analyzing supplier performance.

**Flexibility in Dimension Table Choices:**
- The selection of dimension tables depends on the specific data analyzed and organizational needs in a data warehouse or business intelligence system.