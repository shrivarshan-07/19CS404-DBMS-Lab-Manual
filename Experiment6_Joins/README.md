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
Write the SQL query that achieves the selection of all columns from the "patients" table, with an inner join on the "doctor_id" column, and includes a condition filtering for patients whose doctors have the first name 'John' and last name 'Smith'.
```sql
SELECT p.patient_id,
       p.first_name,
       p.last_name,
       p.date_of_birth,
       p.admission_date,
       p.discharge_date,
       p.doctor_id
FROM patients p
INNER JOIN doctors d
  ON p.doctor_id = d.doctor_id
WHERE d.first_name = 'John'
  AND d.last_name = 'Smith';
```

**Output:**

<img width="956" height="300" alt="image" src="https://github.com/user-attachments/assets/f2307751-fea4-4e50-bc1a-08e9db007b4a" />

**Question 2**
---
Write the SQL query that achieves the selection of all columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column and a condition filtering for salesman with the name 'Mc Lyon'.


```sql
SELECT c.customer_id,
       c.cust_name,
       c.city,
       c.grade,
       c.salesman_id
FROM customer c
LEFT JOIN salesman s
  ON c.salesman_id = s.salesman_id
WHERE s.name = 'Mc Lyon';
```

**Output:**

<img width="700" height="290" alt="image" src="https://github.com/user-attachments/assets/bd442fda-bc75-4578-a368-d3cce85ff028" />

**Question 3**
---
Write the SQL query that achieves the selection of admission dates from the "patients" table and surgery dates from the "surgeries" table, with an inner join on the "patient_id" column.


```sql
SELECT p.admission_date,
       s.surgery_date
FROM patients p
INNER JOIN surgeries s
  ON p.patient_id = s.patient_id;
```

**Output:**

<img width="660" height="495" alt="image" src="https://github.com/user-attachments/assets/5a7b82b4-5f65-453b-890b-46809976db9a" />

**Question 4**
---
Write the SQL query that achieves the selection of all columns from the "nurses" table (aliased as "n") and the "department_name" column from the "departments" table, with an inner join on the "department_id" column.

```sql
SELECT n.nurse_id,
       n.first_name,
       n.last_name,
       n.department_id,
       d.department_name
FROM nurses n
INNER JOIN departments d
  ON n.department_id = d.department_id;
```

**Output:**

<img width="732" height="427" alt="image" src="https://github.com/user-attachments/assets/09450033-f837-4b0d-99a3-63d39dc3349a" />

**Question 5**
---
From the following tables write a SQL query to display the customer name, customer city, grade, salesman, salesman city. The results should be sorted by ascending customer_id.  


```sql
SELECT c.cust_name,
       c.city,
       c.grade,
       s.name AS Salesman,
       s.city
FROM customer c
JOIN salesman s
  ON c.salesman_id = s.salesman_id
ORDER BY c.customer_id ASC;
```

**Output:**

<img width="707" height="752" alt="image" src="https://github.com/user-attachments/assets/a32a5f35-c868-4845-b13b-a07a32ee8c0b" />

**Question 6**
---
From the following tables write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.


```sql
SELECT o.ord_no,
       o.purch_amt,
       c.cust_name,
       c.city
FROM orders o
JOIN customer c
  ON o.customer_id = c.customer_id
WHERE o.purch_amt BETWEEN 500 AND 2000;
```

**Output:**

<img width="1207" height="417" alt="image" src="https://github.com/user-attachments/assets/7fc4aae2-b744-4381-a06b-a14060f11b0f" />

**Question 7**
---
SQL statement to generate a report with customer name, city, order number, order date, order amount, salesperson name, and commission to determine if any of the existing customers have not placed orders or if they have placed orders through their salesman or by themselves.


```sql
SELECT c.cust_name,
       c.city,
       o.ord_no,
       o.ord_date,
       o.purch_amt AS "Order Amount",
       s.name AS name,
       s.commission
FROM customer c
LEFT JOIN orders o
  ON c.customer_id = o.customer_id
LEFT JOIN salesman s
  ON o.salesman_id = s.salesman_id;
```

**Output:**

<img width="782" height="847" alt="image" src="https://github.com/user-attachments/assets/d22b23dc-add0-4429-87c4-8cd966c22671" />

**Question 8**
---
Write the SQL query that achieves the selection of all columns from the "salesman" table (aliased as "s"), with a left join on the "salesman_id" column and a condition filtering for customers with the name 'Fabian Johns'.


```sql
SELECT s.salesman_id,
       s.name,
       s.city,
       s.commission
FROM salesman s
LEFT JOIN customer c
  ON s.salesman_id = c.salesman_id
WHERE c.cust_name = 'Fabian Johns';
```

**Output:**

<img width="1022" height="281" alt="image" src="https://github.com/user-attachments/assets/853be3d3-debe-41e4-b994-0583afb2fb89" />

**Question 9**
---
Write a SQL statement to join the tables salesman, customer and orders so that the same column of each table appears once and only the relational rows are returned. 


```sql
SELECT o.ord_no,
       o.purch_amt,
       o.ord_date,
       c.cust_name,
       c.city AS customer_city,
       c.grade,
       s.name AS salesman_name,
       s.city AS salesman_city,
       s.commission
FROM orders o
JOIN customer c
  ON o.customer_id = c.customer_id
JOIN salesman s
  ON o.salesman_id = s.salesman_id;
```

**Output:**

<img width="961" height="817" alt="image" src="https://github.com/user-attachments/assets/518ca0c3-80fa-49c3-9b3a-90dab8252e25" />


**Question 10**
---
From the following tables write a SQL query to locate those salespeople who do not live in the same city where their customers live and have received a commission of more than 12% from the company. Return Customer Name, customer city, Salesman, salesman city, commission.  


```sql
SELECT c.cust_name AS "Customer Name",
       c.city AS "city",
       s.name AS "Salesman",
       s.city AS "city",
       s.commission
FROM customer c
JOIN salesman s
  ON c.salesman_id = s.salesman_id
WHERE c.city <> s.city
  AND s.commission > 0.12;

```

**Output:**

<img width="1185" height="462" alt="image" src="https://github.com/user-attachments/assets/60c67a8a-a0ce-43fa-b545-4faba9ca42d1" />


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
