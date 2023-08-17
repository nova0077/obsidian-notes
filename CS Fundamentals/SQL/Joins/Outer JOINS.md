INNER JOINS => does not display NULL values, only returns the valid data rows
OUTER JOINS => returns all the data, if the value does not exist it returns NULL values

```Mysql
SELECT 
	c.customer_id,
	c.first_name,
	o.order_id
FROM customers c
JOIN orders o
	ON c.customer_id = o.customer_id
ORDER BY c.customer_id
```
This code returns only the customers with order_id.

>[!important]
> - When we use LEFT JOIN all the records from the left table are returned irrespective of the condition
> - When we use RIGHT JOIN all the records from the right table are returned irrespective of the condition

```mysql
SELECT 
	c.customer_id,
	c.first_name,
	o.order_id
FROM customers c
LEFT JOIN orders o
	ON c.customer_id = o.customer_id
ORDER BY c.customer_id
```
This code returns all the customers with or without order_id

```mysql
```mysql
SELECT 
	c.customer_id,
	c.first_name,
	o.order_id
FROM customers c
RIGHT JOIN orders o
	ON c.customer_id = o.customer_id
ORDER BY c.customer_id
```
This query returns all the customers who are in the orders table.
This result will be same as the INNER JOIN result, because only customers with order_id are placed in the orders table.

>[!note]
> We can use RIGHT OUTER JOIN instead of RIGHT JOIN also

## SELF OUTER JOIN
Write a query that specifies the manager for each employee
```mysql
SELECT *
FROM employees e
JOIN employees m
	on e.reports_to = m.employee_id
```
We will get the records for all the employees, except the CEO ( whose reports_to = NULL)
So we use here OUTER JOIN.
```mysql
SELECT
	e.employee_id,
	e.first_name,
	m.first_name AS manager
FROM employees e
LEFT JOIN employee m
	on e.reports_to = m.employee_id
```