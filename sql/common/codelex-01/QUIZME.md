@credits
[codelex.io](https://codelex.io)
@creditsEnd

---
What does SQL stand for?

a) Structured Question Language

b) Strong Question Language

c*) Structured Query Language

---
Which SQL statement is used to fetch data from a database?

a*) SELECT

b) GET

c) FETCH

---
Which SQL statement is used to update data in a database?

a) SAVE AS

b) SAVE

c) MODIFY

d*) UPDATE

---
Which SQL statement is used to delete data from a database?

a*) DELETE

b) REMOVE

c) INVALIDATE

d) UPDATE

---
Which SQL statement is used to insert new data in a database?

a*) INSERT INTO

b) INSERT

c) ADD

d) INSERT NEW

---
With SQL, how do you select a column named "first_name" from a table named "students"?

a*) SELECT first_name FROM students

b) SELECT students.first_name

c) EXTRACT first_name FROM students

---
With SQL, how do you select all the columns from a table named "students"?

a*) SELECT * FROM students

b) SELECT students

c) SELECT [all] FROM students

d) SELECT *.students

---
With SQL, how do you select all the records from a table named "students" where the value of the column "first_name" is "John"?

a) SELECT [all] FROM students WHERE first_name LIKE 'John'

b) SELECT [all] FROM students WHERE first_name = 'John'

c) SELECT * FROM students WHERE first_name <> 'John'

d*) SELECT * FROM students WHERE first_name = 'John'

---
With SQL, how do you select all the records from a table named "students" where the value of the column "first_name" starts with an "a"?

a*) SELECT * FROM students WHERE first_name LIKE 'a%'

b) SELECT * FROM students WHERE first_name LIKE '%a'

c) SELECT * FROM students WHERE first_name = '%a%'

d) SELECT * FROM students WHERE first_name = 'a'

---
The OR operator displays a record if ANY conditions listed are true. The AND operator displays a record if ALL of the conditions listed are true

a*) TRUE

b) FALSE

---
With SQL, how do you select all the records from a table named "students" where the "first_name" is "John" and the "last_name" is "Doe"?

a*) SELECT * FROM students WHERE first_name = 'John' AND last_name = 'Doe'

b) SELECT * FROM students WHERE first_name <> 'John' AND last_name <> 'Doe'

c) SELECT first_name = 'John', last_name = 'Doe' FROM students

---
With SQL, how do you select all the records from a table named "students" where the "last_name" is alphabetically between (and including) "Doe" and "Smith"?

a*) SELECT * FROM students WHERE last_name BETWEEN 'Doe' AND 'Smith'

b) SELECT LastName > 'Doe' AND last_name < 'Smith' FROM students

c) SELECT * FROM students WHERE last_name > 'Doe' AND last_name < 'Smith'

---
Which SQL statement is used to return only different values?

a*) SELECT DISTINCT

b) SELECT DIFFERENT

c) SELECT UNIQUE

---
Which SQL keyword is used to sort the result-set?

a*) ORDER BY

b) SORT

c) SORT BY

d) ORDER

---
With SQL, how can you return all the records from a table named "students" sorted descending by "first_name"?

a) SELECT * FROM students SORT BY 'first_name' DESC

b*) SELECT * FROM students ORDER BY first_name DESC

c) SELECT * FROM students SORT 'first_name' DESC

d) SELECT * FROM students ORDER first_name DESC

---
With SQL, how can you insert a new record into the "students" table?

a*) INSERT INTO students VALUES ('John', 'Doe')

b) INSERT VALUES ('John', 'Doe') INTO students

c) INSERT ('John', 'Doe') INTO students

---
With SQL, how can you insert "Doe" as the "last_name" in the "students" table?

a) INSERT INTO students ('Doe') INTO last_name

b*) INSERT INTO students (last_name) VALUES ('Doe')

c) INSERT ('Doe') INTO students (last_name)

---
How can you change "Doe" into "Smith" in the "last_name" column in the "students" table?

a) MODIFY students SET last_name = 'Smith' WHERE LastName = 'Doe'

