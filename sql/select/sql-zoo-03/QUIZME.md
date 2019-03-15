@credits
[sqlzoo.net](https://sqlzoo.net)
@creditsEnd

@snippet(id: 'tables')

**nobel**

| yr   | subject    | winner                      |
|------|------------|-----------------------------|
| 1960 | Chemistry  | Willard F. Libby            |
| 1960 | Literature | Saint-John Perse            |
| 1960 | Medicine   | Sir Frank Macfarlane Burnet |
| 1960 | Medicine   | Peter Medawar               |
| 1960 | Physics    | Donald A. Glaser            |
| 1960 | Peace      | Albert Lutuli               |

@snippetEnd

---
@insertSnippet('tables')

Pick the code which shows the name of winner's names beginning with C and ending in n

a)
```sql
SELECT name FROM nobel WHERE winner LIKE '%C%' AND winner LIKE '%n%'
```

b)
```sql
SELECT name FROM nobel WHERE winner LIKE '%C' AND winner LIKE 'n%'
```

c)
```sql
SELECT name FROM nobel WHERE winner LIKE 'C%' AND winner LIKE '%n'
```

d)
```sql
SELECT winner FROM nobel WHERE winner LIKE '%C' AND winner LIKE 'n%'
```

e*)
```sql
SELECT winner FROM nobel WHERE winner LIKE 'C%' AND winner LIKE '%n'
```

---
@insertSnippet('tables')

Select the code that shows how many Chemistry awards were given between 1950 and 1960

a)
```sql
SELECT COUNT(subject) FROM nobel WHERE subject = 'Chemistry' AND BETWEEN 1950 and 1960
```

b)
```sql
SELECT COUNT(subject) FROM nobel WHERE subject = 'Chemistry' AND yr BETWEEN (1950, 1960)
```

c*)
```sql
SELECT COUNT(subject) FROM nobel WHERE subject = 'Chemistry' AND yr BETWEEN 1950 and 1960
```

d)
```sql
SELECT subject FROM nobel WHERE subject = 'Chemistry' AND yr BETWEEN 1950 and 1960
```

e)
```sql
SELECT subject FROM nobel WHERE subject = 'Chemistry' AND yr BETWEEN (1950, 1960)
```

---
@insertSnippet('tables')

Pick the code that shows the amount of years where no Medicine awards were given

a)
```sql
SELECT COUNT(DISTINCT yr) FROM nobel WHERE yr IN (SELECT DISTINCT yr FROM nobel WHERE subject <> 'Medicine')
```

b*)
```sql
SELECT COUNT(DISTINCT yr) FROM nobel WHERE yr NOT IN (SELECT DISTINCT yr FROM nobel WHERE subject = 'Medicine')
```

c)
```sql
SELECT DISTINCT yr FROM nobel WHERE yr NOT IN (SELECT DISTINCT yr FROM nobel WHERE subject LIKE 'Medicine')
```

d)
```sql
SELECT COUNT(DISTINCT yr) FROM nobel WHERE yr NOT IN (SELECT DISTINCT yr FROM nobel WHERE subject NOT LIKE 'Medicine')
```

e)
```sql
SELECT COUNT(yr) FROM nobel WHERE yr NOT IN (SELECT DISTINCT yr FROM nobel WHERE subject = 'Medicine')
```

---
@insertSnippet('tables')

Select the result that would be obtained from the following code:

```sql
SELECT subject, winner FROM nobel WHERE winner LIKE 'Sir%' AND yr LIKE '196%'
```

a)
+----------+-------------------------+
| Medicine | John Eccles             |
+----------+-------------------------+
| Medicine | Frank Macfarlane Burnet |
+----------+-------------------------+

b)
+-----------+-----------------------+
| Chemistry | Sir Cyril Hinshelwood |
+-----------+-----------------------+

c*)
+----------+-----------------------------+
| Medicine | Sir John Eccles             |
+----------+-----------------------------+
| Medicine | Sir Frank Macfarlane Burnet |
+----------+-----------------------------+

