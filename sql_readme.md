# ✅ SQL Learning

1. SQL Database is like tables and rows in excel.
2. To create a database named learning

 ```
 create database learning;
 ```
3. To use a specific database or another database, let's say here we have database named learning

```
use learning;
```
4. To create a table named `users`

```

create table users(
id INT auto_increment Primary Key,
Name varchar(100) not null,
email varchar(100) unique not null,
date_of_birth date,
gender enum('Male', 'Female', 'Others'),
created_at timestamp default current_timestamp
);

```

Here `int`, `varchar(100)`, `date`, `enum`, `timestamp` are datatype.
Also, `not null`, `unique`, `default`, `Primary Key,` `Auto Increment` are 	Constraints.

You can use **INSERT** to fill the data in the table

```

INSERT INTO users (Name, email, date_of_birth, gender)
VALUES
('Mohit', 'msaini@gmail.com', '2002-05-19', 'Male'),
('Anjali Verma', 'anjali.verma@example.com', '1998-09-25', 'Female'),
('Rohit Kumar', 'rohit.kumar@example.com', '1997-03-22', 'Others');

```

5. To see eveything inside users table

```
Select * from users;
```

To select specific columns inside a table

```
select name, gender from users;
```

To rename a table to something else like `programmers`

```
rename table users to programmers;

or

rename table programmers  to users;
```

6. To drop the database

```
Drop database learning;
```

### 📌 Alterring A Table

7. To add a column in users table like `is_active` by setting its default value to true

```
alter table users add column is_active boolean default true;
```

8. Droping a column in a table

```
alter table users drop is_active;
```

9. To drop the `is_active` column from the users table, use this query:

```
ALTER TABLE users DROP COLUMN is_active;
```

10 To modify a column, let's say increasing the char length of the name

```
Alter table users modify column name varchar(150);

```

11. You can alter the structure of the database so that email comes first before name. **`make sure to add contrains and datatype`** if you are using this

```
ALTER TABLE users
MODIFY COLUMN email VARCHAR(100) UNIQUE NOT NULL FIRST,
MODIFY COLUMN Name VARCHAR(150) NOT NULL AFTER email;
```

## ✅ CRUD Operations in SQL

## 📌  Creating

13. Inserting something into the table

```
INSERT INTO users(email, Name, date_of_birth, gender) 
Values
('alex@gmail.com', 'Alex', '2001-08-13', 'Female'),
('john@gmail.com', 'John', '1998-02-27', 'Male');
```

### Quering some data 

creating a seprate database 

```
CREATE TABLE students (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    gender ENUM('Male', 'Female', 'Other'),
    date_of_birth DATE,
    salary DECIMAL(10, 2),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

Add some values in it

```
INSERT INTO students (name, email, gender, date_of_birth, salary) VALUES
('Aarav', 'aarav@example.com', 'Male', '1995-05-14', 65000.00),
('Ananya', 'ananya@example.com', 'Female', '1990-11-23', 72000.00),
('Raj', 'raj@example.com', 'Male', '1988-02-17', 58000.00),
('Sneha', 'sneha@example.com', 'Female', '2000-08-09', 50000.00),
('Farhan', 'farhan@example.com', 'Male', '1993-12-30', 61000.00),
('Priyanka', 'priyanka@example.com', 'Female', '1985-07-12', 84000.00),
('Aisha', 'aisha@example.com', 'Female', '1997-03-25', 56000.00),
('Aditya', 'aditya@example.com', 'Male', '1992-06-17', 69000.00),
('Meera', 'meera@example.com', 'Female', '1989-09-05', 77000.00),
('Ishaan', 'ishaan@example.com', 'Male', '2001-10-02', 45000.00),
('Tanvi', 'tanvi@example.com', 'Female', '1994-04-18', 62000.00),
('Rohan', 'rohan@example.com', 'Male', '1986-12-01', 75000.00),
('Zoya', 'zoya@example.com', 'Female', '1998-01-15', 54000.00),
('Karan', 'karan@example.com', 'Male', '1990-08-22', 68000.00),
('Nikita', 'nikita@example.com', 'Female', '1987-03-10', 71000.00),
('Manav', 'manav@example.com', 'Male', '1996-11-29', 61000.00),
('Divya', 'divya@example.com', 'Female', '1991-02-28', 57000.00),
('Harshit', 'harshit@example.com', 'Male', '1993-09-09', 65000.00),
('Ritika', 'ritika@example.com', 'Female', '1999-05-05', 52000.00),
('Imran', 'imran@example.com', 'Male', '1995-07-30', 63000.00),
('Juhi', 'juhi@example.com', 'Female', '1992-10-14', 59000.00),
('Tushar', 'tushar@example.com', 'Male', '1990-01-08', 73000.00),
('Lata', 'lata@example.com', 'Female', '1984-11-11', 78000.00),
('Yash', 'yash@example.com', 'Male', '1997-06-06', 64000.00),
('Fatima', 'fatima@example.com', 'Female', '1993-03-03', 55000.00);

```

## 📌 Reading

#### Where clause

14. we will find the values using the **where clause**

```
Select * from students where gender='Female';

or 

Select * from students where gender='Female' and salary >='70000';

or

-- smaller value has to be in front, we. cannot do '70000' and '60000'
Select * from students where salary between '60000' AND '70000';

or

-- in this case all the male will be selected even there salary will be less than 70000 because we are using the geneder condition only as well as female with salary >= 70000 will be selected as well because of `or` condition
Select * from students where gender='Male' or salary >='70000'
```

we can use different things like `between`, `And`, `or` `not equal to (!=)`, `greater (<)` or `less than(>)` different combinations

#### `order by` or `asc` or `dec` order, or `limit`


16. `order by` will arrange the data in a specific order we can make the order in ascending`(ASC)` or decending order`(DESC)`.

```
Select * from students where gender='Male' and salary >= '65000' order by date_of_birth ASC

or

Select * from students where gender='Male' and salary >= '65000' order by date_of_birth DESC
```

#### limit

17. Limit can be used to limit the number of rows or columns to be shown

```
-- this will only show first 5 rows.
Select * from students where gender='Male' and salary >= '65000' order by date_of_birth DESC limit 5;
```

## 📌 Updating the data

18. You can update a specific row in the table using different parameter like the `id`, `salary`, etc

```
-- here we can only use id not name because id is a primary key and it will be unique. Two person can have the same name

UPDATE students set salary='40000', email='aarav2@gmail.com' where id='1';

or

-- here also while creating the schema of students we made sure the email id was unique

UPDATE students set name='Raj shani' where email='raj@example.com';
```

🧵 Question increase salary of all the students whose salary is less than or equal to 45000 and set it to 55000.

```
Update students set salary='55000' WHERE salary <= 45000;
```

## 📌  Deleting

19. Deleting from the table is quite a important comand so check it before running and make sure to use where condition to specifically delete only the selected portion.

```
Delete from students where id=3;
```

20. Droping a table

```
Drop table students;
```

## 📌 SQL Contraints







