# **Database Schema Documentation**

## **Overview**

The `schema.py` module outlines the database schema for the Customer Retention Toolkit. It utilizes SQLAlchemy ORM for defining tables and relationships. This document provides details about each table and its fields, along with information on how to generate the database schema.

## **Setup**

To use this module, ensure SQLAlchemy is installed:

```bash
pip install sqlalchemy
```

## **Tables**

### `CustomerMetrics`

- **Description**: Holds customer churn metrics.
- **Fields**:
  - `CustomerID` (Integer): Primary key. Unique identifier for a customer.
  - `StateID` (Integer): Foreign key to the `State` table. Represents the state ID associated with the customer.
  - ... (additional fields) ...
  - `ChurnStatus` (Integer): The churn status of the customer.

### `State`

- **Description**: Represents the State table in the database.
- **Fields**:
  - `StateID` (Integer): Primary key. Unique identifier for a state.
  - `StateName` (String): The name of the state.

... (repeat for each class/table) ...

### **Relationships**

- The `CustomerMetrics` table has foreign keys linking to the `State`, `PlanDetails`, `DayUsage`, `EveUsage`, `NightUsage`, and `IntlUsage` tables.
- Each relationship is represented by a `ForeignKey` constraint in the SQLAlchemy model.

## **Functions**

### `create_database`

**Description**: Initializes the database by creating all tables based on the defined schema if they do not exist.

**Usage**:

```python
from db.schema import create_database

# Create the database and all tables
create_database()
```

## **Logging**

Logging is set up to capture and format output from database operations. The custom formatter from `logger` sub-package is used for colored and formatted output.

**Example Log Output**:

```plaintext
2023-03-15 10:00:00 - schema.py - create_database - INFO - (Database tables created) - line: 150
```

## **Integration Example**

To integrate the database schema into your main application, you can call the `create_database` function at the application's entry point after configuring the logging and database engine.

```python
from db.schema import create_database

# Set up logging here (omitted for brevity)

# Initialize the database
create_database()
```