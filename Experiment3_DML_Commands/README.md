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
Write a SQL query to identify products where the discount amount is greater than $50. Return product_id, original_price, discount_percentage, and discount_amount.

Sample table: products

product_id | original_price | discount_percentage 

------------+----------------+--------------------- 

101 | 100.00 | 0.60 

102 | 150.00 | 0.40 

103 | 200.00 | 0.10
```sql
SELECT product_id,original_price,discount_percentage,(original_price*discount_percentage)AS discount_amount FROM products WHERE discount_amount>50;
```

**Output:**

<img width="1207" height="271" alt="image" src="https://github.com/user-attachments/assets/47eef6a8-08a7-4c43-8493-962d095036bf" />


**Question 2**
---
Write a SQL statement to Increase the selling price per unit by 5% for product ID 15 who's sale is on '2023-01-31'.

sales(sale_id,sale_date,product_id,quantity,sell_price,total_sell_price)

```sql
UPDATE sales
SET sell_price=sell_price*1.05
WHERE product_id=15 AND sale_date='2023-01-31';
```

**Output:**

<img width="1206" height="456" alt="image" src="https://github.com/user-attachments/assets/6394abee-2e30-4abb-b4cc-c7367c2539e0" />


**Question 3**
---
Write a SQL query to Delete All Doctors whose ID ranges from 2 to 4.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

```sql
DELETE FROM Doctors WHERE doctor_id>=2 AND doctor_id<=4;
```

**Output:**

<img width="1205" height="834" alt="image" src="https://github.com/user-attachments/assets/16334f4f-f59e-4ff0-a59e-2e0592980877" />


**Question 4**
---
Write a SQL query to Delete All Doctors with a NULL Last Name

Sample table: Doctors

attributes: doctor_id, first_name, last_name, specialization

```sql
DELETE FROM Doctors WHERE last_name IS NULL;
```

**Output:**

<img width="1194" height="722" alt="image" src="https://github.com/user-attachments/assets/b945aeb1-3d69-4946-ba79-0b09d97054a0" />


**Question 5**
---
Write a SQL statement to Increase the selling price by 15% in the products table where quantity in stock is less than 50 and supplier ID is 10.

Products Table 

name          type       
----------    ---------- 
product_id     INT PRIMARY KEY        

product_name   VARCHAR(10) 

category       VARCHAR(50) 

cost_price     DECIMAL(10) 

sell_price     DECIMAL(10) 

reorder_lv     INT        

quantity       INT        

supplier_id    INT     

```sql
UPDATE Products
SET sell_price=sell_price*1.15
WHERE quantity<50 AND supplier_id IS 10;
```

**Output:**

<img width="1207" height="502" alt="image" src="https://github.com/user-attachments/assets/a1855441-793d-4070-bdd8-f413aa757985" />


**Question 6**
---
Write a SQL statement to Increase quantity of all products by 10% to adjust for surplus stock counted

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
UPDATE Products
SET quantity=quantity*1.10
```

**Output:**

<img width="1200" height="632" alt="image" src="https://github.com/user-attachments/assets/45bdb045-6052-4e43-b5be-400617e9f8aa" />


**Question 7**
---
Write a query to fetch details of employees with the address as “DELHI(DEL)” from EmployeeInfo table.

```sql
SELECT * FROM EmployeeInfo WHERE Address IS 'Delhi(DEL)';
```

**Output:**

<img width="1210" height="270" alt="image" src="https://github.com/user-attachments/assets/1e0bcc8f-9318-44ef-8b89-2841948e8e12" />


**Question 8**
---
Write a SQL query to calculate the absolute value of the value1 column from the Calculations table.

```sql
SELECT id,value1,ABS(value1) AS absolute_value FROM Calculations;
```

**Output:**

<img width="1199" height="300" alt="image" src="https://github.com/user-attachments/assets/2cf0f419-a37e-422d-ac9d-64b726ac1526" />


**Question 9**
---
Write a SQL query to Select all patients who was admitted in hospital for more than 3 days.

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
SELECT first_name,last_name,(julianday(discharge_date)-julianday(admission_date)+1) AS no_of_days FROM Patients WHERE no_of_days>3;
```

**Output:**

<img width="1198" height="335" alt="image" src="https://github.com/user-attachments/assets/361adc45-8939-42b0-87ec-c6624e9838a9" />


**Question 10**
---
write a SQL query to find details of all orders with a purchase amount less than 200 or exclude orders with an order date greater than or equal to '2012-02-10' and a customer ID less than 3009. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

```sql
SELECT ord_no,purch_amt, ord_date, customer_id, salesman_id FROM orders WHERE purch_amt<200 OR NOT (ord_date>='2012-02-10' AND customer_id<3009);
```

**Output:**

<img width="1206" height="478" alt="image" src="https://github.com/user-attachments/assets/18dbc13a-0de0-498b-882d-3667759965ac" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
