# Experiment 3: DML Commands
## Name: Lakshanya.N
## Register Number: 21222423036

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
Write a SQL statement to Increase the selling price per unit by 5% for product ID 15 who's sale is on '2023-01-31'.

sales(sale_id,sale_date,product_id,quantity,sell_price,total_sell_price)

```sql
UPDATE sales
SET sell_price =sell_price*1.05
WHERE product_id=15
    AND sale_date='2023-01-31';
```

**Output:**

<img width="1326" height="430" alt="Screenshot 2026-08-21 113604" src="https://github.com/user-attachments/assets/2ac4afb5-2ec1-4903-9aa7-3e1db62c34d4" />


**Question 2**
---
Write a SQL query to find customers who are from the city 'London' who have a grade greater than 200. Return customer_id, cust_name, city, grade, and salesman_id.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002

```sql
SELECT customer_id,cust_name,city,grade,salesman_id
FROM customer
WHERE city='London'     
    AND grade>200;
```

**Output:**

<img width="1370" height="344" alt="Screenshot 2026-08-21 113557" src="https://github.com/user-attachments/assets/50ba0a99-ee45-4b9b-a448-4e00813a13e8" />


**Question 3**
---
Write a SQL query to Select all patients whose name starts with A.

Table: Patients

name                  type
--------------------  ----------
patient_id            INT
first_name            VARCHAR(50)
last_name             VARCHAR(50)
date_of_birth         DATE
admission_date        DATE
discharge_date        DATE
doctor_id             INT
```sql
SELECT *
FROM Patients
WHERE first_name LIKE 'A%';
```

**Output:**

<img width="1309" height="306" alt="Screenshot 2026-08-21 113549" src="https://github.com/user-attachments/assets/95b574c2-71cd-48fa-a407-ba0f5bfefe56" />


**Question 4**
---
Write a SQL statement to change salary of employee to 8000 whose Employee ID is 105, if the existing salary is less than 5000.


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
UPDATE employees
SET salary=8000
WHERE employee_id=105
    AND salary<5000;
```

**Output:**

<img width="1258" height="274" alt="Screenshot 2026-08-21 113538" src="https://github.com/user-attachments/assets/a66c3a4b-aea7-4de3-973e-d5b27e8ac3b1" />

**Question 5**
---
Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.

Suppliers Table 

name               type
-----------------  ---------------
supplier_id        INT
supplier_name      VARCHAR(100)
contact_person     VARCHAR(100)
phone_number       VARCHAR(20)
email              VARCHAR(100)
address            VARCHAR(250)
```sql
UPDATE suppliers
SET address='58 Lakeview, Magnolia'
WHERE supplier_id=5;
```

**Output:**

<img width="1370" height="383" alt="Screenshot 2026-08-21 113530" src="https://github.com/user-attachments/assets/921f88c7-95a0-4a06-b53d-2e511b80d2d0" />


**Question 6**
---
Write a SQL query to delete a specific doctor from Doctors table whose ID is 1.

Sample table: Doctors

attributes: doctor_id, first_name, last_name, specialization

```sql
DELETE FROM Doctors
WHERE doctor_id=1;
```

**Output:**

<img width="1294" height="298" alt="Screenshot 2026-08-21 113514" src="https://github.com/user-attachments/assets/3750d508-a36f-4776-9784-ff4e00d38cca" />

**Question 7**
---
Write a SQL query to calculate the final price after applying both the discount and the tax. Return product_id, original_price, discount_percentage, tax_rate, and final_price.

Sample table: Products

product_id | original_price | discount_percentage | tax_rate

 ------------+----------------+---------------------+--------- 

101 | 50.00 | 0.10 | 0.08 

102 | 75.00 | 0.15 | 0.05 

103 | 100.00 | 0.20 | 0.10
```sql
SELECT product_id,
    original_price,
    discount_percentage,
    tax_rate,
    original_price*(1-
    discount_percentage)*(1+tax_rate)
AS final_price
FROM Products;
```

**Output:**

<img width="1345" height="307" alt="Screenshot 2026-08-21 113506" src="https://github.com/user-attachments/assets/1ed89241-c8b6-4c5d-b4ae-7794dcdc8abb" />


**Question 8**
---
Write a SQL query to Delete customers with 'GRADE' 3 or 'AGENT_CODE' 'A008' whose 'OUTSTANDING_AMT' is less than 5000

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |

```sql
DELETE FROM Customer
WHERE(GRADE=3 OR AGENT_CODE='A008') 
    AND OUTSTANDING_AMT <5000;
```

**Output:**

<img width="1358" height="351" alt="Screenshot 2026-08-21 113458" src="https://github.com/user-attachments/assets/8ac1cedd-241f-41b5-91ef-fe25c167923f" />


**Question 9**
---
Write a SQL statement to display name and commission of first 5 salesmen.

table info

salesman(name,commission) 

```sql
SELECT name,commission 
FROM salesman
LIMIT 5;
```

**Output:**

<img width="1301" height="443" alt="Screenshot 2026-08-21 113449" src="https://github.com/user-attachments/assets/3d409d98-6d1e-456f-b066-aa047e793661" />


**Question 10**
---
Write a SQL statement to show all the contact_name, address, city of all customers who are from 'Germany', 'Mexico' and 'Spain' countries.

customers table

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           CustomerID    INTEGER      0                       1
1           CustomerName  VARCHAR(50)  0                       0
2           ContactName   VARCHAR(50)  0                       0
3           Address       VARCHAR(50)  0                       0
4           City          VARCHAR(20)  0                       0
5           PostalCode    VARCHAR(10)  0                       0
6           Country       VARCHAR(15)  0                       0

```sql
SELECT ContactName,Address,City 
FROM customers
WHERE Country IN('Germany','Mexico','Spain');
```

**Output:**

<img width="1022" height="718" alt="Screenshot 2026-08-21 113438" src="https://github.com/user-attachments/assets/bee5c623-4a30-4635-b001-73210d445bc5" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
