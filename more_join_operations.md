# More JOIN operations

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

