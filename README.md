# Data-Wrangling-in-Python-Pandas

Here's the GitHub README-style format for documenting Data Wrangling in Python with Pandas. You can copy-paste this directly into a README.md file on your GitHub repo:

markdown
Copy
Edit
# 🧹 Data Wrangling in Python using Pandas

Data wrangling (also called data munging) is the process of cleaning, transforming, and preparing raw data for analysis. This guide covers key operations using the **Pandas** library in Python.

---

## 📥 1. Loading Data

```python
import pandas as pd

# Load from CSV
df = pd.read_csv('data.csv')

# Load from Excel
df = pd.read_excel('data.xlsx')
🔍 2. Exploring & Cleaning Data
View Data
python
Copy
Edit
df.head()          # First 5 rows
df.tail()          # Last 5 rows
df.info()          # Column types & non-nulls
df.describe()      # Summary statistics
df.columns         # Column names
df.shape           # (rows, columns)
Rename Columns
python
Copy
Edit
df.rename(columns={'OldName': 'NewName'}, inplace=True)
Drop Columns or Rows
python
Copy
Edit
df.drop(['Col1', 'Col2'], axis=1, inplace=True)  # Drop columns
df.drop([0, 1], axis=0, inplace=True)            # Drop rows
Handle Missing Values
python
Copy
Edit
df.isnull().sum()                      # Check nulls
df.dropna(inplace=True)                # Drop rows with any null
df.fillna(0, inplace=True)             # Fill nulls with 0
df['col'].fillna(df['col'].mean(), inplace=True)  # Fill with mean
🔄 3. Transforming Data
Change Data Types
python
Copy
Edit
df['col'] = df['col'].astype('int')
Replace Values
python
Copy
Edit
df['gender'].replace({'M': 'Male', 'F': 'Female'}, inplace=True)
Apply Functions
python
Copy
Edit
df['price_with_tax'] = df['price'].apply(lambda x: x * 1.18)
📊 4. Filtering & Sorting
Filter Rows
python
Copy
Edit
df[df['age'] > 25]
df[(df['age'] > 25) & (df['gender'] == 'Male')]
Sort Data
python
Copy
Edit
df.sort_values(by='age', ascending=False)
🔢 5. Grouping & Aggregation
python
Copy
Edit
df.groupby('category')['sales'].sum()
df.groupby(['region', 'product']).agg({'sales': 'sum', 'quantity': 'mean'})
🔗 6. Merging & Joining
python
Copy
Edit
# Merge on common column
pd.merge(df1, df2, on='id', how='inner')  # Options: inner, outer, left, right

# Concatenate vertically or horizontally
pd.concat([df1, df2], axis=0)  # Stack rows
pd.concat([df1, df2], axis=1)  # Combine columns
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
✅ Key Takeaways
Use .info() and .describe() to understand your data quickly.

Handle missing values early.

Use groupby() and aggregation to get insights.

Transform your data with .apply() and .astype().

Always validate your changes before proceeding to analysis or modeling.

📁 Requirements
Python 3.x

pandas

bash
Copy
Edit
pip install pandas
Feel free to fork this and add your own examples or notebooks! 🚀

yaml
Copy
Edit

---

Let me know if you'd like me to create a Jupyter Notebook version of this too, or help you push it to GitHub.
