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
--
Create a table named Products with the following columns:

ProductID as INTEGER ProductName as TEXT Price as REAL Stock as INTEGER

```sql
create table products(
ProductID INTEGER,
ProductName TEXT,
Price REAL,
Stock INTEGER
);
```

**Output:**

<img width="1205" height="366" alt="q1" src="https://github.com/user-attachments/assets/dc824766-3a48-464d-9078-e7b9d07f7259" />


**Question 2**
---
Write an SQL Query to add the attributes designation, net_salary, and dob to the Companies table with the following data types: designation as VARCHAR(50) net_salary as NUMBER dob as DATE

```sql
alter table Companies add column designation varchar(50);
alter table Companies add column net_salary number;
alter table Companies add column dob date;
```

**Output:**

<img width="1185" height="401" alt="q2" src="https://github.com/user-attachments/assets/721db2ce-af3e-4d81-bc06-3289b78c74f8" />


**Question 3**
---
Create a table named Locations with the following columns:

LocationID as INTEGER LocationName as TEXT Address as TEXT

```sql
create table Locations(
LocationID INTEGER,
LocationName TEXT,
Address TEXT
);
```

**Output:**

<img width="1179" height="369" alt="592988297-f2df3e1f-733a-468d-9957-1c90a9956551" src="https://github.com/user-attachments/assets/0b9767ee-8dd2-48bb-917a-2c937a33b045" />


**Question 4**
---
Create a table named Orders with the following constraints: OrderID as INTEGER should be the primary key. OrderDate as DATE should be not NULL. CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).

```sql
create table Orders(
OrderID INTEGER primary key,
OrderDate DATE not null,
CustomerID INTEGER,
foreign key (CustomerID) references Customers(CustomerID)
);
```

**Output:**

<img width="1188" height="272" alt="q4" src="https://github.com/user-attachments/assets/a0f796ab-1feb-488d-8695-7fc45bef4ca3" />

**Question 5**
---
Create a table named Events with the following columns:

EventID as INTEGER EventName as TEXT EventDate as DATE

```sql
create table Events(
EventID INTEGER,
EventName TEXT,
EventDate DATE
);
```

**Output:**

<img width="1192" height="366" alt="q5" src="https://github.com/user-attachments/assets/6cce4853-ee06-40f2-bc6e-a0cea7166269" />
**Question 6**
---
Create a table named Orders with the following columns:

OrderID as INTEGER OrderDate as TEXT CustomerID as INTEGER

```sql
create table Orders(
OrderID INTEGER,
OrderDate TEXT,
CustomerID INTEGER
);
```

**Output:**

<img width="1179" height="363" alt="q6" src="https://github.com/user-attachments/assets/8dc5640e-5894-4a4d-a163-20743eeb215f" />

**Question 7**
---
Insert the following products into the Products table:

```sql
insert into Products (Name,Category,Price,Stock)
 values
 ('Smartphone','Electronics',800,150),
 ('Headphones','Accessories',200,300);
```

**Output:**

<img width="1190" height="342" alt="q7" src="https://github.com/user-attachments/assets/7c3454bb-c18c-4da1-a160-2243cc1ec23a" />

**Question 8**
---
Insert a student with RollNo 201, Name David Lee, Gender M, Subject Physics, and MARKS 92 into the Student_details table.
```sql
insert into Student_details (RollNo,Name,Gender,Subject,Marks)
values 
(201,'David Lee','M','Physics',92);
```

**Output:**

<img width="1186" height="234" alt="q8" src="https://github.com/user-attachments/assets/e589022b-f60f-43aa-96a3-3deb362477fe" />

**Question 9**
---
Write a SQL query to modify the Student_details table by adding a new column Email of type VARCHAR(50) and updating the column MARKS to have a default value of 0.

```sql
ALTER table Student_details add Email varchar(50);
alter table Student_details 
add column MARKS integer default 0;
```

**Output:**

<img width="1180" height="231" alt="9q" src="https://github.com/user-attachments/assets/eff30b68-c159-4e52-886d-8b329cad2f3a" />

**Question 10**
---
Insert all students from Archived_students table into the Student_details table.

```sql
insert into Student_details(RollNo,Name,Gender,Subject,Marks)
select RollNo,Name,Gender,Subject,Marks
from Archived_students;
```

**Output:**

<img width="1262" height="294" alt="Screenshot 2026-05-24 204551" src="https://github.com/user-attachments/assets/c2b6f00e-3a92-4af8-be5b-9c01c6b0c7f8" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
