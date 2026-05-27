# 📘 Advanced DML Statements – Summary

## 🎯 Lesson Objectives
- [SQL Joins] in SQL Server  
- [Subqueries]in SQL Server  
- [CTE and Ranking Functions]
- Apply Joins, Subqueries, and CTEs to real projects  

---

## 🔗 SQL Joins
SQL Joins combine rows from two or more tables based on logical relationships.

### Types of Joins
- [Inner Join] → Returns rows with matching values in both tables.  
- [Outer Join] → Includes unmatched rows.  
  - Left Outer Join  
  - Right Outer Join  
  - Full Outer Join  
- [Cross Join] → Cartesian product of rows.  
- [Self Join] → Table joined with itself.  

### Excluding Joins
- Left Excluding Join → Rows in left table not matching right.  
- Right Excluding Join → Rows in right table not matching left.  
- Full Outer Excluding Join → Non-matching rows from both tables.  

### Multi-Table Joins
- Joins can be extended to 3+ tables using multiple join conditions.

---

## 🔍 Subqueries
A **subquery** is a query nested inside another query (SELECT, INSERT, UPDATE, DELETE).

### Types
- [Single Row Subquery] → Returns one row.  
- [Multiple Row Subquery] → Returns multiple rows (IN, ANY, ALL).  
- [Multiple Column Subquery] → Returns multiple columns.  
- [Correlated Subquery]→ References outer query columns.  
- [Nested Subquery] → Subquery inside another subquery.

### Execution Flow
- Inner query executes first, stores results.  
- Outer query runs on stored results.  

---

## 📊 Key Examples
- **Inner Join**: Match customers with orders.  
- **Left Join**: Show all customers, even without orders.  
- **Right Join**: Show all orders, even without customers.  
- **Full Join**: Combine all customers and orders, including unmatched.  
- **Self Join**: Employees matched with their managers.  
- **Subquery Example**: Filter sales by region using nested queries.  

---

## ✅ Takeaway
This document provides practical SQL techniques:
- Use joins to combine data across tables.  
- Apply subqueries for complex filtering.  
- Leverage CTEs and ranking functions for advanced analytics.  
