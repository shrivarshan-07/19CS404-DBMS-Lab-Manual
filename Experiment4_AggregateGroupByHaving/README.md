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
How many patients have insurance coverage valid in each year?

Sample table:Insurance Table
```sql
select strftime('%Y',validityperiod) as ValidityYear,count(patientid) as TotalPatients
from Insurance group by ValidityYear;
```

**Output:**

<img width="691" height="367" alt="Screenshot 2026-09-02 123939" src="https://github.com/user-attachments/assets/69b13ee9-9f6d-4620-8a66-0f76fdc84440" />

**Question 2**
---
How many prescriptions were written by each doctor?

Sample tablePrescriptions Table

```sql
select DoctorID, count(*) as TotalPrescriptions
from Prescriptions group by DoctorID;
```

**Output:**

<img width="791" height="736" alt="Screenshot 2026-09-02 124016" src="https://github.com/user-attachments/assets/a82630e5-5fbb-46c6-9274-2c3b810ba1b1" />

**Question 3**
---
How many prescriptions were written in each frequency category (e.g., once daily, twice daily)?
```sql
select Frequency, count(*) as TotalPrescriptions 
from Prescriptions group by Frequency;
```

**Output:**

<img width="761" height="515" alt="Screenshot 2026-09-02 124106" src="https://github.com/user-attachments/assets/d49ead2d-d15e-425b-907c-85587f63f018" />

**Question 4**
---
Write a SQL query to find the difference between the maximum and minimum price of fruits?
```sql
select MAX(price) - MIN(price) as price_diff
from fruits;
```

**Output:**

<img width="381" height="295" alt="Screenshot 2026-09-02 124145" src="https://github.com/user-attachments/assets/7fb29343-b55e-44fb-9590-d5610cccd6a5" />

**Question 5**
---
Write a SQL query to find the youngest employee in the company?
```sql
select  name as Employee_Name , MIN(age) as Age
from employee;
```

**Output:**

<img width="592" height="296" alt="Screenshot 2026-09-02 124243" src="https://github.com/user-attachments/assets/609d5d32-3eba-46f6-a135-ccc002fed523" />

**Question 6**
---
Write a SQL query to Calculate the average income of the employees with names starting with 'A': 
```sql
select avg(income) as avg_income from employee where name LIKE 'A%';
```

**Output:**

<img width="407" height="300" alt="Screenshot 2026-09-02 124315" src="https://github.com/user-attachments/assets/9a5be429-7017-462f-9380-c8ac85b6a7e0" />

**Question 7**
---
Write a SQL query to calculate the total number of working hours of all employees
```sql
select SUM(workhour) as "Total working hours"
from employee1;
```

**Output:**

<img width="507" height="302" alt="Screenshot 2026-09-02 124347" src="https://github.com/user-attachments/assets/4df5735e-edeb-41a3-8121-c63d8d72474d" />

**Question 8**
---
Write the SQL query that accomplishes the selection of average price for each category from the "products" table and includes only those products where the average price falls between 10 and 15.
```sql
select category_id, AVG(Price) from  products group by category_id having AVG(price) 
between 10 and 15;
```

**Output:**

<img width="577" height="323" alt="Screenshot 2026-09-02 124421" src="https://github.com/user-attachments/assets/ebf7f32f-0cb9-42ac-a82f-af33438ec136" />

**Question 9**
---
Write the SQL query that accomplishes the selection of total number of products for each category from the "products" table, and includes only those products where the minimum category ID is less than 3.
```sql
select category_id,count(product_name) from products
group by category_id
having MIN(category_id) <3;
```

**Output:**

<img width="737" height="352" alt="Screenshot 2026-09-02 124504" src="https://github.com/user-attachments/assets/a674b370-de5e-4283-b91c-be0821d2bfdc" />

**Question 10**
---
Write the SQL query that achieves the selection of product names and the maximum price for each category from the "products" table, and includes only those products where the maximum price is greater than 15.
```sql
select category_id,product_name, price as Price
from products group by category_id having MAX(Price) >15;
```

**Output:**

<img width="817" height="370" alt="Screenshot 2026-09-02 124543" src="https://github.com/user-attachments/assets/de4c2630-cb55-49bc-88a9-2f82d5b8ff88" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
