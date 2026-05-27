# 📘 Summary: Advanced DML & Built-in Functions (FU-02)

## 🎯 Overall Learning Objectives

- Combine data across tables using **JOINs**
- Write **subqueries** for complex filtering and reporting
- Use **CTEs** and **ranking functions** for advanced analytics (intro level)
- Transform and format data with **CAST**, **CONVERT**, **date/time**, and **string** functions

---

# Part 1 — Advanced DML

## 1.1 SQL Joins

**Joins** combine rows from two or more tables based on related columns (usually PK / FK).

| Join type | Result |
|-----------|--------|
| **INNER JOIN** | Only rows with matching values in **both** tables |
| **LEFT OUTER JOIN** | All rows from **left** + matches from right (NULL if no match) |
| **RIGHT OUTER JOIN** | All rows from **right** + matches from left |
| **FULL OUTER JOIN** | All rows from both sides; NULL where no match |
| **CROSS JOIN** | Cartesian product (every row × every row) |
| **SELF JOIN** | Same table joined to itself (e.g. employee → manager) |

### Excluding joins (anti-join style)

| Type | Meaning |
|------|---------|
| **Left excluding** | Rows in left table **with no** match in right |
| **Right excluding** | Rows in right table **with no** match in left |
| **Full outer excluding** | Non-matching rows from **both** sides |

### Multi-table joins

- Chain **3+ tables** with multiple `ON` conditions in one query.

### Example patterns

```sql
-- INNER: customers who placed orders
SELECT c.CustomerName, o.OrderDate
FROM Customer c
INNER JOIN Orders o ON c.CustomerID = o.CustomerID;

-- LEFT: all customers, even without orders
SELECT c.CustomerName, o.OrderID
FROM Customer c
LEFT JOIN Orders o ON c.CustomerID = o.CustomerID;

-- SELF: employee and manager names
SELECT e.FullName AS Employee, m.FullName AS Manager
FROM Employee e
LEFT JOIN Employee m ON e.ManagerID = m.EmployeeID;
```

---

## 1.2 Subqueries

A **subquery** is a query nested inside another (`SELECT`, `INSERT`, `UPDATE`, `DELETE`).

| Type | Description |
|------|-------------|
| **Single-row** | Returns one row (one value or one row of values) |
| **Multiple-row** | Returns many rows — use `IN`, `ANY`, `ALL` |
| **Multiple-column** | Returns more than one column |
| **Correlated** | References columns from the **outer** query |
| **Nested** | Subquery inside another subquery |

### Execution flow

1. **Inner** query runs first (usually) and produces a result set or value.  
2. **Outer** query uses that result for filtering, listing, or inserting.

### Example

```sql
-- Customers in a region (subquery in WHERE)
SELECT CustomerName
FROM Customer
WHERE RegionID IN (
    SELECT RegionID FROM Region WHERE RegionName = 'Southeast'
);

-- Correlated: orders above customer's average
SELECT OrderID, OrderAmount
FROM Orders o
WHERE OrderAmount > (
    SELECT AVG(OrderAmount)
    FROM Orders
    WHERE CustomerID = o.CustomerID
);
```

---

## 1.3 CTEs & Ranking (overview)

> Listed in course objectives; use for readable complex queries and analytics.

| Feature | Purpose |
|---------|---------|
| **CTE** (`WITH ... AS`) | Named temporary result set for cleaner multi-step SQL |
| **Ranking** (`ROW_NUMBER`, `RANK`, `DENSE_RANK`) | Number rows within partitions (e.g. top N per group) |

```sql
-- CTE example
WITH ActiveStudents AS (
    SELECT StudentID, FullName
    FROM Student
    WHERE IsActive = 1
)
SELECT * FROM ActiveStudents;

-- Ranking example
SELECT StudentID, Score,
       RANK() OVER (PARTITION BY CourseID ORDER BY Score DESC) AS RankInCourse
FROM Enrollment;
```

---

## 1.4 Advanced DML — Key Takeaways

| Topic | Remember |
|-------|----------|
| **INNER JOIN** | Only matches |
| **LEFT JOIN** | Keep all from left |
| **Subquery** | Inner first, then outer; `IN` for lists |
| **Correlated** | Inner references outer row |
| **CTE** | Readable multi-step queries |

---

# Part 2 — Built-in Functions

## 2.1 Conversion Functions

| Function | Use |
|----------|-----|
| **CAST** | Standard type conversion (portable) |
| **CONVERT** | SQL Server conversion + **date style** codes |

```sql
SELECT CAST('2026-05-19' AS DATE);
SELECT CAST(99.7 AS INT);                    -- 99
SELECT CONVERT(VARCHAR(10), GETDATE(), 103); -- dd/mm/yyyy
SELECT CAST('150' AS INT) * 2;
```

| Choose | When |
|--------|------|
| **CAST** | Simple type change |
| **CONVERT** | Formatted date/time output (style parameter) |

---

## 2.2 Date and Time Functions

| Function | Description |
|----------|-------------|
| **GETDATE()** | Current date and time |
| **DATEPART()** | Extract part (year, month, day, hour, …) |
| **DAY() / MONTH() / YEAR()** | Integer part of date |
| **DATEADD()** | Add or subtract interval |
| **DATEDIFF()** | Count of boundaries between two dates |

