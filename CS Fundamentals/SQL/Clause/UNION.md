We can combine also combine results from multiple queries using UNION
EX: We want to set the orders of this year to "ACTIVE" and previous year as "ARCHIVED" and want to show them

```mysql
SELECT
	order_id,
	order_date,
	'Active' AS status
FROM orders
WHERE order_date >= '2019-01-01'
UNION -- we combine the results of the 2 queries using UNION
SELECT
	order_id,
	order_date,
	'Archived' AS status
FROM orders
WHERE order_date < '2019-01-01'
```

>[!note]
> - The number of columns that each query returns must be equal otherwise we get an error.
> - The name of the column will be the column name of the first query.
> - We can also combine the data from different tables.

EX: write a query to give the customers rank according to their points.
`< 2000 => bronze`
`2000 - 3000 => silver`
`> 3000 => gold `

```mysql
SELECT
	customer_id,
	first_name,
	points,
	'Bronze' AS type
FROM customers
WHERE points < 2000 
UNION
SELECT
	customer_id,
	first_name,
	points,
	'Silver' AS type
FROM customers
-- WHERE points >= 2000 AND points < 3000
WHERE points BETWEEN 2000 AND 3000
UNION
SELECT
	customer_id,
	first_name,
	points,
	'GOLD' AS type
FROM customers
WHERE points > 3000 
ORDER BY first_name
```



