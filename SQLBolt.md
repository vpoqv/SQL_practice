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
```
SELECT column, another_column, ...
FROM mytable
INNER/LEFT/RIGHT/FULL JOIN another_table
  ON mytable.id = another_table.matching_id
WHERE condition(s)
ORDER BY column, ... ASC/DESC
LIMIT num_limit OFFSET num_offset;
```

Table: Buildings
<img width="455" height="128" alt="image" src="https://github.com/user-attachments/assets/aa285ebb-99e6-4869-b733-3b679ed0c98b" />

Table: Employees
<img width="449" height="176" alt="image" src="https://github.com/user-attachments/assets/b8f61e1b-7c20-4bcf-97b0-451e3be5c4ce" />

```
# Find the list of all buildings that have employees
SELECT DISTINCT building FROM emplyess;
```

```
# Find the list of all buildings and their capacity
SELECT * FROM buildings;
```

```
# List all buildings and the distinct employee roles in each building (including empty buildings)
SELECT DISTINCT building_name, role FROM buildings LEFT JOIN employees ON building_name = building;
```

### Lesson 8
```
SELECT column, another_column, ...
FROM mytable
WHERE column IS/IS NOT NULL
AND/OR another_condition
AND/OR ...;
```

```
# Find the name and role of all employees who have not been assigned to a building
SELECT name, role FROM employees WHERE building IS NULL;
```

```
# Find the names of the buildings that hold no employees
SELECT DISTINCT building_name FROM buildings LEFT JOIN employees ON building_name = building WHERE role IS NULL;
```

### Lesson 9
```
SELECT column AS better_column_name, ...
FROM a_long_widgets_table_name AS mywidgets
INNER JOIN wedget_sales
  ON mywidgets.id = widget_sales.widget_id;
```

```
# List all movies and their combined sales in millions of dollars
SELECT title, (domestic_sales + international_sales) / 1000000 AS gross_sales_millions FROM movies JOIN boxoffice ON movies.id = boxoffice.movie_id;
```

```
# List all movies and their ratings in percent
SELECT title, rating * 10 AS rating_percent FROM movies JOIN boxoffice ON movies.id = boxoffice.movie_id;
```

```
# List all movies that were released on even number years
SELECT title, year FROM movies WHERE year % 2 = 0;
```

### Lesson 10
Function: COUNT(*), COUNT(column) / MIN(column) / MAX(column) / AVG(column) / SUM (column)

```
SELECT AGG_FUNC(column_or_expression) AS aggregate_description, ...
FROM mytable
WHERE constrain_expression
GROUP BY column;
```

```
# Find the longest time that an employee has been at the studio
SELECT MAX(years_employed) as Max_years_employed FROM employees;
```

```
# For each role, find the average number of years employed by employees in that role
SELECT role, AVG(years_employed) as Average_years_employed FROM employees GROUP BY role;
```

### Lesson 11
```
SELECT group_by_column, AGG_FUNC(column_expression) AS aggregate_result_alias, ...
FROM mytable
WHERE condition
GROUP BY column
HAVING group_condition;
```

```
# Find the number of Artists in the studio (without a HAVING clause)
SELECT role, COUNT(*) as Number_of_artists FROM employees WHERE role = "Artist";
```

```
# Find the number of Employees of each role in the studio
SELECT role, COUNT(*) FROM employees GROUP BY role;
```

```
# Find the total number of years employed by all Engineers
SELECT role, SUM(years_employed) FROM employees GROUP BY role HAVING role = "Engineer";
```

### Lesson 12
```
SELECT DISTINCT column, AGG_FUNC(column_or_expression), ...
FROM mytable
  JOIN another_table
    ON mytable.column = another_table.column
  WHERE constraint_expression
  GROUP BY column
  HAVING constraint_expression
  ORDER BY column ASC/DESC
  LIMIT count OFFSET COUNT;
```

```
# Find the number of movies each director has directed
SELECT director, COUNT(id) as Num_movies_directed FROM movies GROUP BY director;
```

```
# Find the total domestic and international sales that can be attributed to each director
SELECT director, SUM(domestic_sales + international_sale) as Cumulative_sales_from_all_movies FROM movies INNER JOIN boxoffice ON movies.id = boxoffice.movie_id GROUP BY director;
```

