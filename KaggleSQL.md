## Lesson 1 Getting Started With SQL and BigQuery

```
from google.cloud import bigquery
```

```
# Create a "Client" object
client = bigquery.Client()
```

```
# Construct a reference to the "hacker_news" dataset
dataset_ref = client.dataset("hacker_news", project = "bigquery-pulic-data")

# API request - fetch the dataset
dateset = client.get_dataset(dataset_ref)
```

```
# List all the tables in the "hacker_news" dataset
tables = list(client.list_tables(dataset))

# Print names of all tables in the dataset (there are four)
for table in tables:
  print(table.table_id)
```
result
```
comments
full
full_201510
stories
```

```
Construct a reference to the "full" table
table_ref = dataset_ref.table("full")

# API request - fetch the table
table = client.get_table(table_ref)
```

<img width="919" height="326" alt="image" src="https://github.com/user-attachments/assets/9edaad2a-645f-43a4-b810-be8c0336e512" />

### Table schema
```
# Print informationa on all the columns in the "full" tavle in the "hacker_news" dataset
table.schema
```

Each 'SchemaField' tells us about a specific column(which we also refer to as a fiels)
In order, the information is:
- The name of the column
- The field type (of datatype) in the column
- The mode of the column ('NULLABLE' means that a column allows NULL values, and is the default)
- A description of the data in that column

SchemaField('by', 'string', 'NULLABLE', "The username of the item's author.", ())
- the field (or column) is called by
- the data in this field is strings
- NULL values are allowed
- it contains the usernames corresponding to each item's author

```
# Preview the first five lines of the "full" table
client.list_rows(table, max_results = 5).to_dataframe()
```

```
# Preview the first five entries in the "by" column of the "full" table
client.list_rows(table, selected_fields = table.schema[:1], max_results = 5).to_dataframe()
```

### Excercise
```
from google.cloud import bigquery

# Create a "Client" object
client = bigquery.Client()

# Construct a reference to the "chicago_crime" dataset
dataset_ref = client.dataset("chicago_crime", project="bigquery-public-data")

# API request - fetch the dataset
dataset = client.get_dataset(dataset_ref)
```

#### 1 Count tables in the dataset
How many tables are in the Chicago Crime dataset?

```
# List all the tables in the "chicago_crime" dataset
tables = list(client.list_tables(dataset))
print(len(tables))
````
result
1

#### 2 Explore the table schema
How many columns in the 'crime' table have 'TIMESTAMP' data?

```
# Construct a reference to the "crime" table
table_ref = dataset_ref.table('crime')
# API request - fetch the table
table = client.get_table(table_ref)
# Print information on all the columns in the "crime" table in the "chicago_crime" dataset
print(table.schema)
```
result
2

#### 3 Create a crime map
If you wanted to create a map with a dot at the location of each crime, what are the names of the two fields you likely need to pull out of the 'crime' table to plot the crimes on a map?

```
# Look at the table schema. There are a couple options, but two of the fields are things commonly used to plot on maps. Both are 'FLOAT' types
fields_for_plotting = ['latitude', 'longitude']
```

## Lesson 2