d)
+-----------+-------------------------+
| Medicine  | John Eccles             |
+-----------+-------------------------+
| Medicine  | Frank Macfarlane Burnet |
+-----------+-------------------------+
| Chemistry | Willard F.Libby         |
+-----------+-------------------------+

e)
+-----------------------------+
| Sir John Eccles             |
+-----------------------------+
| Sir Frank Macfarlane Burnet |
+-----------------------------+

---
@insertSnippet('tables')

Select the code which would show the year when neither a Physics or Chemistry award was given

a)
```sql
SELECT yr FROM nobel
  WHERE subject NOT IN(SELECT yr FROM nobel WHERE subject IN ('Chemistry','Physics'))
```

b)
```sql
SELECT yr FROM nobel
  WHERE subject NOT IN(SELECT subject FROM nobel WHERE subject IN ('Chemistry','Physics'))
```

c*)
```sql
SELECT yr FROM nobel
  WHERE yr NOT IN(SELECT yr FROM nobel WHERE subject IN ('Chemistry','Physics'))
```

d)
```sql
SELECT yr FROM nobel
  WHERE yr NOT IN(SELECT subject FROM nobel WHERE subject IN ('Chemistry','Physics'))
```

e)
```sql
SELECT yr FROM subject
  WHERE yr NOT IN (SELECT yr FROM nobel WHERE subject IN ('Chemistry','Physics'))
```

---
@insertSnippet('tables')

Select the code which shows the years when a Medicine award was given but no Peace or Literature award was

a)
```sql
SELECT DISTINCT yr
  FROM nobel
  WHERE subject='Medicine' AND subject NOT IN (SELECT yr from nobel WHERE subject='Literature')
  AND yr NOT IN (SELECT yr FROM nobel WHERE subject='Peace')
```

b)
```sql
SELECT DISTINCT yr
  FROM nobel WHERE subject='Medicine'
  AND yr NOT IN (SELECT yr from nobel WHERE subject='Literature' AND subject='Peace')
```

c*)
```sql
SELECT DISTINCT yr
  FROM nobel
  WHERE subject='Medicine' 
  AND yr NOT IN (SELECT yr FROM nobel WHERE subject='Literature')
  AND yr NOT IN (SELECT yr FROM nobel WHERE subject='Peace')
```

d)
```sql
SELECT DISTINCT yr
  FROM subject
  WHERE subject='Medicine'
  AND yr NOT IN (SELECT yr from nobel WHERE subject='Literature' AND subject='Peace')
```

e)
```sql
SELECT DISTINCT yr
  FROM subject
  WHERE subject='Medicine' AND yr NOT IN('Literature','Peace')
```

---
@insertSnippet('tables')

Pick the result that would be obtained from the following code:

```sql
SELECT subject, COUNT(subject) 
  FROM nobel 
  WHERE yr ='1960' 
  GROUP BY subject
```

a)
+---+
| 1 |
+---+
| 1 |
+---+
| 2 |
+---+
| 1 |
+---+
| 1 |
+---+

b)
+-----------+---+
| Chemistry | 6 |
+-----------+---+

c)
+------------+---+
| Chemistry  | 3 |
+------------+---+
| Literature | 1 |
+------------+---+
| Medicine   | 2 |
+------------+---+
| Peace      | 0 |
+------------+---+
| Physics    | 2 |
+------------+---+

d*)
+------------+---+
| Chemistry  | 1 |
+------------+---+
| Literature | 1 |
+------------+---+
| Medicine   | 2 |
+------------+---+
| Peace      | 1 |
+------------+---+
| Physics    | 1 |
+------------+---+

e)
+------------+---+
| Chemistry  | 1 |
+------------+---+
| Literature | 1 |
+------------+---+
| Peace      | 1 |
+------------+---+
| Physics    | 1 |
+------------+---+
