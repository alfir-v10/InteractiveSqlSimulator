```sql
CREATE TABLE supply(
    supply_id INT PRIMARY KEY AUTO_INCREMENT,
                   title VARCHAR(50),
                   author VARCHAR(30),
                    price DECIMAL(8, 2),
                    amount INT);
```

```sql
INSERT INTO supply (title, author, price, amount)
VALUES ('Лирика','Пастернак Б.Л.','518.99',	'2'),
       ('Черный человек', 	'Есенин С.А.',	'570.20',	'6'),
       ('Белая гвардия',	'Булгаков М.А.',	'540.50',	'7'),
       ('Идиот',	'Достоевский Ф.М.',	'360.80',	'3');
```

```sql
NSERT INTO book (title, author, price, amount)
SELECT title, author, price, amount
FROM supply
WHERE author NOT IN ('Булгаков М.А.', 'Достоевский Ф.М.');

SELECT * FROM book;

```

```sql
INSERT INTO book (title, author, price, amount)
SELECT title, author, price, amount
FROM supply
WHERE author NOT IN (SELECT author FROM book);

SELECT * FROM book;


```

```sql
UPDATE book 
SET price = price * 0.9
WHERE amount BETWEEN 5 AND 10;

```

```sql
UPDATE book
SET buy = IF(amount < buy, amount, buy), 
	price = IF(buy=0, price * 0.9, price);

SELECT * FROM book;
```

```sql
UPDATE book, supply
SET book.amount = book.amount + supply.amount, 
	book.price = (book.price + supply.price) / 2
WHERE book.title = supply.title;

SELECT * FROM book;
```

```sql
DELETE FROM supply
WHERE author IN (SELECT author
                 FROM book 
                 GROUP BY author
                 HAVING SUM(amount) > 10);

SELECT * FROM supply;

```

```sql
CREATE TABLE ordering AS
SELECT author, title,
       (
           SELECT ROUND(AVG(amount)) 
           FROM book
       ) AS amount
FROM book
WHERE amount < (SELECT ROUND(AVG(amount)) FROM book);

SELECT * FROM ordering;


```
