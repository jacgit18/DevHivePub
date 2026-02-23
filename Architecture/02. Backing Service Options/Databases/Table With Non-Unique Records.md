---
tags:
  - databases
  - tables
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses table With Non-Unique Records.
Status: Done
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
There are scenarios where tables may not necessarily require each record to be unique. These situations often involve tables that store non-relational or aggregated data. Here are some examples:

1. **Log Tables:**
   - Tables used for logging events, where uniqueness may not be critical since the primary purpose is to track occurrences.

   ```sql
   CREATE TABLE EventLog (
       event_id INT PRIMARY KEY,
       event_description VARCHAR(255),
       event_timestamp TIMESTAMP
   );
   ```

2. **Summary or Aggregated Tables:**
   - Tables that store summarized or aggregated data where uniqueness is not a primary concern.

   ```sql
   CREATE TABLE MonthlySales (
       month INT,
       total_sales DECIMAL(10, 2)
   );
   ```

3. **Temporary Tables:**
   - Tables used for temporary storage during data processing, where uniqueness might not be a crucial requirement.

   ```sql
   CREATE TEMPORARY TABLE TempData (
       data_value INT
   );
   ```

4. **Reference Tables with Duplicate Values:**
   - Some reference tables might intentionally allow duplicate values, for example, if the same product can have multiple categories.

   ```sql
   CREATE TABLE ProductCategory (
       product_id INT,
       category_id INT
   );
   ```

5. **Non-relational Data Tables:**
   - Tables storing data with a one-to-many or many-to-many relationship that doesn't require unique records.

   ```sql
   CREATE TABLE EmployeeProjects (
       employee_id INT,
       project_id INT
   );
   ```

It's important to note that the decision to allow non-unique records should be based on the specific requirements of your application and the nature of the data you are working with. Always consider the business logic and design principles relevant to your use case.