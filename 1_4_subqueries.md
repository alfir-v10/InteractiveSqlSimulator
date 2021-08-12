```sql
SELECT author, title, price
FROM book
WHERE price <= (
           SELECT AVG(price) 
           FROM book
      )
ORDER BY price DESC;
```

```sql
SELECT author, title, price
FROM book
WHERE ABS(price - (SELECT MIN(price) FROM book)) <= 150
ORDER BY price ASC;
```

```sql
SELECT author, title, amount
FROM book
WHERE amount in (
				SELECT amount 
            	FROM book
                 GROUP BY amount
                 HAVING COUNT(amount) = 1
    );
```

```sql
SELECT author, title, price
FROM book
WHERE price < ANY(
              SELECT MIN(price)
              FROM book
              GROUP BY author
              ORDER BY price ASC
    );
```

```sql
SELECT title, author, amount, 
		((SELECT MAX(amount) FROM book) - amount) AS Заказ
FROM book
WHERE amount NOT IN (
			SELECT MAX(amount) 
			FROM book
	);

```
