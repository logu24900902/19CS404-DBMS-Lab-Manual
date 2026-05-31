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
--
How many appointments are scheduled for each doctor?

```sql
SELECT DoctorID, COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY DoctorID
ORDER BY DoctorID;
```

**Output:**

<img width="715" height="614" alt="506091703-e7d213cb-9996-46c7-ac2f-e1772a81947c" src="https://github.com/user-attachments/assets/303f301c-cc69-415c-a24c-c6a994444aa9" />

**Question 2**
---
What is the average dosage prescribed for each medication?

```sql
SELECT Medication,AVG(Dosage) AS AvgDosage
FROM Prescriptions
GROUP BY Medication
ORDER BY Medication;
```

**Output:**

<img width="615" height="726" alt="q222" src="https://github.com/user-attachments/assets/7c4a9a07-2050-49e6-8509-b698f0e30281" />

**Question 3**
---
How many patients are there in each city?



```sql
SELECT Address,COUNT(*) AS TotalPatients
FROM Patients
GROUP BY Address
ORDER BY Address;
```

**Output:**

<img width="615" height="391" alt="q333" src="https://github.com/user-attachments/assets/a4e63caa-2d0b-46ad-8e5c-a35d3d1aba94" />

**Question 4**
---
Write a SQL query to return the total number of rows in the 'customer' table where the city is not Noida.

```sql
SELECT COUNT(*) AS COUNT FROM customer
WHERE city!='Noida';
```

**Output:**

<img width="325" height="271" alt="q444" src="https://github.com/user-attachments/assets/6e82fd8e-9ef2-467b-84d6-f088d71a0bec" />

**Question 5**
---
Write a SQL query to calculate the average purchase amount of all orders. Return average purchase amount.

Sample table: orders

ord_no purch_amt ord_date customer_id salesman_id

70001 150.5 2012-10-05 3005 5002

70009 270.65 2012-09-10 3001 5005

70002 65.26 2012-10-05 3002 5001

```sql
SELECT AVG(purch_amt) AS AVERAGE
FROM orders;
```

**Output:**

<img width="343" height="298" alt="q555" src="https://github.com/user-attachments/assets/88e8edf7-440d-4285-ac89-b491e10deed0" />

**Question 6**
---
Write a SQL query to determine the number of customers who received at least one grade for their activity.

Sample table: customer

customer_id | cust_name | city | grade | salesman_id

-------------+----------------+------------+-------+-------------

    3002 | Nick Rimando   | New York   |   100 |        5001

    3007 | Brad Davis     | New York   |   200 |        5001

    3005 | Graham Zusi    | California |   200 |        5002

```sql
SELECT COUNT(*) AS COUNT FROM customer
WHERE grade IS NOT NULL;
```

**Output:**

<img width="327" height="289" alt="q666" src="https://github.com/user-attachments/assets/eb929525-8c72-4b45-bcc2-afe8f1385275" />

**Question 7**
---
Write a SQL query to find how many employees have an income greater than 50K?

Table: employee

name type

id INTEGER name TEXT age INTEGER city TEXT income INTEGER

```sql
SELECT COUNT(*) AS employees_count FROM employee
WHERE income>50000;
```

**Output:**

<img width="417" height="299" alt="777q" src="https://github.com/user-attachments/assets/7ee07db7-f3a0-4546-b5c0-25b25b2bfc14" />

**Question 8**
---
Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the total salary sum for each group, and excludes groups where the total salary sum is not greater than 5000.

```sql
SELECT (age/5)*5 AS age_group,SUM(salary)
FROM customer1
GROUP BY age_group
HAVING SUM(salary)>5000;
```

**Output:**

<img width="694" height="412" alt="Screenshot 2026-05-24 213139" src="https://github.com/user-attachments/assets/0c5912c2-6a78-454c-8cf4-7ff7a8cdabd6" />

**Question 9**
---
Write the SQL query that achieves the grouping of data by city, calculates the average income for each city, and includes only those cities where the average income is greater than 500,000.

```sql
SELECT city,AVG(income)
FROM employee
GROUP BY city
HAVING AVG(income)>500000;
```

**Output:**

<img width="701" height="499" alt="Screenshot 2026-05-24 213217" src="https://github.com/user-attachments/assets/5d8aa710-1a70-44c4-abb5-dcdb5c0c02cb" />

**Question 10**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the average work hours for each occupation, and includes only those occupations where the average work hour falls between 10 and 12.

```sql
SELECT occupation,AVG(workhour)
FROM employee1
GROUP BY occupation
HAVING AVG(workhour) BETWEEN 10 AND 12;
```

**Output:**

<img width="763" height="446" alt="Screenshot 2026-05-24 213305" src="https://github.com/user-attachments/assets/5624569c-d79d-486c-875b-6a99bf831d43" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
