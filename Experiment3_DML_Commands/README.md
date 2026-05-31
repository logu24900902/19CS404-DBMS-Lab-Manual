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
--
Write a SQL statement to Update the product_name to 'Premium Bread' whose product ID is 5 in the products table.
Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity

supplier_id
```sql
UPDATE products SET product_name = 'Premium Bread' WHERE product_id = 5;
```

**Output:**

<img width="1453" height="228" alt="q11 1" src="https://github.com/user-attachments/assets/108639b3-385c-4446-a8c6-cfc5cf341e1d" />


**Question 2**
---
Write a SQL statement to Increase the salary by 500 and email as 'updated' for employees with job ID 'SA_REP' and commission percentage greater than 0.15

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id

```sql
UPDATE EMPLOYEES SET salary = salary + 500, email = 'updated' WHERE job_id = 'SA_REP' AND commission_pct > 0.15;
```

**Output:**

<img width="1224" height="319" alt="q22 2" src="https://github.com/user-attachments/assets/4d00d0c2-7e7f-4bb9-a593-ee4a6e585b67" />


**Question 3**
---
Update the reorder level to 40 pieces for all products belonging to the 'Grocery' category in the products table.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT

```sql
UPDATE products SET reorder_lvl = 40 WHERE category = 'Grocery';
```

**Output:**

<img width="1274" height="182" alt="q33" src="https://github.com/user-attachments/assets/3ff94f92-43d3-4da0-aefd-a068bd576518" />

**Question 4**
---
Write a SQL query to Delete a Specific Surgery whose ID is 3

Sample table: Surgeries

attributes: surgery_id, patient_id, surgeon_id, surgery_date

```sql
DELETE FROM Surgeries WHERE surgery_id = 3;
```

**Output:**

<img width="1114" height="311" alt="q44" src="https://github.com/user-attachments/assets/17308778-cee8-456f-becf-09ed45d5cf4b" />

**Question 5**
---
Write a SQL query to Delete customers with 'GRADE' 3 or 'AGENT_CODE' 'A008' whose 'OUTSTANDING_AMT' is less than 5000

Sample table: Customer
<img width="1202" height="123" alt="aa" src="https://github.com/user-attachments/assets/9cb57698-3386-49d1-851d-6aa6a496130f" />


```sql
DELETE FROM Customer WHERE (GRADE = 3 OR AGENT_CODE = 'A008') AND OUTSTANDING_AMT < 5000;
```

**Output:**

<img width="1171" height="248" alt="q55" src="https://github.com/user-attachments/assets/ddbaafe8-db23-491d-aea4-68e8dc1e029e" />

**Question 6**
---
Write a SQL statement to Find those salesmen with all information whose name containing the 1st character is 'N' and the 4th character is 'l' and rests may be any character.

salesman table

cid         name         type        
----------  -----------  ----------  
0           salesman_id  numeric(5)  
1           name         varchar(30)  
2           city         varchar(15)  
3           commission   decimal(5,2) 

```sql
SELECT * FROM salesman WHERE name LIKE 'N__L%';
```

**Output:**

<img width="1249" height="357" alt="Screenshot 2026-05-24 210503" src="https://github.com/user-attachments/assets/271b03ec-5c5e-4db2-87ef-e8596cc8b91b" />

**Question 7**
---
Write a SQL query to assess the performance of value2 as 'Poor', 'Average', or 'Excellent' based on whether it is less than 30, between 30 and 70, or greater than 70 in the Calculations table

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          INTEGER     0                       1
1           value1      REAL        0                       0
2           value2      REAL        0                       0
3           base        INTEGER     0                       0
4           exponent    INTEGER     0                       0
5           number      REAL        0                       0
6           decimal     REAL        0                       0

```sql
SELECT id, value2,
    CASE 
        WHEN value2 < 30 THEN 'Poor'
        WHEN value2 BETWEEN 30 AND 70 THEN 'Average'
        WHEN value2 > 70 THEN 'Excellent'
    END AS performance 
FROM calculations;
```

**Output:**

<img width="949" height="494" alt="Screenshot 2026-05-24 210604" src="https://github.com/user-attachments/assets/cbff54db-08fd-4e5a-a631-4eda8a6998b8" />

**Question 8**
---
Write a SQL query to find all those customers who does not have any grade. Return customer_id, cust_name, city, grade, salesman_id.

Sample table: customer

customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
```sql
SELECT customer_id, cust_name, city, grade, salesman_id FROM customer WHERE grade IS NULL;
```

**Output:**

<img width="1252" height="388" alt="Screenshot 2026-05-24 211126" src="https://github.com/user-attachments/assets/d38c0793-bdf3-4c9e-bb7b-3e7d7326b752" />



**Question 9**
---
Find Products with a Discounted Price Greater than a Given Amount:

Write a query to list all products that have a discounted price greater than $100. Return product_id, original_price, discount_percentage, and discounted_price.

Sample table: Products

product_id | original_price | discount_percentage

"101"           "50"                "0.1"

"102"           "150"               "0.15"

"103"           "200"               "0.2"

"104"           "300"               "0.25"

```sql
SELECT 
    product_id, 
    original_price,
    discount_percentage,
    original_price * (1-discount_percentage) AS discounted_price 
FROM Products
WHERE discounted_price > 100;
```

**Output:**

<img width="1262" height="221" alt="Screenshot 2026-05-24 210636" src="https://github.com/user-attachments/assets/1d92a401-18e7-4945-ae0a-d2ed666cfa97" />

**Question 10**
---
Write a SQL statement to get the EmployeeID, FirstName, BirthDate, Age from employees table whose age is older than 50.

[Note: Calculate age from BirthDate field (consider current date as '2023-12-30')] employees table

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           EmployeeID  INTEGER       0                       1
1           LastName    VARCHAR(15)   0                       0
2           FirstName   VARCHAR(15)   0                       0
3           BirthDate   DATETIME      0                       0
4           Photo       VARCHAR(25)   0                       0
5           Notes       VARCHAR(10)   0                       0

```sql
SELECT 
    EmployeeID, 
    FirstName, 
    BirthDate, 
    CAST((JULIANDAY('2023-12-30') - JULIANDAY(BirthDate)) / 365.25 AS INTEGER) AS age
FROM employees 
WHERE age > 50;
```

**Output:**

<img width="1201" height="679" alt="Screenshot 2026-05-24 211054" src="https://github.com/user-attachments/assets/c925cd6b-e3bd-4a84-8988-36d61a0e7aac" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
