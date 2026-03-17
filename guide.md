# QUICK REFERENCE GUIDE

# Reading Data
df = pd.read_csv('file.csv')
df = pd.read_excel('file.xlsx')
df = pd.DataFrame(dict_data)

# Exploring Data
df.head()          # First 5 rows
df.info()          # Data types and memory
df.describe()      # Statistics
df.shape           # Dimensions
df.columns         # Column names
df.dtypes          # datatype


# Selecting Data
df['column']                # Single column
df[['col1', 'col2']]        # Multiple columns
df.iloc[0]                  # First row by position
df.loc[df['col'] > 5]       # Filter rows
df['col'].value_counts()    # Count unique values

# Modifying Data
df['new_col'] = values       # Add column
df.drop('col', axis=1)       # Drop column
df.sort_values('col')        # Sort
df.groupby('col').mean()     # Group by

# Handling Missing Data
df.isnull().sum()            # Count missing
df.dropna()                  # Remove missing
df.fillna(value)             # Fill missing