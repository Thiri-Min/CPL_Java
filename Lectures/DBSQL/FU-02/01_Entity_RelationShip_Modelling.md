# 📘 Summary: Entity-Relationship Modelling

## 🎯 Lesson Objectives
- [Fundamental concepts](ca://s?q=Explain_fundamental_concepts_of_databases) of databases  
- [Database architecture](ca://s?q=Database_architecture_and_components) and components  
- [Entities, attributes, relationships](ca://s?q=Entities_attributes_relationships_in_ERD) in data modeling  
- [Converting ER model](ca://s?q=Convert_ER_model_to_relational_schema) to relational schema  

---

## 🗂 Introduction to Databases
- **Database**: Organized collection of data (e.g., student management, retail inventory).  
- **DBMS**: Software to manage databases (MySQL, PostgreSQL, SQL Server, Oracle, MongoDB).  
- **Types of Databases**:  
  - [Relational](ca://s?q=Relational_databases) (SQL, structured tables)  
  - [NoSQL](ca://s?q=NoSQL_databases) (JSON, key-value, documents)  

---

## 📊 Data Types
- **Structured**: Predefined format (tables).  
- **Unstructured**: No fixed format (images, videos, reviews).  
- **Semi-structured**: Tagged/metadata (JSON, XML).  

---

## 🔑 Key Concepts
- **Table**: Structured collection of data.  
- **Row (Record)**: Single entry.  
- **Column (Field)**: Attribute of data.  
- **Primary Key (PK)**: Unique identifier.  
- **Foreign Key (FK)**: Reference to PK in another table.  

---

## 🖼 Entity-Relationship Diagram (ERD)
- **Definition**: Visual representation of entities, attributes, and relationships.  
- **Components**:  
  - Entities (Customer, Order, Product)  
  - Attributes (Customer Name, Order Date)  
  - Relationships (Customer places Order)  
  - PKs & FKs  

### Notations
- **Chen Notation**: Rectangles (entities), ovals (attributes), diamonds (relationships).  
- **Crow’s Foot Notation**: Rectangles with attributes, detailed cardinality (1:1, 1:N, M:N).  

---

## 🧩 ERD Design Process
1. Identify purpose & requirements.  
2. Define entities, attributes, relationships.  
3. Draw ERD.  
4. Convert ERD → relational schema.  
5. Apply [normalization](ca://s?q=Database_normalization) (1NF, 2NF, 3NF, BCNF).  
6. Implement with chosen DBMS.  

---

## 🔐 Keys
- **Primary Key**: Unique record identifier.  
- **Foreign Key**: Links entities across tables.  

---

## 🔗 Relationships & Cardinality
- **One-to-One**: Employee ↔ Department.  
- **One-to-Many**: Department → Employees.  
- **Many-to-Many**: Employee ↔ Project.  

---

## 🏗 Data Models
| Feature        | Conceptual | Logical | Physical |
|----------------|------------|---------|----------|
| Entities       | ✔️         | ✔️      | ✔️       |
| Relationships  | ✔️         | ✔️      | ✔️       |
| Columns        | ❌         | ✔️      | ✔️       |
| Column Types   | ❌         | Optional| ✔️       |
| Primary Key    | ❌         | ❌      | ✔️       |
| Foreign Key    | ❌         | ❌      | ✔️       |

- **Conceptual**: High-level business objects (Customer, Product, Supplier).  
- **Logical**: Adds attributes, operational entities (Order).  
- **Physical**: Blueprint with column types, PKs, FKs, constraints.  

---

## 🛠 How to Draw ERD
- Define scope & purpose.  
- Identify entities & attributes.  
- Establish relationships with cardinality.  
- Normalize to reduce redundancy.  
- Use tools like **Draw.io**.  

---

## 🎓 Practice Example
**University Student Management System**  
- Entities: Student, Lecturer, Course, Class, Department, Classroom, Schedule, Grade.  
- Relationships:  
  - Student enrolls in Courses.  
  - Lecturer teaches Courses.  
  - Classes belong to Programs.  
  - Courses conducted in Semesters.  
  - Grades track performance.  

---

# ✅ Key Takeaways
- ERDs are essential for [database design](ca://s?q=Database_design_process).  
- Keys (PK, FK) ensure integrity.  
- Cardinality defines relationship strength.  
- Conceptual → Logical → Physical models refine design.  
- Normalization improves efficiency and reduces redundancy.  
