# Introduction to SQL

## Topics Covered
1. Tables
2. Relationships
3. Joins
4. Subqueries
5. Regular Expressions

## Key points to remember
1. Order of Clause is important
2. Query is case insensitive
3. -- comment in sql

```sql
SELECT *
FROM Customers
WHERE customer_id=1
ORDER BY first_name
```

```sql
SELECT last_name, first_name, points, points * 10 FROM Customers
```
## Alias

```sql
SELECT
  first_name,
  points,
  (points + 10) * 100 AS discount_factor
FROM Customers
```

## Distinct

```sql
SELECT DISTINCT state
FROM Customers
```

## WHERE

```sql
SELECT *
FROM Customers
WHERE birth_date > '1990-01-01'
```

> Date format in SQL '1990-01-01' -> 'year-month-day'
## Where clause conditions 
```
<> ---> Not Equal
!= ---> Not Equal
=  ---> Equal
>= ---> Greater than Equal
<= ---> Less than Equal
<  ---> Less than
>  ---> Greater than
```
## AND, OR and NOT Operators
> Combining multiple search conditions

```sql
SELECT *
FROM Customers
WHERE birth_date > '1990-01-01' AND points > 1000

SELECT *
FROM Customers
WHERE birth_date > '1990-01-01' OR points > 1000 AND state = 'VA'
```

> AND has higer precedence over OR

```sql
SELECT *
FROM Customer
WHERE NOT(birth_date > '1990-01-01' AND points > 1000)
```
## IN
> Used to match the values within a list

```sql
SELECT *
FROM Customers
WHERE state IN('VA', 'FL', 'GA')
```

```sql
SELECT *
FROM Customers
WHERE state NOT IN('VA', 'FL', 'GA')
```

```sql
SELECT *
FROM Customers
WHERE state='VA' OR state='FL' OR state='GA'
```

```sql
SELECT * FROM products
WHERE quantity_in_stock IN (49, 38, 72);
```

## BETWEEN

```sql
USE sql_store;

SELECT * 
FROM customers
WHERE points >= 1000 AND points <= 3000;

SELECT *
FROM customers
WHERE points BETWEEN 1000 AND 3000;

SELECT *
FROM customers
WHERE birth_date BETWEEN '1990-01-01' AND '2000-01-01';
```

## LIKE

> % any number of characters

> _ single character

```sql
-- Customers whose last name starts with B
SELECT *
FROM customers
WHERE last_name LIKE 'b%';

-- Customers with name starts with brush
SELECT *
FROM customers
WHERE last_name LIKE 'brush%';

-- Customers with name contains letter b
SELECT *
FROM customers
WHERE last_name LIKE '%b%';

-- Customers with name only two charaters and ends with y
SELECT *
FROM customers
WHERE last_name LIKE '_y';

-- Customers with name with b and 4 characters in between can be anything and ends with letter y
SELECT *
FROM customers
WHERE last_name LIKE 'b____y';

-- Excercise
SELECT *
FROM customers
WHERE address LIKE '%TRAIL%' OR address LIKE '%AVENUE%';

SELECT *
FROM customers
WHERE phone LIKE '%9'
```
## REGEXP

> ^ beginning

> $ end

> | logical or

> [abdc] charcters in the set

> [a-f] characters ranging from a-f

```sql
-- last name containing feild
SELECT *
FROM customers
WHERE last_name REGEXP 'field';

-- ^ must begin with string
SELECT *
FROM customers
WHERE last_name REGEXP '^field';

-- $ must begin with string
SELECT *
FROM customers
WHERE last_name REGEXP 'field$';

-- multiple search patterns
SELECT *
FROM customers
WHERE last_name REGEXP 'field|mac|rose';

-- should end with field or can contains mac or rose
SELECT *
FROM customers
WHERE last_name REGEXP 'field$|mac|rose';

-- starts with given set of characters and ends with letter e
SELECT *
FROM customers
WHERE last_name REGEXP '[gim]e';

-- characters ranging from a to h and ends with e
SELECT *
FROM customers
WHERE last_name REGEXP '[a-h]e';

-- Exercise

SELECT * 
FROM customers
WHERE first_name REGEXP 'ELKA|AMBUR';

SELECT * 
FROM customers
WHERE last_name REGEXP 'EY$|ON$';

SELECT * 
FROM customers
WHERE last_name REGEXP '^my|se';

SELECT * 
FROM customers
WHERE last_name REGEXP 'b[ru]';
```

## NULL OPERATOR

```sql
SELECT *
FROM customers
WHERE phone IS NULL;

SELECT *
FROM customers
WHERE phone IS NOT NULL;

SELECT *
FROM orders
WHERE shipped_date IS NULL OR shipper_id IS NULL;
```
## ORDER BY Clause

