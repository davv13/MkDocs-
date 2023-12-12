# **API Documentation**

## **Overview**

The `api.py` module contains the FastAPI application that serves as an interface to interact with the Customer Retention Toolkit. This document outlines the available API endpoints and their usage.

## **Setup**

Ensure FastAPI and required packages are installed:

```bash
pip install fastapi[all] pandas pydantic
```

Run the FastAPI server:

```bash
uvicorn api:app --reload
```

## **Endpoints**

### Root Endpoint (`GET /`)

Returns a welcome message.

**Response**:

```json
{
  "message": "Initializing"
}
```

### Fetch Record (`GET /get_data/{CustomerID}`)

Fetches a record from the CustomerMetrics table by CustomerID.

**Parameters**:

- `CustomerID` (int): The ID of the customer to fetch.

**Response**:

A dictionary with the customer's data or an error message if not found.

### Create Record (`POST /create_data`)

Creates a new record in the CustomerMetrics table.

**Request Body**:

- `UserRequest` model: Contains customer data to be inserted.

**Response**:

A message indicating the success of the operation.

### Update Record (`PUT /update_data`)

Updates a record in the CustomerMetrics table.

**Request Body**:

- `UpdateRecordRequest` model: Contains the column to be updated, the new value, and the CustomerID of the record to update.

**Response**:

A message indicating the success of the operation.

### Predict Churn (`GET /predict_churn/{CustomerID}`)

Predicts churn status for a given CustomerID using the machine learning workflow.

**Parameters**:

- `CustomerID` (int): The ID of the customer for churn prediction.

**Response**:

A dictionary containing the CustomerID and the churn prediction.

## **Models**

### `UserRequest`

Pydantic model representing a user request for creating a record.

**Attributes**:

- `CustomerID` (int): The customer's ID.
- ... (other attributes) ...
- `CustomerServiceCalls` (int): The number of customer service calls made.

### `UpdateRecordRequest`

Pydantic model representing a request to update a record.

**Attributes**:

- `column_name` (str): The name of the column to update.
- `new_value` (Any): The new value for the column.
- `CustomerID` (int): The ID of the customer whose record is to update.

## **Examples**

Here are the examples extracted from the Jupyter notebook that demonstrate how to use the API with the `requests` library in Python:

### **Example 1: Root Endpoint**

```python
import requests

# The base URL for your API
base_url = "http://127.0.0.1:5000"

# GET request to the root endpoint
response = requests.get(f"{base_url}/")
print(response.json())
```

### **Example 2: Get Customer Data**

```python
# Replace with a valid customer ID
customer_id = 1
response = requests.get(f"{base_url}/get_data/{customer_id}")
print(response.json())
```

### **Example 3: Create New Customer Data**

```python
new_customer_data = {
    "CustomerID": 2749,
    "ChurnStatus": 1,
    "StateID": 1,  # Assuming '1' is a valid StateID in your database
    "PlanID": 1,  # Assuming '1' is a valid PlanID in your database
    "DayUsageID": 1,  # Assuming '1' is a valid DayUsageID in your database
    "EveUsageID": 1,  # Assuming '1' is a valid EveUsageID in your database
    "NightUsageID": 1,  # Assuming '1' is a valid NightUsageID in your database
    "IntlUsageID": 1,  # Assuming '1' is a valid IntlUsageID in your database
    "CustomerServiceCalls": 1  # Number of customer service calls
}

response = requests.post(f"{base_url}/create_data", json=new_customer_data)
print(response.json())
```

### **Example 4: Update Customer Data**

```python
update_data = {
    "column_name": "ChurnStatus",
    "new_value": 1,
    "CustomerID": 2749  # Make sure this ID exists in your database
}
response = requests.put(f"{base_url}/update_data", json=update_data)
print(response.json())
```

### **Example 5: Predict Customer Churn**

```python
customer_id = 555
response = requests.get(f"{base_url}/predict_churn/{customer_id}")
print('Status Code:', response.status_code)

if response.status_code == 200:
    try:
        data = response.json()
        print(data)
    except JSONDecodeError:
        print('Response could not be decoded as JSON:', response.text)
else:
    print('Failed to fetch data:', response.text)
```
