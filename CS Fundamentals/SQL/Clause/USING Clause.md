- If the **column names are same**, then instead of using ON Clause we can use USING Clause
```mysql
SELECT 
	o.order_id,
	c.first_name,
	sh.name AS shipper
FROM orders o
JOIN customers c
	-- ON o.customer_id = c.customer_id
	USING (customer_id) -- instead of above ON condition, we can use USING
LEFT JOIN shippers sh
	USING (shipper_id)
```

```mysql
SELECT *
FROM order_items oi
JOIN order_item_notes oin
	-- ON oi.order_id = oin.order_id AND
		-- oi.product_id = oin.product_id
	USING (order_id, product_id)
```