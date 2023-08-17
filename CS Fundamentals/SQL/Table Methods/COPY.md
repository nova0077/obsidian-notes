## Creating a Copy Of a Table

```Mysql
CREATE TABLE orders_archived AS
SELECT * FROM orders -- subquery to create query
```

>[!info]
>- If you create a new table and assign it like mentioned above, MYSQL will ignore the attributes of the columns
>- TRUNCATE => only deletes the values inside a table

EX: If we want to add all the orders that are before 2019, 
```mysql
INSERT INTO orders_archived
SELECT *
FROM orders
WHERE order_date < '2019-01-01'
```

EX: you are having two tables invoices, clients. Create a new table with name, "invoice_archived" and replace "client_id" with "client_name" from clients table, and display only results which have "payment_date".
```mysql
CREATE TABLE invoices_archived AS
SELECT 
	i.invoice_id,
	i.number,
	c.client_name,
	i.invoice_total,
	i.payment_total,
	i.invoice_date,
	i.payment_date,
	due_date 
-- u can directly write due_date because clients table doesnot have column name with due_date
FROM invoices i
JOIN clients c
	USING (client_id) -- ON i.client_id = c.client_id
WHERE payment_date IS NOT NULL
```
