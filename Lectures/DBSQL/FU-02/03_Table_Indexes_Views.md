# 📘 Summary: Table Indexes and Views

## 🎯 Lesson Objectives
- Understand what [indexes](ca://s?q=SQL_Server_indexes) are and when to use them  
- Create, manage, and drop indexes on tables in [SQL Server](ca://s?q=SQL_Server_indexes)  
- Explain how indexes improve query performance (B-Tree concept)  
- Understand [views](ca://s?q=SQL_Server_views) as virtual tables  
- Create, query, and manage views for security and reporting  

---

## 🗂 Section 1: Table Indexes

### 1.1 What Is an Index?
- An **index** is a database structure that speeds up data retrieval (like an index in a book).  
- Without an index, SQL Server may scan the entire table (**table scan**).  
- With an index, the engine can locate rows faster using a **B-Tree** (balanced tree) structure.  
- **Trade-off**: Faster `SELECT` / `JOIN` / `WHERE` / `ORDER BY`, but slower `INSERT` / `UPDATE` / `DELETE` and extra storage space.

### 1.2 Types of Indexes (SQL Server)
| Type | Description |
|------|-------------|
| **Clustered** | Sorts and stores table rows in index order. **One per table.** Often on PRIMARY KEY. |
| **Nonclustered** | Separate structure with pointers to rows. **Multiple allowed** per table. |
| **Unique** | Ensures indexed column values are unique (clustered or nonclustered). |
| **Composite** | Index on **two or more columns** (order of columns matters). |
| **Filtered** | Index on a subset of rows (e.g. only `Status = 'Active'`). |

### 1.3 When Indexes Help
- `WHERE` on indexed columns  
- `JOIN` on indexed foreign key / primary key columns  
- `ORDER BY` on indexed columns  
- Large tables with frequent read queries  

### 1.4 When to Avoid Too Many Indexes
- Small tables (full scan may be faster)  
- Tables with heavy write traffic  
- Columns that change very often  
- Low-selectivity columns (e.g. boolean with only two values) unless filtered index is appropriate  

### 1.5 Creating Indexes (T-SQL)

**Nonclustered index on one column:**
```sql
CREATE INDEX IX_Student_Email
ON Student (Email);
```

**Composite index:**
```sql
CREATE INDEX IX_Enrollment_Student_Course
ON Enrollment (StudentID, CourseID);
```

**Unique index:**
```sql
CREATE UNIQUE INDEX UX_Student_StudentCode
ON Student (StudentCode);
```

**Clustered index** (if table has no clustered index yet):
```sql
CREATE CLUSTERED INDEX CX_Student_StudentID
ON Student (StudentID);
```

### 1.6 Viewing and Dropping Indexes
```sql
-- List indexes on a table
EXEC sp_helpindex 'Student';

-- Drop an index
DROP INDEX IX_Student_Email ON Student;
```

### 1.7 Execution Plans (Concept)
- Use **Estimated Execution Plan** or `SET SHOWPLAN_TEXT ON` in SSMS to see if a query uses an index seek vs. scan.  
- **Index Seek** → generally good (targeted lookup).  
- **Index Scan / Table Scan** → may need index tuning on large tables.

```sql
SET SHOWPLAN_ALL ON;
GO
SELECT * FROM Student WHERE Email = 'student@example.com';
GO
SET SHOWPLAN_ALL OFF;
```

---

## 🗂 Section 2: Views

### 2.1 What Is a View?
- A **view** is a **virtual table** defined by a `SELECT` query.  
- It does **not** store data itself (unless it is an **indexed view** — advanced topic).  
- Data comes from underlying base tables when you query the view.

### 2.2 Why Use Views?
| Benefit | Example |
|---------|---------|
| **Simplify queries** | Hide complex joins behind one object |
| **Security** | Expose only safe columns (no salary, no password) |
| **Consistency** | Same business logic for all reports |
| **Reusability** | `SELECT * FROM vw_ActiveStudents` instead of repeating `WHERE` |

### 2.3 Creating a View
```sql
CREATE VIEW vw_StudentSummary
AS
SELECT
    s.StudentID,
    s.FullName,
    s.Email,
    d.DepartmentName
FROM Student s
INNER JOIN Department d ON s.DepartmentID = d.DepartmentID
WHERE s.IsActive = 1;
GO
```

**Query the view:**
```sql
SELECT * FROM vw_StudentSummary;
```

### 2.4 Altering and Dropping Views
```sql
-- Change view definition
ALTER VIEW vw_StudentSummary
AS
SELECT
    s.StudentID,
    s.FullName,
    s.Email,
    d.DepartmentName,
    s.EnrollmentYear
FROM Student s
INNER JOIN Department d ON s.DepartmentID = d.DepartmentID
WHERE s.IsActive = 1;
GO

-- Remove view
DROP VIEW vw_StudentSummary;
GO
```

### 2.5 Views with Joins and Aggregation
```sql
CREATE VIEW vw_CourseEnrollmentCount
AS
SELECT
    c.CourseID,
    c.CourseName,
    COUNT(e.StudentID) AS TotalStudents
FROM Course c
LEFT JOIN Enrollment e ON c.CourseID = e.CourseID
GROUP BY c.CourseID, c.CourseName;
GO

SELECT * FROM vw_CourseEnrollmentCount
WHERE TotalStudents > 10;
```

### 2.6 Important Rules for Views
- Views can be used in `SELECT` like tables (often in `JOIN`s with other tables/views).  
- **Standard views** are generally **read-only** for inserts/updates unless rules allow it (simple single-table views).  
- Changing base table structure may **break** a view if columns are removed or renamed.  
- Always document view purpose for your team.

### 2.7 View vs. Table (Quick Comparison)
| Feature | Table | View |
|---------|-------|------|
| Stores data | Yes | No (by default) |
| Physical storage | Yes | No (definition only) |
| INSERT/UPDATE/DELETE | Yes | Limited / depends on view |
| Purpose | Persist data | Simplify access & security |

---

## 🗂 Section 3: Indexes + Views Together

**Example:** Report view on indexed columns for performance.

```sql
-- Index supports the join and filter
CREATE INDEX IX_Enrollment_StudentID ON Enrollment (StudentID);

CREATE VIEW vw_StudentGrades
AS
SELECT
    s.FullName,
    c.CourseName,
    e.Grade
FROM Student s
INNER JOIN Enrollment e ON s.StudentID = e.StudentID
INNER JOIN Course c ON e.CourseID = c.CourseID;
GO
```

---

## ✅ Key Takeaways
1. **Indexes** speed up reads; use on columns in `WHERE`, `JOIN`, and `ORDER BY`.  
2. Each table has **one clustered index**; you can add **many nonclustered** indexes.  
3. **Views** simplify queries and improve security; they are virtual tables based on `SELECT`.  
4. Tune indexes using execution plans; avoid over-indexing write-heavy tables.  
5. Name indexes clearly (e.g. `IX_TableName_ColumnName`).

---

## 🔗 Practice & Reference
- [Microsoft Docs – Indexes](https://learn.microsoft.com/en-us/sql/relational-databases/indexes/indexes)  
- [Microsoft Docs – Views](https://learn.microsoft.com/en-us/sql/relational-databases/views/views)  
- [SQLZoo](https://sqlzoo.net/) – Practice SQL  
- [W3Schools SQL Indexes](https://www.w3schools.com/sql/sql_create_index.asp)  

---

## 📝 Quick Review Questions
1. What is the difference between a **clustered** and **nonclustered** index?  
2. Why might too many indexes slow down `INSERT` operations?  
3. What is a view, and how is it different from a table?  
4. Write a `CREATE VIEW` that shows student name and course name from two joined tables.  
5. When would you use a **composite index** instead of two separate indexes?
