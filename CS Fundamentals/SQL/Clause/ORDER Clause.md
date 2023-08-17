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

