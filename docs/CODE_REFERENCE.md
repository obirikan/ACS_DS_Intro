# API & Code Reference

This document provides a technical reference for the codebase.

## Module Analysis

# TECHNICAL_DOCS.md

## Module: pandas.ipynb

This notebook provides practical examples and patterns for manipulating pandas DataFrames. Below is an exhaustive reference for all pandas DataFrame methods, attributes, and operations as used and demonstrated in this codebase.

### Imported Modules

- **pandas** (`import pandas as pd`)

---

### DataFrame Instantiation

#### pd.read_csv(filepath: str) -> pd.DataFrame
- **Arguments:**
  - `filepath`: str  
    Path to a CSV file.
- **Returns:**  
  `pd.DataFrame`  
  DataFrame loaded from the specified CSV file.
- **Description:**  
  Reads a comma-separated values (CSV) file into a DataFrame.
- **Example:**  
  `df = pd.read_csv("dataset.csv")`

#### pd.read_excel(filepath: str) -> pd.DataFrame
- **Arguments:**
  - `filepath`: str  
    Path to an Excel file.
- **Returns:**  
  `pd.DataFrame`  
  DataFrame loaded from the specified Excel file.
- **Description:**  
  Reads an Excel file into a DataFrame.
- **Example:**  
  `df = pd.read_excel("file.xlsx")`

#### pd.DataFrame(data: dict) -> pd.DataFrame
- **Arguments:**
  - `data`: dict  
    Dictionary of data.
- **Returns:**  
  `pd.DataFrame`  
  DataFrame created from the dictionary.
- **Description:**  
  Constructs a DataFrame from dict of array-like or dicts.
- **Example:**  
  `df = pd.DataFrame(dict_data)`

---

### Data Exploration Methods and Attributes

#### DataFrame.head(n: int = 5) -> pd.DataFrame
- **Arguments:**
  - `n`: int (default=5)  
    Number of rows to return from the top.
- **Returns:**  
  `pd.DataFrame`
- **Description:**  
  Returns the first n rows.

#### DataFrame.info(verbose: bool = None, buf = None, max_cols: int = None, memory_usage: bool = None, null_counts: bool = None, show_counts: bool = None) -> None
- **Arguments:**  
  - Standard DataFrame.info parameters, typically called with no arguments.
- **Returns:**  
  `None`  
- **Description:**  
  Prints concise summary of DataFrame (index dtype, columns, non-null values, memory usage, datatypes).

#### DataFrame.describe(percentiles: list = None, include = None, exclude = None, datetime_is_numeric: bool = False) -> pd.DataFrame
- **Arguments:**  
  - Standard DataFrame.describe parameters, typically called with no arguments.
- **Returns:**  
  `pd.DataFrame`  
- **Description:**  
  Generates descriptive statistics (count, mean, std, min, max, percentiles) for numeric columns.

#### DataFrame.shape
- **Type:**  
  `tuple[int, int]`
- **Description:**  
  Returns a tuple representing the dimensionality of the DataFrame as (rows, columns).

#### DataFrame.columns
- **Type:**  
  `pd.Index`
- **Description:**  
  Returns column labels of the DataFrame.

#### DataFrame.dtypes
- **Type:**  
  `pd.Series`
- **Description:**  
  Returns the data type of each column.

---

### Data Selection

#### DataFrame.__getitem__(key)
- **Arguments:**
  - `key`: str or list  
    If str, select single column; if list, select subset of columns.
- **Returns:**  
  `pd.Series` for a single column, `pd.DataFrame` for multiple columns.
- **Description:**  
  Standard column selection.

##### Examples:
- `df['column']`  
  Select single column as Series.
- `df[['col1', 'col2']]`  
  Select subset columns as DataFrame.

#### DataFrame.iloc
- **Type:**  
  `pandas.core.indexing._iLocIndexer`
- **Description:**  
  Purely integer-location based indexing for selection by position.  
  Used in: `df.iloc[0:5]` for slicing rows.

#### DataFrame.loc
- **Type:**  
  `pandas.core.indexing._LocIndexer`
- **Description:**  
  Access a group of rows and columns by labels or boolean array.
- **Example:**  
  `df.loc[df['col'] > 5]` - filter rows.

