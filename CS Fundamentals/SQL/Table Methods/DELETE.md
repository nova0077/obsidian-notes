# Deleting Rows

```mysql
DELETE FROM invoices
WHERE client_id IN (
	SELECT *
	FROM clients
	WHERE name = 'Myworks'
)
```

# Restoring Databases

Goto FileMenu => SQL Scripts => Open create_databases script and execute it