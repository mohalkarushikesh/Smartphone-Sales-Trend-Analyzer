### Project: SmartPhone Sales Trend Analyzer

#### Step 1: Set up the environment
Install Pandas and other required libraries if you haven't already:
```python
pip install pandas matplotlib seaborn
```

#### Step 2: Import libraries
```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

#### Step 3: Load the dataset
Let's assume we have a CSV file named `sales_data.csv` with columns like `Date`, `Product`, `Quantity`, `Price`.
```python
# Load the dataset
df = pd.read_csv('sales_data.csv')
```

#### Step 4: Explore the dataset
```python
# Display the first few rows of the dataset
print(df.head())

# Summary statistics
print(df.describe())

# Check for missing values
print(df.isnull().sum())
```

#### Step 5: Clean the dataset
```python
# Drop rows with missing values
df = df.dropna()

# Convert 'Date' column to datetime format
df['Date'] = pd.to_datetime(df['Date'])
```

#### Step 6: Analyze the data
```python
# Total sales for each product
product_sales = df.groupby('Product')['Quantity'].sum()
print(product_sales)

# Ensure the DataFrame is sorted by date
df = df.sort_values('Date')

# Set the 'Date' column as the index
df = df.set_index('Date')

# Resample the data to get monthly sales
monthly_sales = df['Quantity'].resample('M').sum()
print(monthly_sales)
```

#### Step 7: Visualize the data
```python
# Bar plot of total sales per product
plt.figure(figsize=(10, 6))
sns.barplot(x=product_sales.index, y=product_sales.values)
plt.title('Total Sales per Product')
plt.xlabel('Product')
plt.ylabel('Quantity Sold')
plt.show()

# Line plot of monthly sales trend
plt.figure(figsize=(10, 6))
plt.plot(monthly_sales.index, monthly_sales.values, marker='o', linestyle='-', color='b')
plt.title('Monthly Sales Trend')
plt.xlabel('Month')
plt.ylabel('Quantity Sold')
plt.grid(True)
plt.show()
```

This updated project file should help you analyze and visualize the sales data for the products Samsung, Apple, Xiaomi, OPPO, and Vivo. Let me know if you need any further assistance!
