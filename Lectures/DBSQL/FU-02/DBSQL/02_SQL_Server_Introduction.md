# 📘 Summary: SQL Server Introduction

## 🎯 Lesson Objectives
- Understand [SQL Server](ca://s?q=What_is_SQL_Server) and supported data types  
- Create and modify databases, tables, and constraints  
- Distinguish between types of [constraints](ca://s?q=SQL_Server_constraints)  

---

## 🗂 Section 1: Introduction to SQL Server
- **Definition**: SQL Server is a [relational database management system](ca://s?q=SQL_Server_RDBMS) (RDBMS) developed by Microsoft.  
- **Language**: Supports ANSI SQL; extended with [T-SQL](ca://s?q=Transact_SQL) (Microsoft proprietary).  
- **Version History**: First released in 1989 (with Sybase). Major versions: 2000, 2005, 2008, 2012, 2014, 2016, 2017, 2019.  
- **Editions**:  
  - Enterprise – mission-critical, advanced analytics, ML  
  - Standard – mid-tier apps, data marts  
  - Web – affordable for web hosting  
  - Developer – full features, non-production  
  - Express – free, small-scale apps  
- **Instances**: Multiple instances allow version separation, cost reduction, environment isolation, and security management.  

---

## 🗄 Section 2: SQL Server Database
### Database Operations
- **Create Database**:  
  - Using SQL Server Management Studio (GUI)  
  - Using T-SQL:  
    ```sql
    CREATE DATABASE Edu_TSQL;
    ```
- **Alter Database**:  
  ```sql
  ALTER DATABASE Edu_TSQL MODIFY NAME = Edu_TSQL_Alter;

- Delete Database:
```
DROP DATABASE Edu_TSQL_Alter;
```