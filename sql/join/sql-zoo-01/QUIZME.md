@credits
[sqlzoo.net](https://sqlzoo.net)
@creditsEnd

@snippet(id: 'tables')

*game*

| id   | mdate        | stadium                   | team1 | team2 |
|------|--------------|---------------------------|-------|-------|
| 1001 | 8 June 2012  | National Stadium, Warsaw  | POL   | GRE   |
| 1002 | 8 June 2012  | Stadion Miejski (Wroclaw) | RUS   | CZE   |
| 1003 | 12 June 2012 | Stadion Miejski (Wroclaw) | GRE   | CZE   |
| 1004 | 12 June 2012 | National Stadium, Warsaw  | POL   | RUS   |
| ...  |              |                           |       |       |

*goal*

| matchid | teamid | player               | gtime |
|---------|--------|----------------------|-------|
| 1001    | POL    | Robert Lewandowski   | 17    |
| 1001    | GRE    | Dimitris Salpingidis | 51    |
| 1002    | RUS    | Alan Dzagoev         | 15    |
| 1001    | RUS    | Roman Pavlyuchenko   | 82    |
| ...     |        |                      |       |

*eteam*

| id  | teamname       | coach            |
|-----|----------------|------------------|
| POL | Poland	       | Franciszek Smuda |
| RUS | Russia	       | Dick Advocaat    |
| CZE | Czech Republic | Michal Bilek     |
| GRE | Greece         | Fernando Santos  |
| ... |                |                  |

@snippetEnd

---
@insertSnippet('tables')

You want to find the stadium where player 'Dimitris Salpingidis' scored. Select the JOIN condition to use:

a)
```sql
eteam JOIN game ON (id=team1)
```

b)
```sql
eteam JOIN game ON (id=team2)
```

c)
```sql
eteam JOIN goal ON (teamid=id)
```

d*)
```sql
game  JOIN goal ON (id=matchid)
```

e)
```sql
game  JOIN goal ON (team1=teamid OR team2=teamid)
```

---
@insertSnippet('tables')

You JOIN the tables goal and eteam in an SQL statement. Indicate the list of column names that may be used in the SELECT line:

a)
```sql
gtime, mdate, stadium, matchid
```

b)
```sql
mdate, stadium, id
```

c*)
```sql
matchid, teamid, player, gtime, id, teamname, coach
```

d)
```sql
matchid, teamid, player, gtime, mdate, stadium, team1
```

e)
```sql
stadium, team1, team2
```

---
@insertSnippet('tables')

Select the code which shows players, their team and the amount of goals they scored against Greece(GRE).

a*)
```sql
SELECT player, teamid, COUNT(*)
  FROM game JOIN goal ON matchid = id
  WHERE (team1 = "GRE" OR team2 = "GRE")
  AND teamid != 'GRE'
  GROUP BY player, teamid
```

b)
```sql
SELECT player, teamid, COUNT(*)
  FROM game JOIN goal ON matchid = id
  WHERE (team1 = "GRE") AND teamid != 'GRE'
  GROUP BY player, teamid
```

c)
```sql
SELECT player, teamid, COUNT(*)
  FROM game JOIN goal ON matchid = id
  WHERE (team1 = "POL" OR team2 = "POL")
  AND teamid != 'POL'
  GROUP BY player, teamid
```

d)
```sql
SELECT player, teamid, COUNT(*)
  FROM game JOIN goal WITH matchid = id
  WHERE (team1 = "GRE" OR team2 = "GRE")
  AND teamid != 'GRE'
  GROUP BY player, teamid
```

e)
```sql
SELECT player, teamid
  FROM game JOIN goal ON matchid = id
  WHERE (team1 = "GRE" OR team2 = "GRE")
  AND teamid != 'GRE'
  GROUP BY player, teamid
```

---
@insertSnippet('tables')

Select the result that would be obtained from this code:

```sql
SELECT DISTINCT teamid, mdate
  FROM goal JOIN game on (matchid=id)
  WHERE mdate = '9 June 2012'
```

a*)
```
+-----+-------------+
| DEN | 9 June 2012 |
+-----+-------------+
| GER | 9 June 2012 |
+-----+-------------+
```

b)
```
+-----+
| DEN |
+-----+
| GER |
+-----+
```

c)
```
+-----+-------------+
| DEN | 9 June 2012 |
+-----+-------------+
| DEN | 9 June 2012 |
+-----+-------------+
| POL | 9 June 2012 |
+-----+-------------+
| RUS | 9 June 2012 |
+-----+-------------+
```

