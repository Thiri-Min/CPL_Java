QL Homework: Joins, Functions, Procedures & Case Studies

🎯 Objective

Strengthen your understanding of SQL by practicing joins with aggregation, writing functions, creating stored procedures, and solving case studies.

### 1. JOIN + Aggregation Query

Question: Write a query to display each course name along with:

- The total number of students enrolled.

- The average grade of students in that course.

- Only include courses with more than 5 students.

Hint: Use JOIN, GROUP BY, and HAVING.

### 2. Function (Report / Compute)

Question: Create a SQL function named CalculateGPA that:

- Accepts a student ID as input.

- Computes the average grade (GPA) of that student.

- Returns the GPA rounded to 2 decimal places.

### Task: Test the function by calculating GPA for student ID = 101.

### 3. Stored Procedure (Transactional Flow)

Question: Write a stored procedure named TransferCredits that:

- Transfers a specified number of credits from one student to another.

- Uses a transaction to ensure atomicity.

- Rolls back if the source student does not have enough credits.

## Task: Execute the procedure to transfer 3 credits from student 101 to student 102. Then test rollback by attempting to transfer more credits than available.

### 4. Case Studies

Case Study 1: Reporting

A university wants a report of all courses with more than 10 students enrolled. The report should include:

- Course name

- Total students

- Average grade

## Question: Write a query using JOIN and GROUP BY to generate this report.

Case Study 2: GPA Ranking

- The academic office wants to rank students by GPA.

## Question: Use the CalculateGPA function to:

Compute GPA for all students.

Display the top 5 students with the highest GPA.

Case Study 3: Transactional Flow

The registrar needs to handle credit transfers safely.

Question: Implement and test the TransferCredits stored procedure:

Perform a successful transfer.

Test rollback when credits are insufficient.

✅ Deliverables

SQL scripts for queries, functions, and procedures.

Written explanation of each case study.

Screenshots of query results (optional).

📌 Notes

Ensure queries run on MySQL or MS SQL Server.

Test with sample data before submission.

Focus on correctness and clarity.