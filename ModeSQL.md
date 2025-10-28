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

