## Updating a Single Row

```Mysql
UPDATE invoices
SET payment_total =10, payment_date = '2019-03-01'
WHERE invoice_id=1
```

Updates values in invoices which has "invoice_id"=3 to 50% of total and date to "due_date"
```Mysql
UPDATE invoices
SET 
	payment_total = invoice_total*0.5, 
	payment_date = due_date
WHERE invoice_id=3
```

## Update Multiple Records

Instead of updating only one invoice, we are updating all the invoices of client_id in range `[3, 4]` in invoices table
```Mysql
UPDATE invoices
SET
	payment_total = invoice_total*0.5,
	payment_date = due_date
WHERE client_id IN (3,4)
```

Ex: Write a SQL statement to give any customers born before 1990 50 extra points
```Mysql
UPDATE customers
SET
	points = points + 50
WHERE birth_date < '1990-01-01'
```

## Using SubQueries in Update
>[!info]
>SUBQUERY => A subquery is a select statement which is inside another SQL statement

Suppose we know only the client_name, and we want to update invoices table with client_id.
```Mysql
UPDATE invoices
SET
	payment_total = invoice_total*0.5,
	payment_date = due_date
WHERE client_id IN 
(
	SELECT client_id
	FROM clients
	WHERE name = "Myworks"
)
```