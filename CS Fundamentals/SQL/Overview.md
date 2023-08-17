- Database => A database is a collection of data stored in a format that can easily be accessed
- In order to manage our databases, we use software called DBMS.
- 
![[Pasted image 20230809160134.png]]

- Database
	1. Relational Databases: we store data in tables that are linked to each other using relationships. we use SQL to  work with these relational database.
	   Ex: MySQL, SQL Server, Oracle
	2. NoSQL: NoSQL systems don't understand SQL

## SQL COMMENT
- It is done by "--"
```mysql
USE sql_store;

SELECT * FROM customers
-- WHERE customer_id = 1 
```

##  SQL Select Clause

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

## Where Clause

>Note: <> represent not equal to in comparison

EX: Get the orders placed this year with points greater than 1000
```mysql
SELECT *
FROM orders
WHERE order_date >= '2023-08-11'  AND points>1000-- 'yyyy-mm-dd'
```

>Note: In logical operators, AND has more precedence than OR

## IN
```mysql
SELECT *
FROM Customers
WHERE state='VA' OR state='GA' OR state='FL'
```

the same code can be implemented easily with **IN** operator
```mysql
SELECT *
FROM Customers
WHERE state IN ('VA', 'FL', 'GA')
```

## BETWEEN

```Mysql
SELECT *
FROM customers
-- WHERE points >=1000 AND points<=3000
WHERE points BETWEEN 1000 AND 3000
```

## LIKE 
- Allows you to search any string patterns
>Note: '%' represents any number of chars in a string
>Ex: 'b%' returns strings starting with b

```mysql
SELECT * FROM customers
WHERE name LIKE '%b%' -- we can have any no.of chars before and after b
-- '%y' => last name ends with y
```

>Note: `"_"` represents single char
>EX: `"__y"` indicates 3 letter word ending with y


## REGEXP 
>[!important] 
>More powerful to search strings
>^ => represents the beginning of the string
>$ => represents end of the string
> `\` => represents or
> [ ] => represents any char inside it
> [ x - y] => represents any char in range [x, y]
> 

```MYsql
SELECT *
FROM customers
-- WHERE last_name LIKE '%field%'
REGEXP last_name REGEXP 'field' -- It is same as above
```

```mysql
SELECT *
FROM customers
WHERE last_name REGEXP '^field' -- starts with field
WHERE last_name REGEXP 'field$' -- ends with field
WHERE last_name REGEXP '^field|mac$' -- should either start with field or end    
									 -- with mac

WHERE last_name REGEXP '[gim]e' -- can have 'gi' or 'ie' or 'me' 
WHERE last_name REGEXP 'e[a-h]' -- can have any char from 'a' to 'h' before e
                                -- like 'ea', 'eb', 'ec', ...... 'eh'

```


## The IS NULL Operator
> NULL => absence of a value

```Mysql
SELECT *
FROM customers
WHERE phone IS NOT NULL
```

## The ORDER CLAUSE

> [!note]
> By default data is sorted according to "PRIMARY KEY"

```MYSQL
SELECT *
FROM customers
ORDER BY first_name -- by default ascending
ORDER BY frirst_name DESC -- will sort in descending
ORDER BY state, first_name -- will sort state, 2nd priority for firstname
```

>[!important]
>Order by 1, 2 => sorts the data according to column positions in the select statement.
>We can also use arithmetic expressions instead of col_names and col_nums


```MYsql
SELECT first_name, last_name
FROM customers
ORDER BY 1,2
-- Here orde by 1, 2 represents the first_name & last_name, (which are being used by the select clause)
```

EX: Sort the data according to the to the total price when quantity and unit_price of an item are given.
```Mysql
SELECT *, quantity*unit_price AS total_price
FROM order_items
WHERE order_id = 2;
-- ORDER BY quantity * unit_price DESC
ORDER BY total_price DESC;
```

>[!note] 
>VALID points in mysql

```mysql
SELECT first_name, last_name, 10 AS points
FROM customers
ORDER BY date
-- 1) we can select any columns and sort them according to any of the columns
-- 2) we can alias any value which is not a column in our table (10) using alias
-- Many other softwares will give errors for these
```


## The LIMIT clause

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