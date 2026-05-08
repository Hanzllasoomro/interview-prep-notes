# SQL Interview Questions

## Role
Data Analyst / Data Engineer / Backend Developer / Software Engineer / BI Developer

## Experience Level
Beginner / Intermediate / Senior

## Key Concepts
- **RDBMS**: Relational Database Management Systems.
- **DML vs DDL**: Data Manipulation Language vs Data Definition Language.
- **Joins**: Combining data from multiple tables.
- **Aggregations**: Summarizing data (GROUP BY, HAVING).
- **Subqueries & CTEs**: Breaking down complex queries.
- **Window Functions**: Performing calculations across related rows.
- **Indexing**: Optimizing query performance.
- **Normalization**: Reducing data redundancy.
- **ACID Properties**: Ensuring reliable transactions.

---

## Common Interview Questions

### 🟢 Beginner Level

#### 1. What is the difference between `DELETE` and `TRUNCATE`?
- **DELETE**: A DML command that deletes rows one by one and logs each deletion. It can be rolled back and can have a `WHERE` clause.
- **TRUNCATE**: A DDL command that removes all rows from a table by deallocating the pages. It is faster, cannot be rolled back (in most systems), and cannot have a `WHERE` clause.

#### 2. What is a Primary Key vs. a Foreign Key?
- **Primary Key**: A unique identifier for each record in a table. It cannot be NULL.
- **Foreign Key**: A column that creates a relationship between two tables, pointing to the Primary Key of another table.

#### 3. What is the difference between `INNER JOIN` and `LEFT JOIN`?
- **INNER JOIN**: Returns only the rows that have matching values in both tables.
- **LEFT JOIN**: Returns all rows from the left table and the matching rows from the right table. If no match exists, it returns NULL for the right side.

---

### 🟡 Intermediate Level

#### 4. What is the difference between `WHERE` and `HAVING`?
- **WHERE**: Filters rows **before** any grouping or aggregation (DML).
- **HAVING**: Filters groups **after** the `GROUP BY` clause has been applied.

#### 5. Explain the difference between `UNION` and `UNION ALL`.
- **UNION**: Combines the result of two queries and removes duplicate rows (requires an extra sorting step).
- **UNION ALL**: Combines the result of two queries but keeps all rows, including duplicates. It is faster because it skip the deduplication step.

#### 6. What are Common Table Expressions (CTEs)?
A CTE is a temporary result set defined within the execution scope of a single `SELECT`, `INSERT`, `UPDATE`, or `DELETE` statement. It is defined using the `WITH` keyword and improves query readability.

---

### 🔴 Advanced Level

#### 7. What are Window Functions? Give examples.
Window functions perform calculations across a set of table rows that are related to the current row. Unlike aggregate functions, they do not group rows into a single output row.
- `ROW_NUMBER()`: Assigns a unique sequential integer to rows.
- `RANK()`: Assigns a rank with gaps if there are ties.
- `DENSE_RANK()`: Assigns a rank without gaps.
- `LEAD()` / `LAG()`: Accesses data from subsequent or previous rows.

#### 8. Explain ACID properties.
- **Atomicity**: The transaction is "all or nothing."
- **Consistency**: The database remains in a valid state after the transaction.
- **Isolation**: Concurrent transactions do not interfere with each other.
- **Durability**: Changes are permanent once the transaction is committed.

#### 9. What is Database Normalization?
The process of organizing data to reduce redundancy and improve data integrity.
- **1NF**: Atomic values, no repeating groups.
- **2NF**: In 1NF + all non-key attributes are fully functional dependent on the primary key.
- **3NF**: In 2NF + no transitive dependencies.

---

## Practical Coding Challenges

### Challenge 1: Find the 2nd Highest Salary
```sql
SELECT MAX(salary) 
FROM employees 
WHERE salary < (SELECT MAX(salary) FROM employees);
```

### Challenge 2: Find Duplicate Emails
```sql
SELECT email
FROM users
GROUP BY email
HAVING COUNT(email) > 1;
```

### Challenge 3: Get the latest order for each customer (using Window Function)
```sql
WITH RankedOrders AS (
    SELECT customer_id, order_date,
           ROW_NUMBER() OVER(PARTITION BY customer_id ORDER BY order_date DESC) as rn
    FROM orders
)
SELECT customer_id, order_date
FROM RankedOrders
WHERE rn = 1;
```

---

## Practical Tips
- **Index Wisely**: Don't index every column; focus on columns used in `WHERE`, `JOIN`, and `ORDER BY`.
- **Avoid SELECT ***: Always specify the columns you need to reduce I/O and memory usage.
- **Understand Execution Plans**: Use `EXPLAIN` to see how the database executes your query.
- **Be Consistent**: Use standard SQL keywords and consistent naming conventions.

## Useful Resources
- [SQLZoo](https://sqlzoo.net/) - Interactive SQL tutorials.
- [Mode SQL Tutorial](https://mode.com/sql-tutorial/) - Comprehensive guide for data analysis.
- [LeetCode SQL](https://leetcode.com/problemset/database/) - Practice real-world SQL problems.
- [PostgreSQL Documentation](https://www.postgresql.org/docs/) - In-depth reference for one of the most popular RDBMS.
