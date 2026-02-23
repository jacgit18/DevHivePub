---
tags:
  - example
  - databases
  - query
author:
  - gitUserNamePlaceHolder
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: Done
Started: 2024-05-18
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
In SQL, the `IN` operator allows you to specify multiple values in a `WHERE` clause to filter data based on a list of values. It is commonly used to compare a column's value against a list of literals or a subquery result.  
  
Here's the basic syntax of the `IN` operator:  
  
```sql  
SELECT column1, column2, ...  
FROM table_name  
WHERE column_name IN (value1, value2, ...);  
```  
  
- `column_name`: The column you want to filter.  
- `(value1, value2, ...)`: A list of values or a subquery result to compare against the column's value.  
  
Example 1: Using `IN` with Literal Values:  
```sql  
SELECT *  
FROM employees  
WHERE department IN ('HR', 'Finance', 'Marketing');  
```  
This query selects all employees whose department is either 'HR', 'Finance', or 'Marketing'.  
  
Example 2: Using `IN` with Subquery:  
```sql  
SELECT *  
FROM orders  
WHERE customer_id IN (SELECT customer_id FROM customers WHERE country = 'USA');  
```  
This query selects all orders placed by customers from the USA by using a subquery to retrieve the customer IDs.  
  
The `IN` operator is useful when you need to filter data based on multiple possible values without using multiple `OR` conditions. It provides a concise and efficient way to perform such filtering in SQL queries.

## Query Example 
The two SQL queries provided have different purposes and outputs, despite being somewhat similar in their structure and logic.  
  
### First Query:  
```sql  
SELECT COUNT(*),  
CASE  
WHEN number_grade > 90 THEN "A"  
WHEN number_grade >80 THEN "B"  
WHEN number_grade >70 THEN "C"  
ELSE "F"  
END as "letter_grade"  
FROM student_grades  
GROUP BY letter_grade;  
```  
  
### Second Query:  
```sql  
SELECT  
CASE  
WHEN number_grade > 90 THEN 'A'  
WHEN number_grade > 80 THEN 'B'  
WHEN number_grade > 70 THEN 'C'  
ELSE 'F'  
END AS letter_grade,  
COUNT(*) AS student_count  
FROM student_grades  
GROUP BY letter_grade;  
```  
  
### Differences:  
  
1. **Output Columns and Order**:  
- **First Query**: Returns two columns: the count of students in each grade category and the corresponding letter grade. The columns are ordered as `COUNT(*)` first and `letter_grade` second.  
- **Second Query**: Returns two columns as well, but in reverse order: the letter grade first and the count of students in each grade category second. The columns are ordered as `letter_grade` first and `COUNT(*)` (renamed as `student_count`) second.  
  
2. **Column Naming**:  
- **First Query**: The count column has no explicit alias (it's just `COUNT(*)`), and the letter grade column is aliased as `letter_grade`.  
- **Second Query**: The count column is explicitly aliased as `student_count`, and the letter grade column is also aliased as `letter_grade`.  
  
3. **Readability and Conventional Practice**:  
- The second query follows a more conventional practice by explicitly naming the count column, which makes the output more readable and self-explanatory. In the first query, although it works, the absence of an alias for the count might make it slightly less clear.  
  
### Similarities:  
- Both queries use a `CASE` statement to categorize `number_grade` into letter grades.  
- Both queries use `GROUP BY` to group results based on the `letter_grade`.  
  
### Example Output:  
Assume `student_grades` table has the following data:  
```plaintext  
number_grade  
95  
85  
75  
65  
92  
88  
78  
```  
  
**First Query Output**:  
```plaintext  
COUNT(*) | letter_grade  
---------|--------------  
2 | A  
2 | B  
2 | C  
1 | F  
```  
  
**Second Query Output**:  
```plaintext  
letter_grade | student_count  
-------------|---------------  
A | 2  
B | 2  
C | 2  
F | 1  
```  
  
In conclusion, while both queries achieve similar grouping and counting based on the grade categories, the second query is typically preferred for its clarity in labeling the count column, making the results easier to interpret.