# Experiment 1: Entity-Relationship (ER) Diagram

## 🎯 Objective:
To understand and apply the concepts of ER modeling by creating an ER diagram for a real-world application.

## 📚 Purpose:
The purpose of this workshop is to gain hands-on experience in designing ER diagrams that visually represent the structure of a database including entities, relationships, attributes, and constraints.

### 🔹 Scenario 1: University Database
Design a database to manage students, instructors, programs, courses, and student enrollments. Include prerequisites for courses.

**User Requirements:**
- Academic programs grouped under departments.
- Students have admission number, name, DOB, contact info.
- Instructors with staff number, contact info, etc.
- Courses have number, name, credits.
- Track course enrollments by students and enrollment date.
- Add support for prerequisites (some courses require others).

## 📝 Tasks:
1. Identify entities, relationships, and attributes.<br>
2. Draw the ER diagram using any tool (draw.io, dbdiagram.io, hand-drawn and scanned)..<br>
3. Include:
   - Cardinality & participation constraints<br<
   - Prerequisites for University OR Billing for Hospita<br>
4. Explain:
   - Why you chose the entities and relationships.<br>
   - How you modeled prerequisites or billing.<br>

# ER Diagram Submission -Thiyaga Sri Charumathy

## Scenario Chosen:
University 

## ER Diagram:
![image](https://github.com/user-attachments/assets/315de6a4-e170-43ae-9f2e-db6484a2e134)

## Entities and Attributes:
### STUDENT
1.AdmissionNumber (Primary Key)<br>
2.Name<br>
3.DateOfBirth<br>
4.ContactInfo<br>
### INSTRUCTOR
1.StaffNumber (Primary Key)<br>
2.Name<br>
3.ContactInfo<br>
4.Department<br>
5.Specialization<br>
### PROGRAM
1.ProgramID (Primary Key)<br>
2.Name<br>
3.Department<br>
### COURSE
1.CourseNumber (Primary Key)<br>
2.Name<br>
3.Credits<br>
### DEPARTMENT
1.DepartmentID (Primary Key)<br>
2.Name<br>

## Relationships and Constraints:
### STUDENT ENROLLS IN COURSE
1.Attributes: EnrollmentDate<br>
2.Cardinality: Many-to-Many (N:M)<br>
3.Participation: Total participation from STUDENT side (each student must enroll in at least one course)<br>
### INSTRUCTOR BELONGS TO PROGRAM
4.Cardinality: Many-to-One<br>
5.Participation: Partial<br>
### STUDENT BELONGS TO PROGRAM
6.Cardinality: Many-to-One<pr>
### COURSE HAS PREREQUISITE (PREREQ)<br>
7.Recursive relationship<br>
8.A course may require one or more other courses as prerequisites<br>
9.Cardinality: Many-to-Many<br>

## Extension (Prerequisite / Billing):
To model Prerequisites, I used a recursive relationship on the COURSE entity.<br>
 1.Each course can be linked to multiple other courses as prerequisites.<br>
 2.This is modeled as a binary relationship from COURSE to itself named PREREQ.<br>
 3.This allows for complex chains of prerequisite courses, such as Course C requiring Course A and B.<br>

## Design Choices:
Chose STUDENT, INSTRUCTOR, PROGRAM, COURSE, and DEPARTMENT as core entities to fully reflect university operations.
Introduced recursive relationship for prerequisites to make the design scalable and accurate.
Considered many-to-many relationships for course enrollments and prerequisites, reflecting real-world academic scenarios.
Added participation constraints (total/partial) to show required involvement in relationships (e.g., every course must belong to a program, but an instructor may or may not belong to a program).

## RESULT:
 Successfully designed and explained an ER diagram for the University Database scenario. The model captures all user requirements including students, instructors, departments, programs, courses, enrollments, and prerequisites.
