

>[!important]
>LIMIT x, y => represents skip 1st x records and then take y records

```
```mysql
SELECT *
FROM customers
LIMIT 3 -- returns only the provided top no.of data
		-- If provide a num where num > size of data, then it reurns all the 
		-- available data 
```

>[!note] 
>The LIMIT clause should always come at the end.
>Maintaining the order of clauses is important in Mysql

Ex: Get 3 most loyal customers
```mysql
SELECT *
FROM customers
ORDER BY points DESC
LIMIT 3 
```