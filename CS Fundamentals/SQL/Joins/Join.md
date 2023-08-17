- If you want to connect 2 tables, we use joins
	for example: order_details in a table and customer details in another table,
	now you want to know the customer name for that particular order.
	We use inner join
	
>[!Note] 
>For INNER JOIN "INNER" keyword is optional
 
``` mysql
SELECT order_id, first_name, last_name
FROM orders
JOIN customers 
	ON orders.customer_id = customers.customer_id
```

>[!important]
>we cannot just simply write customer_id in the select clause,
>because we need to define which table it belongs to, because both customers and orders table contains it

- Instead of writing the table names repeatedly, we can use alias to simplify our code
>[!note]
>If we use alias, then we should use the same alias for the rest of the code, otherwise we get errors

```mysql
SELECT order_id, o.customer_id, first_name, last_name
FROM orders o
JOIN customers c
	ON o.customer_id = c.customer_id
```

>[!Imp]
>If you want to join tables across different databases, you should mention the other database before the table name. `sql_store.order_items oi`


## SELF JOINS

- To join in the same table itself. we have to use different alias for the table name.

Ex: Given a table "employees" where we have employe data and "reports_to" column (manager_id). now write a query to get the name of the manager for each employee.
The manager itself an employee
```mysql
USE sql_hr;

SELECT
	e.employee_id,
	e.first_name AS employe,
	m.first_name AS manager
FROM employees e
JOIN employees m
	ON e.reports_to == m.employee_id
```


## Joining MULTIPLE TABLES 

Ex: order_statuses => order_status_id, name
	 orders => order_id, customer_id, order_date, status
	 customers => customer_id, customer_name

```mysql
USE sql_store;

SELECT
	o.order_id,
	o.order_date,
	c.first_name,
	c.last_name,
	os.name AS "status"
FROM orders o
JOIN customers c
	ON o.customer_id = c.customer_id
JOIN order_statuses os
	ON o.statuses = os.order_status_id
```


## Compound Join Conditions

- There may be some duplicates values in that particular column, so we consider **composite primary key** (a table with multiple primary keys) in this case.
```mysql
SELECT *
FROM order_items oi
JOIN order_item_notes oin
	ON oi.order_id = oin.order_id
	AND oi.product_id = oin.product_id
```

## Implicit JOIN Syntax
- Join can also be done by `WHERE` clause
- If we don't write where clause it results in cross join.
- It is better to use explicit join syntax.
```Mysql
SELECT *
FROM orders o, customers c
WHERE o.customer_id = c.customer_id
```
