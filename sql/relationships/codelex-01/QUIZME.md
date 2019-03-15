@credits
[codelex.io](https://codelex.io)
@creditsEnd

@snippet(id: 'movies')

**movies**

| id  | title | year |
|-----|-------|------|
| ... |       |      |

@snippetEnd

@snippet(id: 'actors')

**actors**

| id  | name |
|-----|------|
| ... |      |

@snippetEnd

@snippet(id: 'reviews')

**reviews**

| id  | movie_id | review |
|-----|----------|--------|
| ... |          |        |

@snippetEnd

---
Which relationship would be appropriate between "reviews" -> "movies":

@insertSnippet('reviews')

@insertSnippet('movies')

a) many-to-many

b) one-to-one

c) one-to-many

d*) many-to-one

---
Which relationship would be appropriate between "movies" -> "reviews":

@insertSnippet('movies')

@insertSnippet('reviews')

a) many-to-many

b) one-to-one

c*) one-to-many

d) many-to-one

---
Which relationship would be appropriate between "movies" -> "actors":

@insertSnippet('movies')

@insertSnippet('actors')

a*) many-to-many

b) one-to-one

c) one-to-many

d) many-to-one

---
Which relationship would be appropriate between "actors" -> "movies":

@insertSnippet('actors')

@insertSnippet('movies')

a*) many-to-many

b) one-to-one

c) one-to-many

d) many-to-one

---
Intermediate table is needed to achieve one-to-many relationship

a) TRUE

b*) FALSE

---
Intermediate table is needed to achieve many-to-many relationship

a*) TRUE

b) FALSE