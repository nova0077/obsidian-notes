## Inserting a Single Row
```mysql
INSERT INTO customers
VALUES (
	DEFAULT, 
	'John', 
	'Smith', 
	'1990-01-01',
	NULL, 
	'address',
	'city',
	'CA',
	DEFAULT	
)

```

>[!note] 
> - We can also choose the columns that we want to add values and specify them like below, for this we no need to mention DEFAULT or NULL

```mysql
INSERT INTO customers (
	first_name,
	last_name,
	birth_date,
	address,
	city,
	state
)
VALUES( 
	'John', 
	'Smith', 
	'1990-01-01',
	'address',
	'city',
	'CA',
)
```

## Inserting Multiple Rows

```mysql
INSERT INTO shippers (name)
VALUES 
	('Shipper1'),
	('Shipper2'),
	('Shipper3')
```

>[!important]
>The auto increment function, increments the value by 1,
>But consider this case, if we insert 5 values and delete last 2, and insert a new value using auto increment, the new value will be 6 not 4.


## Inserting Hierarchical Rows

**INSERT INTO MULTIPLE TABLES**
orders => parent table,
order_items => child table
One row in the orders table can have multiple values in order_items

```Mysql
INSERT INTO orders(customer_id, order_date, status)
VALUES (1, '2019-01-02', 1);

INSERT INTO order_items
VALUES 
	(LAST_INSERT_ID(), 1, 1, 2.95)
	(LAST_INSERT_ID(), 2c, 1, 2.95)
```

>[!info]
>LAST_INSERT_ID() => it is a function that returns the id of the last inserted value
