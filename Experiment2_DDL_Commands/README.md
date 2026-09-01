# Experiment 2: DDL Commands
## Name: Lakshanya.N
## Register Number :212224230136

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

ProductID as INTEGER
ProductName as TEXT
Price as REAL
Stock as INTEGER

```sql
Create table Products(
 ProductID  INTEGER ,
 ProductName  TEXT ,
 Price  REAL,
 Stock  INTEGER 
);
```

**Output:**

<img width="1281" height="278" alt="Screenshot 2026-08-20 225644" src="https://github.com/user-attachments/assets/93cb5487-f45e-4a46-8f86-58237ed95fe4" />


**Question 2**
---
Insert the following students into the Student_details table:
RollNo      Name        Gender      Subject     MARKS
----------  ----------  ----------  ----------  ----------
202            Ella King         F           Chemistry   87
203            James Bond   M          Literature    78

 

```sql
INSERT INTO Student_details 
(RollNo,Name,Gender,Subject, MARKS)
VALUES
(202, 'Ella King','F','Chemistry',87),
(203,'James Bond','M','Literature',78);
```

**Output:**

<img width="1228" height="237" alt="Screenshot 2026-08-20 225735" src="https://github.com/user-attachments/assets/112ec1b4-0e00-4a42-b8ee-2dc10b4e0666" />


**Question 3**
---
Create a table named Invoices with the following constraints:
InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
Amount as REAL should be greater than 0.
DueDate as DATE should be greater than the InvoiceDate.
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
Create  table  Invoices (
   InvoiceID  INTEGER primary key ,
   InvoiceDate  DATE,
   Amount REAL CHECK (Amount >0),
   DueDate DATE CHECK (DueDate >InvoiceDate), 
   OrderID INTEGER,
   FOREIGN KEY(orderID) REFERENCES Orders(OrderID)
);   
```

**Output:**

<img width="1368" height="261" alt="Screenshot 2026-08-20 225813" src="https://github.com/user-attachments/assets/5394b4b2-7b86-472e-9720-562ea9c1ea21" />


**Question 4**
---
Insert all books from Out_of_print_books into Books

Table attributes are ISBN, Title, Author, Publisher, YearPublished

For example:

Test	Result
select * from Books;
ISBN            Title           Author              Publisher      YearPublished
--------------  --------------  ------------------  -------------  -------------
978-1234567890  The Lost World  Arthur Conan Doyle  Vintage Books  1912
978-0987654321  Gone with the   Margaret Mitchell   Macmillan      1936
978-1122334455  Moby Dick       Herman Melville     Harper & Brot  1851

```sql
INSERT INTO Books(ISBN,Title,Author,PUblisher,YearPublished)
SELECT  ISBN, Title, Author, Publisher, YearPublished
FROM out_of_print_books;
```

**Output:**

<img width="1280" height="283" alt="Screenshot 2026-08-20 225920" src="https://github.com/user-attachments/assets/0f0fdea3-5e07-4ae3-a3f2-565d734fda91" />


**Question 5**
---
Write an SQL Query to add the attributes designation, net_salary, and dob to the Companies table with the following data types:
designation as VARCHAR(50)
net_salary as NUMBER
dob as DATE

```sql
ALTER TABLE Companies ADD COLUMN
designation varchar(50);
ALTER TABLE Companies ADD COLUMN
net_salary number;
ALTER TABLE Companies ADD COLUMN dob
date;
```

**Output:**

<img width="1315" height="346" alt="Screenshot 2026-08-20 230001" src="https://github.com/user-attachments/assets/7aa435ec-b8a2-448a-90e8-c8bdf8ad93d7" />


**Question 6**
---
Create a new table named products with the following specifications:
product_id as INTEGER and primary key.
product_name as TEXT and not NULL.
list_price as DECIMAL (10, 2) and not NULL.
discount as DECIMAL (10, 2) with a default value of 0 and not NULL.
A CHECK constraint at the table level to ensure:
list_price is greater than or equal to discount
discount is greater than or equal to 0
list_price is greater than or equal to 0

```sql
Create table  products(
    product_id INTEGER primary key,
    product_name TEXT  not NULL,
    list_price  DECIMAL (10, 2)  not NULL,
    discount DECIMAL (10, 2) NOT null default 0,
    CHECK(list_price>=discount AND discount>=0 AND list_price>=0)
);
```

**Output:**

<img width="1301" height="330" alt="Screenshot 2026-08-20 230150" src="https://github.com/user-attachments/assets/544fa3f5-b8b4-4ef8-9d30-f0b7b3362dc4" />


**Question 7**
---
In the Student_details table, insert a student record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

RollNo      Name            Gender      Subject      MARKS
----------  ------------    ----------  ----------   ----------
205         Olivia Green    F
207         Liam Smith      M           Mathematics  85
208         Sophia Johnson  F           Science
```sql
INSERT INTO Student_details VALUES (205,'Olivia Green','F',NULL,NULL);
INSERT INTO Student_details VALUES (207,'Liam Smith','M', 'Mathematics',85);
INSERT INTO Student_details VALUES (208,'Sophia Johnson','F','Science',NULL); 
```

**Output:**

<img width="1297" height="298" alt="Screenshot 2026-08-20 230209" src="https://github.com/user-attachments/assets/df1993d6-1e97-465c-aa67-d4212f7631b9" />


**Question 8**
---
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should cascade updates and deletes.
item_desc and rate should not accept NULL.

```sql
Create table  item (
    item_id TEXT primary key,
    item_desc TEXT NOT NULL,
    rate  INTEGER NOT NULL,
    icom_id  TEXT(4),
    foreign key (icom_id)references Company(com_id)
    ON UPDATE CASCADE
    ON DELETE CASCADE
);
```

**Output:**

<img width="1248" height="283" alt="Screenshot 2026-08-20 230226" src="https://github.com/user-attachments/assets/6a91f76a-f12b-473b-980e-f23e296fa5c5" />


**Question 9**
---
Write a SQL Query  to add attribute ISBN as varchar(30) and domain_dept as varchar(30) in the table 'books'

```sql
ALTER TABLE books ADD column ISBN
varchar(30);
ALTER TABLE books ADD COLUMN
domain_dept varchar(30);
```

**Output:**

<img width="1269" height="230" alt="Screenshot 2026-08-20 230241" src="https://github.com/user-attachments/assets/47e292b4-b960-4820-aeab-249fe77ec3d2" />

**Question 10**
---
Create a table named Members with the following columns:

MemberID as INTEGER
MemberName as TEXT
JoinDate as DATE

```sql
Create table Members(
    MemberID  INTEGER,
    MemberName  TEXT,
    JoinDate  DATE
)
```

**Output:**

<img width="1322" height="299" alt="Screenshot 2026-08-20 230301" src="https://github.com/user-attachments/assets/6b9ccb54-6466-4d66-bb2c-95b2bba9b6de" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