```sql
SELECT GETDATE();

SELECT YEAR(HireDate), MONTH(HireDate) FROM Employee;

SELECT DATEADD(day, 30, GETDATE()) AS DueIn30Days;
SELECT DATEADD(month, -6, GETDATE()) AS SixMonthsAgo;

SELECT DATEDIFF(day, OrderDate, GETDATE()) AS DaysSinceOrder;
SELECT DATEDIFF(year, BirthDate, GETDATE()) AS Age FROM Student;
```

**Note:** `DATEDIFF` counts **interval boundaries**, not always exact calendar length.

---

## 2.3 String Functions

| Function | Description |
|----------|-------------|
| **LTRIM()** | Remove leading spaces |
| **RTRIM()** | Remove trailing spaces |
| **SUBSTRING()** | Extract part of string (**start = 1**) |
| **LEN()** | String length |
| **CHARINDEX()** | Find substring position (no wildcards) |
| **PATINDEX()** | Find pattern position (`%`, `_` allowed) |

```sql
SELECT LTRIM(RTRIM('  Hello  '));

SELECT SUBSTRING('Bill Gates', 1, 4);  -- Bill

SELECT LEN('SQL Server');

SELECT CHARINDEX('@', 'student@school.com');

SELECT PATINDEX('%Gates%', 'Bill Gates');
```

| | CHARINDEX | PATINDEX |
|---|-----------|----------|
| Wildcards | No | Yes |
| Use for | Exact text | Pattern search |

---

## 2.4 Built-in Functions — Key Takeaways

| Category | Functions |
|----------|-----------|
| **Conversion** | `CAST`, `CONVERT` |
| **Date/Time** | `GETDATE`, `DATEPART`, `DAY`, `MONTH`, `YEAR`, `DATEADD`, `DATEDIFF` |
| **String** | `LTRIM`, `RTRIM`, `SUBSTRING`, `LEN`, `CHARINDEX`, `PATINDEX` |

**Rules to remember:**
- **SUBSTRING** starts at position **1**, not 0  
- **DATEDIFF** returns a **number**, not a date  
- Use **CONVERT** for display formats; **CAST** for simple conversion  
- Trim with **LTRIM** / **RTRIM** before compare or store  

---

# Part 3 — Combined Practice

```sql
-- Join + date functions: orders in last 30 days
SELECT c.CustomerName, o.OrderDate,
       DATEDIFF(day, o.OrderDate, GETDATE()) AS DaysAgo
FROM Customer c
INNER JOIN Orders o ON c.CustomerID = o.CustomerID
WHERE DATEDIFF(day, o.OrderDate, GETDATE()) <= 30;

-- Subquery + string: students with long emails
SELECT FullName, Email
FROM Student
WHERE LEN(Email) > (
    SELECT AVG(LEN(Email)) FROM Student
);

-- Functions together: report formatting
SELECT
    StudentID,
    LTRIM(RTRIM(FullName)) AS CleanName,
    SUBSTRING(FullName, 1, CHARINDEX(' ', FullName + ' ') - 1) AS FirstName,
    YEAR(EnrollDate) AS EnrollYear,
    DATEDIFF(day, EnrollDate, GETDATE()) AS DaysEnrolled,
    CONVERT(VARCHAR(10), EnrollDate, 103) AS EnrollDateUK
FROM Student;
```

---

# ✅ Master Checklist

| Skill | Can you…? |
|-------|-----------|
| Joins | Write INNER and LEFT JOIN on two tables? |
| Subqueries | Filter with `IN (SELECT …)`? |
| CTE | Write a simple `WITH` block? |
| CAST/CONVERT | Change types and format a date? |
| Dates | Use `DATEADD` and `DATEDIFF` in a report? |
| Strings | Trim, substring, and find text with `CHARINDEX`? |

---

## 📝 Review Questions

### Advanced DML
1. What is the difference between **INNER JOIN** and **LEFT JOIN**?  
2. When would you use a **correlated subquery**?  
3. What does a **CROSS JOIN** produce?

### Built-in Functions
4. What is the difference between **CAST** and **CONVERT**?  
5. Write SQL for **90 days from today**.  
6. What does `SUBSTRING('Hello World', 7, 5)` return?  
7. When use **PATINDEX** instead of **CHARINDEX**?

---

## 🔗 Reference

- [Microsoft Docs – JOINs](https://learn.microsoft.com/en-us/sql/t-sql/queries/select-from-clauses-transact-sql)
- [Subqueries](https://learn.microsoft.com/en-us/sql/relational-databases/performance/subqueries)
- [CAST and CONVERT](https://learn.microsoft.com/en-us/sql/t-sql/functions/cast-and-convert-transact-sql)
- [Date and time functions](https://learn.microsoft.com/en-us/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)
- [String functions](https://learn.microsoft.com/en-us/sql/t-sql/functions/string-functions-transact-sql)

---

*Sources: `05_Advanced DML Statements .md`, `06_Built_in_Function.md` — FU-02 SQL Server*
