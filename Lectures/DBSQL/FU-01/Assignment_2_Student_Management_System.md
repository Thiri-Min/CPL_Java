# Assignment: Student Management System (SMS)
(Database Fundamentals & SQL)

---

## 📘 Assignment Overview

In this assignment, students will design and implement a **Student Management System database** using **MySQL or MS SQL Server**.  
The goal is to apply **database fundamentals, SQL queries, relationships, and data integrity rules** in a real-world scenario.

---

## 🎯 Learning Objectives

By completing this assignment, students will be able to:

- Design a relational database schema
- Apply primary keys and foreign keys
- Implement one-to-many and many-to-many relationships
- Write SQL queries using joins, subqueries, and aggregation
- Generate meaningful reports from data

---

## 🛠️ Technology Requirements

Students may use **one** of the following:

- MySQL + MySQL Workbench  
- MS SQL Server + SQL Server Management Studio (SSMS)

---

## 📂 System Description

The **Student Management System** manages information about:

- Students
- Courses
- Teachers
- Enrollments
- Student performance

---

## 🧩 Database Requirements

### 1. Student Table
Must include:
- student_id (Primary Key)
- student_name
- email
- date_of_birth
- gender
- status (Active / Inactive)

---

### 2. Course Table
Must include:
- course_id (Primary Key)
- course_name
- credit_hours
- department

---

### 3. Teacher Table
Must include:
- teacher_id (Primary Key)
- teacher_name
- email
- department

---

### 4. Enrollment Table (Junction Table)
Must include:
- enrollment_id (Primary Key)
- student_id (Foreign Key)
- course_id (Foreign Key)
- enrollment_date
- grade

👉 This table represents a **many-to-many relationship** between Students and Courses.

---

## 🔑 Relationship Rules

- One student can enroll in many courses
- One course can have many students
- Each enrollment must reference a valid student and course
- Foreign key constraints must be enforced

---

## 📌 SQL Tasks (Required)

### 1️⃣ Database Creation
- Create a database named `StudentManagementDB`
- Create all required tables with proper constraints

---

### 2️⃣ Data Insertion
- Insert at least:
  - 10 students
  - 5 courses
  - 3 teachers
  - 15 enrollment records

---

### 3️⃣ Basic Queries
Write SQL queries to:

- Display all students
- Display all courses
- Find students with status = 'Active'

---

### 4️⃣ JOIN Queries
Write queries to:

- List students with their enrolled courses
- List courses with total number of enrolled students
- Show student name, course name, and grade

---

### 5️⃣ Aggregation Queries
Write queries using:

- COUNT
- AVG
- GROUP BY
- HAVING

Examples:
- Total students per course
- Average grade per course
- Courses with more than 3 students

---

### 6️⃣ Subqueries / CTE
Write at least **one** query using:
- Subquery **or**
- Common Table Expression (CTE)

Example:
- Students whose average grade is above the overall average

---

### 7️⃣ Views (Optional Bonus)
Create a view:
- `vw_student_courses`
- Shows student name, course name, and grade

---

## 🧪 Testing Requirements

- All queries must run without errors
- Foreign key constraints must prevent invalid inserts
- Data should be realistic and consistent

---

## 📦 Submission Requirements

Students must submit:

1. SQL script file:
   - `student_management.sql`
2. ER Diagram (image or PDF)
3. Screenshots of:
   - Table creation
   - Sample query results

---

## 📊 Evaluation Criteria

| Criteria | Weight |
|--------|--------|
| Database Design & Relationships | 30% |
| SQL Queries Correctness | 30% |
| Use of Joins & Aggregation | 20% |
| Data Integrity & Constraints | 10% |
| Documentation & Clarity | 10% |

---

## ⭐ Bonus (Optional)
- Index usage
- Stored procedures
- Clean naming conventions
- Well-formatted SQL

---

## ✅ Expected Outcome

After completing this assignment, students should be confident in:
- Designing relational databases
- Writing real-world SQL queries
- Understanding how backend systems store and retrieve data

---

**Good luck! 🚀**
