# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
Write a SQL statement to Increase the selling price by 10% for all products in the 'Bakery' category in the products table.


```
UPDATE Products
SET sell_price=sell_price*1.10 
Where category='Bakery';
```

**Output:**
![image](https://github.com/user-attachments/assets/798512d0-3331-4a0d-9d15-17973f92b1b9)


**Question 2**
Write a SQL query to reduce the reorder level by 30% where cost price is more than 50 and quantity in stock is less than 100 in the products table.

```UPDATE Products
SET reorder_lvl=reorder_lvl *0.7
where cost_price >50 AND  quantity<100;
```

**Output:**
![image](https://github.com/user-attachments/assets/7822f586-579e-4cd6-9dc9-5afd9ad8796a)



**Question 3**
For  Increase the selling price per unit by 3 for all products supplied by supplier ID 4 in the sales table.

```
UPDATE SALES
SET sell_price=sell_price+3
where product_id IN
(SELECT product_id FROM products
Where supplier_id=4
);
```

**Output:**
![image](https://github.com/user-attachments/assets/11a21882-520e-4c7c-bf70-5f1258790b6e)

**Question 4**
Update the reorder level to 40 pieces for all products belonging to the 'Grocery' category in the products table.

```
UPDATE PRODUCTS
SET reorder_lvl=40
where category='Grocery';
```
**Output:**
![image](https://github.com/user-attachments/assets/ea993366-e508-46be-9ce4-b36c86bd9007)

**Question 5**
Write a SQL query to Delete customers from 'customer' table where 'CUST_COUNTRY' is neither 'India' nor 'USA'.

```
DELETE FROM Customer
Where CUST_COUNTRY NOT IN('India','USA');
```

**Output:**
![image](https://github.com/user-attachments/assets/9008fb26-6225-48d9-b6bb-b7abed51ed0f)

**Question 6**
Write a SQL query to Delete all Doctors whose Specialization is either 'Pediatrics' or 'Cardiology' and Last Name is Brown

```
DELETE FROM Doctors
where specialization IN ('Pediatrics','Cardiology') and last_name ='Brown';
```

**Output:**
![image](https://github.com/user-attachments/assets/37a7810e-39aa-4edb-8843-ba83aab3c90f)

**Question 7**
Write a SQL query to Delete customers with 'GRADE' 3 or 'AGENT_CODE' 'A008' whose 'OUTSTANDING_AMT' is less than 5000

```
DELETE FROM Customer
where (GRADE = 3 or AGENT_CODE='A008') and OUTSTANDING_AMT < 5000;
```

**Output:**
![image](https://github.com/user-attachments/assets/accd0231-b177-4982-b191-98e56d714191)

**Question 8**
Write a SQL query to Delete All Doctors with a NULL Last Name

```DELETE FROM Doctors
where last_name is NULL;
```

**Output:**
![image](https://github.com/user-attachments/assets/497841d4-9ae8-48c4-9abe-1d95e103d141)


**Question 9**
Write a SQL query to Delete customers from 'customer' table where 'WORKING_AREA' is 'New York'.

```DELETE FROM Customer
where WORKING_AREA='New York';
```

**Output:**
![image](https://github.com/user-attachments/assets/9159af09-f387-40de-b60d-276142807311)

**Question 10**
Write a SQL statement to Find the salesmen with all information who gets the commission within a range of 0.12 and 0.14.

```
Select * From salesman
where commission BETWEEN 0.12 and 0.14;
```

**Output:**
![image](https://github.com/user-attachments/assets/8ba745eb-37d2-4373-8809-f207b56c9f80)




## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
