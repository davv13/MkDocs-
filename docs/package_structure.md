## **Package Structure Overview**

- **api**: Contains the interface for interacting with the predictive model.
- **db**: Database scripts, including the schema and SQL interactions.
- **docs**: Documentation files, such as the Entity Relationship Diagram (ERD), usage instructions, roadmap, and use cases.
- **logger**: Logging functionality to keep track of operations and errors.
- **models**: The machine learning models and related workflows.



## **Setup and Configuration**
Steps to run the code:

Create new env. 
```py
python -m venv venv
```
Install the requirements.txt in the env by running the following code.
```py
pip install -r requirements.txt
```
Run the cells in `example.ipynb`

When you reach the `API` part, start the api by running the following code:
```py
python run.py
```

The following steps are for web usage of API:

`http://127.0.0.1:5000` add `http://127.0.0.1:5000/docs` press enter.

Press on the `get_info`, then press on `try it out` and on the `ID` write any id from 1 to 3 and press `execute`.

You will find the result in `Response` body. 