### Lesson 13
```
INSERT INTO mytable
(column, another_column, ...)
VALUES (value_or_expr, another_value_or_expr, ...),
      (value_or_expr_2, another_value_or_expr_2, ...), ...;
```

```
INSERT INTO boxoffice
(movie_id, rating, saled_in_millions)
VALUES (1, 9.9, 283742034 / 1000000);
```

```
# Add the studio's new production, Toy Story 4 to the list of movies (you can use any director)
INSERT INTO movies VALUES(4, "Toy Story 4", "El Directore", 2015, 90);
```

```
# Toy Story 4 has been released to critical acclaim! It had a rating of 8.7, and made 340 million domestically and 270 million internationally. Add the record to the BoxOffice table
INSERT INTO boxoffice VALUES (4, 8.7, 340000000, 270000000);
```

### Lesson 14
```
UPDATE mytable
SET column = value_or_expr,
    other_column = another_value_or_expr, ...
WHERE condition;
```

```
# Both the title and director for Toy Story 8 is incorrect! The title should be "Toy Story 3" and it was directed by Lee Unkrich
UPDATE movies SET title = "Toy Story 3", director = "Lee Unkrich" WHERE id = 11;
```

### Lesson 15
```
DELETE FROM mytable
WHERE condition;
```

```
# This database is getting too big, lets remove all movies that were released before 2005
DELETE FROM movies WHERE year < 2005;
```

```
# Andrew Stanton has also left the studio, so please remove all movies directed by him
DELETE FROM movies WHERE director = "Andrew Stanton";
```

### Lesson 16
```
CREATE TABLE IF NOT EXISTS mytable (
  column DataType TableConstraint DEFAULT default_value,
  another_column DataType TableConstraint DEFAULT default_value, ...);
```

Data Type | Description
------------|--------------------------------|
INTEGER, BOOLEAN | The integer datatypes can store whole integer values like the count of a number or an age. In some implementations, the boolean value is just represented as an integer value of just 0 or 1 |
FLOAT, DOUBLE, REAL | The floating point datatypes can store more precise numerical data like measurements or fractional values. Different types can be used depending on the floating point precision required for that value |
CHARACTER(num_chars), VARCHAR(num_chars), TEXT | The text based datatypes can store strings and text in all sorts of locales. The distinction between the various types generally amount to underlaying efficiency of the database when working with these columns. Both the CHARACTER and VARCHAR (variable character) types are specified with the max number of characters that they can store (longer values may be truncated), so can be more efficient to store and query with big tables |
DATE, DATETIME | SQL can also store date and time stamps to keep track of time series and event data. They can be tricky to work with especially when manipulating data across timezones |
BLOB | Finally, SQL can store binary data in blobs right in the database. These values are often opaque to the database, so you usually have to store them with the right metadata to requery them |

Constraint | Description
------------|--------------------------------|
PRIMARY KEY | This means that the values in this column are unique, and each value can be used to identify a single row in this table |
AUTOINCREMENT | For integer values, this means that the value is automatically filled in and incremented with each row insertion. Not supported in all databases |
UNIQUE | This means that the values in this column have to be unique, so you can't insert another row with the same value in this column as another row in the table. Differs from the `PRIMARY KEY` in that it doesn't have to be a key for a row in the table |
NOT NULL | This means that the inserted value can not be `NULL` |
CHECK (expression) | This allows you to run a more complex expression to test whether the values inserted are valid. For example, you can check that values are positive, or greater than a specific size, or start with a certain prefix, etc
FOREIGN KEY | This is a consistency check which ensures that each value in this column corresponds to another value in a column in another table. For example, if there are two tables, one listing all Employees by ID, and another listing their payroll information, the `FOREIGN KEY` can ensure that every row in the payroll table corresponds to a valid employee in the master Employee list |

```
CREATE TABLE movies (
  id INTEGER PRIMARY KEY,
  title TEXT,
  director TEXT,
  year INTEGER,
  length_minutes INTEGER);
```

```
# Create a new table named Database with the following columns:
– Name A string (text) describing the name of the database
– Version A number (floating point) of the latest version of this database
– Download_count An integer count of the number of times this database was downloaded
This table has no constraints
CREATE TABLE Database (Name TEXT, Version FLOAT, Download_count INTEGER);
```

### Lesson 17
