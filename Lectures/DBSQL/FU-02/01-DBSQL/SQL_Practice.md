# Student Management System - SQL Practice

This file provides SQL practice tasks for trainees. It covers:
- Database creation
- Schema with 5 tables
- CRUD operations (Create, Read, Update, Delete)
- Join queries (INNER, LEFT, RIGHT, FULL OUTER)
- Insert, Update, Delete examples
- Comments and instructions for each query

---

## 1. Create Database
```sql
-- Step 1: Create the database
CREATE DATABASE StudentManagement;

-- Step 2: Switch to the database
USE StudentManagement;

-- Table 1: Students
-- Stores basic student information
CREATE TABLE Students (
    StudentID INT PRIMARY KEY AUTO_INCREMENT,
    FirstName VARCHAR(50),
    LastName VARCHAR(50),
    DOB DATE,
    Email VARCHAR(100)
);

-- Table 2: Courses
-- Stores course details
CREATE TABLE Courses (
    CourseID INT PRIMARY KEY AUTO_INCREMENT,
    CourseName VARCHAR(100),
    Credits INT
);

-- Table 3: Instructors
-- Stores instructor details
CREATE TABLE Instructors (
    InstructorID INT PRIMARY KEY AUTO_INCREMENT,
    FirstName VARCHAR(50),
    LastName VARCHAR(50),
    Department VARCHAR(100)
);

-- Table 4: Enrollments
-- Links students to courses
CREATE TABLE Enrollments (
    EnrollmentID INT PRIMARY KEY AUTO_INCREMENT,
    StudentID INT,
    CourseID INT,
    Grade VARCHAR(2),
    FOREIGN KEY (StudentID) REFERENCES Students(StudentID),
    FOREIGN KEY (CourseID) REFERENCES Courses(CourseID)
);

-- Table 5: CourseAssignments
-- Links instructors to courses
CREATE TABLE CourseAssignments (
    AssignmentID INT PRIMARY KEY AUTO_INCREMENT,
    InstructorID INT,
    CourseID INT,
    FOREIGN KEY (InstructorID) REFERENCES Instructors(InstructorID),
    FOREIGN KEY (CourseID) REFERENCES Courses(CourseID)
);

-- Insert sample students
INSERT INTO Students (FirstName, LastName, DOB, Email)
VALUES ('Alice', 'Nguyen', '2000-05-12', 'alice@example.com'),
       ('Bob', 'Tran', '1999-08-21', 'bob@example.com'),
       ('Charlie', 'Pham', '2001-01-15', 'charlie@example.com'),
       ('David', 'Le', '2000-11-30', 'david@example.com'),
       ('Eva', 'Hoang', '1998-07-07', 'eva@example.com');

-- Insert sample courses
INSERT INTO Courses (CourseName, Credits)
VALUES ('Database Systems', 3),
       ('Operating Systems', 4),
       ('Computer Networks', 3),
       ('Software Engineering', 4),
       ('Artificial Intelligence', 3);

-- Insert sample instructors
INSERT INTO Instructors (FirstName, LastName, Department)
VALUES ('John', 'Smith', 'Computer Science'),
       ('Maria', 'Lopez', 'Information Technology'),
       ('Ken', 'Tanaka', 'Software Engineering');

-- Insert enrollments
INSERT INTO Enrollments (StudentID, CourseID, Grade)
VALUES (1, 1, 'A'),
       (2, 2, 'B'),
       (3, 3, 'A'),
       (4, 4, 'C'),
       (5, 5, 'B');

-- Insert course assignments
INSERT INTO CourseAssignments (InstructorID, CourseID)
VALUES (1, 1),
       (2, 2),
       (3, 3),
       (1, 4),
       (2, 5);


-- INNER JOIN: Get students with their enrolled courses
SELECT s.FirstName, s.LastName, c.CourseName, e.Grade
FROM Students s
INNER JOIN Enrollments e ON s.StudentID = e.StudentID
INNER JOIN Courses c ON e.CourseID = c.CourseID;

-- LEFT JOIN: Get all students and their enrollments (including those not enrolled)
SELECT s.FirstName, s.LastName, c.CourseName
FROM Students s
LEFT JOIN Enrollments e ON s.StudentID = e.StudentID
LEFT JOIN Courses c ON e.CourseID = c.CourseID;

-- RIGHT JOIN: Get all courses and the students enrolled (including courses with no students)
SELECT s.FirstName, s.LastName, c.CourseName
FROM Students s
RIGHT JOIN Enrollments e ON s.StudentID = e.StudentID
RIGHT JOIN Courses c ON e.CourseID = c.CourseID;

-- FULL OUTER JOIN (Note: Some SQL dialects use UNION of LEFT + RIGHT)
SELECT s.FirstName, s.LastName, c.CourseName
FROM Students s
LEFT JOIN Enrollments e ON s.StudentID = e.StudentID
LEFT JOIN Courses c ON e.CourseID = c.CourseID
UNION
SELECT s.FirstName, s.LastName, c.CourseName
FROM Students s
RIGHT JOIN Enrollments e ON s.StudentID = e.StudentID
RIGHT JOIN Courses c ON e.CourseID = c.CourseID;


-- Update student email
UPDATE Students
SET Email = 'alice.new@example.com'
WHERE StudentID = 1;

-- Update course credits
UPDATE Courses
SET Credits = 5
WHERE CourseID = 2;


-- Delete a student record
DELETE FROM Students
WHERE StudentID = 5;

-- Delete a course assignment
DELETE FROM CourseAssignments
WHERE AssignmentID = 3;



---

This file is structured for **hands-on training**: schema design, CRUD operations, and join practice.  
Hope this file helpful for you!!!