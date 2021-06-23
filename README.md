# Introduction to SQL

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

## BETWEEN
