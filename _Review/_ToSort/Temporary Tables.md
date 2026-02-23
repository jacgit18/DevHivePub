---
tags: 
author:
  - gitUserNamePlaceHolder
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: 
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
### SQL Temporary Tables

**Temporary tables** in SQL are used to store intermediate results temporarily during a session. They are particularly useful for complex queries where intermediate steps are required or when you need to store results temporarily for further manipulation.

#### Characteristics of Temporary Tables:
1. **Scope**: Temporary tables are available only within the session that created them. They are automatically dropped when the session ends.
2. **Naming**: They are usually prefixed with a hash symbol (#) for local temporary tables and double hash symbols (##) for global temporary tables.
3. **Creation and Usage**:
   - You create a temporary table using the `CREATE TABLE` statement, just like a regular table, but with a prefix.
   - They can be used in joins, subqueries, and any other place where a regular table can be used.

#### Example:
```sql
-- Creating a temporary table
CREATE TABLE #TempSales (
    ProductId INT,
    UnitPrice DECIMAL(10, 2),
    Quantity INT
);

-- Inserting data into the temporary table
INSERT INTO #TempSales (ProductId, UnitPrice, Quantity)
SELECT ProductId, UnitPrice, Quantity
FROM Sales
WHERE SaleDate = '2023-06-20';

-- Using the temporary table
SELECT ProductId, SUM(UnitPrice * Quantity) AS TotalSales
FROM #TempSales
GROUP BY ProductId;

-- Dropping the temporary table (optional, as it will be dropped automatically at the end of the session)
DROP TABLE #TempSales;
```

### SQL WITH Clause (Common Table Expressions - CTEs)

**Common Table Expressions (CTEs)**, introduced with the `WITH` clause, are used to define a temporary result set that can be referenced within a `SELECT`, `INSERT`, `UPDATE`, or `DELETE` statement. They are particularly useful for breaking down complex queries into simpler, more readable parts.

#### Characteristics of CTEs:
1. **Scope**: CTEs are valid only for the duration of the single query in which they are defined.
2. **Readability**: They help make complex queries more readable and maintainable.
3. **Recursion**: CTEs can be recursive, making them useful for hierarchical or tree-structured data.

#### Example:
```sql
-- Defining a CTE
WITH SalesCTE AS (
    SELECT ProductId, UnitPrice, Quantity
    FROM Sales
    WHERE SaleDate = '2023-06-20'
)
-- Using the CTE in a query
SELECT ProductId, SUM(UnitPrice * Quantity) AS TotalSales
FROM SalesCTE
GROUP BY ProductId;
```

#### Recursive CTE Example:
```sql
-- Example of a recursive CTE to calculate factorial
WITH RECURSIVE FactorialCTE AS (
    SELECT 1 AS Number, 1 AS Factorial
    UNION ALL
    SELECT Number + 1, Factorial * (Number + 1)
    FROM FactorialCTE
    WHERE Number < 5
)
SELECT * FROM FactorialCTE;
```

### Differences and Use Cases

1. **Scope**:
   - **Temporary Tables**: Persist for the duration of the session and can be used across multiple queries.
   - **CTEs**: Exist only within the scope of a single query.

2. **Performance**:
   - **Temporary Tables**: Can be indexed and may provide better performance for complex operations requiring multiple uses of the same intermediate result set.
   - **CTEs**: More lightweight, used within a single query, and are easier to read and write for single-use scenarios.

3. **Usage**:
   - **Temporary Tables**: Suitable for complex scenarios where intermediate results need to be reused across multiple queries or parts of a larger query.
   - **CTEs**: Ideal for simplifying complex queries, especially when you need a clear and readable way to break down the logic into steps within a single query.

By understanding both temporary tables and CTEs, you can choose the most appropriate tool for organizing and optimizing your SQL queries, depending on the specific requirements and complexity of the tasks at hand.