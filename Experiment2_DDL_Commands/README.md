# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.

```sql
CREATE TABLE ProjectAssignments
( AssignmentID  INTEGER PRIMARY KEY,
  EmployeeID INTEGER,
  ProjectID INTEGER,
  AssignmentDate DATE NOT NULL,
  FOREIGN KEY(EmployeeID) REFERENCES Employees(EmployeeID),
  FOREIGN KEY(ProjectID) REFERENCES Projects(ProjectID)
);
```

**Output:**
![image](https://github.com/user-attachments/assets/c39f4694-978b-48f2-b4a8-e8fe88f2527b)

**Question 2**
Write a SQL query to Add a new column named "discount" with the data type DECIMAL(5,2) to the "customer" table.

```sql
ALTER TABLE customer
ADD COLUMN discount DECIMAL(5,2);
```
**Output:**
![image](https://github.com/user-attachments/assets/b683b685-a081-488a-90f7-a475ce8eadbb)

**Question 3**
In the Products table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

```sql
INSERT INTO Products(ProductID ,Name ,Category ,Price,Stock)
VALUES
(106,'Fitness Tracker','Wearables',' ',' '),
(107,'Laptop','Electronic','999.99',50),
(108,'Wireless Earbud','Accessorie',' ',100);
```

**Output:**
![image](https://github.com/user-attachments/assets/b6c04f2c-ea2d-4047-a972-60ff55965ee2)

**Question 4**
Insert the below data into the Customers table, allowing the City and ZipCode columns to take their default values.
```
INSERT INTO Customers
(CustomerID,Name,Address)
VALUES
(304,'Peter Parker','Spider St');

```
**Output:**
![image](https://github.com/user-attachments/assets/fa106b98-95a3-4e0e-b231-e11adb8d448c)

**Question 5**
Create a new table named contacts with the following specifications:
contact_id as INTEGER and primary key.
first_name as TEXT and not NULL.
last_name as TEXT and not NULL.
email as TEXT.
phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.

```
CREATE TABLE contacts
( contact_id INTEGER PRIMARY KEY,
  first_name TEXT NOT NULL,
  last_name TEXT NOT NULL,
  email TEXT,
  phone TEXT NOT NULL CHECK(LENGTH(phone)>=10)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/46264b78-95ca-444b-88a8-4a0ef1996df2)


**Question 6**
Create a table named Department with the following constraints:
DepartmentID as INTEGER should be the primary key.
DepartmentName as TEXT should be unique and not NULL.
Location as TEXT.

```CREATE TABLE Department
( DepartmentID INTEGER PRIMARY KEY,
  DepartmentName TEXT NOT NULL UNIQUE,
  Location TEXT
);

```
**Output:**
![image](https://github.com/user-attachments/assets/ba7a0c8a-538f-46f3-914d-3362c5729cb1)

**Question 7**
Create a table named Events with the following columns:

EventID as INTEGER
EventName as TEXT
EventDate as DATE

```
CREATE TABLE Events
(
EventID INTEGER,
EventName TEXT,
EventDate DATE
);

```

**Output:**
![image](https://github.com/user-attachments/assets/939458c5-396e-4643-889b-8d790d960f5c)


**Question 8**
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should cascade updates and deletes.
item_desc and rate should not accept NULL.

```CREATE TABLE item
(
item_id TEXT PRIMARY KEY,
item_desc TEXT NOT NULL,
rate INTEGER NOT NULL,
icom_id TEXT CHECK(LENGTH(icom_id)=4),
FOREIGN KEY(icom_id)REFERENCES company(com_id)
ON UPDATE CASCADE
ON DELETE CASCADE

);
```
**Output:**

![image](https://github.com/user-attachments/assets/d38d8590-6b9a-4c79-8cb9-7f1cf6883001)

**Question 9**
Insert all employees from Former_employees into Employee

Table attributes are EmployeeID, Name, Department, Salary


```INSERT INTO Employee
(EmployeeID,Name,Department,Salary)
SELECT EmployeeID,Name,Department,Salary
FROM Former_employees;
```

**Output:**

![image](https://github.com/user-attachments/assets/e67f139e-b656-4b31-a5ae-20e6a8260d1b)

**Question 10**
Write a SQL Query  to change the name of attribute "name" to "first_name"  and add mobilenumber as number ,DOB as Date in the table Companies

```
ALTER TABLE Companies
RENAME COLUMN name TO first_name;
ALTER TABLE Companies 
ADD COLUMN mobilenumber number;
ALTER TABLE Companies 
ADD COLUMN DOB Date;
```

**Output:**
![image](https://github.com/user-attachments/assets/d2fdc449-4a66-46a7-ab1f-d215bbdbfc60)



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
