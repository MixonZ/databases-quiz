@credits
[sqlzoo.net](https://sqlzoo.net)
@creditsEnd

@snippet(id: 'tables')

**bbc**

| name        | region      | area    | population | gdp         |
|-------------|-------------|---------|------------|-------------|
| Afghanistan | South Asia  | 652225  | 26000000   |             |
| Albania     | Europe      | 28728   | 3200000    | 6656000000  |
| Algeria     | Middle East | 2400000 | 32900000   | 75012000000 |
| Andorra     | Europe      | 468     | 64000      |             |

@snippetEnd

---
@insertSnippet('tables')

Select the statement that shows the sum of population of all countries in 'Europe'

a)
```sql
SELECT name, population FROM bbc WHERE region = 'Europe'
```

b)
```sql
SELECT population FROM bbc WHERE region = 'Europe' SUM BY region
```

c*)
```sql
SELECT SUM(population) FROM bbc WHERE region = 'Europe'
```

d)
```sql
SELECT SUM(population FROM bbc WHERE region = 'Europe')
```

e)
```sql
SUM population FROM bbc WHERE region = 'Europe'
```

---
@insertSnippet('tables')

Select the statement that shows the number of countries with population smaller than 150000

a*)
```sql
SELECT COUNT(name) FROM bbc WHERE population < 150000
```

b)
```sql
SELECT COUNT(population < 150000) FROM bbc
```

c)
```sql
SELECT name FROM bbc WHERE population < 150000
```

d)
```sql
SELECT population AS COUNT FROM bbc WHERE population < 150000
```

e)
```sql
SELECT SUM() FROM bbc WHERE population < 150000
```

---
Select the list of core SQL aggregate functions

a) AVG(), COUNT(), FIRST(), LAST(), SUM()

b) AVG(), COUNT(), MAX(), MEDIAN(), MIN(), ROUND(), SUM()

c) AVG(), COUNT(), CONCAT(), FIRST(), LAST(), MAX(), MIN(), SUM()

d*) AVG(), COUNT(), MAX(), MIN(), SUM()

e) COUNT(), SUM()

---
@insertSnippet('tables')

Select the result that would be obtained from the following code:

```sql
SELECT region, SUM(area) FROM bbc WHERE SUM(area) > 15000000 GROUP BY region
```

a)
+--------+----------+
| Europe | 17000000 |
+--------+----------+

b)
+---------------+----------+
| Europe        | 17000000 |
+---------------+----------+
| Asia-Pacific  | 23460000 |
+---------------+----------+
| North America | 21660000 |
+---------------+----------+

c)
+---------------+
| Europe        |
+---------------+
| Asia-Pacific  |
+---------------+
| North America |
+---------------+

d) No result due to invalid use of the GROUP BY function

e*) No result due to invalid use of the WHERE function

---
@insertSnippet('tables')

Select the statement that shows the average population of 'Poland', 'Germany' and 'Denmark'

a)
```sql
SELECT AVG(population) FROM bbc WHERE name = ('Poland', 'Germany', 'Denmark')
```

b*)
```sql
SELECT AVG(population) FROM bbc WHERE name IN ('Poland', 'Germany', 'Denmark')
```

c)
```sql
SELECT AVG(population) FROM bbc WHERE name LIKE ('Poland', 'Germany', 'Denmark')
```

d)
```sql
SELECT AVG(population) FROM bbc WHERE name LIKE (Poland, Germany, Denmark)
```

e)
```sql
SELECT population FROM bbc WHERE name IN ('Poland', 'Germany', 'Denmark')
```

---
@insertSnippet('tables')

Select the statement that shows the medium population density of each region

a)
```sql
SELECT region, AVG(population/area) AS density FROM bbc
```

b)
```sql
SELECT region, COUNT(population)/COUNT(area) AS density FROM bbc GROUP BY region
```

c)
```sql
SELECT region, SUM(population)/COUNT(area) AS density FROM bbc GROUP BY region
```

d)
```sql
SELECT region, SUM(population)/SUM(area) AS density FROM bbc HAVING region
```

e*)
```sql
SELECT region, SUM(population)/SUM(area) AS density FROM bbc GROUP BY region
```

---
@insertSnippet('tables')

Select the statement that shows the name and population density of the country with the largest population

a)
```sql
SELECT name, density AS population/area FROM bbc WHERE population = MAX(population)
```

b)
```sql
SELECT name, density AS population/area FROM bbc WHERE population = (SELECT MAX(population) FROM bbc)
```

c)
```sql
SELECT name, MAX (population) FROM bbc WHERE population / (SELECT area FROM bbc)
```

d*)
```sql
SELECT name, population/area AS density FROM bbc WHERE population = (SELECT MAX(population) FROM bbc)
```

e)
```sql
 SELECT name, population/area AS density FROM bbc WHERE population > (SELECT MAX(population) FROM bbc)
```

---
@insertSnippet('tables')

Pick the result that would be obtained from the following code:

```sql
SELECT region, SUM(area) FROM bbc GROUP BY region HAVING SUM(area) <= 20000000
```

a)
+----------+
| 732240   |
+----------+
| 13403102 |
+----------+
| 17740392 |
+----------+
| 4943771  |
+----------+

b)
+---------------+----------+
| Africa        | 22550927 |
+---------------+----------+
| Asia-Pacific  | 28759578 |
+---------------+----------+
| Europe        | 23866987 |
+---------------+----------+
| North America | 21660000 |
+---------------+----------+

c)
+---------------+
| Africa        |
+---------------+
| Asia-Pacific  |
+---------------+
| Europe        |
+---------------+
| North America |
+---------------+

d*)
+---------------+----------+
| Americas      | 732240   |
+---------------+----------+
| Middle East   | 13403102 |
+---------------+----------+
| South America | 17740392 |
+---------------+----------+
| South Asia    | 9437710  |
+---------------+----------+

e)
+---------------+
| Americas      |
+---------------+
| Middle East   |
+---------------+
| South America |
+---------------+
| South Asia    |
+---------------+
