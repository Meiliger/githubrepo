# SQL HomeWork-2

<details>
  <summary>Схема базы данных</summary>
  
  ![drawSQL-emploeesDB](https://user-images.githubusercontent.com/83915765/136953203-86a40d2f-3a8c-4e16-955c-34d0e638b6f9.png)
</details>

*1. Formulate an SQL query to create the book table, enter it in the code window (located below) and send it for verification (the Submit button). Structure of the book table:*
<details>
  
  ![drawSQL-emploeesDB](https://user-images.githubusercontent.com/83915765/136953203-86a40d2f-3a8c-4e16-955c-34d0e638b6f9.png)
</details>
```
sql
CREATE TABLE book
  (
     book_id INT PRIMARY KEY auto_increment,
     title   VARCHAR(50),
     author  VARCHAR(30),
     price   DECIMAL(8, 2),
     amount  INT
  ); 
```
*2. Enter a new row in the book table (text values (VARCHAR type) must be enclosed in either double or single quotes):*
<details>
  
  ![drawSQL-emploeesDB](https://user-images.githubusercontent.com/83915765/136953203-86a40d2f-3a8c-4e16-955c-34d0e638b6f9.png)
</details>
```
sql
INTO book (title, author, price, amount) VALUES ('Мастер и Маргарита', 'Булгаков М.А.', 670.99, 3);
```
*3. Enter the last three records in the book table, the first record has already been added in the previous step:*
<details>
  
  ![drawSQL-emploeesDB](https://user-images.githubusercontent.com/83915765/136953203-86a40d2f-3a8c-4e16-955c-34d0e638b6f9.png)
</details>
```
sql
INSERT INTO book
            (title,
             author,
             price,
             amount)
VALUES      ('Белая гвардия',
             'Булгаков М.А.',
             540.50,
             5),
            ('Идиот',
             'Достоевский Ф.М.',
             460.00,
             10),
            ('Братья Карамазовы',
             'Достоевский Ф.М.',
             799.01,
             2);
```
*4. Display information about all books stored in the warehouse*
```sql
SELECT *
FROM book; 
```
*5. At the end of the year, the price of all books in stock is recalculated and reduced by 30%. Write an SQL query that selects titles, authors, quantities from the book table and calculates new book prices. Name the column with the new price new_price, round the price to 2 decimal places*
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
*13. Вывести имена и зарплаты Middle специалистов*
```sql
SELECT employee_name, monthly_salary 
FROM employees 
INNER JOIN employees_salary
ON employees.id = employees_salary.employee_id
INNER JOIN roles_employees 
ON employees.id = roles_employees.employee_id
INNER JOIN roles
ON roles.id = roles_employees.role_id
WHERE role_name LIKE '%Middle%';
```
*14. Вывести имена и зарплаты Senior специалистов*
```sql
SELECT employee_name, monthly_salary 
FROM employees 
INNER JOIN employees_salary
ON employees.id = employees_salary.employee_id
INNER JOIN roles_employees 
ON employees.id = roles_employees.employee_id
INNER JOIN roles
ON roles.id = roles_employees.role_id
WHERE role_name LIKE '%Senior%';
```
*15. Вывести зарплаты Java разработчиков*
```sql
SELECT monthly_salary
FROM employees_salary
LEFT JOIN employees 
ON employees_salary.employee_id = employees.id
INNER JOIN roles_employees 
ON employees.id = roles_employees.employee_id
INNER JOIN roles
ON roles.id = roles_employees.role_id
WHERE role_name LIKE '%Java developer%';
```
*16. Вывести зарплаты Python разработчиков*
```sql
SELECT monthly_salary
FROM employees_salary
LEFT JOIN employees 
ON employees_salary.employee_id = employees.id
INNER JOIN roles_employees 
ON employees.id = roles_employees.employee_id
INNER JOIN roles
ON roles.id = roles_employees.role_id
WHERE role_name LIKE '%Python developer%';
```
*17. Вывести имена и зарплаты Junior Python разработчиков*
```sql
SELECT employee_name, monthly_salary 
FROM employees 
INNER JOIN employees_salary
ON employees.id = employees_salary.employee_id
INNER JOIN roles_employees 
ON employees.id = roles_employees.employee_id
INNER JOIN roles
ON roles.id = roles_employees.role_id
WHERE role_name  = 'Junior Python developer';
```
*18. Вывести имена и зарплаты Middle JS разработчиков*
```sql
SELECT employee_name, monthly_salary 
FROM employees 
INNER JOIN employees_salary
ON employees.id = employees_salary.employee_id
INNER JOIN roles_employees 
ON employees.id = roles_employees.employee_id
INNER JOIN roles
ON roles.id = roles_employees.role_id
WHERE role_name  = 'Middle JavaScript developer';
```
*19. Вывести имена и зарплаты Senior Java разработчиков*
```sql
SELECT employee_name, monthly_salary 
FROM employees 
INNER JOIN employees_salary
ON employees.id = employees_salary.employee_id
INNER JOIN roles_employees 
ON employees.id = roles_employees.employee_id
INNER JOIN roles
ON roles.id = roles_employees.role_id
WHERE role_name LIKE '%Senior Java developer%';
```
*20. Вывести зарплаты Junior QA инженеров*
```sql
SELECT monthly_salary
FROM employees_salary
INNER JOIN employees 
ON employees_salary.employee_id = employees.id
INNER JOIN roles_employees 
ON employees.id = roles_employees.employee_id
INNER JOIN roles
ON roles.id = roles_employees.role_id
WHERE role_name LIKE '%Junior%QA engineer%';
```
*21. Вывести среднюю зарплату всех Junior специалистов*
```sql
SELECT AVG(monthly_salary)
FROM employees 
INNER JOIN employees_salary
ON employees.id = employees_salary.employee_id
INNER JOIN roles_employees 
ON employees.id = roles_employees.employee_id
INNER JOIN roles
ON roles.id = roles_employees.role_id
WHERE role_name LIKE '%Junior%';
```
*22. Вывести сумму зарплат JS разработчиков*
```sql
SELECT SUM(monthly_salary)
FROM employees 
INNER JOIN employees_salary
ON employees.id = employees_salary.employee_id
INNER JOIN roles_employees 
ON employees.id = roles_employees.employee_id
INNER JOIN roles
ON roles.id = roles_employees.role_id
WHERE role_name LIKE '%JavaScript developer%';
```
*23. Вывести минимальную ЗП QA инженеров*
```sql
SELECT MIN(monthly_salary)
FROM employees 
INNER JOIN employees_salary
ON employees.id = employees_salary.employee_id
INNER JOIN roles_employees 
ON employees.id = roles_employees.employee_id
INNER JOIN roles
ON roles.id = roles_employees.role_id
WHERE role_name LIKE '%QA engineer%';
```
*24. Вывести максимальную ЗП QA инженеров*
```sql
SELECT MAX(monthly_salary)
FROM employees 
INNER JOIN employees_salary
ON employees.id = employees_salary.employee_id
INNER JOIN roles_employees 
ON employees.id = roles_employees.employee_id
INNER JOIN roles
ON roles.id = roles_employees.role_id
WHERE role_name LIKE '%QA engineer%';
```
*25. Вывести количество QA инженеров*
```sql
SELECT COUNT(employee_name)
FROM employees 
INNER JOIN roles_employees 
ON employees.id = roles_employees.employee_id
INNER JOIN roles
ON roles.id = roles_employees.role_id
WHERE role_name LIKE '%QA engineer%';
```
*26. Вывести количество Middle специалистов.*
```sql
SELECT COUNT(employee_name)
FROM employees 
INNER JOIN roles_employees 
ON employees.id = roles_employees.employee_id
INNER JOIN roles
ON roles.id = roles_employees.role_id
WHERE role_name LIKE '%Middle%';
```
*27. Вывести количество разработчиков*
```sql
SELECT COUNT(employee_name)
FROM employees 
INNER JOIN roles_employees 
ON employees.id = roles_employees.employee_id
INNER JOIN roles
ON roles.id = roles_employees.role_id
WHERE role_name LIKE '%developer%';
```
*28. Вывести фонд (сумму) зарплаты разработчиков.*
```sql
SELECT SUM(monthly_salary)
FROM employees 
INNER JOIN employees_salary
ON employees.id = employees_salary.employee_id
INNER JOIN roles_employees 
ON employees.id = roles_employees.employee_id
INNER JOIN roles
ON roles.id = roles_employees.role_id
WHERE role_name LIKE '%developer%';
```
*29. Вывести имена, должности и ЗП всех специалистов по возрастанию*
```sql
SELECT employee_name, role_name, monthly_salary 
FROM employees 
LEFT JOIN employees_salary
ON employees.id = employees_salary.employee_id
INNER JOIN roles_employees 
ON employees.id = roles_employees.employee_id
INNER JOIN roles
ON roles.id = roles_employees.role_id
ORDER BY monthly_salary;
```
*30. Вывести имена, должности и ЗП всех специалистов по возрастанию у специалистов, у которых ЗП от 1700 до 2300*
```sql
SELECT employee_name, role_name, monthly_salary 
FROM employees 
LEFT JOIN employees_salary
ON employees.id = employees_salary.employee_id
INNER JOIN roles_employees 
ON employees.id = roles_employees.employee_id
INNER JOIN roles
ON roles.id = roles_employees.role_id
WHERE monthly_salary BETWEEN 1700 AND 2300
ORDER BY monthly_salary;
```
*31. Вывести имена, должности и ЗП всех специалистов по возрастанию у специалистов, у которых ЗП меньше 2300*
```sql
SELECT employee_name, role_name, monthly_salary 
FROM employees 
LEFT JOIN employees_salary
ON employees.id = employees_salary.employee_id
INNER JOIN roles_employees 
ON employees.id = roles_employees.employee_id
INNER JOIN roles
ON roles.id = roles_employees.role_id
WHERE monthly_salary < 2300
ORDER BY monthly_salary;
```
*32. Вывести имена, должности и ЗП всех специалистов по возрастанию у специалистов, у которых ЗП равна 1100, 1500, 2000*
```sql
SELECT employee_name, role_name, monthly_salary 
FROM employees 
LEFT JOIN employees_salary
ON employees.id = employees_salary.employee_id
INNER JOIN roles_employees 
ON employees.id = roles_employees.employee_id
INNER JOIN roles
ON roles.id = roles_employees.role_id
WHERE monthly_salary IN (1100, 1500, 2000)
ORDER BY monthly_salary;
```


