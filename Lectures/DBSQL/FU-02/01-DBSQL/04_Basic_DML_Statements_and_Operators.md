# 📘 Summary: Basic DML Statements and Operators

## 🎯 Lesson Objectives
- Understand [DML](ca://s?q=SQL_DML_data_manipulation_language) (Data Manipulation Language) in SQL Server  
- Write basic `INSERT`, `UPDATE`, and `DELETE` statements  
- Use comparison, logical, and pattern-matching operators in `WHERE` clauses  
- Apply `NULL` handling and common expression operators safely  
- Combine DML with simple `SELECT` filters for real table operations  

---

## 🗂 Section 1: Introduction to DML

### 1.1 What Is DML?
**DML** changes or reads **data inside tables** (unlike DDL, which defines structure).

| Statement | Purpose |
|-----------|---------|
| `SELECT` | Read / query data |
| `INSERT` | Add new rows |
| `UPDATE` | Modify existing rows |
| `DELETE` | Remove rows |
| `MERGE` | Insert, update, or delete in one statement (advanced) |

> In this lesson we focus on **INSERT**, **UPDATE**, **DELETE**, and operators used with `WHERE`.

### 1.2 Sample Tables (Reference)
```sql
-- Department
CREATE TABLE Department (
    DepartmentID   INT PRIMARY KEY,
    DepartmentName VARCHAR(100) NOT NULL
);

-- Student
CREATE TABLE Student (
    StudentID      INT PRIMARY KEY,
    FullName       VARCHAR(100) NOT NULL,
    Email          VARCHAR(150) UNIQUE,
    Age            INT,
    DepartmentID   INT,
    IsActive       BIT DEFAULT 1,
    FOREIGN KEY (DepartmentID) REFERENCES Department(DepartmentID)
);
```

---

## 🗂 Section 2: INSERT — Add Data

### 2.1 Insert One Row (All Columns)
```sql
INSERT INTO Department
VALUES (1, 'Information Technology');
```

### 2.2 Insert One Row (Named Columns — Recommended)
```sql
INSERT INTO Student (StudentID, FullName, Email, Age, DepartmentID, IsActive)
VALUES (101, N'Thiri Min', N'thiri@example.com', 22, 1, 1);
```

### 2.3 Insert Multiple Rows
```sql
INSERT INTO Student (StudentID, FullName, Email, Age, DepartmentID)
VALUES
    (102, N'Aung Aung', N'aung@example.com', 21, 1),
    (103, N'Su Su', N'susu@example.com', 23, 1),
    (104, N'Kyaw Lin', N'kyaw@example.com', 20, 2);
```

### 2.4 Insert from a Query
```sql
INSERT INTO Student (StudentID, FullName, Email, DepartmentID)
SELECT 200 + DepartmentID, DepartmentName, N'admin@dept.com', DepartmentID
FROM Department;
```

### 2.5 INSERT Tips
- Always list column names when possible (clear and safe).  
- Respect `PRIMARY KEY`, `UNIQUE`, `NOT NULL`, and `FOREIGN KEY` rules.  
- Use `N'...'` for Unicode text in SQL Server when needed.

---

## 🗂 Section 3: UPDATE — Modify Data

### 3.1 Update One Column
```sql
UPDATE Student
SET Age = 23
WHERE StudentID = 101;
```

### 3.2 Update Multiple Columns
```sql
UPDATE Student
SET
    Email = N'thirithiri@example.com',
    IsActive = 1
WHERE StudentID = 101;
```

### 3.3 Update with Expression
```sql
UPDATE Student
SET Age = Age + 1
WHERE DepartmentID = 1;
```

### 3.4 Update from Another Table (Join Style)
```sql
UPDATE s
SET s.DepartmentID = d.DepartmentID
FROM Student s
INNER JOIN Department d ON s.Email LIKE '%' + d.DepartmentName + '%'
WHERE s.DepartmentID IS NULL;
```

### 3.5 UPDATE Safety Rules
- **Always use `WHERE`** unless you intend to update every row.  
- Run a `SELECT` with the same `WHERE` first to preview affected rows.  
- Use transactions when updating production data (see Section 7).

```sql
-- Preview first
SELECT * FROM Student WHERE DepartmentID = 1;

-- Then update
UPDATE Student SET IsActive = 0 WHERE DepartmentID = 1;
```

---

## 🗂 Section 4: DELETE — Remove Data

### 4.1 Delete Specific Rows
```sql
DELETE FROM Student
WHERE StudentID = 104;
```

### 4.2 Delete with Condition
```sql
DELETE FROM Student
WHERE IsActive = 0;
```

### 4.3 Delete All Rows (Keep Table Structure)
```sql
DELETE FROM Student;   -- removes all rows; table remains

-- Faster reset when you do not need triggers/logs (careful):
TRUNCATE TABLE Student;
```

### 4.4 DELETE vs TRUNCATE
| Feature | `DELETE` | `TRUNCATE` |
|---------|----------|------------|
| `WHERE` clause | Yes | No |
| Row-by-row logging | Yes | Minimal logging |
| Triggers | Can fire | Does not fire per row |
| Foreign key | Safer with FK checks | May be blocked by FK |

---

## 🗂 Section 5: SQL Operators

Operators are used in `WHERE`, `SELECT` expressions, and `UPDATE`/`DELETE` conditions.

### 5.1 Comparison Operators
| Operator | Meaning | Example |
|----------|---------|---------|
| `=` | Equal | `Age = 21` |
| `<>` or `!=` | Not equal | `DepartmentID <> 1` |
| `>` | Greater than | `Age > 20` |
| `<` | Less than | `Age < 25` |
| `>=` | Greater or equal | `Age >= 18` |
| `<=` | Less or equal | `Age <= 30` |

```sql
SELECT * FROM Student WHERE Age >= 20 AND Age <= 25;
```

### 5.2 Logical Operators
| Operator | Meaning |
|----------|---------|
| `AND` | All conditions must be true |
| `OR` | At least one condition true |
| `NOT` | Reverses condition |

```sql
SELECT *
FROM Student
WHERE DepartmentID = 1
  AND (Age > 21 OR Email LIKE N'%@example.com');
```

**Tip:** Use parentheses to control `AND` / `OR` priority.

### 5.3 Pattern Matching — `LIKE`
| Wildcard | Meaning |
|----------|---------|
| `%` | Zero or more characters |
| `_` | Exactly one character |

```sql
-- Names starting with 'T'
SELECT * FROM Student WHERE FullName LIKE N'T%';

-- Emails ending with .com
SELECT * FROM Student WHERE Email LIKE N'%.com';

-- Second letter is 'h'
SELECT * FROM Student WHERE FullName LIKE N'_h%';
```

### 5.4 Range — `BETWEEN`
```sql
SELECT * FROM Student
WHERE Age BETWEEN 20 AND 23;   -- inclusive both ends
```

Equivalent to:
```sql
WHERE Age >= 20 AND Age <= 23;
```

### 5.5 List Match — `IN`
```sql
SELECT * FROM Student
WHERE DepartmentID IN (1, 2, 3);
```

### 5.6 NULL Handling — `IS NULL` / `IS NOT NULL`
- `NULL` means **unknown / missing**, not zero or empty string.  
- Never use `= NULL` or `<> NULL`.

```sql
-- Wrong
-- SELECT * FROM Student WHERE Email = NULL;

-- Correct
SELECT * FROM Student WHERE Email IS NULL;

SELECT * FROM Student WHERE Email IS NOT NULL;
```

### 5.7 Arithmetic Operators
Used in `SELECT` and `UPDATE` expressions.

| Operator | Example |
|----------|---------|
| `+` | `Age + 1` |
| `-` | `Price - Discount` |
| `*` | `Quantity * UnitPrice` |
| `/` | `Total / Count` |
| `%` | `Amount % 2` (remainder) |

```sql
SELECT FullName, Age, Age + 5 AS AgeInFiveYears
FROM Student;
```

---

## 🗂 Section 6: Combining DML with Operators (Practice)

```sql
-- 1) Add a new student
INSERT INTO Student (StudentID, FullName, Email, Age, DepartmentID)
VALUES (105, N'Mai Mai', N'mai@example.com', 19, 2);

-- 2) Promote age for IT department students over 20
UPDATE Student
SET Age = Age + 1
WHERE DepartmentID = 1 AND Age > 20;

-- 3) Deactivate students without email
UPDATE Student
SET IsActive = 0
WHERE Email IS NULL;

-- 4) Remove inactive students in department 2
DELETE FROM Student
WHERE DepartmentID = 2 AND IsActive = 0;

-- 5) Verify results
SELECT StudentID, FullName, Email, Age, DepartmentID, IsActive
FROM Student
WHERE DepartmentID IN (1, 2)
ORDER BY FullName;
```

---

## 🗂 Section 7: Transactions (Safe DML)

Use a transaction so you can **commit** or **rollback** changes.

```sql
BEGIN TRANSACTION;

    UPDATE Student SET Age = Age + 1 WHERE DepartmentID = 1;

    -- Check before saving
    SELECT * FROM Student WHERE DepartmentID = 1;

    -- COMMIT;     -- save changes
    -- ROLLBACK;   -- undo changes
```

---

## ✅ Key Takeaways
1. **DML** manipulates table data: `INSERT`, `UPDATE`, `DELETE`, and `SELECT`.  
2. Always use **`WHERE`** on `UPDATE` and `DELETE` unless you mean all rows.  
3. Use **`IS NULL` / `IS NOT NULL`** for missing values, not `= NULL`.  
4. Combine **`AND` / `OR` / LIKE / IN / BETWEEN`** to build flexible filters.  
5. Preview with `SELECT`, then run DML; use **transactions** for safety.

---

## 🔗 Practice & Reference
- [Microsoft Docs – INSERT](https://learn.microsoft.com/en-us/sql/t-sql/statements/insert-transact-sql)  
- [Microsoft Docs – UPDATE](https://learn.microsoft.com/en-us/sql/t-sql/statements/update-transact-sql)  
- [Microsoft Docs – DELETE](https://learn.microsoft.com/en-us/sql/t-sql/statements/delete-transact-sql)  
- [W3Schools SQL Operators](https://www.w3schools.com/sql/sql_operators.asp)  
- [SQLZoo](https://sqlzoo.net/)  

---

## 📝 Quick Review Questions
1. What is the difference between `INSERT` and `UPDATE`?  
2. Why should you avoid `UPDATE` or `DELETE` without a `WHERE` clause?  
3. Write a query to find students whose name starts with **M**.  
4. How do you check for rows where `Email` is missing?  
5. What is the difference between `DELETE` and `TRUNCATE`?
