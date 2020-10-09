# More JOIN operations
## UPDATED: 8 OCT 2020

1. List the films where the yr is 1962 
~~~sql
SELECT id, title
 FROM movie
 WHERE yr=1962
 ~~~

2. Give year of 'Citizen Kane'. 
~~~sql
SELECT yr
FROM movie
WHERE title = 'Citizen Kane'
~~~

3. List all of the Star Trek movies, include the id, title and yr (all of these movies include the words Star Trek in the title). Order results by year. 
~~~sql
SELECT id, title, yr
FROM movie
WHERE title LIKE '%Star Trek%'
ORDER BY yr
~~~

4. What id number does the actor 'Glenn Close' have? 
~~~sql
SELECT id
FROM actor
WHERE name = 'Glenn Close'
~~~

5. What is the id of the film 'Casablanca' 
~~~sql
SELECT id
FROM movie
WHERE title = 'Casablanca'
~~~

6. Obtain the cast list for 'Casablanca'. 
~~~sql
SELECT name
FROM casting JOIN actor ON casting.actorid = actor.id
WHERE movieid = (SELECT id
                 FROM movie
                 WHERE title = 'Casablanca')
~~~

7. Obtain the cast list for the film 'Alien' 
~~~sql
SELECT name
FROM casting JOIN actor ON casting.actorid = actor.id
WHERE movieid = (SELECT id
                 FROM movie
                 WHERE title = 'Alien')
~~~

8. List the films in which 'Harrison Ford' has appeared 
~~~sql
SELECT title
FROM movie
WHERE id IN (SELECT movieid
             FROM actor JOIN casting ON actor.id = casting.actorid
             WHERE name = 'Harrison Ford')
~~~

9. List the films where 'Harrison Ford' has appeared - but not in the starring role. 
~~~sql
SELECT title
FROM movie
WHERE id IN (SELECT movieid
             FROM actor JOIN casting ON actor.id = casting.actorid
             WHERE name = 'Harrison Ford' AND ord != 1)
~~~


10. List the films together with the leading star for all 1962 films. 
~~~sql
SELECT title, name
FROM casting JOIN actor ON casting.actorid = actor.id
JOIN movie ON movie.id = casting.movieid
WHERE ord = 1 AND yr = 1962
~~~

