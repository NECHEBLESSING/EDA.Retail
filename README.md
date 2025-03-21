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
- Convert the Date column into a proper datetime format.

```python
df.index = pd.to_datetime(df.index)
print(df.index.dtype)
```
`Day of Week` – Extracted from the `Date` column to analyze sales trends based on the day of the week.
Example values: "Monday", "Tuesday".
     
# Exploratory Data Analysis(EDA).
1. **DATACLEANING**
-  Check for Missing Values
```
missing_values = df.isnull().sum()
print("Missing Values:\n", missing_values)
```
- Convert 'Date' column to datetime type for proper time series analysis
```
df["Date"] = pd.to_datetime(df["Date"], format="%m/%d/%Y")
```
- Check for and Remove Duplicates
```duplicates = df.duplicated().sum()
print("Number of duplicates:", duplicates)
```
- Convert columns to appropriate numeric types if not already set
```
df["Transaction ID"] = df["Transaction ID"].astype(int)
df["Age"] = df["Age"].astype(int)
df["Quantity"] = df["Quantity"].astype(int)
df["Price per Unit"] = df["Price per Unit"].astype(int)
df["Total Amount"] = df["Total Amount"].astype(int)
```





