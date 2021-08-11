```sql
SELECT DISTINCT amount
FROM book;
```

```sql
SELECT author AS Автор, 
       COUNT(amount) AS Различных_книг,
       SUM(amount) AS Количество_экземпляров
FROM book
GROUP BY Автор;
```

```sql
SELECT author,
       MIN(price) AS Минимальная_цена,
       MAX(price) AS Максимальная_цена,
       AVG(price) AS Средняя_цена
FROM book
GROUP BY author;
```

```sql
SELECT author,
       ROUND(SUM(price * amount), 2) AS Стоимость,
       ROUND(SUM(price * amount) * 0.18 / (1 + 0.18), 2) AS НДС,
       ROUND(SUM(price * amount) / (1 + 0.18), 2) AS Стоимость_без_НДС
FROM book
GROUP BY author;
```

```sql
SELECT MIN(price) AS Минимальная_цена,
       MAX(price) AS Максимальная_цена,
       ROUND(AVG(price), 2) AS Средняя_цена
FROM book;
```

```sql
SELECT ROUND(AVG(price), 2) AS Средняя_цена,
       ROUND(SUM(price * amount), 2) AS Стоимость
FROM book
WHERE amount BETWEEN 5 AND 14;
```

```sql
SELECT author, ROUND(SUM(price * amount), 2) AS Стоимость
FROM book
WHERE title <> 'Идиот' AND author <> 'Белая гвардия'
GROUP BY author
HAVING ROUND(SUM(price * amount), 2) > 5000
ORDER BY Стоимость DESC;
```