# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
How many patients are there in each city?

```
Select Address,count(*) as TotalPatients from Patients group by Address;
```

**Output:**
![image](https://github.com/user-attachments/assets/6eb6f966-c029-4a05-8033-52bec3d561a4)


**Question 2**
How many medical records were created in each month?

```
SELECT Date,count(*) as TotalRecords from MedicalRecords group by Date;
```

**Output:**
![image](https://github.com/user-attachments/assets/478b4480-1ee4-4547-adbb-55d4000a7e0f)


**Question 3**
How many appointments are scheduled for each patient?
Sample table: Appointments Table
name type AppointmentID INTEGER PatientID INTEGER DoctorID INTEGER AppointmentDateTime DATETIME Purpose TEXT Status TEXT
```
SELECT PatientID,COUNT(*) AS TotalAppointments from Appointments group by PatientID;
```

**Output:**

![image](https://github.com/user-attachments/assets/c244397b-6d16-486c-8449-99b6ff8e4cf3)


**Question 4**
Write a SQL query to find Who has the highest income among employee living in California?
Table: employee
name type
id INTEGER name TEXT age INTEGER city TEXT income INTEGER
```
select name,max(income) as 'max(income)' from employee where city='California';
```
**Output:**
![image](https://github.com/user-attachments/assets/1f3a9096-cd6b-4b5c-b20d-d62f9cba287b)


**Question 5**
Write a SQL query to find the number of employees whose age is greater than 32.

```
select count(*) as COUNT from employee where age>32;
```

**Output:**
![image](https://github.com/user-attachments/assets/04278a51-1e65-4b17-ac40-22a9d83e04cc)

**Question 6**
Write a SQL query to find the number of employees who are having the same age removing the duplicate values.

```
 select count(distinct age) as COUNT from employee;
```

**Output:**
![image](https://github.com/user-attachments/assets/9e1db240-66f4-4abe-baa9-ba30fbef1428)


**Question 7**
Write a SQL query to find the average length of email addresses (in characters):
Table: customer
name type id INTEGER name TEXT city TEXT email TEXT phone INTEGER

```
 select avg(length(email)) as avg_email_length from customer;
```

**Output:**
![image](https://github.com/user-attachments/assets/0f4e963e-a1e0-434e-bd1f-15886abb4855)


**Question 8**
Write the SQL query that accomplishes the selection of total number of products for each category from the "products" table, and includes only those products where the minimum category ID is less than 3

```
 select category_id,count(*) as 'count(product_name)' from products group by category_id having category_id<3;
```

**Output:**
![image](https://github.com/user-attachments/assets/ed38af65-3d46-498b-86b9-35d6a3843919)



**Question 9**
Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 1,000,000.

```
select age,income as Income from employee group by age having min(income)<1000000;
```

**Output:**
![image](https://github.com/user-attachments/assets/3781fcab-ec50-47f1-a5e5-f81bc7875524)


**Question 10**
Write the SQL query that accomplishes the selection of number of products for each category from products table which includes only those products where the category ID is greater than 2.

```
select category_id,count(*) as 'COUNT' from products group by category_id having category_id>2;
```

**Output:**

![image](https://github.com/user-attachments/assets/105d33d1-9f90-4a89-8adc-214aa6cce051)



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
