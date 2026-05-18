# Database Self-Study Roadmap – Beginner
(MySQL & MS SQL Server)

## 🎯 Goal
Understand database fundamentals and write basic SQL queries confidently.

---

## 1. Core Database Concepts
Learn and understand:

- What is a Database
- DBMS vs RDBMS
- Tables, Rows, Columns
- Primary Key
- Foreign Key
- Data Types
- Relationships:
  - One-to-One
  - One-to-Many
  - Many-to-Many

👉 Outcome: You should be able to explain how tables are related.

---

## 2. Install Database Tools

### MySQL
- Install MySQL Server
- Install MySQL Workbench

### MS SQL Server
- Install SQL Server Express
- Install SQL Server Management Studio (SSMS)

Create a test database:
```sql
CREATE DATABASE PracticeDB;
```

### 3. SQL Basics (Learn in Order)
### 3.1 Basic SELECT Queries

```bash
SELECT * FROM students;
SELECT name, age FROM students;
SELECT * FROM students WHERE age > 20;
SELECT * FROM students ORDER BY name;
```

### 3.2 Insert, Update, Delete
```bash
INSERT INTO students VALUES (1, 'Aung Aung', 20);
UPDATE students SET age = 21 WHERE id = 1;
DELETE FROM students WHERE id = 1;
```

### 3.3 Constraints
- PRIMARY KEY
- FOREIGN KEY
- NOT NULL
- UNIQUE
```bash
CREATE TABLE students (
  id INT PRIMARY KEY,
  name VARCHAR(50) NOT NULL
);
```

### 3.4 Aggregation Functions
- COUNT
- SUM
- AVG
-	MIN
- MAX
```bash
SELECT COUNT(*) FROM students;
SELECT department, COUNT(*) FROM students GROUP BY department;
```

### 4. Practice Tables

Create and practice using:

-	Student
-	Course
-	Enrollment

### 5. Daily Practice Routine

-	Practice 30–60 minutes daily
-	Write at least 5–10 queries
-	Always run queries and check output


✅ Beginner Outcome

You can:

-	Create databases and tables
-	Write CRUD queries
-	Use basic filtering and aggregation