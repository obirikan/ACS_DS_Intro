#Pandas Quick Reference Guide

---

## Reading Data

```python
df = pd.read_csv('file.csv')      # Read CSV file
df = pd.read_excel('file.xlsx')   # Read Excel file
df = pd.DataFrame(dict_data)      # Create DataFrame from dictionary
```

---

## Exploring Data

```python
df.head()        # First 5 rows
df.info()        # Data types + memory usage
df.describe()    # Summary statistics (mean, min, max, etc.)
df.shape         # (rows, columns)
df.columns       # Column names
df.dtypes        # Data types of each column
```

---

## Selecting Data

```python
df['column']              # Select single column
df[['col1', 'col2']]      # Select multiple columns

df.iloc[0]                # First row (by position)
df.loc[df['col'] > 5]     # Filter rows based on condition

df['col'].value_counts()  # Count unique values
```

---

## Modifying Data

```python
df['new_col'] = values        # Add or update column

df.drop('col', axis=1)        # Drop column
df.sort_values('col')         # Sort by column

df.groupby('col').mean()      # Group by column and compute mean
```

---

## Handling Missing Data

```python
df.isnull().sum()   # Count missing values per column

df.dropna()         # Remove rows with missing values
df.fillna(value)    # Replace missing values
```

---

## Notes (Important)

* `axis=1` → column operation
* `axis=0` → row operation
* `iloc` → position-based (index numbers)
* `loc` → label-based (column names / conditions)
* `groupby` → core of data analysis (aggregation + patterns)

---

## Reality Check

Memorizing this is not enough.

You must understand:

* Why data is missing
* What each column represents
* What transformations mean in real-world context

Next step:
→ Combine operations into workflows (filter → group → aggregate → analyze)
