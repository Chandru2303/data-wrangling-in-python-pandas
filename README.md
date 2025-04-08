# Data-Wrangling-in-Python-Pandas

 1. Loading Data
python
Copy
Edit
import pandas as pd

# Load from CSV
df = pd.read_csv('data.csv')

# Load from Excel
df = pd.read_excel('data.xlsx')

# Load from SQL (if connected)
# pd.read_sql(query, connection)
🧼 2. Exploring & Cleaning Data
✅ View data
python
Copy
Edit
df.head()      # First 5 rows
df.tail()      # Last 5 rows
df.info()      # Column types and nulls
df.describe()  # Summary stats
df.columns     # Column names
df.shape       # Rows and columns
✅ Rename columns
python
Copy
Edit
df.rename(columns={'OldName': 'NewName'}, inplace=True)
✅ Drop columns or rows
python
Copy
Edit
df.drop(['Col1', 'Col2'], axis=1, inplace=True)  # Drop columns
df.drop([0, 1], axis=0, inplace=True)            # Drop rows
✅ Handle missing values
python
Copy
Edit
df.isnull().sum()              # Check nulls
df.dropna(inplace=True)        # Drop rows with any null
df.fillna(0, inplace=True)     # Fill nulls with 0
df['col'].fillna(df['col'].mean(), inplace=True)  # Fill with mean
🔄 3. Transforming Data
✅ Change data types
python
Copy
Edit
df['col'] = df['col'].astype('int')
✅ Replace values
python
Copy
Edit
df['gender'].replace({'M': 'Male', 'F': 'Female'}, inplace=True)
✅ Apply functions
python
Copy
Edit
df['price_with_tax'] = df['price'].apply(lambda x: x * 1.18)
📊 4. Filtering & Sorting
✅ Filter rows
python
Copy
Edit
df[df['age'] > 25]
df[(df['age'] > 25) & (df['gender'] == 'Male')]
✅ Sort data
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
🧱 6. Merging & Joining
python
Copy
Edit
pd.merge(df1, df2, on='id', how='inner')     # Types: inner, outer, left, right
pd.concat([df1, df2], axis=0)                # Stack rows
pd.concat([df1, df2], axis=1)                # Add columns
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
🧪 Example
python
Copy
Edit
df = pd.read_csv('sales_data.csv')
df.dropna(subset=['price'], inplace=True)
df['price'] = df['price'].astype(float)
df['total'] = df['price'] * df['quantity']
df.groupby('region')['total'].sum().sort_values(ascending=False)
