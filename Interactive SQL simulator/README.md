# SQL

<details>
  <summary>Схема базы данных</summary>
  
  ![drawSQL-emploeesDB](https://github.com/Meiliger/githubrepo/blob/main/Interactive%20SQL%20simulator/2022-12-17_17-47-00.png)
</details>
 
*4. Display information about all books stored in the warehouse*

<details>
  <summary>Схема базы данных</summary>
  
  ![drawSQL-emploeesDB](https://user-images.githubusercontent.com/83915765/136953203-86a40d2f-3a8c-4e16-955c-34d0e638b6f9.png)
</details>

```sql
SELECT *
FROM book; 
```
*5. At the end of the year, the price of all books in stock is recalculated and reduced by 30%. Write an SQL query that selects titles, authors, quantities from the book table and calculates new book prices. Name the column with the new price new_price, round the price to 2 decimal places*

<details>
  <summary>Схема базы данных</summary>
  
  ![drawSQL-emploeesDB](https://user-images.githubusercontent.com/83915765/136953203-86a40d2f-3a8c-4e16-955c-34d0e638b6f9.png)
</details>

 ```sql
SELECT title, author, amount, ROUND((price*0.7),2) AS new_price
FROM book;
```
*6. When analyzing book sales, it turned out that the most popular are the books of Mikhail Bulgakov, in second place are the books of Sergei Yesenin. Based on this, they decided to raise the price of Bulgakov's books by 10%, and the price of Yesenin's books - by 5%. Write a query where to include the author, book title and new price, name the last column new_price. Round the value to two decimal places*
 ```sql
SELECT author, title, ROUND(IF(author = "Булгаков М.А.", price * 1.1, IF (author = "Есенин С.А.", price * 1.05, price)), 2) AS new_price
FROM book;
```
*7. Output the title and authors of those books whose prices belong to the interval from 540.50 to 800 (including borders), and the number is either 2, or 3, or 5, or 7*
```sql
SELECT title, author
FROM book
WHERE price BETWEEN 540.50 AND 800 AND amount IN(2, 3, 5, 7);
```
*8. Output the title and author of those books whose title consists of two or more words, and the author's initials contain the letter "C". Consider that in the title the words are separated from each other by spaces and do not contain punctuation marks, a space is required between the author's surname and initials, initials are written without a space in the format: letter, dot, letter, dot. Sort information alphabetically by book title*
```sql
SELECT title, author
FROM book
WHERE title LIKE '_% _%' AND (author LIKE '_% С._.' OR author LIKE '% _.С.')
ORDER BY title;
```
*9. ВSelect different (unique) elements of the amount column of the book table*
```sql
select distinct amount
from book;
```
*10. Display information (author, title and price) about books whose prices are less than or equal to the average price of books in stock. Display information sorted by price in descending order. Calculate the average as the average of the price of the book*
```sql
SELECT author, title, price
FROM book
WHERE price <= (
    SELECT AVG(price)
    FROM book)
ORDER BY price DESC;  
```
*11. Display information (author, book, and quantity) about those books whose number of copies in the book table is not duplicated*
```sql
SELECT author, title, amount 
FROM book
WHERE amount IN (
                SELECT amount
                FROM book
                GROUP BY amount
                HAVING COUNT(amount)=1);
```
*12. Display information about books (author, title, price) whose price is less than the highest of the minimum prices calculated for each author*
```sql
SELECT author, title, price
FROM book
WHERE price < any(
    SELECT MIN(price)
    FROM book
    GROUP BY author
)
```
