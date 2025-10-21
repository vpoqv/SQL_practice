Table: Movies
<img width="596" height="281" alt="image" src="https://github.com/user-attachments/assets/79c3172e-e60e-4524-8207-4e317f33b8be" />

### Lesson 1
```
SELECT column, another_column, ...
FROM mytable;
```

```
# Find the title of each film
SELECT title FROM movies;
```

```
# Find the title and director of each film
SELECT title, director FROM movies;
```

```
# Find all the information about each film
SELECT * FROM movies;
```

### Lesson 2
```
SELECT column, another_column, ...
FROM mytable
WHERE condition
  AND/OR another_condition
  AND/OR ...;
```

Operator | Condition | SQL Example
------------|--------------------------------|---------------|
=, !=, <, <=, >, >= | Standard numerical operators | col_name != 4
BETWEEN ... AND ... | Number is within range of two values (inclusive) | col_name BETWEEN 1.5 AND 10.5
NOT BETWEEN ... AND ... | Number is not within range of two values (inclusive) | col_name NOT BETWEEN 1 AND 10
IN (...) | Number exists in a list | col_name IN (2, 4, 6)
NOT IN (...) | Number does not exist in a list | col_name NOT IN (1, 3, 5)

```
# Find the movie with a row id of 6
SELECT id, title FROM movies WHERE id = 6;
```

```
# Find the movies released in the years between 2000 and 2010
SELECT title, year FROM movies WHERE year BETWEEN 2000 AND 2010;
```

```
# Find the movies not released in the years between 2000 and 2010
SELECT title, year FROM movies WHERE year < 2000 OR year > 2010;
```

### Lesson 3
Operator | Condition | SExample
------------|--------------------------------|---------------|
= | Case sensitive exact string comparison (notice the single equals) | col_name = "abc"
!= or <> | Case sensitive exact string inequality comparison | col_name != "abcd"
LIKE | Case insensitive exact string comparison | col_name LIKE "ABC"
NOT LIKE | Case insensitive exact string inequality comparison | col_name NOT LIKE "ABCD"
% | Used anywhere in a string to match a sequence of zero or more characters (only with LIKE of NOT LIKE) | col_name LIKE "%AT%" (matches "AT", "ATTIC", "CAT" or "BATS")
_ | Used anywhere in a string to match a single character (only with LIKE or NOT LIKE) | col_name LIKE "AN_" (matched "AND" but not "AN")
IN (...) | String exists in a list | col_name IN ("A", "B", "C")
NOT IN (...) | String does not exist in a list | col_name NOT IN ("D", "E", "F")

```
# Find all the Toy Story movies
SELECT title FROM movies WHERE title LIKE "Toy Story%";
```

```
# Find all the movies directed by John Lasseter
SELECT title, director FROM movies WHERE director = "John Lasseter";
```

```
# Find all the movies (and director) not directed by John Lasseter
SELECT title, director FROM movies WHERE director != "John Lasseter";
```

```
# Find all the WALL-* movies
SELECT title FROM movies WHERE title LIKE "WALL-_";
```

### Lesson 4
```
SELECT DISTINCT column, another_column, ...
FROM mytable
WHERE condition(s)
ORDER BY column ASC/DESC
LIMIT num_limit OFFSET num_offset;
```

```
# List all directors of Pixar movies (alphabetically), without duplicates
SELECT DISTINCT director FROM movies ORDER BY director ASC;
```

```
# List the last four Pixar movies released (ordered from most recent to least)
SELECT title, year FROM movies ORDER BY year DESC LIMIT 4;
```

```
# List the first five Pixar movies sorted alphabetically
SELECT title FROM movies ORDER BY title ASC LIMIT 5;
```

```
# List the next five Pixar movies sorted alphabetically
SELECT title FROM movies ORDER BY title ASC LIMIT 5 OFFSET 5;
```

### Lesson 5
Table: north_american_cities
<img width="598" height="286" alt="image" src="https://github.com/user-attachments/assets/80cd5257-3053-4ffd-bb51-e31acaebda33" />

```
# List all the Canadian cities and their populations
SELECT city, population FROM north_american_cities WHERE country = "Canada";
```

```
# Order all the cities in the United States by their latitude from north to south
SELECT city, latitude FROM north_american_cities WHERE country = "United States" ORDER BY latitude DESC;
```

```
# List all the cities west of Chicago, ordered from west to east
SELECT city, longitude FROM north_american_cities WHERE longitude < -87.629798 ORDER BY longitude ASC;
```

```
# List the two largest cities in Mexico (by population)
SELECT city, population FROM north_american_cities WHERE country LIKE "Mexio" ORDER BY population DESC LIMIT 2;
```

```
# List the third and fourth largest cities (by population) in the United States and their population
SELECT city, population FROM north_american_cities WHERE country LIKE "United Stated" ORDER BY population DESC LIMIT 2 OFFSET 2;
```

### Lesson 6
```
SELECT column, another_table_column, ...
FROM mytable
INNTER JOIN another_table
  ON mytable.id = another_table.id
WHERE condition(s)
ORDER BY column, ... ASC/DESC
LIMIT num_limit OFFSET num_offset;
```

Table: Boxoffice
<img width="452" height="182" alt="image" src="https://github.com/user-attachments/assets/2c418e91-759b-4361-b7f1-a9ac76eca2ed" />

```
# Find the domestic and international sales for each movie
SELECT title, domestic_sales, international_sales FROM movies JOIN boxoffice ON movies.id = boxoffice.movie_id;
```

```
# Show the sales numbers for each movie that did better internationally rather than domestically
SELECT title, domestic_sales, international_sales FROM movies JOIN boxoffice ON movies.id = boxoffice.movie_id WHERE internationa_sales > domestic_sales;
```

```
# List all the movies by their ratings in descending order
SELECT title, rating FROM movies JOIN boxoffice ON movies.id = boxoffice.movie_id ORDER BY rating DESC;
```

### Lesson 7