d)
```
+-----+
| GRE |
+-----+
| CZE |
+-----+
| POL |
+-----+
| RUS |
+-----+
```

e)
```
+-----+-------------+
| RUS | 9 June 2012 |
+-----+-------------+
| GRE | 9 June 2012 |
+-----+-------------+
| RUS | 9 June 2012 |
+-----+-------------+
| CZE | 9 June 2012 |
+-----+-------------+
```

---
@insertSnippet('tables')

Select the code which would show the player and their team for those who have scored against Poland(POL) in National Stadium, Warsaw.

a)
```sql
SELECT DISTINCT player, teamid 
  FROM game JOIN goal ON matchid = id 
  WHERE stadium = 'National Stadium, Warsaw' 
  AND (team1 = 'GER' OR team2 = 'GER')
  AND teamid != 'GER'
```

b*)
```sql
SELECT DISTINCT player, teamid 
  FROM game JOIN goal ON matchid = id 
  WHERE stadium = 'National Stadium, Warsaw' 
  AND (team1 = 'POL' OR team2 = 'POL')
  AND teamid != 'POL'
```

c)
```sql
SELECT DISTINCT player, teamid
  FROM game JOIN goal ON matchid = id
  WHERE stadium = 'National Stadium, Warsaw' AND teamid != 'POL'
```

d)
```sql
SELECT DISTINCT player, teamid
  FROM game JOIN goal ON matchid = id
  WHERE stadium = 'Stadion Miejski (Wroclaw)'
  AND (team1 = 'POL' OR team2 = 'POL')
  AND teamid != 'POL'
```

e)
```sql
SELECT DISTINCT stadium, mdate
  FROM game JOIN goal ON matchid = id
  WHERE stadium = 'National Stadium, Warsaw'
  AND (team1 = 'POL' OR team2 = 'POL')
  AND teamid != 'POL'
```

---
@insertSnippet('tables')

Select the code which shows the player, their team and the time they scored, for players who have played in Stadion Miejski (Wroclaw) but not against Italy(ITA).

a)
```sql
SELECT DISTINCT player, teamid, gtime
  FROM game JOIN goal ON matchid = id
  WHERE stadium = 'National Stadium, Warsaw'
  AND (( teamid = team2 AND team1 != 'ITA') OR ( teamid = team1 AND team2 != 'ITA'))
```

b)
```sql
SELECT DISTINCT player, teamid, gtime
  FROM game JOIN goal ON matchid = id
  WHERE stadium = 'Stadion Miejski (Wroclaw)'
  AND (( teamid = team2 AND team1 != 'ESP') OR ( teamid = team1 AND team2 != 'ESP'))
```

c*)
```sql
SELECT DISTINCT player, teamid, gtime
  FROM game JOIN goal ON matchid = id
  WHERE stadium = 'Stadion Miejski (Wroclaw)'
  AND (( teamid = team2 AND team1 != 'ITA') OR ( teamid = team1 AND team2 != 'ITA'))
```

d)
```sql
SELECT DISTINCT teamid, gtime
  FROM game JOIN goal ON matchid = id
  WHERE stadium = 'Stadion Miejski (Wroclaw)'
  AND (( teamid = team2 AND team1 != 'ITA') OR ( teamid = team1 AND team2 != 'ITA'))
```

e)
```sql
SELECT DISTINCT player, teamid, gtime
  FROM game JOIN goal ON matchid = id
  WHERE team1 != 'ITA' AND team2 !='ITA'
```

---
@insertSnippet('tables')

Select the result that would be obtained from this code:

```sql
SELECT teamname, COUNT(*)
  FROM eteam JOIN goal ON teamid = id
  GROUP BY teamname
  HAVING COUNT(*) < 3
```

a)
```
+---+
| 2 |
+---+
| 2 |
+---+
| 1 |
+---+
| 2 |
+---+
```

b*)
```
+---------------------+---+
| Netherlands         | 2 |
+---------------------+---+
| Poland              | 2 |
+---------------------+---+
| Republic of Ireland | 1 |
+---------------------+---+
| Ukraine             | 2 |
+---------------------+---+
```

c)
```
+---------------------+
| Netherlands         |
+---------------------+
| Poland              |
+---------------------+
| Republic of Ireland |
+---------------------+
| Ukraine             |
+---------------------+
```

d)
```
+--------+----+
| Poland | 76 |
+--------+----+
```

e)
```
+---------------------+---+
| Republic of Ireland | 1 |
+---------------------+---+
```
