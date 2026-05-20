# 📘 FU-02 Complete Summary — Database Fundamentals (SQL Server)

> **One-file overview** of all FU-02 lessons: Entity-Relationship Modelling, SQL Server Introduction, Table Indexes & Views, and Basic DML & Operators.

| # | Topic | Source file |
|---|--------|-------------|
| 1 | Entity-Relationship Modelling | `01_Entity_RelationShip_Modelling.md` |
| 2 | SQL Server Introduction | `02_SQL_Server_Introduction.md` |
| 3 | Table Indexes and Views | `03_Table_Indexes_Views.md` |
| 4 | Basic DML Statements and Operators | `04_Basic_DML_Statements_and_Operators.md` |

---

## 🎯 FU-02 Learning Goals (Overall)

By the end of FU-02 you should be able to:

1. Design databases using **ERD** and convert models to relational schemas  
2. Work with **Microsoft SQL Server** and **T-SQL** (create/alter/drop databases)  
3. Use **indexes** and **views** to improve performance and simplify access  
4. Write safe **DML** (`INSERT`, `UPDATE`, `DELETE`) with **operators** and **transactions**

---

# Part 1 — Entity-Relationship Modelling

## 1.1 Database Basics

| Term | Meaning |
|------|---------|
| **Database** | Organized collection of data |
| **DBMS** | Software that manages databases (SQL Server, MySQL, PostgreSQL, Oracle, etc.) |
| **Relational DB** | SQL, structured tables, rows & columns |
| **NoSQL** | Documents, key-value, flexible schema |

**Data types (by structure):**

- **Structured** — tables with fixed columns  
- **Unstructured** — images, videos, free text  
- **Semi-structured** — JSON, XML with tags/metadata  

## 1.2 Core Table Concepts

- **Table** — collection of related data  
- **Row (record)** — one instance  
- **Column (field)** — one attribute  
- **Primary Key (PK)** — unique identifier per row  
- **Foreign Key (FK)** — references PK in another table (links tables)  

## 1.3 ERD (Entity-Relationship Diagram)

Visual model of **entities**, **attributes**, and **relationships**.

| Notation | Features |
|----------|----------|
| **Chen** | Rectangles = entities, ovals = attributes, diamonds = relationships |
| **Crow’s Foot** | Common in industry; shows cardinality (1:1, 1:N, M:N) |

**Design process:**

1. Define purpose & requirements  
2. Identify entities, attributes, relationships  
3. Draw ERD  
4. Convert ERD → relational schema (tables, PK, FK)  
5. **Normalize** (1NF, 2NF, 3NF, BCNF) — reduce redundancy  
6. Implement in chosen DBMS  

## 1.4 Relationships & Cardinality

| Type | Example |
|------|---------|
| **One-to-One (1:1)** | Employee ↔ one Department head role |
| **One-to-Many (1:N)** | Department → many Employees |
| **Many-to-Many (M:N)** | Students ↔ Courses (needs junction table) |

## 1.5 Data Model Levels

| Level | Focus |
|-------|--------|
| **Conceptual** | Business entities (Customer, Product) — no column types |
| **Logical** | Attributes, relationships, operational detail |
| **Physical** | Tables, data types, PK/FK, constraints — ready to build |

## 1.6 Practice Example — University System

**Entities:** Student, Lecturer, Course, Class, Department, Classroom, Schedule, Grade  

**Relationships:** enrollments, teaching assignments, grades, scheduling  

**Takeaways:** ERD → schema; PK/FK enforce integrity; normalization improves design quality.

---

# Part 2 — SQL Server Introduction

## 2.1 What Is SQL Server?

- **RDBMS** by Microsoft  
- Supports **ANSI SQL** + **T-SQL** (Transact-SQL)  
- **Editions:** Enterprise, Standard, Web, Developer (full, non-prod), **Express** (free, small apps)  
- **Instances:** Multiple instances on one server for isolation, versions, security  

## 2.2 Database Operations (T-SQL)

