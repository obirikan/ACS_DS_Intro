# Developer Guide

## 1. Development Setup

To set up the development environment, follow these steps:

1. # Developer Guide

## 1. Development Setup

1. Clone the repository:
   git clone <REPO_URL>
   cd <REPO_NAME>

2. (Optional but recommended) Create and activate a Python virtual environment:
   python3 -m venv .venv
   source .venv/bin/activate      # On macOS/Linux
   .venv\Scripts\activate         # On Windows

3. Install project dependencies:
   pip install pandas

   If working in a Jupyter environment:
   pip install notebook

4. Open the Jupyter notebook for development:
   jupyter notebook pandas.ipynb

## 2. Running Tests

There are no automated tests provided in the current codebase.

To manually verify the functionalities:
- Open `pandas.ipynb` in Jupyter Notebook.
- Execute the cells sequentially to confirm data is loaded, explored, and manipulated correctly. 
- Check for cell output and ensure there are no errors except for the known invalid syntax in the cell with `df.shape`.

## 3. Adding a New Feature

To add or extend functionality:

1. Open `pandas.ipynb` in Jupyter.
2. Add a new cell after the relevant code section (for example, after data cleaning or after data exploration).
3. Import any additional libraries if necessary using `import`.
4. Write new code for your feature, such as:
   - Reading and merging new datasets
   - Adding new data analysis or visualization
   - Introducing new transformation, grouping, or filtering operations

Example: To add a column for the order year:
   df['order_year'] = pd.to_datetime(df['order_date']).dt.year

5. Execute the new cell to verify your addition works as intended.
6. Document your changes and update `guide.md` as needed for quick usage reference.

**Note:** If you want to add robust testing, consider adding separate Python scripts or test notebooks, and use testing frameworks (e.g. pytest or unittest), then update this guide accordingly.