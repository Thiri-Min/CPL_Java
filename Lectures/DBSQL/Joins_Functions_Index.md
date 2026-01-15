# SQL Core Concepts: Joins, Aggregation, Procedures, Indexes & Transactions
(MySQL & MS SQL Server)

---

## 🎯 Purpose
This document explains key SQL concepts required for real-world database usage, focusing on **data retrieval, performance, and data integrity**.

---

# 1. Joins & Aggregation

## 1.1 INNER JOIN
Returns only rows that have matching values in both tables.

```sql
SELECT s.student_name, e.course_id
FROM student s
INNER JOIN enrollment e ON s.student_id = e.student_id;
```

### 1.2 Left Join

Returns all rows from the left table and matching rows from the right table.

```
SELECT s.student_name, e.course_id
FROM student s
LEFT JOIN enrollment e ON s.student_id = e.student_id;
```

### 1.3 GROUP BY

Groups rows to perform aggregation.
```
SELECT course_id, COUNT(*) AS total_students
FROM enrollment
GROUP BY course_id;
```

### 1.4 HAVING

Filters aggregated results (used with GROUP BY).
```
SELECT course_id, COUNT(*) AS total_students
FROM enrollment
GROUP BY course_id
HAVING COUNT(*) > 5;
```
🔑 Difference:

- WHERE → filters rows

- HAVING → filters groups

### 1.5 Aggregation Functions

Common functions:

- COUNT()
- SUM()
- AVG()
- MIN()
- MAX()

```
SELECT AVG(grade) FROM enrollment;
```
### 1.6 Common Table Expression (CTE)

A temporary named result set used for complex queries.
```
WITH AvgGrade AS (
  SELECT AVG(grade) AS avg_grade
  FROM enrollment
)
SELECT *
FROM enrollment
WHERE grade > (SELECT avg_grade FROM AvgGrade);
```
✅ Benefits:

- Improves readability
- Simplifies complex logic

## 1.7 Views
A stored query that behaves like a table.

```
CREATE VIEW vw_student_courses AS
SELECT s.student_name, c.course_name, e.grade
FROM student s
JOIN enrollment e ON s.student_id = e.student_id
JOIN course c ON e.course_id = c.course_id;
```
✅ Use for:

- Reporting
- Security (limit column access)
- Reusability

------------------------------------

### 2.2 Input & Output Parameters
Stored Procedure Example (MSSQL)

```
CREATE PROCEDURE GetStudentCount
  @courseId INT,
  @total INT OUTPUT
AS
BEGIN
  SELECT @total = COUNT(*)
  FROM enrollment
  WHERE course_id = @courseId;
END;
```

### 2.3 Control Flow

Used to control logic inside procedures.

Common statements:

- IF / ELSE
- WHILE
- CASE

```
IF @score >= 50
  PRINT 'PASS'
ELSE
  PRINT 'FAIL';
```

### 3. Indexes
### 3.1 Index & B-Tree (Concept)

Index = data structure to speed up search

Most DBs use B-Tree indexes

Works like a book index

### 3.2 When Index Helps

WHERE conditions

JOIN columns

ORDER BY

### 3.3 EXPLAIN (Idea Level)

Shows how the database executes a query.
```
EXPLAIN SELECT * FROM enrollment WHERE course_id = 1;
```

### 4. Transactions & Data Integrity
### 4.1 Transaction Lifecycle

- BEGIN TRANSACTION

- Execute SQL statements

- COMMIT (save)

- ROLLBACK (undo)

```
BEGIN TRANSACTION;
UPDATE account SET balance = balance - 100 WHERE id = 1;
UPDATE account SET balance = balance + 100 WHERE id = 2;
COMMIT;
```

✅ Summary

After studying this module, you should understand:

- How joins and aggregation work together

- How to avoid common join mistakes

- Differences between functions and procedures

- Index basics and performance concepts

- How transactions protect data integrity
