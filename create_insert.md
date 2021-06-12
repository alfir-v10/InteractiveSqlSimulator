```sql 
CREATE TABLE book(
    book_id INT PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(50),
    author VARCHAR(30),
    price DECIMAL(8, 2),
    amount INT);
```

```sql
INSERT INTO book (book_id, title, author, price, amount)
VALUES (1, 'Мастер и Маргарита', 'Булгаков М.А.', 670.99, 3);
```

```sql
INSERT INTO book (book_id, title, author, price, amount)
VALUES (2, 'Белая гвардия', 'Булгаков М.А.', 540.50, 5),
       (3, 'Идиот', 'Достоевский Ф.М.', 460.00, 10),
       (4, 'Братья Карамазовы', 'Достоевский Ф.М.', 799.01, 2);
```
