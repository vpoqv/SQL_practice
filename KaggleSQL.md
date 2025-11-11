### Lesson 1 Getting Started With SQL and BigQuery

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

#### Table schema
