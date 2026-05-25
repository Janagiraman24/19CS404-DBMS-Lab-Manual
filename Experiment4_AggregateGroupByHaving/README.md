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
Write a SQL query to find the average length of names for people living in Chennai?

Table: customer

name        type
----------  ----------
id          INTEGER

name        TEXT   

city        TEXT

email       TEXT

phone       INTEGER

```sql
SELECT AVG(LENGTH(name)) AS avg_name_length FROM customer WHERE  city="Chennai";
```

**Output:**

<img width="1202" height="312" alt="image" src="https://github.com/user-attachments/assets/d3c35201-8574-4abb-997f-ea87cf94d359" />


**Question 2**
---
Write a SQL query to find the number of employees who are having the same age removing the duplicate values.

Sample table: employee

```sql
SELECT COUNT(DISTINCT(age)) AS COUNT FROM employee;
```

**Output:**

<img width="1202" height="309" alt="image" src="https://github.com/user-attachments/assets/16de4f8e-1361-43c5-ad1d-471deee6f844" />

**Question 3**
---
Write a SQL query to find the total income of employees aged 40 or above.

Table: employee

name        type
----------  ----------
id          INTEGER

name        TEXT

age         INTEGER

city        TEXT

income      INTEGER

```sql
SELECT SUM(income) AS total_income FROM employee WHERE age>=40;
```

**Output:**

<img width="1194" height="317" alt="image" src="https://github.com/user-attachments/assets/deab0778-e3c8-4197-94fd-3879fa01d5f4" />

**Question 4**
---
How many patients are there in each city?

Sample table: Patients Table


```sql
SELECT Address,COUNT(patientID) AS TotalPatients FROM Patients GROUP BY Address;
```

**Output:**

<img width="1199" height="415" alt="image" src="https://github.com/user-attachments/assets/e97242d1-045a-40b4-b371-9eba4ccf97fb" />

**Question 5**
---
What is the total number of medications prescribed for each patient?

Sample tablePrescriptions Table


```sql
SELECT PatientID,COUNT(Medication) AS TotalMedications FROM Prescriptions GROUP BY PatientID;
```

**Output:**

<img width="1205" height="766" alt="image" src="https://github.com/user-attachments/assets/1525cda8-2737-4c38-9087-93c691833356" />

**Question 6**
---
How many patients are there in each age group category (e.g., under 20, 20-30, 30-40, etc.)?

Sample table: Patients Table


```sql
SELECT 
    CASE 
    WHEN strftime("%Y","2025-01-01")-strftime("%Y",DateOfBirth) BETWEEN 20 AND 30 THEN '20-30'
    WHEN strftime("%Y","2025-01-01")-strftime("%Y",DateOfBirth) BETWEEN 31 AND 40 THEN '31-40'
    WHEN strftime("%Y","2025-01-01")-strftime("%Y",DateOfBirth) BETWEEN 41 AND 50 THEN '41-50'
    ELSE 'Above 50'
    END AS AgeGroup,
    COUNT(*) AS TotalPatients
FROM Patients
GROUP BY AgeGroup
ORDER BY AgeGroup;
```

**Output:**

<img width="1218" height="460" alt="image" src="https://github.com/user-attachments/assets/357c4046-76c0-4c54-986e-9ccd353665fd" />

**Question 7**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the maximum work hours for each date, and excludes dates where the maximum work hour is not greater than 12.

Sample table: employee1

```sql
SELECT jdate,MAX(workhour) AS "MAX(workhour)" FROM employee1 GROUP BY jdate HAVING MAX(workhour)>12;
```

**Output:**

<img width="1205" height="393" alt="image" src="https://github.com/user-attachments/assets/a62eba0b-118c-49b1-b115-ed5f84563a0b" />

**Question 8**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the average work hours for each date, and excludes dates where the average work hour is not less than 10.

Sample table: employee1


```sql
SELECT jdate,AVG(workhour) AS "AVG(workhour)" FROM employee1 GROUP BY jdate HAVING AVG(workhour)<10;
```

**Output:**

<img width="1195" height="337" alt="image" src="https://github.com/user-attachments/assets/2d0b3d84-de3a-49a6-b97c-6e93a1f50a1b" />

**Question 9**
---
Write the SQL query that achieves the grouping of data by city, calculates the total income for each city, and includes only those cities where the total income sum is greater than 200,000.

Sample table: employee

```sql
SELECT city,SUM(income) AS Income FROM employee GROUP BY city HAVING Income>200000;
```

**Output:**

<img width="1198" height="538" alt="image" src="https://github.com/user-attachments/assets/bacac462-0e4c-452f-bfa1-92de6c6c7b04" />

**Question 10**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the minimum work hours for each date, and excludes dates where the minimum work hour is not less than 10.

Sample table: employee1
```sql
SELECT jdate,MIN(workhour) AS "MIN(workhour)" FROM employee1 GROUP BY jdate HAVING MIN(workhour)<10;
```

**Output:**

<img width="1212" height="452" alt="image" src="https://github.com/user-attachments/assets/64cb0534-fd46-4e0d-b2d1-81a1516667a2" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
