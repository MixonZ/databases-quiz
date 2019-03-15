@credits
[sqlzoo.net](https://sqlzoo.net)
@creditsEnd

@snippet(id: 'tables')

**world**

| name        | region      | area    | population | gdp         |
|-------------|-------------|---------|------------|-------------|
| Afghanistan | South Asia  | 652225  | 26000000   |             |
| Albania     | Europe      | 28728   | 3200000    | 6656000000  |
| Algeria     | Middle East | 2400000 | 32900000   | 75012000000 |
| Andorra     | Europe      | 468     | 64000      |             |
| ...         |             |         |            |             |

@snippetEnd

---
@insertSnippet('tables')

Select the code which produces this table:

| name        | population |
|-------------|------------|
| Bahrain     | 1234571    |
| Swaziland   | 1220000    |
| Timor-Leste | 1066409    |
| ...         |            |

a)
```sql
FROM world SELECT name, population BETWEEN 1000000 AND 1250000
```

b)
```sql
FROM name, population WHERE population BETWEEN 1000000 AND 1250000 SELECT world
```

c*)
```sql
SELECT name, population FROM world WHERE population BETWEEN 1000000 AND 1250000
```

d)
```sql
SELECT population BETWEEN 1000000 AND 1250000 FROM world
```

e)
```sql
WHERE population BETWEEN 1000000 AND 1250000 SELECT name, population FROM world
```

---
@insertSnippet('tables')

Pick the result you would obtain from this code:

```sql
SELECT name, population FROM world WHERE name LIKE "Al%"
```

a)
```
+---------+
| Albania |
+---------+
| Algeria |
+---------+
```

b)
```
+--------+----------+
| %bania | 3200000  |
+--------+----------+
| %geria | 32900000 |
+--------+----------+
```

c)
```
+----+---+
| Al | 0 |
+----+---+
```

d)
```
+---------+---------+
| Albania | 3200000 |
+---------+---------+
```

e*)
```
+---------+----------+
| Albania | 3200000  |
+---------+----------+
| Algeria | 32900000 |
+---------+----------+
```

---
@insertSnippet('tables')

Select the code which shows the countries that end in A or L

a)
```sql
SELECT name FROM world WHERE name LIKE 'a%' AND name LIKE 'l%'
```

b)
```sql
SELECT name FROM world WHERE name LIKE 'a%' OR name LIKE 'l%'
```

c)
```sql
SELECT name FROM world WHERE name LIKE '%a' AND name LIKE '%l'
```

d)
```sql
SELECT name FROM world WHERE name LIKE '%a' OR 'l%'
```

e*)
```sql
SELECT name FROM world WHERE name LIKE '%a' OR name LIKE '%l'
```

---
@insertSnippet('tables')

Pick the result from the query

a)
```
+-------+--------------+
| name	| length(name) |
+-------+--------------+
| Benin	| 5            |
+-------+--------------+
| Lybia	| 5            |
+-------+--------------+
| Egypt	| 5            |
+-------+--------------+
```

b)
```
+-------+--------------+
| name  | length(name) |
+-------+--------------+
| Italy	| 5            |
+-------+--------------+
| Egypt	| 5            |
+-------+--------------+
| Spain	| 5            |
+-------+--------------+
```

c*)
```
+-------+--------------+
| name  | length(name) |
+-------+--------------+
| Italy	| 5            |
+-------+--------------+
| Malta	| 5            |
+-------+--------------+
| Spain	| 5            |
+-------+--------------+
```

d)
```
+--------+--------------+
| name	 | length(name) |
+--------+--------------+
| Italy	 | 5            |
+--------+--------------+
| France | 6            |
+--------+--------------+
| Spain	 | 5            |
+--------+--------------+
```

e)
```
+--------+--------------+
| name	 | length(name) |
+--------+--------------+
| Sweden | 6            |
+--------+--------------+
| Norway | 6            |
+--------+--------------+
| Poland | 6            |
+--------+--------------+
```

---
@insertSnippet('tables')

Here are the first few rows of the world table:

| name | region | area | population | gdp |
| --- | --- | --- | --- | --- |
| Afghanistan | South Asia | 652225 | 26000000 |
| Albania | Europe | 28728 | 3200000 | 6656000000 |
| Algeria | Middle East | 2400000 | 32900000 | 75012000000 |
| Andorra | Europe | 468 | 64000 |
| ... | | | |

Pick the result you would obtain from this code:

```sql
SELECT name, area*2 FROM world WHERE population = 64000
```

a)
```
+---------+-----+
| Andorra | 234 |
+---------+-----+
```

b)
```
+---------+-----+
| Andorra |	468 |
+---------+-----+
```

c*)
```
+---------+-----+
| Andorra | 936 |
+---------+-----+
```

d)
```
+---------+------+
| Andorra | 4680 |
+---------+------+
```

e)
```
+---------+-------+
| Andorra | 936   |
| Albania | 57456 |
+---------+-------+
```

---
@insertSnippet('tables')

Select the code that would show the countries with an area larger than 50000 and a population smaller than 10000000

a)
```sql
SELECT name, area, population FROM world WHERE area < 50000 AND population < 10000000
```

b)
```sql
SELECT name, area, population FROM world WHERE area < 50000 AND population > 10000000
```

c*)
```sql
SELECT name, area, population FROM world WHERE area > 50000 AND population < 10000000
```

d)
```sql
SELECT name, area, population FROM world WHERE area > 50000 AND population > 10000000
```

e)
```sql
SELECT name, area, population FROM world WHERE area = 50000 AND population = 10000000
```

---
@insertSnippet('tables')

Select the code that shows the population density of China, Australia, Nigeria and France

a)
```sql
SELECT name, area/population FROM world WHERE name IN ('China', 'Nigeria', 'France', 'Australia')
```

b)
```sql
SELECT name, area/population FROM world WHERE name LIKE ('China', 'Nigeria', 'France', 'Australia')
```

c*)
```sql
SELECT name, population/area FROM world WHERE name IN ('China', 'Nigeria', 'France', 'Australia')
```

d)
```sql
SELECT name, population/area FROM world WHERE name LIKE ('China', 'Nigeria', 'France', 'Australia')
```

e)
```sql
SELECT name, population FROM world WHERE name IN ('China', 'Nigeria', 'France', 'Australia')
```