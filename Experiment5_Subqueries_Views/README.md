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
--
Write a SQL query to Retrieve the medications with dosages equal to the lowest dosage

Medications Table



```sql
SELECT medication_id AS medic,medication_name,dosage FROM Medications WHERE dosage<=(SELECT MIN(dosage) FROM Medications);
```

**Output:**

<img width="1197" height="393" alt="image" src="https://github.com/user-attachments/assets/345ba10b-e2d9-4803-b633-53e5b607dd59" />

**Question 2**
---
From the following tables write a SQL query to find the order values greater than the average order value of 10th October 2012. Return ord_no, purch_amt, ord_date, customer_id, salesman_id.

Note: date should be yyyy-mm-dd format

ORDERS TABLE

name            type
----------     ----------
ord_no          

purch_amt    real

ord_date       text

customer_id  int

salesman_id  int

```sql
SELECT *
FROM orders
WHERE purch_amt>(SELECT AVG(purch_amt) FROM orders WHERE ord_date='2012-10-10');
```

**Output:**

<img width="1200" height="485" alt="image" src="https://github.com/user-attachments/assets/46593bde-4e3f-4721-a0a8-d885044865cd" />


**Question 3**
---
From the following tables, write a SQL query to find those salespeople who earned the maximum commission. Return ord_no, purch_amt, ord_date, and salesman_id.

salesman table

name             type
---------------  ---------------
salesman_id      numeric(5)

name                 varchar(30)

city                    varchar(15)

commission       decimal(5,2)


orders table

name             type
---------------  --------
order_no         int

purch_amt        real

order_date       text

customer_id      int

salesman_id      int

```sql
SELECT ord_no, purch_amt, ord_date, salesman_id FROM orders 
WHERE salesman_id IN (SELECT salesman_id FROM salesman WHERE commission=(SELECT MAX(commission) FROM salesman));
```

**Output:**

<img width="1194" height="474" alt="image" src="https://github.com/user-attachments/assets/3e8c807a-d9a3-45d2-b1e9-d6e83f850aa4" />

**Question 4**
---
Write a query to display all the customers whose ID is the difference between the salesperson ID of Mc Lyon and 2001.

salesman table

name             type
---------------  ---------------
salesman_id      numeric(5)

name                 varchar(30)

city                    varchar(15)

commission       decimal(5,2)

customer table

name         type
-----------  ----------

customer_id  int

cust_name    text

city         text

grade        int

salesman_id  int

```sql
SELECT * FROM customer 
WHERE customer_id IN (SELECT (salesman_id-2001) FROM salesman WHERE name="Mc Lyon");
```

**Output:**

<img width="1204" height="339" alt="image" src="https://github.com/user-attachments/assets/07b1eff7-28b8-4089-9b91-0d7c2234923a" />

**Question 5**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is LESS than $2500.

Sample table: CUSTOMERS

```sql
SELECT * FROM CUSTOMERS WHERE salary<2500;
```

**Output:**

<img width="1192" height="452" alt="image" src="https://github.com/user-attachments/assets/ac51fef4-e332-4496-85a9-ebc4ae362a63" />

**Question 6**
---
Write a SQL query that retrieves the names of students and their corresponding grades, where the grade is equal to the minimum grade achieved in each subject.

Sample table: GRADES

```sql
SELECT student_name,grade FROM GRADES g1 WHERE GRADE =(SELECT MIN(grade) FROM GRADES g2 WHERE g1.subject=g2.subject);
```

**Output:**

<img width="1205" height="442" alt="image" src="https://github.com/user-attachments/assets/1a7ff589-f30f-4c2f-a5c3-1790e4b42328" />

**Question 7**
---
Write a SQL query to Find employees who have an age less than the average age of employees with incomes over 1 million

Employee Table

name             type

------------   ---------------

id                    INTEGER

name              TEXT

age                 INTEGER

city                 TEXT

income           INTEGER

```sql
SELECT * FROM Employee WHERE age<(SELECT AVG(age) FROM Employee WHERE income>1000000);
```

**Output:**

<img width="1203" height="426" alt="image" src="https://github.com/user-attachments/assets/4bb91d0f-6e3b-4fc9-b9dc-68e3d2278c3c" />

**Question 8**
---
Write a SQL query to Retrieve the names and cities of customers who have the same city as customers with IDs 3 and 7

SAMPLE TABLE: customer

name             type
---------------  ---------------
id               INTEGER

name             TEXT

city             TEXT

email            TEXT

phone            INTEGER

```sql
SELECT name,city FROM customer WHERE city IN (SELECT city FROM customer WHERE id IN (3,7));
```

**Output:**

<img width="1205" height="443" alt="image" src="https://github.com/user-attachments/assets/59409234-dc88-4d9f-9410-11d838967149" />

**Question 9**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose AGE is LESS than $30

Sample table: CUSTOMERS
```sql
SELECT * FROM CUSTOMERS WHERE AGE<30;
```

**Output:**

<img width="1199" height="587" alt="image" src="https://github.com/user-attachments/assets/146581f5-301a-4b7c-9c5b-f5d3aa91c615" />

**Question 10**
---
From the following tables write a SQL query to find all orders generated by London-based salespeople. Return ord_no, purch_amt, ord_date, customer_id, salesman_id.

```sql
SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id FROM Orders WHERE salesman_id IN (SELECT salesman_id FROM Salesman WHERE city='London');
```

**Output:**

<img width="1204" height="435" alt="image" src="https://github.com/user-attachments/assets/41cd2cd3-bf2e-494d-9619-b5fc49800442" />


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