#### pd.Series.value_counts(normalize: bool = False, sort: bool = True, ascending: bool = False, bins = None, dropna: bool = True) -> pd.Series
- **Arguments:**  
  - Standard value_counts parameters, usually called as is.
- **Returns:**  
  `pd.Series`
- **Description:**  
  Returns a Series containing counts of unique values.
- **Example:**  
  `df['customer_id'].value_counts()`

---

### Data Modification

#### DataFrame.__setitem__(key, value)
- **Arguments:**  
  - `key`: str  
    Name of the new/existing column.
  - `value`: array-like, scalar, or Series  
    New column values.
- **Returns:**  
  `None`
- **Description:**  
  Assignment operation for adding or modifying columns.
- **Example:**  
  `df['new_col'] = values`

#### DataFrame.drop(labels=None, axis=0, index=None, columns=None, level=None, inplace=False, errors='raise') -> pd.DataFrame or None
- **Arguments:**  
  - `labels`: single label or list-like  
    Labels to drop.
  - `axis`: int or str (0/'index', 1/'columns')  
    Axis along which to drop.
  - `inplace`: bool  
    If True, perform operation in place.
  - Other standard parameters.
- **Returns:**  
  DataFrame without the specified labels or None (if inplace=True).
- **Description:**  
  Drop specified labels from rows or columns.
- **Examples:**  
  - Drop column: `df.drop('col', axis=1)`
  - Drop column and assign: `new_data = df.drop('refund_status', axis=1)`

#### DataFrame.sort_values(by, axis=0, ascending=True, inplace=False, kind='quicksort', na_position='last', ignore_index=False, key=None) -> pd.DataFrame or None
- **Arguments:**  
  - Standard sort_values parameters.
- **Returns:**  
  Sorted DataFrame (or None if inplace=True).
- **Description:**  
  Sorts DataFrame by the values along either axis.
- **Example:**  
  `df.sort_values('col')`

#### DataFrame.groupby(by=None, axis=0, level=None, as_index=True, sort=True, group_keys=True, squeeze=None, observed=False, dropna=True) -> DataFrameGroupBy
- **Arguments:**  
  - `by`: str, list, or dict  
    Column(s) to group by.
  - Other standard parameters.
- **Returns:**  
  DataFrameGroupBy object.
- **Description:**  
  Used for grouping DataFrame and performing aggregation/computation functions.
- **Example:**  
  `df.groupby('col').mean()`

---

### Handling Missing Data

#### DataFrame.isnull() -> pd.DataFrame
- **Returns:**  
  DataFrame of booleans, same shape as calling DataFrame, entries are True if NaN/missing.
- **Description:**  
  Detect missing values.

#### DataFrame.sum(axis=None, skipna=None, level=None, numeric_only=None, min_count=0)
- **Arguments:**  
  - Standard sum parameters.
- **Returns:**  
  Scalar, Series, or DataFrame.
- **Description:**  
  Returns sum of the values over the requested axis.  
  Used after `isnull()` to count missing per column:  
  `df.isnull().sum()`

#### DataFrame.dropna(axis=0, how='any', thresh=None, subset=None, inplace=False) -> pd.DataFrame or None
- **Arguments:**  
  - Standard dropna parameters.
- **Returns:**  
  DataFrame with missing values dropped (or None if inplace=True).
- **Description:**  
  Remove missing values.
- **Examples:**  
  - Drop all rows with NaN: `df.dropna()`
  - Clean DataFrame assignment: `df_clean = df.dropna()`

#### DataFrame.fillna(value=None, method=None, axis=None, inplace=False, limit=None, downcast=None) -> pd.DataFrame or None
- **Arguments:**  
  - `value`: scalar, dict, Series, or DataFrame  
    Value to use to fill holes.
  - Standard fillna parameters.
- **Returns:**  
  DataFrame with NaN filled (or None if inplace=True).
- **Description:**  
  Fill NA/NaN values.

---

### Example Workflow Summary (as demonstrated):

1. **Loading Data:**  
   `df = pd.read_csv("dataset.csv")`

2. **Inspecting Data:**  
   `df.head()`  
   `df.info()`  
   `df.describe()`  
   `df.shape`  
   `df.columns`  
   `df.dtypes`

