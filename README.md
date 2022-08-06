#### [SELECT](#select)
- #### [COUNT](#count)
- #### [DISTINCT](#distinct)
- #### [GROUP BY](#groupby)
- #### [HAVING](#having)
- #### [ORDER BY](#orderby)
- #### [ASC | DESC](#asc)
- #### [LIMIT](#limit)

- Select all values from the table.

```SQL
SELECT * FROM table-name;
```
- Select `сolumn-1`, `column-2` from the table

```SQL
SELECT сolumn-1, сolumn-2 FROM table-name;
```

- Select **unique** values from the table and `column-2`

```SQL
SELECT DISTINCT сolumn-2 FROM table-name;
```

- Select data with specific condition

valid condition operators:

```SQL
=
>
<
>=
<=
!= or <>
AND
OR
```

```SQL
SELECT column-1, сolumn-2 FROM table-name WHERE condition;
---
SELECT * FROM staff WHERE first_name = 'John' AND last_name = 'Doe';
SELECT * FROM staff WHERE experience > 1 AND experience <= 3;
```

<h4 id="count">
  - Get the number of fields 
</h4>

```SQL
SELECT COUNT (сolumn-name) FROM table-name WHERE condition;
---
SELECT COUNT (name) FROM products WHERE discount > 10;
```

<h4 id="distinct">
  - Get the number of **unique** fields 
</h4>

```SQL
SELECT COUNT (DISTINCT сolumn-name) FROM table-name WHERE condition;
---
SELECT COUNT (DISTINCT manufacturer) FROM products;
```

<h4 id="limit">
  - Set a limit on the number of requested fields
</h4>

```SQL
SELECT * FROM table-name LIMIT 100;
---
SELECT * FROM staff WHERE first_name = 'John' LIMIT 100;
```

- Set offset for selection of values 
```SQL
SELECT * FROM table-name OFFSET 100;
---
SELECT * FROM staff WHERE first_name = 'John' LIMIT 100;
```

<h4 id="asc">
  - Sort the received data in ascending (ASC - default) / descending (DESC) order
</h4>

```SQL
SELECT * FROM table-name ORDER BY column-name ASC / DESC;
---
SELECT * FROM staff ORDER BY first_name DESC;
```

<h4 id="orderby">
  - Set interval for selection of values
</h4>

```SQL
SELECT * FROM table-name WHERE column-name BETWEEN from-value AND to-value;
---
SELECT * FROM staff WHERE performance_rating BETWEEN 8 AND 10 ORDER BY last_name;
---
SELECT * FROM staff WHERE performance_rating NOT BETWEEN 0 AND 7 ORDER BY last_name;
```

- Specify the search parameters for the operator `WHERE` (exact match - the specified value **fully matches** the field value - `IN` parameter)
```SQL
SELECT * FROM table-name WHERE column-name IN (avalue-1, value-2);
---
SELECT * FROM staff WHERE salary IN (1000, 2000, 3000);
---
SELECT * FROM staff WHERE salary NOT IN (1000, 2000, 3000);
```

- Specify the search parameters for the operator `WHERE` (partial match - the specified value **partially matches** the value of the field - `LIKE` parameter)

```SQL
SELECT * FROM table-name WHERE column-name LIKE 'Value%';
---
SELECT * FROM staff WHERE first_name LIKE 'Jo%';
```
The `I` prefix in the `LIKE` parameter allows you to ignore the case of letters in the search results:

```SQL
SELECT * FROM staff WHERE first_name ILIKE 'Jo%';
```

<h4 id="groupby">
  - The GROUP BY clause determines how rows will be grouped.
</h4>

```SQL
SELECT Manufacturer, COUNT(*) AS ModelsCount
FROM Products
GROUP BY Manufacturer
```

<h4 id="having">
  - The following SQL statement lists the number of customers in each country. Only include countries with more than 5 customers:
</h4>

```SQL
SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country
HAVING COUNT(CustomerID) > 5;
```

search patterns:

| String variable | Action                 |
|-----------------|------------------------|
| %               | any length string      |
| _               | any single symbol      |
| []              | symbol range           |
| ^               | excluding symbol range |




