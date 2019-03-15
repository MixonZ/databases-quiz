@credits
[sqlzoo.net](https://sqlzoo.net)
@creditsEnd

---
Select the statement which lists the unfortunate directors of the movies which have caused financial loses (gross < budget)

a)
```sql
SELECT JOIN(name FROM actor, movie
  ON actor.id:director WHERE gross < budget)
  GROUP BY name
```

b)
```sql
SELECT name
  FROM actor INNER JOIN movie BY actor.id = director
  HAVING gross < budget
```

c*)
```sql
SELECT name
  FROM actor INNER JOIN movie ON actor.id = director
  WHERE gross < budget
```

d)
```sql
SELECT name
  FROM actor INNER JOIN movie ON actor.id:director
  WHERE gross < budget
```

e)
```sql
SELECT name
  FROM director INNER JOIN movie ON movie.id = director.id
  WHERE gross < budget
```

---
Select the correct example of JOINing three tables

a)
```sql
SELECT * 
  FROM actor JOIN casting BY actor.id = actorid
  JOIN movie BY movie.id = movieid
```

b)
```sql
SELECT *
  FROM actor JOIN casting ON actor.id = actorid
  AND JOIN movie ON movie.id = movieid
```

c)
```sql
SELECT *
  FROM actor JOIN casting
  JOIN movie ON actor.id = actorid
  AND movie.id = movieid
```

d)
```sql
SELECT *
  FROM actor JOIN casting ON actor.id = actorid
  AND movie ON movie.id = movieid
```

e*)
```sql
SELECT *
  FROM actor JOIN casting ON actor.id = actorid
  JOIN movie ON movie.id = movieid
```

---
Select the statement that shows the list of actors called 'John' by order of number of movies in which they acted

a)
```sql
SELECT name, COUNT(movieid)
  FROM actor JOIN casting ON actorid=actor.id
  WHERE name IN 'John %'
  GROUP BY name ORDER BY 2
```

b)
```sql
SELECT name, COUNT(movieid)
  FROM actor JOIN casting ON actorid=actor.id
  WHERE name LIKE 'J%'
  GROUP BY name ORDER BY 2 DESC
```

c*)
```sql
SELECT name, COUNT(movieid)
  FROM casting JOIN actor ON actorid=actor.id
  WHERE name LIKE 'John %'
  GROUP BY name ORDER BY 2 DESC
```

d)
```sql
SELECT name, COUNT(movieid)
  FROM casting JOIN actor
  WHERE (actorid ON actor.id)
  AND name LIKE 'John %'
  GROUP BY name ORDER BY 2 DESC
```

e)
```sql
SELECT name, COUNT(movieid)
  FROM casting JOIN actor
  WHERE name LIKE 'John %'
  GROUP BY name ORDER BY COUNT(movieid) DESC
```

---
Select the result that would be obtained from the following code:

```sql
SELECT title 
  FROM movie JOIN casting ON (movieid=movie.id)
  JOIN actor   ON (actorid=actor.id)
  WHERE name='Paul Hogan' AND ord = 1
```

a)
+---------------------------------+---+
| "Crocodile" Dundee              | 1 |
+---------------------------------+---+
| Crocodile Dundee in Los Angeles | 1 |
+---------------------------------+---+
| Flipper                         | 1 |
+---------------------------------+---+
| Lightning Jack                  | 1 |
+---------------------------------+---+

b*)
+---------------------------------+
| "Crocodile" Dundee              |
+---------------------------------+
| Crocodile Dundee in Los Angeles |
+---------------------------------+
| Flipper                         |
+---------------------------------+
| Lightning Jack                  |
+---------------------------------+

c)
+--------------------+
| "Crocodile" Dundee |
+--------------------+
| Paul Hogan         |
+--------------------+
| 1                  |
+--------------------+


d)
+---------------------------------+------------+---+
| "Crocodile" Dundee              | Paul Hogan | 1 |
+---------------------------------+------------+---+
| Crocodile Dundee in Los Angeles | Paul Hogan | 1 |
+---------------------------------+------------+---+
| Flipper                         | Paul Hogan | 1 |
+---------------------------------+------------+---+
| Lightning Jack                  | Paul Hogan | 1 |
+---------------------------------+------------+---+

e)
+---------------------------------+------------+
| "Crocodile" Dundee              | Paul Hogan |
+---------------------------------+------------+
| Crocodile Dundee in Los Angeles | Paul Hogan |
+---------------------------------+------------+
| Flipper                         | Paul Hogan |
+---------------------------------+------------+
| Lightning Jack                  | Paul Hogan |
+---------------------------------+------------+

---
Select the statement that lists all the actors that starred in movies directed by Ridley Scott who has id 351

a)
```sql
SELECT name
  FROM movie JOIN casting
  AND actor ON movie.id = movieid
  AND actor.id = actorid
  WHERE ord = 1
  AND actor = 351
```

b)
```sql
SELECT name
  FROM movie JOIN casting
  JOIN actor ON movie.id = movieid
  OR actor.id = actorid
  WHERE ord = 1 AND director = 351
```

c)
```sql
SELECT name
  FROM movie JOIN casting ON movie.id = movieid
  JOIN actor ON actor.id = actorid
  WHERE ord = 1 AND actorid = 351
```

d*)
```sql
SELECT name
  FROM movie JOIN casting ON movie.id = movieid
  JOIN actor ON actor.id = actorid
  WHERE ord = 1 AND director = 351
```

e)
```sql
SELECT name
  FROM movie JOIN casting ON movie.id = actorid
  JOIN actor ON actor.id = movieid
  WHERE director = 351
```

---
There are two sensible ways to connect movie and actor. They are:

a)
- link the director column in movies with the id column in actor
- join casting to itself

b)
- link the actor column in movies with the primary key in actor
- connect the primary keys of movie and actor via the casting table

c*)
- link the director column in movies with the primary key in actor
- connect the primary keys of movie and actor via the casting table

d)
- link the director column in movies with the primary key in actor
- connect the primary keys of movie and casting via the actor table

e)
- link the movie column in actor with the director column in actor
- connect movie and actor via the casting table

---
Select the result that would be obtained from the following code:

```sql
SELECT title, yr 
  FROM movie, casting, actor 
  WHERE name='Robert De Niro' AND movieid=movie.id AND actorid=actor.id AND ord = 3
```

a)
+----------------------+------+---+
| A Bronx Tale         | 1993 | 3 |
+----------------------+------+---+
| Bang the Drum Slowly | 1973 | 3 |
+----------------------+------+---+
| Limitless            | 2011 | 3 |
+----------------------+------+---+

b*)
+----------------------+------+
| A Bronx Tale         | 1993 |
+----------------------+------+
| Bang the Drum Slowly | 1973 |
+----------------------+------+
| Limitless            | 2011 |
+----------------------+------+

c)
+----------------------+---+
| A Bronx Tale         | 3 |
+----------------------+---+
| Bang the Drum Slowly | 3 |
+----------------------+---+
| Limitless            | 3 |
+----------------------+---+

d)
+----------------------+
| A Bronx Tale         |
+----------------------+
| Bang the Drum Slowly |
+----------------------+
| Limitless            |
+----------------------+

e)
+----------------------+----------------+------+
| A Bronx Tale         | Robert De Niro | 1993 |
+----------------------+----------------+------+
| Bang the Drum Slowly | Robert De Niro | 1973 |
+----------------------+----------------+------+
| Limitless            | Robert De Niro | 2011 |
+----------------------+----------------+------+
