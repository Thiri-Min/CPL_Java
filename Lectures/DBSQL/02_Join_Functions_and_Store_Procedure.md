# Joins & Aggregation, Functions & Stored Procedures Study Guide

---

## 📌 Joins & Aggregation

### 1. INNER / LEFT JOIN
- **Explanation**:  
  - **INNER JOIN** returns rows that have matching values in both tables.  
  - **LEFT JOIN** returns all rows from the left table, and matched rows from the right table. If no match exists, NULLs are returned for right table columns.
- **Example**:
  ```sql
  -- INNER JOIN
  SELECT e.EmployeeID, e.Name, d.DepartmentName
  FROM Employees e
  INNER JOIN Departments d ON e.DepartmentID = d.DepartmentID;

  -- LEFT JOIN
  SELECT e.EmployeeID, e.Name, d.DepartmentName
  FROM Employees e
  LEFT JOIN Departments d ON e.DepartmentID = d.DepartmentID;
  ```

### 2. GROUP BY / HAVING
- **Explanation**:

  - GROUP BY groups rows that have the same values into summary rows.

  -  HAVING filters groups after aggregation (similar to WHERE but for grouped data).

```
SELECT DepartmentID, COUNT(*) AS EmployeeCount
FROM Employees
GROUP BY DepartmentID
HAVING COUNT(*) > 5;
```

### 3. Aggregation Functions
- **Explanation**:
  - Aggregation functions perform calculations on a set of values and return a single value. Common ones include:

  - COUNT(), SUM(), AVG(), MIN(), MAX().

```
SELECT AVG(Salary) AS AvgSalary, MAX(Salary) AS HighestSalary
FROM Employees;
```

### 4 Common Table Expression (CTE)

- **Explanation**:
  - A CTE is a temporary result set defined within the execution scope of a single query. It improves readability and can be recursive.

```
  WITH HighEarners AS (
    SELECT EmployeeID, Name, Salary
    FROM Employees
    WHERE Salary > 5000
)
SELECT * FROM HighEarners;
```

### 5. Views
- **Explanation**:
  - A View is a virtual table based on the result of a query. It simplifies complex queries and enhances security by restricting access to specific columns.

```
CREATE VIEW EmployeeSummary AS
SELECT Name, DepartmentID, Salary
FROM Employees;

SELECT * FROM EmployeeSummary;
```

### 6. Join Pitfalls
-  **Explanation**:

    - Forgetting join conditions → Cartesian product (huge unintended result set).

    - Using INNER JOIN when you need unmatched rows → missing data.

    - Performance issues with too many joins.


```
-- Pitfall: Missing ON condition
SELECT * 
FROM Employees e, Departments d;  -- Cartesian product!
```

-----------------

## Functions & Stored Procedures
### 1. Function vs Procedure
- **Explanation**:

    - Function: Returns a single value or table, can be used in SELECT statements.

    - Procedure: Performs operations, may return multiple result sets, cannot be used directly in SELECT.

```
-- Function
CREATE FUNCTION GetTotalSalary(@DeptID INT)
RETURNS INT
AS
BEGIN
    RETURN (SELECT SUM(Salary) FROM Employees WHERE DepartmentID = @DeptID);
END;

-- Procedure
CREATE PROCEDURE GetEmployeesByDept @DeptID INT
AS
BEGIN
    SELECT * FROM Employees WHERE DepartmentID = @DeptID;
END;
```

## 2. Input / Output Parameters
- **Explanation**:

    - Input parameters pass values into functions/procedures.

    - Output parameters return values back to the caller.

```
CREATE PROCEDURE GetEmployeeCount 
    @DeptID INT, 
    @Count INT OUTPUT
AS
BEGIN
    SELECT @Count = COUNT(*) FROM Employees WHERE DepartmentID = @DeptID;
END;
```

## 3. Control Flow
- **Explanation**:
  - Stored procedures can use control flow statements (IF, WHILE, CASE) to handle logic.

```
CREATE PROCEDURE CheckSalary @EmpID INT
AS
BEGIN
    DECLARE @Salary INT;
    SELECT @Salary = Salary FROM Employees WHERE EmployeeID = @EmpID;

    IF @Salary > 5000
        PRINT 'High Salary';
    ELSE
        PRINT 'Normal Salary';
END;
```

