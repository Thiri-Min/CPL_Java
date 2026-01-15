# Database Fundamentals & SQL – Complete Guide
(MySQL & MS SQL Server)

---

## 🎯 Course Goal
Build strong database fundamentals and SQL skills from **basic concepts** to **intermediate real-world querying**, suitable for junior developers and interns.

---

# PART 1: DATABASE FUNDAMENTALS (BEGINNER)

## 1. Core Database Concepts

Learn and understand:

- What is a Database
- DBMS vs RDBMS
- Tables, Rows, Columns
- Data Types
- Primary Key
- Foreign Key
- Relationships:
  - One-to-One
  - One-to-Many
  - Many-to-Many

👉 Outcome: You can explain how tables are structured and related.

---

## 2. Database Tools Setup

### MySQL
- MySQL Server
- MySQL Workbench

### MS SQL Server
- SQL Server Express
- SQL Server Management Studio (SSMS)

Create a practice database:
```sql
CREATE DATABASE PracticeDB;

### 3. SQL Basics (CRUD Operations)
### 3.1 SELECT Queries
```
SELECT * FROM students;
SELECT name, age FROM students;
SELECT * FROM students WHERE age > 20;
SELECT * FROM students ORDER BY name;
```

### 3.2 INSERT, UPDATE, DELETE

```
INSERT INTO students VALUES (1, 'Aung Aung', 20);
UPDATE students SET age = 21 WHERE id = 1;
DELETE FROM students WHERE id = 1;

```
### 4. Constraints & Data Integrity

- PRIMARY KEY
- FOREIGN KEY
- NOT NULL
- UNIQUE

```
CREATE TABLE students (
  id INT PRIMARY KEY,
  name VARCHAR(50) NOT NULL
);
```

5. Aggregation Functions (Basics)
- COUNT
- SUM
- AVG
- MIN
- MAX

```
SELECT COUNT(*) FROM students;
SELECT department, COUNT(*) 
FROM students 
GROUP BY department;
```

------------------------

PART 2: SQL & DATABASES (INTERMEDIATE)
### 6. Table Relationships (Deep Dive)
### 6.1 One-to-Many

Example: Department → Employees
```
SELECT e.name, d.dept_name
FROM employee e
JOIN department d ON e.dept_id = d.id;
```

### 6.2 Many-to-Many
Use a junction table:

Student ↔ Course → Enrollment

### 7. Joins (Very Important)

- INNER JOIN

- LEFT JOIN

- RIGHT JOIN

- SELF JOIN

```
SELECT o.order_id, c.customer_name
FROM orders o
LEFT JOIN customers c ON o.customer_id = c.id;
```

### 8. Advanced Filtering

- BETWEEN
- IN
- LIKE
- IS NULL / IS NOT NULL
```
SELECT * FROM students
WHERE name LIKE 'A%' 
AND age BETWEEN 18 AND 25;
```

### 9.Aggregation & GROUP BY (Advanced)

GROUP BY multiple columns

HAVING vs WHERE

### 10. Subqueries
Subquery in WHERE
```
SELECT * FROM employee
WHERE salary > (SELECT AVG(salary) FROM employee);
```

Subquery in FROM
```
SELECT dept_id, avg_salary
FROM (
  SELECT dept_id, AVG(salary) AS avg_salary
  FROM employee
  GROUP BY dept_id
) t;
```
### 11. Views

```
CREATE VIEW active_employees AS
SELECT * 
FROM employee 
WHERE status = 'ACTIVE';
```
-----------------------------

### Mini Project

### Library Management Database

Tables:

- Books

- Members

- Borrow_Records

Tasks:

Write JOIN queries

Use aggregation for reports

Apply filtering & subqueries

✅ Final Outcome

By completing this guide, you can:

Design relational databases

Write complex SQL queries

Use joins, subqueries, and CTEs

Create views and indexes

Analyze real-world datasets