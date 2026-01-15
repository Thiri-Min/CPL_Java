# Assignment: ERD Design & Relational Schema Conversion
(Database Fundamentals & SQL)

---

## 📘 Assignment Overview

In this assignment, students will:
1. Design an **Entity–Relationship Diagram (ERD)** based on given system requirements.
2. Convert the ERD into a **Relational Schema** by identifying tables, primary keys, and foreign keys.

This assignment emphasizes **database design thinking before SQL implementation**.

---

## 🎯 Learning Objectives

By completing this assignment, students will be able to:

- Analyze system requirements to identify entities and attributes
- Design ERDs using correct relationships and cardinalities
- Resolve many-to-many relationships using junction tables
- Apply normalization rules (1NF → 3NF)
- Convert ERDs into relational schemas (tables)

---

## 🛠️ Tools (Choose One)

Students may use:
- Draw.io
- Lucidchart
- MySQL Workbench (EER Diagram)
- Any ERD design tool

---

## 📂 System Scenario

### System Name: **Course Registration System**

A training institute wants to manage information about:
- Students
- Courses
- Instructors
- Class schedules
- Student enrollment and grades

---

## 🧩 Functional Requirements

### Student
- Each student has a unique student ID
- Student information includes name, email, date of birth, and status
- A student can enroll in multiple courses

---

### Course
- Each course has a unique course ID
- Course includes course name, credit hours, and department
- A course can have many students

---

### Instructor
- Each instructor has a unique instructor ID
- Instructors can teach multiple courses
- Each course is taught by one instructor per semester

---

### Class Schedule
- A course can have multiple class sessions
- Each session includes date, time, and room

---

### Enrollment
- Represents student registration in courses
- Stores enrollment date and final grade

---

## 🔑 PART 1: ERD DESIGN REQUIREMENTS

Students must:

1. Identify all **entities**
2. Define **attributes** for each entity
3. Assign appropriate **primary keys**
4. Identify **relationships** between entities
5. Define **cardinality**:
   - One-to-One (1:1)
   - One-to-Many (1:N)
   - Many-to-Many (M:N)
6. Resolve **M:N relationships** using junction entities
7. Apply **normalization rules (up to 3NF)**

---

## 📐 ERD RULES & CONSTRAINTS

- Each entity must have a primary key
- No multi-valued or repeating attributes
- Avoid data redundancy
- Use clear and meaningful attribute names
- Show cardinality clearly using crow’s foot notation

---

## 🔄 PART 2: CONVERT ERD TO RELATIONAL SCHEMA (REQUIRED)

After completing the ERD, students must convert it into a **Relational Schema**.

### 1️⃣ Identify Tables
Each entity and junction entity must be converted into a table.

---

### 2️⃣ Define Primary Keys
- Each table must have exactly one primary key
- Primary keys must be clearly indicated

---

### 3️⃣ Define Foreign Keys
- Identify foreign keys based on relationships
- Clearly specify references between tables

--------------------------------------------------
Example format:


### 4️⃣ Relationship Mapping Rules

| ERD Relationship | Relational Mapping |
|------------------|--------------------|
| 1 : N | Add FK to N-side table |
| M : N | Create junction table |
| 1 : 1 | Add FK to one side (with justification) |

---

### 5️⃣ Normalization Explanation
Students must briefly explain:
- How 1NF, 2NF, and 3NF are satisfied
- Why no redundant data exists

---

## 📋 Required Deliverables

Students must submit:

1. **ERD Diagram** (PNG / JPG / PDF)
2. **Relational Schema Document** (Text or PDF)
   - List of tables
   - Attributes
   - Primary keys
   - Foreign keys
3. **Design Explanation**
   - Relationship decisions
   - Normalization justification
   - Assumptions made

---

## 📊 Evaluation Criteria

| Criteria | Weight |
|--------|--------|
| ERD Accuracy & Completeness | 25% |
| Relationship & Cardinality | 20% |
| Correct Relational Schema | 25% |
| Normalization (1NF–3NF) | 15% |
| Documentation & Clarity | 15% |

---

## ⭐ Bonus (Optional)

- Add constraints (UNIQUE, NOT NULL)
- Prepare schema ready for SQL implementation
- Use consistent naming conventions
- Provide ERD → SQL mapping notes

---

## ✅ Expected Outcome

After completing this assignment, students will be able to:

- Design ERDs for real-world systems
- Convert ERDs into relational schemas
- Prepare database designs ready for SQL coding
- Understand how logical design maps to physical tables

---

**Design first. SQL later. 🧠📐**
