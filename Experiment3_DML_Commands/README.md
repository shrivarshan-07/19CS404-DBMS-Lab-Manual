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
Write a SQL statement to change the email column of employees table with 'Unavailable' for all employees in employees table.

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
 

For example:

Test	Result
SELECT EMPLOYEE_ID,FIRST_NAME,EMAIL FROM EMPLOYEES LIMIT 2;
EMPLOYEE_ID  FIRST_NAME  EMAIL
-----------  ----------  -----------
100          Steven      Unavailable
101          Neena       Unavailable

```sql
UPDATE employees
SET email = 'Unavailable';
```

**Output:**

<img width="1265" height="826" alt="image" src="https://github.com/user-attachments/assets/8c4f6686-df89-4fd7-af8c-d6a8e77d3b01" />

**Question 2**
---
 Write a SQL statement to Increase the selling price per unit by 5% for product ID 15 who's sale is on '2023-01-31'.

sales(sale_id,sale_date,product_id,quantity,sell_price,total_sell_price)

```sql
UPDATE sales
SET sell_price = sell_price*1.05
WHERE product_id = 15 AND sale_date = '2023-01-31';
```

**Output:**

<img width="1282" height="850" alt="image" src="https://github.com/user-attachments/assets/f7594811-e2e6-469e-82bc-3931eb251fe1" />

**Question 3**
---
Write a SQL statement to Update the per_unit_price to 25 and total_price accordingly in purchases table where purchase_date is '2022-08-15' and product_id is 12.

<img width="293" height="278" alt="image" src="https://github.com/user-attachments/assets/220c3cd3-3925-44a3-ac82-48a95a501024" />

```sql
UPDATE purchases
SET per_unit_price = 25 , total_price = quantity * 25
WHERE product_id = 12;
```

**Output:**

<img width="1285" height="858" alt="image" src="https://github.com/user-attachments/assets/24ce5028-60b7-45e2-8e15-b873630200d2" />

**Question 4**
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
update EMPLOYEES
set salary =salary+500,
    email='updated'
where job_id = 'SA_REP'
    and commission_pct > 0.15;
```

**Output:**

<img width="1277" height="855" alt="image" src="https://github.com/user-attachments/assets/50439b99-2d7f-4385-afce-9e65be192bf0" />

**Question 5**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' has exactly 6 characters.

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
```sql
delete from customer
where length(cust_name)=6;
```

**Output:**

<img width="1276" height="605" alt="image" src="https://github.com/user-attachments/assets/ae3b2b73-e927-4485-89bd-bf1f1f70db83" />

**Question 6**
---
Write a SQL query to Delete customers with following conditions

'CUST_COUNTRY' is not in a list of specified countries ('UK', 'USA', 'Canada')
'GRADE' is greater than or equal to 3
Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |

```sql
delete from customer 
where cust_country not in('UK','USA','Canada')
and grade>=3;
```

**Output:**

<img width="1277" height="813" alt="image" src="https://github.com/user-attachments/assets/6348caa5-9288-438f-848a-338b55770b95" />

**Question 7**
---
    Write a SQL query to locate the details of customers with grade values above 100. Return customer_id, cust_name, city, grade, and salesman_id.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id

-------------+----------------+------------+-------+-------------

        3002 | Nick Rimando   | New York   |   100 |        5001

        3007 | Brad Davis     | New York   |   200 |        5001

        3005 | Graham Zusi    | California |   200 |        5002
        
```sql
SELECT customer_id, cust_name,city,grade,salesman_id
FROM customer
WHERE grade>100;
```

**Output:**

<img width="1295" height="833" alt="image" src="https://github.com/user-attachments/assets/be557265-667e-4423-98dd-00b93b647cb3" />

**Question 8**
---
Write a query to list all products that have a discounted price between $100 and $250. Return product_id, original_price, discount_percentage, and discounted_price from products table.
```sql
select product_id,original_price,discount_percentage,(original_price *(1-discount_percentage)) as discounted_price
from products
where (original_price * (1-discount_percentage)) between 100 and 250;
```

**Output:**

<img width="1277" height="767" alt="image" src="https://github.com/user-attachments/assets/630f42ea-8b3e-4257-91cd-8786450b3f39" />

**Question 9**
---
Write a SQL query to categorize value1 in the Calculations table as 'High' if it is greater than 50, otherwise 'Low'.

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
select id,value1,
case 
when value1>50 then 'High'
else 'Low'
end as value_category
from Calculations;
```

**Output:**

<img width="1291" height="788" alt="image" src="https://github.com/user-attachments/assets/e9b2cf5b-89e5-49c5-9d33-1f1eae34b4aa" />

**Question 10**
---
write a SQL query to find details of all orders with a purchase amount less than 200 or exclude orders with an order date greater than or equal to '2012-02-10' and a customer ID less than 3009. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005
70002       65.26       2012-10-05  3002         5001
```sql
select ord_no,purch_amt, ord_date,customer_id,salesman_id
from orders
where purch_amt<200
or not (ord_date >= '2012-02-10' and customer_id<3009);
```

**Output:**

<img width="1272" height="835" alt="image" src="https://github.com/user-attachments/assets/ef94799b-eb52-4461-bf0a-f3a7bb614edc" />

## GRADE 
<img width="772" height="266" alt="image" src="https://github.com/user-attachments/assets/399e20a9-ee81-4bdc-b218-be21a5bbab92" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
