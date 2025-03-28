# OVERVIEW 
This project performs Exploratory Data Analysis (EDA) on a retail sales dataset to uncover key insights into customer purchasing behavior, sales trends, and product performance. Using Python, Pandas, Seaborn, and Matplotlib.
# DATA SOURCE
- The primary data source is gotten from kaggle.com -
# Landing page
- **Date** – The date when the transaction took place (formatted as MM/DD/YYYY).
- **Customer ID** – A unique identifier assigned to each customer.
- **Gender** – The gender of the customer (e.g., Male, Female).
- **Product Category** – The category of the purchased product (e.g., Electronics, Apparel, Groceries).
- **Product Name** – The specific name of the product purchased.
- **Quantity Sold** – The number of units purchased in a single transaction.
- **Price per Unit** – The cost of one unit of the product.
- **Total Amount** – The total revenue generated from the transaction (Quantity Sold × Price per Unit).
## DATA TOOLS
- pandas,python.
## DATA PROCESSING 
#### During data processing, the following columns were added to enhance analysis and was done on **pandas**.    
# Exploratory Data Analysis(EDA).
1. **DATACLEANING**
- Check for missing values
```
print(df.isnull().sum())
```
No missing values Found
- Convert 'Date' column to datetime format
```
df["Date"] = pd.to_datetime(df["Date"], format="%m/%d/%Y")
```
2. **Descriptive Statistics**
- Summary statistics
```
print(df.describe())
```
- Check the mean, median, mode of sales column
```
print("Mean Sales:", df['Total Amount'].mean())
print("Median Sales:", df['Total Amount'].median())
print("Mode Sales:", df['Total Amount'].mode()[0])
print("Standard Deviation:", df['Total Amount'].std())
```
2. **Time Series Analysis (Sales Trend Over Time)**
- Group by date and sum sales
```
df_time_series = df.groupby('Date')['Total Amount'].sum()
```
- Plot sales trend over time
```
plt.figure(figsize=(12,6))
df_time_series.plot(title='Sales Trend Over Time', marker='o', linestyle='-')
plt.xlabel('Date')
plt.ylabel('Total Amount')
plt.grid()
plt.show()
```
3. **Customer & Product Analysis**
- Top 5 customers by total purchases
```
top_customers = df.groupby('Customer ID')['Total Amount'].sum().sort_values(ascending=False).head(5)
print(top_customers)
```
- Top 5 best-selling products
```
top_products = df.groupby('Product Category')['Total Amount'].sum().sort_values(ascending=False).head(5)
print(top_products)
```
4. Data Visualization
-  Sales Distribution
```
plt.figure(figsize=(10,5))
sns.histplot(df['sales'], bins=20, kde=True)
plt.title('Sales Distribution')
plt.show()
```
- Sales by Product Category (Bar Chart)
```
plt.figure(figsize=(12,6))
df.groupby('product_category')['sales'].sum().sort_values().plot(kind='barh', color='skyblue')
plt.title('Total Sales by Product Category')
plt.xlabel('Total Sales')
plt.ylabel('Product Category')
plt.show()
```
- Correlation Heatmap
```
sns.heatmap(numeric_df.corr(), annot=True, cmap='coolwarm', fmt=".2f")
```






