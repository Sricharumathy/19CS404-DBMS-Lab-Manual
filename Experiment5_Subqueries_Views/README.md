# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**

![image](https://github.com/user-attachments/assets/75fdb7e5-62a4-452b-82fd-3daac63a11eb)


```
SELECT o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
FROM orders o
JOIN salesman s ON o.salesman_id = s.salesman_id
WHERE s.city = 'New York';

```

**Output:**
![image](https://github.com/user-attachments/assets/48fb9120-2ea7-4db9-8f3d-62bc7d68658a)


**Question 2**

![image](https://github.com/user-attachments/assets/0ac9cd92-9315-4b2a-933b-e2b884f690c7)


```
SELECT commission
FROM salesman
WHERE salesman_id IN ( SELECT salesman_id
                       FROM customer
                       WHERE city LIKE 'Paris' ) ;

```

**Output:**
![image](https://github.com/user-attachments/assets/576c7d56-43db-402e-9982-a13017c2b9bd)


**Question 3**

![image](https://github.com/user-attachments/assets/dc3798ce-4d33-4c76-8f00-4dc74737f268)


```
SELECT medication_id AS medic,medication_name,dosage
FROM Medications
WHERE dosage =(SELECT min(dosage)
               FROM Medications);
```

**Output:**
![image](https://github.com/user-attachments/assets/3dfda7ab-7385-4d94-af94-3493817268cb)


**Question 4**

![image](https://github.com/user-attachments/assets/ea92506f-0cb2-49a2-93e2-db92eb4aa33f)



```
SELECT *
FROM CUSTOMERS
WHERE AGE < 30 and address='Delhi'
ORDER BY ID;
```

**Output:**
![image](https://github.com/user-attachments/assets/75b75a39-7f2e-45cf-8f44-5d68505e1480)


**Question 5**

![image](https://github.com/user-attachments/assets/2f06365d-abd9-48ef-ae71-7d03fc0a947c)


```
SELECT s.salesman_id, s.name
FROM salesman s
JOIN (
    SELECT salesman_id
    FROM customer
    GROUP BY salesman_id
    HAVING COUNT(*) > 1
) c ON s.salesman_id = c.salesman_id;
```

**Output:**
![image](https://github.com/user-attachments/assets/acc5db71-16d7-421c-b1b3-2d28f09f88b9)


**Question 6**

![image](https://github.com/user-attachments/assets/3c9aae41-66a4-4245-b6d3-f95129fd7fe0)


```
SELECT o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
FROM orders o
JOIN salesman s ON o.salesman_id = s.salesman_id
WHERE s.city = 'London';
```

**Output:**
![image](https://github.com/user-attachments/assets/f063fbca-9d5d-4ca3-8557-3df683ffb2b9)


**Question 7**

![image](https://github.com/user-attachments/assets/05e4e0a7-bbfe-4284-a18f-fd33e8e80ff7)


```
SELECT o.ord_no, o.purch_amt, o.ord_date, o.salesman_id
FROM orders o
JOIN salesman s ON o.salesman_id = s.salesman_id
WHERE s.commission = (
    SELECT MAX(commission)
    FROM salesman
);

```

**Output:**
![image](https://github.com/user-attachments/assets/07b0db6e-b544-4d34-a34e-095b7354eb52)


**Question 8**

![image](https://github.com/user-attachments/assets/7db6a4b9-ee4d-4ade-99b1-8a1b03ef4763)


```
SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM orders
WHERE salesman_id IN (
    SELECT DISTINCT salesman_id
    FROM orders
    WHERE customer_id = 3007
);
```

**Output:**
![image](https://github.com/user-attachments/assets/acb1599e-1f76-4035-ad90-652340ff60a0)

**Question 9**

![image](https://github.com/user-attachments/assets/63d5d1af-19ec-4a99-90a0-42149b8cf724)

```
SELECT o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
FROM orders o
JOIN salesman s ON o.salesman_id = s.salesman_id
WHERE s.city = 'New York';
```

**Output:**
![image](https://github.com/user-attachments/assets/da338032-fbcc-4e3e-988c-a38cc319415f)


**Question 10**

![image](https://github.com/user-attachments/assets/ad80acd2-7fb8-487b-b8d3-aa4d13831a7c)


```
SELECT o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
FROM orders o
JOIN salesman s ON o.salesman_id = s.salesman_id
WHERE s.name = 'Paul Adam';
```

**Output:**
![image](https://github.com/user-attachments/assets/e222268b-9bdd-4701-ba04-3d535e82d5da)



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
