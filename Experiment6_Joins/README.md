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
--
<img width="1268" height="735" alt="image" src="https://github.com/user-attachments/assets/cabf09c3-9868-4ab7-a0b9-0263ea409825" />


```sql
SELECT patients.first_name, surgeries.*
FROM patients
INNER JOIN surgeries
ON patients.patient_id = surgeries.patient_id
WHERE patients.date_of_birth > '1990-01-01';
```

**Output:**

<img width="1295" height="289" alt="image" src="https://github.com/user-attachments/assets/7df687ff-6c1f-435c-b117-7700d75d91c1" />


**Question 2**
---
<img width="1294" height="778" alt="439278357-80bbc0cc-afae-48cd-8e02-f6a7e23709ae" src="https://github.com/user-attachments/assets/8f276291-7332-4fd2-9151-1b6216ea7749" />

```sql
SELECT orders.ord_no, 
       orders.purch_amt, 
       orders.ord_date, 
       customer.cust_name, 
       customer.city AS customer_city, 
       customer.grade, 
       salesman.name AS salesman_name, 
       salesman.city AS salesman_city, 
       salesman.commission
FROM orders
INNER JOIN customer ON orders.customer_id = customer.customer_id
INNER JOIN salesman ON orders.salesman_id = salesman.salesman_id;
```

**Output:**

<img width="1361" height="613" alt="439278564-f1c29cef-eae4-4ef5-86d2-8c8979ace9a8" src="https://github.com/user-attachments/assets/48f8a761-49e8-454f-81c9-883aae70db99" />

**Question 3**
---
<img width="1310" height="633" alt="image" src="https://github.com/user-attachments/assets/e0f8bab9-9131-4d4c-9b38-125a0dad000a" />


```sql
SELECT customer.cust_name, 
       customer.city AS city, 
       customer.grade, 
       salesman.name AS Salesman, 
       salesman.city AS city
FROM customer
INNER JOIN salesman ON customer.salesman_id = salesman.salesman_id
WHERE customer.grade < 300
ORDER BY customer.customer_id ASC;
```

**Output:**

<img width="1301" height="509" alt="image" src="https://github.com/user-attachments/assets/d6d1683f-5866-4dd2-81ff-902cdafb39a9" />


**Question 4**
---
<img width="1299" height="576" alt="image" src="https://github.com/user-attachments/assets/233fe4ed-2c03-4401-b115-1e03c078e22f" />


```sql
SELECT n.nurse_id, d.department_name
FROM nurses n
INNER JOIN departments d ON n.department_id = d.department_id
WHERE n.first_name = 'David' AND n.last_name = 'Moore';
```

**Output:**

<img width="1097" height="309" alt="image" src="https://github.com/user-attachments/assets/739a3631-3e65-4be2-b655-c624d21ee424" />


**Question 5**
---
<img width="1259" height="813" alt="image" src="https://github.com/user-attachments/assets/2d7ea396-4ee1-4d7f-b761-ddc6976a3637" />


```sql
SELECT o.ord_no, o.ord_date, o.purch_amt, c.cust_name AS "Customer Name", c.grade, s.name AS Salesman, s.commission
FROM orders o
INNER JOIN customer c ON o.customer_id = c.customer_id
INNER JOIN salesman s ON o.salesman_id = s.salesman_id;
```

**Output:**

<img width="1326" height="609" alt="image" src="https://github.com/user-attachments/assets/aa65faa8-b7a0-4a8f-94c4-5dccaa49fe56" />


**Question 6**
---
<img width="1321" height="584" alt="image" src="https://github.com/user-attachments/assets/9a9234a3-85fe-4352-a49a-2ce6d1724755" />


```sql
SELECT c.*
FROM customer c
LEFT JOIN orders o ON c.customer_id = o.customer_id
WHERE o.ord_date > '2012-08-17';
```

**Output:**

<img width="1279" height="629" alt="image" src="https://github.com/user-attachments/assets/cc8b4e72-6404-494f-bd7d-c78018916633" />


**Question 7**
---
<img width="1307" height="579" alt="image" src="https://github.com/user-attachments/assets/6b30a982-0a0c-4d5f-843b-f5b4ca22d3c0" />


```sql
SELECT c.cust_name, s.name
FROM customer c
LEFT JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE c.city = s.city;
```

**Output:**

<img width="1166" height="481" alt="image" src="https://github.com/user-attachments/assets/6c29e4a5-382e-4e18-9bc2-5ce8bbcc5eef" />


**Question 8**
---
<img width="1222" height="782" alt="image" src="https://github.com/user-attachments/assets/5ceae6b8-c7f8-4bd2-a1b6-f920395b710f" />

```sql
SELECT c.cust_name AS "Customer Name", 
       c.city AS "city", 
       s.name AS "Salesman", 
       s.commission AS "commission"
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id;
```

**Output:**

<img width="1211" height="730" alt="image" src="https://github.com/user-attachments/assets/d741c9d4-371c-4619-9a50-1644ef04ef45" />


**Question 9**
---
<img width="1283" height="640" alt="image" src="https://github.com/user-attachments/assets/5375f075-6503-479e-ba06-62c75fe870c3" />


```sql
SELECT n.*
FROM nurses n
INNER JOIN departments d ON n.department_id = d.department_id
WHERE d.department_name = 'Pediatrics';
```

**Output:**

<img width="1234" height="308" alt="image" src="https://github.com/user-attachments/assets/3585d0ea-8f02-49ae-b604-f687e382c74b" />


**Question 10**
---
<img width="1321" height="727" alt="image" src="https://github.com/user-attachments/assets/04252d52-c372-489e-a6df-d611d6bc448d" />


```sql
SELECT c.cust_name as "Customer Name", c.city AS city, s.name AS Salesman, s.city AS city, s.commission
FROM customer c
INNER JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE c.city != s.city
AND s.commission > 0.12;
```

**Output:**

<img width="1263" height="463" alt="image" src="https://github.com/user-attachments/assets/c725a9fd-5e2d-4bbb-9c85-59c018ef7fe0" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