```sql
-- Create
CREATE DATABASE Edu_TSQL;

-- Rename
ALTER DATABASE Edu_TSQL MODIFY NAME = Edu_TSQL_Alter;

-- Delete
DROP DATABASE Edu_TSQL_Alter;
```

Also manageable via **SQL Server Management Studio (SSMS)** GUI.

**Takeaways:** SQL Server uses T-SQL; know editions for learning vs production; databases are created and managed with DDL.

---

# Part 3 — Table Indexes and Views

## 3.1 Indexes

**Purpose:** Speed up data retrieval (like a book index).  
**Structure:** Often **B-Tree** — faster seeks vs full **table scan**.  
**Trade-off:** Faster reads; slower writes (`INSERT`/`UPDATE`/`DELETE`) and more disk space.

### Index Types (SQL Server)

| Type | Notes |
|------|--------|
| **Clustered** | Sorts/stores rows in index order; **one per table**; often on PK |
| **Nonclustered** | Separate structure + pointers; **many per table** |
| **Unique** | No duplicate values in indexed column(s) |
| **Composite** | Multiple columns; **column order matters** |
| **Filtered** | Subset of rows (e.g. `WHERE Status = 'Active'`) |

### When to Use / Avoid

**Use on:** `WHERE`, `JOIN`, `ORDER BY` columns; large read-heavy tables  

**Avoid excess on:** tiny tables, write-heavy tables, low-selectivity columns  

### T-SQL Examples

```sql
CREATE INDEX IX_Student_Email ON Student (Email);

CREATE INDEX IX_Enrollment_Student_Course ON Enrollment (StudentID, CourseID);

CREATE UNIQUE INDEX UX_Student_StudentCode ON Student (StudentCode);

DROP INDEX IX_Student_Email ON Student;

EXEC sp_helpindex 'Student';
```

**Execution plans:** Index **Seek** (good) vs **Scan** (may need tuning on large tables).

## 3.2 Views

**Definition:** **Virtual table** from a `SELECT` — no stored data by default (unless indexed view, advanced).

| Benefit | Use case |
|---------|----------|
| Simplify queries | Hide complex joins |
| Security | Hide sensitive columns |
| Consistency | Shared business logic for reports |

```sql
CREATE VIEW vw_StudentSummary
AS
SELECT s.StudentID, s.FullName, s.Email, d.DepartmentName
FROM Student s
INNER JOIN Department d ON s.DepartmentID = d.DepartmentID
WHERE s.IsActive = 1;
GO

SELECT * FROM vw_StudentSummary;

ALTER VIEW vw_StudentSummary AS ...;
DROP VIEW vw_StudentSummary;
```

| Feature | Table | View |
|---------|-------|------|
| Stores data | Yes | No (default) |
| Purpose | Persist | Simplify access / security |

**Indexes + views:** Index join/filter columns under views used in heavy reports.

**Takeaways:** One clustered index per table; name indexes clearly (`IX_Table_Column`); views are read-mostly virtual tables.

---

# Part 4 — Basic DML Statements and Operators

## 4.1 DML Overview

| Statement | Purpose |
|-----------|---------|
| `SELECT` | Read data |
| `INSERT` | Add rows |
| `UPDATE` | Change rows |
| `DELETE` | Remove rows |
| `MERGE` | Combined upsert (advanced) |

**DDL** defines structure; **DML** manipulates data inside tables.

## 4.2 INSERT

```sql
INSERT INTO Student (StudentID, FullName, Email, Age, DepartmentID)
VALUES (101, N'Thiri Min', N'thiri@example.com', 22, 1);

-- Multiple rows
INSERT INTO Student (StudentID, FullName, Email)
VALUES (102, N'Aung', N'a@ex.com'), (103, N'Su', N's@ex.com');

-- From query
INSERT INTO Student (StudentID, FullName, DepartmentID)
SELECT 200 + DepartmentID, DepartmentName, DepartmentID FROM Department;
```

**Tips:** List column names; respect PK/UNIQUE/NOT NULL/FK; use `N'...'` for Unicode in SQL Server.

