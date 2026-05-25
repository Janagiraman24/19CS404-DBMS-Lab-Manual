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
Insert a book with ISBN 978-1234567890, Title Data Science Essentials, Author Jane Doe, Publisher TechBooks, and Year 2024 into the Books table.


```sql
INSERT INTO Books(ISBN,Title,Author,Publisher,Year)
VALUES('978-1234567890','Data Science Essentials','Jane Doe','TechBooks',2024);
```

**Output:**

<img width="1215" height="246" alt="image" src="https://github.com/user-attachments/assets/9e58bb4e-e015-4e14-9cb1-e7c8ab709a02" />


**Question 2**
---
Insert the following customers into the Customers table:

CustomerID  Name         Address     City        ZipCode
----------  -----------  ----------  ----------  ----------
302         Laura Croft  456 Elm St  Seattle     98101

303         Bruce Wayne  789 Oak St  Gotham      10001

```sql
INSERT INTO Customers(CustomerID,Name,Address,City,ZipCode)
VALUES(302,'Laura Croft','456 Elm St','Seattle',98101);
INSERT INTO Customers(CustomerID,Name,Address,City,ZipCode)
VALUES(303,'Bruce Wayne','789 Oak St','Gotham',10001);
```

**Output:**

<img width="1206" height="379" alt="image" src="https://github.com/user-attachments/assets/512e9fd6-d639-401b-a0f4-f6a7d32795c7" />


**Question 3**
---
Create a table named Employees with the following constraints:

EmployeeID should be the primary key.


FirstName and LastName should be NOT NULL.

Email should be unique.

Salary should be greater than 0.

DepartmentID should be a foreign key referencing the Departments table.

```sql
CREATE TABLE Employees(
    EmployeeID INTEGER PRIMARY KEY,
    FirstName TEXT NOT NULL,
    LastName TEXT NOT NULL,
    Email TEXT UNIQUE,
    Salary INTEGER CHECK (Salary>0),
    DepartmentID INTEGER,
    FOREIGN KEY(DepartmentID)
        REFERENCES Departments(DepartmentID)
);
```

**Output:**

<img width="1211" height="429" alt="image" src="https://github.com/user-attachments/assets/14b61f0a-acec-45f0-b82e-6a87b686999c" />


**Question 4**
---
Create a table named ProjectAssignments with the following constraints: 


AssignmentID as INTEGER should be the primary key.

EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).

ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).

AssignmentDate as DATE should be NOT NULL.

```sql
CREATE TABLE ProjectAssignments(
    AssignmentID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    ProjectID INTEGER,
    AssignmentDate DATE NOT NULL,
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID),
    FOREIGN KEY (ProjectID) REFERENCES Projects(ProjectID)
);
```

**Output:**

<img width="1210" height="297" alt="image" src="https://github.com/user-attachments/assets/97e90d11-c21b-4aee-bfc1-02e23fe69776" />


**Question 5**
---
Write a SQL Query  to add attribute ISBN as varchar(30) and domain_dept as varchar(30) in the table 'books'

```sql
ALTER TABLE books ADD COLUMN ISBN varchar(30);
ALTER TABLE books ADD COLUMN domain_dep varchar(30);
```

**Output:**

<img width="1204" height="392" alt="image" src="https://github.com/user-attachments/assets/a0bb1d16-8fb1-4d3b-9934-ac04788df333" />


**Question 6**
---
Create a table named Customers with the following columns:

CustomerID as INTEGER

Name as TEXT


Email as TEXT

JoinDate as DATETIME

```sql
CREATE TABLE Customers(
    CustomerID INTEGER,
    Name TEXT,
    Email TEXT,
    JoinDate DATETIME
);
```

**Output:**

<img width="1205" height="412" alt="image" src="https://github.com/user-attachments/assets/78655da7-0be0-4091-868c-fe8c93212896" />


**Question 7**
---
Create a new table named contacts with the following specifications:


contact_id as INTEGER and primary key.

first_name as TEXT and not NULL.

last_name as TEXT and not NULL.

email as TEXT.

phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.

```sql
CREATE TABLE contacts(
    contact_id INTEGER PRIMARY KEY,
    first_name TEXT NOT NULL,
    last_name TEXT NOT NULL,
    email TEXT,
    phone TEXT NOT NULL CHECK(LENGTH(phone)>=10)
);
```

**Output:**

<img width="1209" height="337" alt="image" src="https://github.com/user-attachments/assets/50a80222-2ff0-45eb-8aa9-a8cb39ec517d" />


**Question 8**
---
Write an SQL query to add two new columns, department_id and manager_id, to the table employee with datatype of INTEGER. The manager_id column should have a default value of NULL.
```sql
ALTER TABLE employee ADD COLUMN department_id INTEGER;
ALTER TABLE employee ADD COLUMN manager_id INTEGER DEFAULT NULL;
```

**Output:**

<img width="1198" height="318" alt="image" src="https://github.com/user-attachments/assets/0c0e64cf-1512-437f-9f14-03cd4a7c3df2" />


**Question 9**
---
Create a table named Orders with the following columns:

OrderID as INTEGER


OrderDate as TEXT

CustomerID as INTEGER

```sql
CREATE TABLE Orders(
    OrderID INTEGER,
    OrderDate TEXT,
    CustomerID INTEGER
);
```

**Output:**

<img width="1202" height="381" alt="image" src="https://github.com/user-attachments/assets/1f3ff928-8861-4e3f-b28c-ea3c70f87a07" />


**Question 10**
---
Insert the below data into the Customers table, allowing the City and ZipCode columns to take their default values.

CustomerID  Name          Address
----------  ------------  ----------
304         Peter Parker  Spider St      

Note: The City and ZipCode columns will use their default values.

```sql
INSERT INTO Customers(CustomerID,Name,Address)
VALUES(304,'Peter Parker','Spider St');
```

**Output:**

<img width="1200" height="315" alt="image" src="https://github.com/user-attachments/assets/c28c2e1d-7afa-4acc-94fa-ad354c1d8597" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