3. **Selecting Data:**  
   - Single column: `df['column']`
   - Multiple columns: `df[['customer_id','order_amount','payment_method']]`
   - Row selection by index: `df.iloc[0:5]`
   - Boolean filtering: `df.loc[df['customer_id'] == "CUST_0009"]`
   - Unique value counting: `df['customer_id'].value_counts()`

4. **Modifying Data:**  
   - Add/replace column: `df['new_col'] = values`
   - Drop column: `df.drop('refund_status', axis=1)` or with assignment: `new_data = df.drop('refund_status', axis=1)`
   - Sorting: `df.sort_values('col')`
   - Grouping and aggregation: `df.groupby('col').mean()`

5. **Handling Missing Data:**  
   - Count missing: `df.isnull().sum()`
   - Drop missing: `df.dropna()`
   - Fill missing: `df.fillna(value)`

---

## DataFrame Schema (from dataset.csv and usages):

**Columns:**
- `order_date`: object (string), date of order
- `customer_id`: object (string), ID of the customer
- `product_category`: object (string), product category
- `order_amount`: float64, amount of order
- `discount_percent`: float64, percent discount (may be NaN)
- `discount_amount`: float64, discount amount (may be 0)
- `final_price`: float64, final price after discounts
- `quantity`: int64, ordered quantity (note: may contain invalid negatives)
- `shipping_days`: float64, estimated/actual shipping duration (may be NaN)
- `delivery_date`: object (string), delivery date (may be NaN)
- `order_status`: object (string), status of order
- `refund_status`: object (string), refund status (may be NaN/‘No’/‘Refunded’)
- `customer_rating`: float64, customer’s rating (1-5, may be NaN)
- `payment_method`: object (string), payment method used

---

## NOTE
- No user-defined functions or classes exist in this codebase.  
- All code manipulates and queries pandas DataFrames and uses only standard library and pandas APIs.

---

## Glossary of Main DataFrame Operations

| Operation                        | Example Usage                                 | Description                                             |
|-----------------------------------|-----------------------------------------------|---------------------------------------------------------|
| Load CSV                         | pd.read_csv('dataset.csv')                    | Read CSV to DataFrame                                   |
| Head Rows                        | df.head()                                    | First 5 rows                                            |
| Info                             | df.info()                                    | Print summary info                                      |
| Description/Stats                | df.describe()                                | Descriptive statistics                                  |
| Data Shape                       | df.shape                                     | Tuple of (rows, columns)                                |
| Column Names                     | df.columns                                   | List of column labels                                   |
| Data Types                       | df.dtypes                                    | Data types (by column)                                  |
| Select Single Column             | df['column']                                 | Get a single column (Series)                            |
| Select Multiple Columns          | df[['col1', 'col2']]                         | Subset columns (DataFrame)                              |
| Select Rows by Position          | df.iloc[n]                                   | Get nth row(s) by integer position                      |
| Filter Rows by Condition         | df.loc[df['col'] == val]                     | Filter rows based on boolean mask                       |
| Count Unique Values in Column    | df['col'].value_counts()                     | Counts of each unique value in Series                   |
| Add Column                       | df['new_col'] = values                       | Add/replace column in DataFrame                         |
| Drop Column                      | df.drop('col', axis=1)                       | Remove column                                           |
| Sort                             | df.sort_values('col')                        | Sort rows by column value                               |
| Group By and Aggregate           | df.groupby('col').mean()                     | Group rows and compute aggregate statistic(s)           |
| Null Count Per Column            | df.isnull().sum()                            | Number of missing (NaN) in each column                  |
| Drop Rows with Missing Data      | df.dropna()                                  | Drops any row with at least one NaN                     |
| Fill Missing Data                | df.fillna(value)                             | Fill NaN values with `value`                            |

---

## File: guide.md

This file provides a quick-reference cheatsheet and does **not** contain any unique code or callable functionality outside the notebook.

---

## File: dataset.csv

This file provides sample data referenced in the above analysis.

---

## Further Reading

Refer to the official [pandas documentation](https://pandas.pydata.org/pandas-docs/stable/) for exhaustive API details not covered by usage in this codebase.