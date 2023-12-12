# **MLWorkflow Documentation**

## **Overview**
The `MLWorkflow` class is designed for managing the machine learning workflow, including data loading, preprocessing, model training, evaluation, and prediction. This class simplifies the process of applying machine learning models to datasets.

## **Installation**
Before using `MLWorkflow`, ensure you have the following packages installed:
- pandas
- numpy
- sklearn
- sqlite3

These can be installed via pip:

```bash
pip install pandas numpy scikit-learn sqlite3
```

## **Class Attributes**
- `dbname` (str): Database name to connect to for data loading.
- `model` (RandomForestClassifier): The machine learning model to be used.
- `trained_columns` (list): List of columns used for training the model.

### **Methods**

- `__init__(self, dbname: str)`
Initializes the MLWorkflow class with a database name and model.

### **Arguments**
- `dbname` (str): The name of the database to connect to.

- `load_data_from_db(self, table_names: list) -> pd.DataFrame` : Loads data from a SQLite database from the given table names.

- `table_names` (list): A list of table names to load data from.

### **Returns**
- `DataFrame`: A pandas DataFrame containing the concatenated data from the tables.

### **Preprocess Data**
- `preprocess_data(self, df_comb: pd.DataFrame, target: str = 'ChurnStatus') -> pd.DataFrame`

Preprocesses the data by removing specified columns and one-hot encoding categorical variables.

### **Arguments**
- `df_comb` (DataFrame): The DataFrame to preprocess.
- `target` (str, optional): The target variable to exclude from preprocessing. Defaults to 'ChurnStatus'.

### **Returns**
- `DataFrame`: The preprocessed DataFrame.

### **Additional Methods**
- `split_data`
- `train_model`
- `evaluate_model`
- `predict`
- `run_workflow`
- `save_predictions_to_db`
- `predict_for_customer`

Each of these methods can be documented in a similar format, detailing their purpose, arguments, and return values.

## **Usage Example**

Here is a basic example of how to use the **`MLWorkflow`** class:

``` python
from your_package_name import MLWorkflow

# Initialize the MLWorkflow
workflow = MLWorkflow(dbname="your_database_name")

# Load and preprocess data
data = workflow.load_data_from_db(["table1", "table2"])
preprocessed_data = workflow.preprocess_data(data)

# Split, train, and evaluate the model
X_train, X_test, y_train, y_test = workflow.split_data(preprocessed_data)
workflow.train_model(X_train, y_train)
metrics = workflow.evaluate_model(X_test, y_test)

print(metrics)
```



