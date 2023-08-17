- The database engine will automatically joins them based in the common columns
```mysql
SELECT
	o.order_id,
	c.first_name
FROM orders o
NATURAL JOIN customers c
```