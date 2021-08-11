```sql
SELECT * FROM book;
```

```sql
SELECT author, title, price 
FROM book;
```

```sql
SELECT title AS Название, 
       author AS Автор 
FROM book;
```

```sql
SELECT title, amount, 
       amount * 1.65 AS pack 
FROM book;
```

```sql
SELECT title, author, amount, 
    ROUND(price - price * 0.3, 2) AS new_price 
FROM book;
```

```sql
SELECT author, title,
       ROUND(IF(author = 'Булгаков М.А.', price + price * 0.1, 
             IF(author = 'Есенин С.А.', price + price * 0.05, price)), 2) 
             AS new_price
FROM book;
```

```sql
SELECT author, title, price
FROM book
WHERE amount < 10;
```

```sql
SELECT title, author, price, amount
FROM book
WHERE (price < 500 OR price > 600) 
       AND price * amount >= 5000;
```

```sql
SELECT title, author
FROM book
WHERE price BETWEEN 540.50 AND 800
      AND amount IN (2, 3, 5, 7);
 ```
 
 ```sql
 SELECT author, title
FROM book
WHERE amount BETWEEN 2 AND 14
ORDER BY author DESC, title ASC;
```

```sql
SELECT title, author
FROM book
WHERE title LIKE '%_ %_'
      AND author LIKE '%С.%'
ORDER BY title ASC;
```
