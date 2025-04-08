 Here's your Data Wrangling in Python with Pandas content in proper GitHub-flavored markdown, just like the format used in your repo:

markdown
Copy
Edit
# 🧹 Data Wrangling in Python using Pandas

Data wrangling (or data munging) is the process of cleaning and transforming raw data into a usable format for analysis. This guide covers common techniques using the **Pandas** library in Python.

---

## 📥 1. Loading Data

```python
import pandas as pd

# Load from CSV
df = pd.read_csv('data.csv')

# Load from Excel
df = pd.read_excel('data.xlsx')

# Load from SQL
# df = pd.read_sql(query, connection)
🔍 2. Exploring & Cleaning Data
Viewing Data
python
Copy
Edit
df.head()          # First 5 rows
df.tail()          # Last 5 rows
df.info()          # Column info & missing values
df.describe()      # Summary statistics
df.columns         # Column names
df.shape           # (rows, columns)
Renaming Columns
python
Copy
Edit
df.rename(columns={'OldName': 'NewName'}, inplace=True)
Dropping Columns or Rows
python
Copy
Edit
df.drop(['Col1', 'Col2'], axis=1, inplace=True)  # Drop columns
df.drop([0, 1], axis=0, inplace=True)            # Drop rows
Handling Missing Values
python
Copy
Edit
df.isnull().sum()                               # Check nulls
df.dropna(inplace=True)                         # Drop rows with nulls
df.fillna(0, inplace=True)                      # Fill with 0
df['col'].fillna(df['col'].mean(), inplace=True)  # Fill with mean
🔄 3. Transforming Data
Changing Data Types
python
Copy
Edit
df['col'] = df['col'].astype('int')
Replacing Values
python
Copy
Edit
df['gender'].replace({'M': 'Male', 'F': 'Female'}, inplace=True)
Applying Functions
python
Copy
Edit
df['price_with_tax'] = df['price'].apply(lambda x: x * 1.18)
📊 4. Filtering & Sorting
Filtering Rows
python
Copy
Edit
df[df['age'] > 25]
df[(df['age'] > 25) & (df['gender'] == 'Male')]
Sorting Data
python
Copy
Edit
df.sort_values(by='age', ascending=False)
🔢 5. Grouping & Aggregating
python
Copy
Edit
df.groupby('category')['sales'].sum()
df.groupby(['region', 'product']).agg({'sales': 'sum', 'quantity': 'mean'})
🔗 6. Merging & Joining
python
Copy
Edit
# Merge on a common key
pd.merge(df1, df2, on='id', how='inner')  # Options: inner, outer, left, right

# Concatenate vertically or horizontally
pd.concat([df1, df2], axis=0)  # Rows
pd.concat([df1, df2], axis=1)  # Columns
🧹 7. Removing Duplicates
python
Copy
Edit
df.drop_duplicates(inplace=True)
📆 8. Working with Dates
python
Copy
Edit
df['date'] = pd.to_datetime(df['date'])
df['year'] = df['date'].dt.year
df['month'] = df['date'].dt.month
🧪 Sample Workflow
python
Copy
Edit
df = pd.read_csv('sales_data.csv')
df.dropna(subset=['price'], inplace=True)
df['price'] = df['price'].astype(float)
df['total'] = df['price'] * df['quantity']
df.groupby('region')['total'].sum().sort_values(ascending=False)
✅ Requirements
Python 3.x

pandas

bash
Copy
Edit
pip install pandas
📚 Resources
Pandas Documentation

Python for Data Analysis by Wes McKinney

