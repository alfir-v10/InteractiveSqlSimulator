```sql
SELECT name, city, per_diem, date_first, date_last
FROM trip
WHERE name LIKE '%а %'
ORDER BY date_last DESC;
```

```sql
SELECT DISTINCT name
FROM trip
WHERE city = 'Москва'
ORDER BY name ASC;
```

```sql
SELECT city, 
       COUNT(city) AS Количество
FROM trip
GROUP BY city
ORDER BY city ASC;

```

```sql
SELECT city,
       COUNT(city) as Количество
FROM trip
GROUP BY city
ORDER BY Количество DESC
LIMIT 2;
```

```sql
SELECT name, city, 
	   DATEDIFF(date_last, date_first) + 1 AS Длительность
FROM trip
WHERE city NOT IN ('Москва', 'Санкт-Петербург')
ORDER BY Длительность DESC
```

```sql
SELECT name, city, date_first, date_last
FROM trip
WHERE DATEDIFF(date_last, date_first) = (SELECT MIN(DATEDIFF(date_last, date_first)) 
										 FROM trip);
```

```sql
SELECT name, city, date_first, date_last
FROM trip
WHERE MONTH(date_first) = MONTH(date_last)
ORDER BY city ASC,  name ASC;
```

```sql
SELECT MONTHNAME(date_first) AS Месяц,
       COUNT(MONTHNAME(date_first)) AS Количество
FROM trip
GROUP BY Месяц
ORDER BY Количество DESC, Месяц ASC;
```

```sql
SELECT name, city, date_first, 
       per_diem * (DATEDIFF(date_last, date_first) + 1) AS Сумма
FROM trip
WHERE MONTHNAME(date_first) IN ('February', 'March') 
ORDER BY name ASC, Сумма DESC;
```

```sql
SELECT name, SUM(per_diem * (DATEDIFF(date_last, date_first) + 1)) AS Сумма
FROM trip
WHERE name in (SELECT name
               FROM trip
               GROUP BY name
               HAVING COUNT(name) > 3)
GROUP BY name
ORDER BY Сумма DESC
```