b*) UPDATE students SET last_name = 'Smith' WHERE LastName = 'Doe'

c) UPDATE students SET last_name = 'Doe' INTO LastName = 'Smith'

d) MODIFY students SET last_name = 'Doe' INTO LastName = 'Smith'

---
With SQL, how can you delete the records where the "first_name" is "John" in the  students table?

a*) DELETE FROM students WHERE first_name = 'John'

b) DELETE ROW first_name = 'John' FROM students

c) DELETE first_name = 'John' FROM students

---
With SQL, how can you return the number of records in the "students" table?

a) SELECT LEN(*) FROM students

b) SELECT COLUMNS(*) FROM students

c*) SELECT COUNT(*) FROM students

d) SELECT NO(*) FROM students

---
What is the most common type of join?

a) INSIDE JOIN

b) JOINED TABLE

c) JOINED

d*) INNER JOIN

---
Which operator is used to select values within a range?

a) WITHIN

b) RANGE

c*) BETWEEN

---
The NOT NULL constraint enforces a column to not accept null values.

a*) TRUE

b) FALSE

---
Which operator is used to search for a specified pattern in a column?

a) FROM

b) GET

c*) LIKE

---
Which SQL statement is used to create a table in a database?

a) CREATE DATABASE TABLE

b*) CREATE TABLE

c) CREATE DB

d) CREATE DATABASE TAB

---
The table rows are also known as:

a) attributes

b*) records

c) fields

---
The TRUNCATE TABLE:

a*) deletes all rows from a table

b) checks if the table has primary key specified

c) deletes the table

---
What is an index?

a) Special way to join 2 or more tables

b) The same as alias

c*) Database table attribute, which speeds-up data search within a table

---
What does follow after the SQL WHERE clause?

a) A list of columns to be selected

b) The name of the table we are selecting from

c*) Definition of the condition to be met for the rows to be returned

---
Which of the following SQL statements is correct?

a)
```sql
SELECT FROM Sales WHERE Date BETWEEN ('10/12/2005', '01/01/2006')
```

b)
```sql
SELECT FROM Sales WHERE Date BETWEEN '10/12/2005' AND '01/01/2006'
```

c*)
```sql
SELECT * FROM Sales WHERE Date BETWEEN '10/12/2005' AND '01/01/2006'
```

---
Which SQL statement inserts data into a table called Projects?

a)
```sql
INSERT Projects VALUES ('Content Development', 'Website content development project')
```

b)
```sql
SAVE INTO Projects (ProjectName, ProjectDescription)
  VALUES ('Content Development', 'Website content development project')
```

c*)
```sql
INSERT INTO Projects (ProjectName, ProjectDescription)
  VALUES ('Content Development', 'Website content development project')
```

d)
```sql
INSERT Projects ('Content Development', 'Website content development project')
```

---
The SQL DROP TABLE clause is used to:

a) modify an existing table in a database

b*) delete a table from the database

c) create a new table in the database

---
Which of the following SQL statements is correct?

a)
```sql
SELECT Username, Password WHERE Username = 'user1'
```

b*)
```sql
SELECT Username, Password FROM Users
```

c)
```sql
SELECT Username AND Password FROM Users
```

---
The JOIN is a SQL keyword used to:

a) verify that the inserted data is correct

b) update database table

c) delete data from database table

d*) select data from 2 or more tables related by common attribute (table column)

---
What does the FROM SQL keyword specify?

a*) The FROM SQL keyword specifies the tables, views, and joined tables used in SELECT, UPDATE and DELETE SQL statements

b) The FROM SQL keyword specifies a search condition

c) The FROM SQL keyword specifies a column list

---
Which of the following SQL statements deletes all rows in table called "students"?

a)
```sql
DELETE students
```

b)
```sql
DELETE ALL students
```

c*)
```sql
DELETE FROM students
```

d)
```sql
DELETE * FROM students
```

---
Which SQL functions is used to count the number of rows in a SQL query?

a*) COUNT()

b) NUMBER()

c) SUM()