@credits
[sqlzoo.net](https://sqlzoo.net)
@creditsEnd

@snippet(id: 'tables')

**world**

| name        | continent     | area    | population | gdp          |
|-------------|---------------|---------|------------|--------------|
| Afghanistan | South Asia    | 652225  | 26000000   |              |	
| Albania     | Europe        | 28728   | 3200000    | 6656000000   |
| Algeria     | Middle East   | 2400000 | 32900000   | 75012000000  |
| Andorra     | Europe        | 468     | 64000      |              |
| Brazil      | South America | 8550000 | 182800000  | 564852000000 |
| Colombia    | South America | 1140000 | 45600000   |              |
| Nauru       | Asia-Pacific  | 21      | 9900       |              |
| Uzbekistan  | Central Asia  | 447000  | 26000000   |              |
| ...         |               |         |            |              |

@snippetEnd

---
@insertSnippet('tables')

Select the code which gives the name of countries beginning with U:

a)
```sql
SELECT name FROM world WHERE name BEGIN with U
```

b)
```sql
SELECT name FROM world WHERE name LIKE '%U'
```

c)
```sql
SELECT name FROM world WHERE name LIKE '%u%'
```

d)
```sql
SELECT name FROM world WHERE name LIKE U
```

e*)
```sql
SELECT name FROM world WHERE name LIKE 'U%'
```

---
@insertSnippet('tables')

Select the code which shows just the population of United Kingdom:

a)
```sql
SELECT population FROM 'United Kingdom'
```

b)
```sql
SELECT name FROM world WHERE population = 'United Kingdom'
```

c)
```sql
SELECT FROM world WHERE population IN 'United Kingdom'
```

d*)
```sql
SELECT population FROM world WHERE name = 'United Kingdom'
```

e)
```sql
SELECT population FROM world WHERE 'United Kingdom' IN name
```

---
@insertSnippet('tables')

Select the answer which shows the problem with this SQL code - the intended result should be the continent of France:

```sql
 SELECT continent FROM world WHERE 'name' = 'France'
```

a) continent should be 'continent'

b*) 'name' should be name

c) 'France' should be "France"

d) 'France' should be France

e) = should be IN

---
@insertSnippet('tables')

Select the result that would be obtained from the following code:

```sql
SELECT name, population / 10 FROM world WHERE population < 10000
```

a)
+---------+------+
| Andorra | 6400 |
+---------+------+
| Nauru   | 990  |
+---------+------+

b)
+---------+-------+
| Andorra | 64000 |
+---------+-------+
| Nauru   | 9900  |
+---------+-------+

c)
+-------+----+
| Nauru | 99 |
+-------+----+

d*)
+-------+-----+
| Nauru | 990 |
+-------+-----+

e)
+-------+------+
| Nauru | 9900 |
+-------+------+

---
@insertSnippet('tables')

Select the code which would reveal the name and population of countries in Europe and Asia

a)
```sql
SELECT name FROM world WHERE continent IN ('Europe', 'Asia')
```

b*)
```sql
SELECT name, population FROM world WHERE continent IN ('Europe', 'Asia')
```

c)
```sql
SELECT name, population FROM world WHERE name IN (Europe Asia)
```

d)
```sql
SELECT name, population FROM world WHERE name IS ('Europe', 'Asia')
```

e)
```sql
SELECT name, population FROM world WHERE continent = ('Europe', 'Asia')
```

---
@insertSnippet('tables')

Select the code which would give two rows

a)
```sql
SELECT name FROM world WHERE name = 'Cuba'
```

b)
```sql
SELECT name FROM world WHERE name = 'Cuba' AND name = 'Togo'
```

c)
```sql
SELECT name FROM world WHERE name EITHER ('Cuba', 'Togo')
```

d*)
```sql
SELECT name FROM world WHERE name IN ('Cuba', 'Togo')
```

e)
```sql
SELECT name FROM WHERE name IS 'Mali'
```

---
@insertSnippet('tables')

Select the result that would be obtained from this code

```sql
SELECT name FROM world WHERE continent = 'South America' AND population > 40000000
```

a)

+-------------+
| Afghanistan |
+-------------+
| Brazil      |
+-------------+
| Colombia    |
+-------------+

b)
+-------------+
| Brazil      |
+-------------+

c*)
+-------------+
| Brazil      |
+-------------+
| Colombia    |
+-------------+

d)
+----------+---------------+
| Brazil   | South America |
+----------+---------------+
| Colombia | South America |
+----------+---------------+

e)
+----------+-----------+
| Brazil   | 182800000 |
+----------+-----------+
| Colombia | 45600000  |
+----------+-----------+
