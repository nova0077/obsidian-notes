
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

