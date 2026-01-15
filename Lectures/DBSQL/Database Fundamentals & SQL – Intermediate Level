# Database Fundamentals & SQL – Intermediate Level

## 🎯 Goal
Strengthen SQL skills to handle real-world queries, relationships, and reporting use cases using MySQL and MS SQL Server.

---

## 1. Review of Core Concepts
Before moving forward, ensure you are comfortable with:

- Tables, Rows, Columns
- Primary Key vs Foreign Key
- Basic SELECT, INSERT, UPDATE, DELETE
- Basic WHERE conditions
- Basic aggregation (COUNT, SUM, AVG)

---

## 2. Table Relationships (Deep Dive)

### 2.1 One-to-Many
Example:
- Department → Employees

```sql
SELECT e.name, d.dept_name
FROM employee e
JOIN department d ON e.dept_id = d.id;
```

2.2 Many-to-Many

Using junction table:

- Student ↔ Course → Enrollment

3. Joins (Very Important)

- INNER JOIN
- LEFT JOIN
- RIGHT JOIN
- SELF JOIN

```
SELECT o.order_id, c.customer_name
FROM orders o
LEFT JOIN customers c ON o.customer_id = c.id;
```

👉 Practice: Always draw tables before writing joins.

### 4. Advanced Filtering

- BETWEEN
- IN
- LIKE
- IS NULL / IS NOT NULL
```
SELECT * FROM students
WHERE name LIKE 'A%' AND age BETWEEN 18 AND 25;
```
### 5. Aggregation & GROUP BY
- GROUP BY with multiple columns
- HAVING vs WHERE

```
SELECT department_id, COUNT(*) AS total_emp
FROM employee
GROUP BY department_id
HAVING COUNT(*) > 5;
```

### 6. Subqueries
### 6.1 Subquery in WHERE
```
SELECT * FROM employee
WHERE salary > (SELECT AVG(salary) FROM employee);
```

### 6.2 Subquery in FROM
```
SELECT dept_id, avg_salary
FROM (
  SELECT dept_id, AVG(salary) AS avg_salary
  FROM employee
  GROUP BY dept_id
) t;
```

### 7. Common Table Expressions (CTE)

```
WITH DeptSalary AS (
  SELECT dept_id, AVG(salary) avg_salary
  FROM employee
  GROUP BY dept_id
)
SELECT * FROM DeptSalary;
```

### 8. Index Basics

Understand:

- What is an index
- When to use indexes
- Read vs write performance trade-off
```
CREATE INDEX idx_employee_name ON employee(name);
```

### 9. Views
```
CREATE VIEW active_employees AS
SELECT * FROM employee WHERE status = 'ACTIVE';
```

### 10. Mini Project (Intermediate)

Build a Library Management Database:

- Books

- Members

- Borrow Records

Tasks:

- Use joins

- Write reports

- Use aggregation

✅ Outcome

You can:

- Write complex joins

- Use subqueries & CTEs

- Create views and indexes

- Analyze real-world data