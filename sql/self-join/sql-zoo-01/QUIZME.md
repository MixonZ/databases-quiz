@credits
[sqlzoo.net](https://sqlzoo.net)
@creditsEnd

@snippet(id: 'tables')

**stops**

| id  | name | pos | stop |
|-----|------|-----|------|
| ... |      |     |      |

**route**

| num | company |
|-----|---------|
| ... |         |

@snippetEnd

---
@insertSnippet('tables')

Select the code that would show it is possible to get from Craiglockhart to Haymarket

a)
```sql
SELECT DISTINCT a.name, b.name
  FROM stops a JOIN route z IN a.id=z.stop
  JOIN route y ON y.num = z.num
  JOIN stops b IN y.stop=b.id
  WHERE a.name='Craiglockhart' AND b.name ='Haymarket'
```

b)
```sql
SELECT DISTINCT a.name, b.name
  FROM stops a JOIN route z ON a.id=z.stop
  JOIN route y JOIN stops b ON y.stop=b.id
  WHERE a.name='Craiglockhart' AND b.name ='Haymarket'
```

c*)
```sql
SELECT DISTINCT a.name, b.name
  FROM stops a JOIN route z ON a.id=z.stop
  JOIN route y ON y.num = z.num
  JOIN stops b ON y.stop=b.id
  WHERE a.name='Craiglockhart' AND b.name ='Haymarket'
```

d)
```sql
SELECT DISTINCT a.name, b.name from stops a
  JOIN route z ON a.id=z.stop
  JOIN route y ON y.num = z.num
  JOIN stops b ON y.stop=b.id
  WHERE a.name='Craiglockhart' AND b.name ='Sighthill'
```

e)
```sql
SELECT DISTINCT a.name, b.name
  FROM stops a JOIN route z ON a.id=z.stop
  JOIN route y ON y.num = z.num
  JOIN stops b ON y.stop=b.id
  WHERE y.name='Craiglockhart' AND z.name ='Haymarket'
```

---
@insertSnippet('tables')

Select the code that shows the stops that are on route.num '2A' which can be reached with one bus from Haymarket?

a)
```sql
SELECT S2.id, S2.name, R2.company, R2.num
  FROM stops S1, stops S2, route R1, route R2
  WHERE S1.name='Haymarket' AND S1.id=R1.stop
  AND R1.company=R2.company AND R1.num=R2.num
  AND R2.stop=S2.id AND R1.num='2A'
```

b)
```sql
SELECT S2.id, S2.name, R2.company, R2.num
  FROM stops S1, stops S2, route R1, route R2
  WHERE S1.name='Craiglockhart' AND S1.id=R1.stop
  AND R1.company=R2.company AND R1.num=R2.num
  AND R2.stop=S2.id AND R2.num='2A'
```

c)
```sql
SELECT S2.id, S2.name, R2.company, R2.num
  FROM stops S1, stops S2, route R1, route R2
  WHERE S1.name='Haymarket' AND S1.id=R1.stop
  AND R1.company=R2.company AND R1.num=R2.num
  AND R2.stop=S2.id
```

d)
```sql
SELECT S2.id, S2.name, R2.company, R2.num
  FROM stops S1, stops S2, route R1, route R2
 WHERE S1.name='Haymarket' AND S1.id=R1.stop
   AND R1.company=R2.company AND R1.num=R2.num
   AND R2.stop=S2.id AND R2.num='2'
```

e*)
```sql
SELECT S2.id, S2.name, R2.company, R2.num
  FROM stops S1, stops S2, route R1, route R2
  WHERE S1.name='Haymarket' AND S1.id=R1.stop
  AND R1.company=R2.company AND R1.num=R2.num
  AND R2.stop=S2.id AND R2.num='2A'
```

---
@insertSnippet('tables')

Select the code that shows the services available from Tollcross?

a)
```sql
SELECT a.company, a.num, stopa.name, stopb.name
  FROM route a JOIN route b ON (a.company=b.company AND a.num=b.num)
  JOIN stops stopa ON (a.stop=stopa.id)
  JOIN stops stopb ON (b.stop=stopb.id)
```

b)
```sql
SELECT a.company, a.num, stopa.name, stopb.name
  FROM route a JOIN route b ON (a.company=b.company AND a.num=b.num)
  JOIN stops stopa ON (a.stop=stopa.id)
  JOIN stops stopb ON (b.stop=stopb.id)
  WHERE stopa.name='Sighthill'
```

c)
```sql
SELECT a.company, a.num, stopa.name, stopb.name
  FROM route a JOIN route b IN (a.company=b.company AND a.num=b.num)
  JOIN stops stopa IN (a.stop=stopa.id)
  JOIN stops stopb ON (b.stop=stopb.id)
  WHERE stopa.name='Tollcross'
```

d*)
```sql
SELECT a.company, a.num, stopa.name, stopb.name
  FROM route a JOIN route b ON (a.company=b.company AND a.num=b.num)
  JOIN stops stopa ON (a.stop=stopa.id)
  JOIN stops stopb ON (b.stop=stopb.id)
  WHERE stopa.name='Tollcross'
```

e)
```sql
SELECT a.company, a.num, stopa.name, stopb.name
  FROM route a JOIN route b ON (a.company=b.company AND a.num=b.num)
  JOIN stops stopa ON (a.stop=stopa.id)
  JOIN stops stopb ON (b.stop=stopb.id)
  WHERE stopz.name='Tollcross'
```