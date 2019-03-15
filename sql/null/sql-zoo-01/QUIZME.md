@credits
[sqlzoo.net](https://sqlzoo.net)
@creditsEnd

@snippet(id: 'tables')

*teacher*

| id  | dept | name       | phone |
|-----|------|------------|-------|
| 101 | 1    | Shrivell   | 2753  |
| 102 | 1    | Throd      | 2754  |
| 103 | 1    | Splint     |       |
| 104 | 	 | Spiregrain |       |
| 105 | 2    | Cutflower  | 3212  |
| 106 | 	 | Deadyawn   |       |

*dept*

| id | name        |
|----|-------------|
| 1  | Computing   |
| 2  | Design      |
| 3  | Engineering |

@snippetEnd

---
@insertSnippet('tables')

Select the code which uses an outer join correctly.

a)
```sql
SELECT teacher.name, dept.name FROM teacher JOIN dept ON (dept = id)
```

b)
```sql
SELECT teacher.name, dept.name FROM teacher, dept INNER JOIN ON (teacher.dept = dept.id)
```

c)
```sql
SELECT teacher.name, dept.name FROM teacher, dept JOIN WHERE(teacher.dept = dept.id)
```

d)
```sql
SELECT teacher.name, dept.name FROM teacher OUTER JOIN dept ON dept.id
```

e*)
```sql
SELECT teacher.name, dept.name FROM teacher LEFT OUTER JOIN dept ON (teacher.dept = dept.id)
```

---
@insertSnippet('tables')

Select the correct statement that shows the name of department which employs Cutflower -

a)
```sql
SELECT dept.name FROM teacher
  JOIN dept ON (dept.id = (SELECT dept FROM teacher WHERE name = 'Cutflower'))
```

b)
```sql
SELECT dept.name FROM teacher JOIN dept ON (dept.id = teacher.dept)
  WHERE dept.id = (SELECT dept FROM teacher HAVING name = 'Cutflower')
```

c*)
```sql
SELECT dept.name FROM teacher
  JOIN dept ON (dept.id = teacher.dept) WHERE teacher.name = 'Cutflower'
```

d)
```sql
SELECT dept.name FROM teacher
  JOIN dept WHERE dept.id = (SELECT dept FROM teacher WHERE name = 'Cutflower')
```

e)
```sql
SELECT name FROM teacher
  JOIN dept ON (id = dept) WHERE id = (SELECT dept FROM teacher WHERE name = 'Cutflower')
```

---
@insertSnippet('tables')

Select out of following the code which uses a JOIN to show a list of all the departments and number of employed teachers

a)
```sql
SELECT dept.name, COUNT(*) FROM teacher
  LEFT JOIN dept ON dept.id = teacher.dept
```

b)
```sql
SELECT dept.name, COUNT(teacher.name) FROM teacher, dept
  JOIN ON dept.id = teacher.dept GROUP BY dept.name
```

c)
```sql
SELECT dept.name, COUNT(teacher.name) FROM teacher
  JOIN dept ON dept.id = teacher.dept GROUP BY dept.name
```

d)
```sql
SELECT dept.name, COUNT(teacher.name) FROM teacher
  LEFT OUTER JOIN dept ON dept.id = teacher.dept GROUP BY dept.name
```

e*)
```sql
SELECT dept.name, COUNT(teacher.name) FROM teacher
  RIGHT JOIN dept ON dept.id = teacher.dept GROUP BY dept.name
```

---
@insertSnippet('tables')

Using 

```sql
SELECT name, dept, COALESCE(dept, 0) AS result FROM teacher
```
 
on teacher table will:

a) display 0 in result column for all teachers

b*) display 0 in result column for all teachers without department

c) do nothing - the statement is incorrect

d) set dept value of all teachers to 0

e) set dept value of all teachers without department to 0

---
@insertSnippet('tables')

Query:

```sql
SELECT name,
  CASE WHEN phone = 2752 THEN 'two'
    WHEN phone = 2753 THEN 'three'
    WHEN phone = 2754 THEN 'four'
    END AS digit
  FROM teacher
```
 
shows following 'digit':

a*) 'four' for Throd

b) NULL for all teachers

c) NULL for Shrivell

d) 'two' for Cutflower

e) 'two' for Deadyawn

---
@insertSnippet('tables')

Select the result that would be obtained from the following code:

```sql
SELECT name, 
  CASE 
    WHEN dept 
    IN (1) 
    THEN 'Computing' 
    ELSE 'Other' 
    END 
  FROM teacher
```

a*)
+------------+-----------+
| Shrivell   | Computing |
+------------+-----------+
| Throd      | Computing |
+------------+-----------+
| Splint     | Computing |
+------------+-----------+
| Spiregrain | Other     |
+------------+-----------+
| Cutflower  | Other     |
+------------+-----------+
| Deadyawn   | Other     |
+------------+-----------+

b)
+------------+-----------+
| Shrivell   | Computing |
+------------+-----------+
| Throd      | Computing |
+------------+-----------+
| Splint     | Computing |
+------------+-----------+
| Spiregrain | Computing |
+------------+-----------+
| Cutflower  | Computing |
+------------+-----------+
| Deadyawn   | Computing |
+------------+-----------+

c)
+----------+-----------+
| Shrivell | Computing |
+----------+-----------+
| Throd    | Computing |
+----------+-----------+
| Splint   | Computing |
+----------+-----------+

d)
+------------+-------+
| Spiregrain | Other |
+------------+-------+
| Cutflower  | Other |
+------------+-------+
| Deadyawn   | Other |
+------------+-------+

e)
+------------+---+
| Shrivell   | 1 |
+------------+---+
| Throd      | 1 |
+------------+---+
| Splint     | 1 |
+------------+---+
| Spiregrain | 0 |
+------------+---+
| Cutflower  | 0 |
+------------+---+
| Deadyawn   | 0 |
+------------+---+
