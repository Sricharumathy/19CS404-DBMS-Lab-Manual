# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**

![image](https://github.com/user-attachments/assets/87686b48-584f-4d46-91ba-7169ca3893c7)


```
SELECT 
    c.cust_name,
    c.city AS city,
    c.grade,
    s.name AS Salesman,
    s.city AS city
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE c.grade < 300
ORDER BY c.customer_id ASC;
```

**Output:**
![image](https://github.com/user-attachments/assets/c15a4e91-9a01-4119-bb36-f41e206a695e)


**Question 2**

![image](https://github.com/user-attachments/assets/09fbfc99-4fc2-468d-be09-9014d9c5907a)


```
SELECT 
    o.ord_no,
    o.ord_date,
    o.purch_amt,
    c.cust_name AS "Customer Name",
    c.grade,
    s.name AS "Salesman",
    s.commission
FROM orders o
JOIN customer c ON o.customer_id = c.customer_id
JOIN salesman s ON o.salesman_id = s.salesman_id;
```

**Output:**
![image](https://github.com/user-attachments/assets/5d3c66c9-c4b1-4492-8032-7fbdcd389211)


**Question 3**

![image](https://github.com/user-attachments/assets/8bf70b88-2d93-46dc-b7ac-6100247795b6)


```
SELECT 
    o.ord_no,
    o.purch_amt,
    c.cust_name,
    c.city
FROM orders o
JOIN customer c ON o.customer_id = c.customer_id
WHERE o.purch_amt BETWEEN 500 AND 2000;
```

**Output:**
![image](https://github.com/user-attachments/assets/ed29b1fd-d5d6-4b0b-af9c-deb84a70f822)


**Question 4**

![image](https://github.com/user-attachments/assets/15d3dce2-642d-4bdf-9837-cbeda2dbd468)


```
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.commission
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE s.commission > 0.12;
```

**Output:**
![image](https://github.com/user-attachments/assets/d72b2bc2-ffc9-4e4b-9810-75bbcbfda893)


**Question 5**
![image](https://github.com/user-attachments/assets/415505bb-2a33-47f4-9023-ed3752b509ea)


```
SELECT 
    c.cust_name,
    o.ord_no,
    o.ord_date,
    o.purch_amt
FROM customer c
LEFT JOIN orders o ON c.customer_id = o.customer_id
WHERE o.purch_amt > 1000;
```

**Output:**
![image](https://github.com/user-attachments/assets/0aa8f5a2-1e25-463e-b433-1a304e084e0f)

**Question 6**
![image](https://github.com/user-attachments/assets/ef7cbe82-ce3c-4a63-a982-7fc2947bd3ba)


```
SELECT 
    p.*
FROM 
    patients p
INNER JOIN 
    doctors d ON p.doctor_id = d.doctor_id
WHERE 
    d.first_name = 'John'
    AND d.last_name = 'Smith';
```

**Output:**
![image](https://github.com/user-attachments/assets/513ee823-6053-4ba2-accd-617335f94ef9)


**Question 7**
![image](https://github.com/user-attachments/assets/3a827551-73ad-46f6-8f21-62350e4908ca)

```
SELECT 
    c.cust_name,
    s.commission
FROM 
    customer c
LEFT JOIN 
    salesman s ON c.salesman_id = s.salesman_id;
```

**Output:**
![image](https://github.com/user-attachments/assets/48f347e7-5558-413c-bdf4-199239906d26)


**Question 8**
![image](https://github.com/user-attachments/assets/42d894c1-283f-4973-b258-386976d9d495)


```
SELECT 
    c.cust_name,
    c.city AS city,
    c.grade,
    s.name AS Salesman,
    s.city AS city
FROM 
    customer c
JOIN 
    salesman s ON c.salesman_id = s.salesman_id
ORDER BY 
    c.customer_id ASC;
```

**Output:**

![image](https://github.com/user-attachments/assets/d6c1277e-7fac-488f-9f21-de1718cf7f0f)


**Question 9**
![image](https://github.com/user-attachments/assets/bc23093d-fb36-44d8-ba50-24e0d06a8e9b)


```
SELECT 
    p.admission_date,
    s.surgery_date
FROM 
    patients p
INNER JOIN 
    surgeries s ON p.patient_id = s.patient_id;
```

**Output:**
![image](https://github.com/user-attachments/assets/4ffba2c1-5b9c-46e7-984d-ba6c7c6b5cd2)


**Question 10**
![image](https://github.com/user-attachments/assets/8ed5b532-526f-4d90-bcaa-6146240b91c5)


```
SELECT 
    p.first_name AS patient_name,
    t.*
FROM 
    patients p
INNER JOIN 
    test_results t ON p.patient_id = t.patient_id
WHERE 
    p.admission_date BETWEEN '2024-01-01' AND '2024-01-31';
```

**Output:**
![image](https://github.com/user-attachments/assets/4bb24c43-bd22-4a4e-9693-4906d977f68d)



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
