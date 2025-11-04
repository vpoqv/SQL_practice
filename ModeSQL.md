### SQL SELECT
```
SELECT west AS 'West Region"
FROM tutorial.us_housing_units
```

### SQL LIMIT
```
SELECT *
FROM tutorial.us_housing_units
LIMIT 100
```

### SQL WHERE
```
SELECT *
FROM tutorial.us_housing_units
WHERE month = 1
```

### SQL Comparison Operators
```
SELECT *
FROM tutorial.us_housing_units
WHERE month_name > 'J'
```

```
SELECT year, month, wesy, south, west + south - 4 * year AS nonsense_column
FROM tutorial.us_housing_units
```

### SQL Logical Operators

### SQL LIKE
```
SELECT *
FROM tutorial.billboard_top_100_year_end
WHERE "group_name" LIKE 'Snoop%'
```

```
SELECT *
FROM tutorial.billboard_top_100_year_end
WHERE "group_name" ILIKE 'snoop%'
```

```
SELECT *
FROM tutorial.billboard_top_100_year_end
WHERE artist ILIKE 'dr_ke'
```

### SQL IN
```
SELECT *
FROM tutorial.billboard_top_100_year_end
WHERE year_rank IN (1, 2, 3)
```

```
SELECT *
FROM tutorial.billboard_top_100_year_end
WHERE artist IN ('Taylor Swift', 'Usher', 'Ludacris')
```

### SQL BETWEEN
```
SELECt *
FROM tutorial.billboard_top_100_year_end
WHERE year_rank BETWEEN 5 AND 10
```

### SQL IS NULL
```
SELECT *
FROM tutorial.billboard_top_100_year_end
WHERE artist IS NULL
```

### SQL AND
```
SELECT *
FROM tutorial.billboard_top_100_year_end
WHERE year = 2012
AND year_rank <= 10
AND "group_name" ILIKE '%feat$'
```

### SQL OR
```
SELECT *
FROM tutorial.billboard_top_100_year_3nd
WHERE year = 2013
AND ("group_name" ILIKE '%macklemore%' OR "group_name" ILKE '%timberlake%')
```

### SQL NOT
Using NOT with < and > usually doesn't make sense
NOT is commonly used with LIKE
NOT is frequently used to identify non-null rows, need to include IS beforehand
```
SELECT *
FROM tutorial.billboard_top_100_year_end
WHERE year = 2013
AND year_rank NOT BETWEEN 2 AND 3
```

```
SELCET *
FROM tutorial.billboard_top_100_year_end
WHERE year = 2013
AND "group_name" NOT ILKE '%macklemore%'
```

```
SELECT *
FROM tutorial.billboard_top_100_year_end
WHERE year = 2013
AND artist IS NOT NULL
```

### SQL ORDER BY
```
SELECT *
FROM tutorial.billboard_top_100_year_end
WHERE year = 2013
ORDER BY year_rank
```

comments
```
/* Here's a comment so long and descriptive that
it could only fit on multiple lines */
SELECT * -- This comment won't affect
FROM tutorial.billboard_top_100_year_end
WHERE year_rank <= 3
ORDER BY year DESC, year_rank
```
