# **SQL Interactions Documentation**

## **Overview**

The `SqlHandler` class in the `sql_interactions.py` module provides a convenient interface for interacting with a SQLite database. It enables executing SQL commands, handling data, and managing database tables.

## **Setup**

To use the `SqlHandler`, ensure that `sqlite3`, `pandas`, and `numpy` are installed:

```bash
pip install pandas numpy
```

## **Class** `SqlHandler`

### **Description**

`SqlHandler` manages the connection to a SQLite database and provides methods to interact with a specified table.

### **Initialization**

```python
from db.sql_interactions import SqlHandler

sql_handler = SqlHandler(dbname="your_database_name", table_name="your_table_name")
```

### **Methods**

#### `close_cnxn`

Closes the database connection and commits any pending transactions.

#### `get_table_columns`

Returns the column names of the specified table.

#### `truncate_table`

Deletes all data from the specified table without removing the table structure.

#### `drop_table`

Deletes the specified table from the database.

#### `insert_many`

Inserts multiple records into the specified table from a pandas DataFrame.

#### `from_sql_to_pandas`

Fetches data from the specified table and returns a pandas DataFrame.

#### `update_table`

Updates records in the specified table based on a condition.

### **Examples**

#### **Truncating a Table**

```python
sql_handler.truncate_table()
```

#### **Dropping a Table**

```python
sql_handler.drop_table()
```

#### **Inserting Data**

```python
import pandas as pd

# Assuming df is your DataFrame containing the data to insert
sql_handler.insert_many(df)
```

#### **Fetching Data**

```python
df = sql_handler.from_sql_to_pandas(chunksize=1000, order_by="column_name")
```

#### **Updating Data**

```python
condition = "column_name = value"
update_values = {"column_to_update": "new_value"}
sql_handler.update_table(condition, update_values)
```

## **Logging**

The `SqlHandler` uses a custom logging formatter for informative output during database operations.

**Example Log Output**:

```plaintext
2023-03-15 10:00:00 - sql_interactions.py - get_table_columns - INFO - (The list of columns: ['id', 'name', 'value']) - line: 42
```