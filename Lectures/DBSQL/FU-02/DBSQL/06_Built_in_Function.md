# 📘 Summary: Built-in Functions (SQL Server)

## 🎯 Lesson Objectives
- Use **conversion functions** (`CAST`, `CONVERT`) to change data types  
- Apply **date and time functions** for reporting and calculations  
- Use **string functions** to clean, extract, and search text  
- Combine built-in functions in `SELECT` queries for data transformation and analysis  

---

## 🗂 Section 1: Conversion Functions

Convert values from one data type to another.

| Function | Description |
|----------|-------------|
| **CAST** | ANSI standard; converts expression to a data type |
| **CONVERT** | SQL Server extension; same as CAST plus **style codes** for dates |

### Examples

```sql
-- CAST
SELECT CAST('2026-05-19' AS DATE);
SELECT CAST(99.7 AS INT);              -- 99 (truncates)

-- CONVERT with date style (style 103 = dd/mm/yyyy)
SELECT CONVERT(VARCHAR(10), GETDATE(), 103);

-- String to number
SELECT CAST('150' AS INT) * 2;
```

**When to use:**
- **CAST** — portable, simple type changes  
- **CONVERT** — when you need a specific **date/time display format** (style parameter)

---

## 🗂 Section 2: Date and Time Functions

### 2.1 Overview

| Function | Description |
|----------|-------------|
| **GETDATE()** | Returns current **date and time** on the server |
| **DATEPART()** | Extracts a part of a date (year, month, day, hour, etc.) |
| **DAY()** | Returns day as integer (1–31) |
| **MONTH()** | Returns month as integer (1–12) |
| **YEAR()** | Returns year as integer |
| **DATEADD()** | Adds or subtracts an interval from a date |
| **DATEDIFF()** | Returns difference between two dates |

### 2.2 GETDATE()

```sql
SELECT GETDATE() AS CurrentDateTime;
-- Example output: 2026-05-19 14:30:00.123
```

### 2.3 DATEPART, DAY, MONTH, YEAR

```sql
DECLARE @d DATE = '2026-05-19';

SELECT DATEPART(year, @d)   AS PartYear;    -- 2026
SELECT DATEPART(month, @d) AS PartMonth;   -- 5
SELECT DATEPART(day, @d)   AS PartDay;     -- 19

SELECT YEAR(@d)  AS Y;   -- 2026
SELECT MONTH(@d) AS M;   -- 5
SELECT DAY(@d)   AS D;   -- 19
```

**DATEPART** can also extract hour, minute, second, weekday, etc.:

```sql
SELECT DATEPART(hour, GETDATE()) AS CurrentHour;
```

### 2.4 DATEADD

Adds (or subtracts with a negative number) an interval to a date.

```sql
-- 30 days from today
SELECT DATEADD(day, 30, GETDATE()) AS DueIn30Days;

-- 6 months ago
SELECT DATEADD(month, -6, GETDATE()) AS SixMonthsAgo;

-- 2 years from a hire date
SELECT DATEADD(year, 2, HireDate) AS ReviewDate
FROM Employee;
```

**Common date parts:** `year`, `quarter`, `month`, `week`, `day`, `hour`, `minute`, `second`

### 2.5 DATEDIFF

Returns the **count** of date part boundaries between two dates.

```sql
SELECT DATEDIFF(month, '2024-01-15', '2026-05-19') AS MonthsBetween;

SELECT DATEDIFF(day, OrderDate, GETDATE()) AS DaysSinceOrder
FROM Orders;
```

```sql
-- Example: age in years
SELECT DATEDIFF(year, BirthDate, GETDATE()) AS Age
FROM Student;
```

> **Note:** `DATEDIFF` counts boundaries (e.g. month diff from Jan 31 to Feb 1 may be 1), not always exact calendar duration.

---

## 🗂 Section 3: String Functions

### 3.1 Overview

| Function | Description |
|----------|-------------|
| **LTRIM()** | Removes leading spaces |
| **RTRIM()** | Removes trailing spaces |
| **SUBSTRING()** | Extracts part of a string |
| **LEN()** | Returns length of a string (trailing spaces ignored for non-Unicode) |
| **CHARINDEX()** | Finds starting position of substring (**no** wildcards) |
| **PATINDEX()** | Finds starting position of pattern (**supports** wildcards `%`, `_`) |

### 3.2 LTRIM and RTRIM

