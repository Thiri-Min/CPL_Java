For the following assignments:

• Print out respectively the screenshots to show the query results.

• Pack screenshots and SQL scripts or your answers into the zip file named SQL_Assignment<i>_AccountName.zip (for instance: SQL_Assignment2_NamNT.zip) then handle to the evaluator via email (XYZ@fsoft.com.vn ) or follow the guidance of the class admin.

SQL Basic

Assignment 2_Opt1: Fresher Training Management

Barem: a: 40% (4), b: 10%(1), c: 15%(1.5), d: 15%(1.5), e: 20%(2)

Objective: H5SD - SQL skills

Problem Description:

In the design for the Fresher Training Management, given the Trainee table with below initial attributes fields:

· TraineeID: trainee identifier, auto increment field

· Full_Name: full name of the trainee

· Birth_Date: trainee birth date

· Gender: only have one of two value male, female

· ET_IQ: entry test point (IQ) of trainee, integer, value range from 0 to 20

· ET_Gmath: entry test point (GMath) of trainee, integer, value range from 0 to 20

· ET_English: entry test point (English) of trainee, integer, value range from 0 to 50

· Training_Class: the class code that the trainee is joining

· Evaluation_Notes: trainee evaluation notes, free text.

Questions to answer:

a) Create the tables (with the most appropriate/economic field/column constraints & types) and add at least 10 records to each created table.

b) Change the table TRAINEE to add one more field named Fsoft_Account which is a not-null & unique field.

c) Create a VIEW that includes all the ET-passed trainees. One trainee is considered as ET-passed when he/she has the entry test points satisfied the below criteria:

• ET_IQ + ET_Gmath >=20

• ET_IQ>=8

• ET_Gmath>=8

• ET_English>=18

d) Query all the trainees who is passed the entry test, group them into different birth months.

e) Query the trainee who has the longest name, showing his/her age along with his/her basic information (as defined in the table).

Estimated Time to complete:180 mins.