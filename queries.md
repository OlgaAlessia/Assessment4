Make sure you download the starter code and run the following:

```
  psql < movies.sql
  psql movies_db
```

In markdown, you can place a code block inside of three backticks (```) followed by the syntax highlighting you want, for example

```
SELECT \* FROM users;
```

Using the `movies_db` database, write the correct SQL queries for each of these tasks:

1.  The title of every movie.
```
SELECT title FROM movies;
```

2.  All information on the G-rated movies.  
```
SELECT * FROM movies WHERE rating = 'G';
```

3.  The title and release year of every movie, ordered with the oldest movie first.
```
SELECT title, release_year FROM movies OR;
```


4.  All information on the 5 longest movies.
```
SELECT title, release_year 
FROM movies 
ORDER BY release_year ASC LIMIT 20;
```

5.  A query that returns the columns of `rating` and `total`, tabulating the
    total number of G, PG, PG-13, and R-rated movies.
```
SELECT rating, COUNT(*) AS total 
FROM movies 
GROUP BY rating 
ORDER BY rating;
```

6.  A table with columns of `release_year` and `average_runtime`,
    tabulating the average runtime by year for every movie in the database. The data should be in reverse chronological order (i.e. the most recent year should be first).
```
SELECT release_year, AVG(runtime) AS avarage_runtime 
FROM movies 
GROUP BY release_year 
ORDER BY release_year DESC;
```

7.  The movie title and studio name for every movie in the
    database.
```
SELECT m.title, s.name FROM movies AS m JOIN studios AS s ON m.studio_id = s.id;
```

8.  The star first name, star last name, and movie title for every
    matching movie and star pair in the database.
```
SELECT s.first_name, s.last_name, m.title 
FROM stars AS s JOIN roles AS r ON s.id = r.star_id JOIN movies AS m ON r.movie_id = m.id GROUP BY (s.first_name, s.last_name, m.title) 
ORDER BY (s.first_name, s.last_name);
```

9.  The first and last names of every star who has been in a G-rated movie. The first and last name should appear only once for each star, even if they are in several G-rated movies. *IMPORTANT NOTE*: it's possible that there can be two *different* actors with the same name, so make sure your solution accounts for that.
```
SELECT s.first_name, s.last_name 
FROM stars AS s LEFT JOIN roles AS r ON s.id = r.star_id 
JOIN movies AS m ON r.movie_id = m.id WHERE m.rating = 'G' 
GROUP BY (s.first_name, s.last_name);
`````
10. The first and last names of every star along with the number
    of movies they have been in, in descending order by the number of movies. (Similar to #9, make sure that two different actors with the same name are considered separately).
```
SELECT s.first_name, s.last_name, COUNT(*) AS num_movies 
FROM stars AS s LEFT JOIN roles AS r ON s.id = r.star_id 
GROUP BY (s.first_name, s.last_name) 
ORDER BY num_movies DESC;
```

### The rest of these are bonuses

11. The title of every movie along with the number of stars in
    that movie, in descending order by the number of stars.
```
SELECT m.title, COUNT(*) 
FROM movies AS m JOIN roles AS r ON r.movie_id = m.id 
GROUP BY (m.title);
```

12. The first name, last name, and average runtime of the five
    stars whose movies have the longest average.
```
SELECT s.first_name, s.last_name, AVG(runtime) as avarage_runtime 
FROM stars AS s JOIN roles AS r ON s.id = r.star_id 
JOIN movies AS m ON r.movie_id = m.id
GROUP BY (s.first_name, s.last_name, m.title) 
ORDER BY avarage_runtime DESC LIMIT 5;
```

13. The first name, last name, and average runtime of the five
    stars whose movies have the longest average, among stars who have more than one movie in the database.
```
SELECT s.first_name, s.last_name, AVG(runtime) AS avarage_runtime
FROM stars AS s JOIN roles AS r ON s.id = r.star_id 
JOIN movies AS m ON r.movie_id = m.id
GROUP BY (s.first_name, s.last_name) 
HAVING COUNT(star_id) > 1 
ORDER BY avarage_runtime DESC LIMIT 5;
```

14. The titles of all movies that don't feature any stars in our database.
```
SELECT m.title FROM movies AS m WHERE id NOT IN (SELECT r.movie_id FROM roles AS r);
```

15. The first and last names of all stars that don't appear in any movies in our database.
```
SELECT s.first_name, s.last_name 
FROM stars AS s WHERE id NOT IN (SELECT r.star_id FROM roles AS r);
```

16. The first names, last names, and titles corresponding to every
    role in the database, along with every movie title that doesn't have a star, and the first and last names of every star not in a movie.
```
SELECT s.first_name, s.last_name 
FROM stars AS s WHERE id NOT IN (SELECT r.star_id FROM roles AS r);
```
