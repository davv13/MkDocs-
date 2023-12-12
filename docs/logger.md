# **Custom Logger Documentation**

## **Overview**
The `CustomFormatter` class in the `logger` module provides a way to format logging messages with color coding and custom formatting for better readability during development and debugging. This formatter extends the functionality of Python's built-in `logging` module.

## **Installation**
This module is part of the `customer_retention_toolkit` package and does not require separate installation.

## **Class** `CustomFormatter`

### **Description**
`CustomFormatter` is a custom logging formatter class that provides colored and informative logging output. It is designed to enhance the visibility of different logging levels.

### **Usage**
Here is an example of how to use the `CustomFormatter`:

```python
import logging
from logger import CustomFormatter

logger = logging.getLogger(__name__)
logger.setLevel(logging.DEBUG)
ch = logging.StreamHandler()
ch.setLevel(logging.DEBUG)
ch.setFormatter(CustomFormatter())
logger.addHandler(ch)

logger.debug("This is a debug message.")
logger.info("This is an informational message.")
logger.warning("This is a warning message.")
logger.error("This is an error message.")
logger.critical("This is a critical message.")
```

### **Log Format**
The format for log messages is:

```
%(asctime)s - %(name)s - %(funcName)s - %(levelname)s - (%(message)s) - line: %(lineno)d
```

### **Log Levels and Colors**
The `CustomFormatter` class defines the following log level and color mappings:

- DEBUG: Grey
- INFO: Violet
- WARNING: Yellow
- ERROR: Red
- CRITICAL: Bold Red

### **Method** `format`

#### **Description**
Customizes the format of the log records.

#### **Parameters**
- `record`: The log record that needs to be formatted.

#### **Returns**
The method returns a formatted string with the specified color for the log level.

## **Integration Example**

To integrate the `CustomFormatter` into your main application, you can set it up in the entry-point script. For example, in your `main.py`:

```python
import logging
from logger import CustomFormatter

# Set up logging
logger = logging.getLogger(__name__)
logger.setLevel(logging.DEBUG)
handler = logging.StreamHandler()
handler.setFormatter(CustomFormatter())
logger.addHandler(handler)
```

Now all logging messages from `logger` will be formatted with colors corresponding to their severity levels.
