-- More JOIN operations

--10.
-- List the films together with the leading star for all 1962 films. 
~~~sql
SELECT title, name
FROM casting JOIN actor ON casting.actorid = actor.id
JOIN movie ON movie.id = casting.movieid
WHERE ord = 1 AND yr = 1962
~~~