```sql
SELECT LTRIM('   Hello')     AS LeftTrim;   -- 'Hello'
SELECT RTRIM('Hello   ')     AS RightTrim;  -- 'Hello'
SELECT LTRIM(RTRIM('  Hi ')) AS BothTrim;   -- 'Hi'
```

### 3.3 SUBSTRING

Syntax: `SUBSTRING(string, start, length)` — **start is 1-based** in SQL Server.

```sql
SELECT SUBSTRING('Bill Gates', 1, 4) AS FirstName;
-- Result: Bill

SELECT SUBSTRING(Email, 1, CHARINDEX('@', Email) - 1) AS Username
FROM Student;
```

### 3.4 LEN

```sql
SELECT LEN('SQL Server') AS StringLength;   -- 10
SELECT LEN('  test  ')   AS LenWithSpaces; -- 7 (trailing spaces not counted)
```

### 3.5 CHARINDEX

Finds position of a substring; returns **0** if not found. **No wildcards.**

```sql
SELECT CHARINDEX('Gates', 'Bill Gates') AS Position;
-- Result: 6

SELECT CHARINDEX('@', 'student@school.com') AS AtSignPos;
-- Result: 8
```

### 3.6 PATINDEX

Like CHARINDEX but supports **pattern** wildcards (`%` = any length, `_` = one character).

```sql
SELECT PATINDEX('%Gates%', 'Bill Gates') AS PatternPos;
-- Result: 6

SELECT PATINDEX('%[0-9]%', 'Room 101') AS HasDigit;
-- Result: position of first digit
```

| | CHARINDEX | PATINDEX |
|---|-----------|----------|
| Wildcards | No | Yes (`%`, `_`) |
| Typical use | Exact substring | Pattern / format search |

---

## 🗂 Section 4: Combined Examples

```sql
-- Student report: name parts, enrollment info
SELECT
    StudentID,
    FullName,
    LTRIM(RTRIM(FullName)) AS CleanName,
    SUBSTRING(FullName, 1, CHARINDEX(' ', FullName + ' ') - 1) AS FirstName,
    YEAR(EnrollDate) AS EnrollYear,
    DATEDIFF(day, EnrollDate, GETDATE()) AS DaysEnrolled,
    LEN(Email) AS EmailLength
FROM Student;
```

```sql
-- Orders due within 30 days
SELECT OrderID, OrderDate,
       DATEADD(day, 30, OrderDate) AS FollowUpDate
FROM Orders
WHERE DATEDIFF(day, OrderDate, GETDATE()) <= 30;
```

```sql
-- Convert score to display grade
SELECT
    StudentID,
    CAST(Score AS DECIMAL(5,2)) AS Score,
    CONVERT(VARCHAR(10), ExamDate, 103) AS ExamDateUK
FROM ExamResult;
```

---

## ✅ Key Takeaways

| Category | Functions |
|----------|-----------|
| **Conversion** | `CAST`, `CONVERT` |
| **Date/Time** | `GETDATE`, `DATEPART`, `DAY`, `MONTH`, `YEAR`, `DATEADD`, `DATEDIFF` |
| **String** | `LTRIM`, `RTRIM`, `SUBSTRING`, `LEN`, `CHARINDEX`, `PATINDEX` |

These functions are essential for **data transformation**, **formatting**, and **analysis** in SQL Server.

**Remember:**
- Use **CONVERT** when you need formatted date strings (style codes).  
- **SUBSTRING** start position is **1**, not 0.  
- **DATEDIFF** returns an integer count of intervals, not a date.  
- Trim strings before compare or store with **LTRIM** / **RTRIM**.

---

## 📝 Quick Review Questions

1. What is the difference between `CAST` and `CONVERT`?  
2. Write a query that shows the date **90 days from today**.  
3. How do you get only the **year** from a `BirthDate` column?  
4. What does `SUBSTRING('Hello World', 7, 5)` return?  
5. When would you use `PATINDEX` instead of `CHARINDEX`?  

---

## 🔗 Practice & Reference

- [Microsoft Docs – CAST and CONVERT](https://learn.microsoft.com/en-us/sql/t-sql/functions/cast-and-convert-transact-sql)  
- [Date and Time Data Types and Functions](https://learn.microsoft.com/en-us/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)  
- [String Functions](https://learn.microsoft.com/en-us/sql/t-sql/functions/string-functions-transact-sql)  