## 4.3 UPDATE

```sql
UPDATE Student SET Age = 23 WHERE StudentID = 101;

UPDATE Student SET Age = Age + 1 WHERE DepartmentID = 1;
```

**Safety:** Always use `WHERE` unless updating all rows; preview with `SELECT` first.

## 4.4 DELETE vs TRUNCATE

```sql
DELETE FROM Student WHERE StudentID = 104;
DELETE FROM Student;        -- all rows, table remains
TRUNCATE TABLE Student;     -- fast reset, no WHERE, FK/trigger caveats
```

| | `DELETE` | `TRUNCATE` |
|---|----------|------------|
| `WHERE` | Yes | No |
| Logging | Row-by-row | Minimal |
| Triggers | Can fire | Typically no per-row |

## 4.5 Operators (in `WHERE` / expressions)

| Category | Operators / syntax |
|----------|-------------------|
| **Comparison** | `=`, `<>`, `>`, `<`, `>=`, `<=` |
| **Logical** | `AND`, `OR`, `NOT` (use parentheses) |
| **Pattern** | `LIKE` — `%` (any length), `_` (one char) |
| **Range** | `BETWEEN x AND y` (inclusive) |
| **List** | `IN (1, 2, 3)` |
| **NULL** | `IS NULL`, `IS NOT NULL` — never `= NULL` |
| **Arithmetic** | `+`, `-`, `*`, `/`, `%` |

```sql
SELECT * FROM Student
WHERE DepartmentID = 1
  AND Age BETWEEN 20 AND 25
  AND FullName LIKE N'T%'
  AND Email IS NOT NULL;
```

## 4.6 Transactions

```sql
BEGIN TRANSACTION;
    UPDATE Student SET Age = Age + 1 WHERE DepartmentID = 1;
    SELECT * FROM Student WHERE DepartmentID = 1;
-- COMMIT;   or   ROLLBACK;
```

**Takeaways:** Preview before DML; `WHERE` on UPDATE/DELETE; `IS NULL` for missing values; transactions for safe changes.

---

# ✅ FU-02 Master Checklist

| Skill | Can you…? |
|-------|-----------|
| ERD | Draw entities, PK/FK, and 1:1 / 1:N / M:N relationships? |
| Schema | Convert ERD to tables and apply normalization? |
| SQL Server | Create, rename, and drop a database with T-SQL? |
| Indexes | Choose clustered vs nonclustered and create/drop an index? |
| Views | Create a view that joins tables and query it? |
| DML | Insert, update, delete with correct `WHERE` and operators? |
| Safety | Use `IS NULL`, transactions, and SELECT-before-UPDATE? |

---

# 📝 Combined Review Questions

1. What is the difference between **conceptual**, **logical**, and **physical** data models?  
2. How do **primary** and **foreign keys** support referential integrity?  
3. Name SQL Server **editions** suitable for learning vs enterprise production.  
4. **Clustered** vs **nonclustered** index — how many per table?  
5. Why can too many indexes slow **INSERT** operations?  
6. What is a **view**, and how does it differ from a **table**?  
7. When should you use `DELETE` instead of `TRUNCATE`?  
8. Why must you use `IS NULL` instead of `= NULL`?  
9. Write a query: students in department 1 or 2, age 20–25, name starts with **M**.  
10. What steps do you take before running `UPDATE` on production data?

---

# 🔗 References

- [Microsoft SQL Server Documentation](https://learn.microsoft.com/en-us/sql/sql-server/)  
- [Indexes](https://learn.microsoft.com/en-us/sql/relational-databases/indexes/indexes)  
- [Views](https://learn.microsoft.com/en-us/sql/relational-databases/views/views)  
- [INSERT / UPDATE / DELETE (T-SQL)](https://learn.microsoft.com/en-us/sql/t-sql/statements/)  
- [SQLZoo](https://sqlzoo.net/) — hands-on practice  

---

*Last updated: consolidates FU-02 lessons 01–04 for quick revision and exam prep.*
