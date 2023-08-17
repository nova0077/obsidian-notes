
```mysql
USE sql_store;

SELECT *          -- returns all the columns
FROM customers
WHERE customer_id = 1
ORDER BY first_name
```
It gives all the columns in the customers table whose id is 1 in an ordered way.

- We can use arithmetic expressions and display them directly using query
- We can modify the column name using **ALIAS** keyword
- if you want to add space to your column name using alias, you can keep it in the quotes 'discount factor'
```mysql
SELECT 
	first_name, 
	last_name, 
	(points*10)+100 AS discount -- 'discount factor'
FROM customers
```


- DISTINCT keyword is used to get unique elements
```mysql
SELECT DISTINCT state
FROM customers
```
