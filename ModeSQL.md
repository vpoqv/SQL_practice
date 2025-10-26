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
