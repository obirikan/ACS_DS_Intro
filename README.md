# Project Overview

This project is # Pandas E-commerce Dataset Operations  
Efficient Data Exploration and Cleaning for E-commerce Transactions

## Key Features

- **Read and load CSV data** representing e-commerce orders into pandas DataFrames.
- **Comprehensive data exploration** including column inspection, type checking, and descriptive statistics.
- **Flexible data selection** by columns, rows, or through conditional filtering.
- **Value counting and grouping** for customer-centric or product-based analysis.
- **Data modification utilities** including column creation, sorting, and dropping columns.
- **Missing data analysis and handling** via detection, filling, and row omission.
- **Clean DataFrame production** for downstream analytics or modeling.
- **Sample code and workflow documented via Jupyter Notebook and quick reference guide.

## Quick Start

### Prerequisites
- Python 3.7 or higher
- pandas library

### Installation

Install pandas if not already present:
```
pip install pandas
```

Clone this repository and ensure `dataset.csv` is in your working directory.

## Usage Example

```python
import pandas as pd

# Load the dataset
df = pd.read_csv("dataset.csv")

# Explore data
print(df.head())
df.info()
print(df.describe())

# Select multiple columns
customer_orders = df[['customer_id', 'order_amount', 'payment_method']]

# Filter data for a specific customer
specific_customer_orders = df.loc[df['customer_id'] == "CUST_0009"]

# Count orders per customer
order_counts = df['customer_id'].value_counts()

# Drop a column
df_no_refunds = df.drop('refund_status', axis=1)

# Handle missing data by dropping rows with nulls
df_clean = df.dropna()

# Fill missing values in a column (example: fill missing 'discount_percent' with 0)
df['discount_percent_filled'] = df['discount_percent'].fillna(0)
```

For additional examples and common operations, refer to `guide.md` and the Jupyter Notebook `pandas.ipynb`.