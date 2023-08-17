We use this join to combine every record in the left table to every record in the right table
```mysql
SELECT 
	c.first_name AS customer,
	p.name AS product
FROM customers c
CROSS JOIN products p  -- explicit syntax
ORDER BY c.first_name

-- can also be written as
FROM customers c, orders o -- implicit syntax
```