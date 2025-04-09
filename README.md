# EDA RETAIL
## TABLE OF CONTENTS
. [OVERVIEW](#overview)

. [DATA SOURCE](#data-source)

. [LANDING PAGE](#landing-page)

. [DATA TOOLS](#data-tools)

. [DATA PROCESSING](#data-processing)

. [RECOMMENDATION](#recommendation)

# OVERVIEW 
This project performs Exploratory Data Analysis (EDA) on a retail sales dataset to uncover key insights into customer purchasing behavior, sales trends, and product performance. Using Python, Pandas, Seaborn, and Matplotlib.
# DATA SOURCE
- The primary data source is gotten from kaggle.com [DATASET](https://www.kaggle.com/datasets/mohammadtalib786/retail-sales-dataset)
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

![Isnull](https://github.com/NECHEBLESSING/EDA.Retail/blob/main/project%20EDA%201.PNG)


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
![DesriptiveStaistics](https://github.com/NECHEBLESSING/EDA.Retail/blob/main/PJ%20EDA%207.PNG)

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
![SALESSTRENDOVERTIME](https://github.com/NECHEBLESSING/EDA.Retail/blob/main/PJ%20EDA%202.PNG)

3. **Customer & Product Analysis**
- Top 5 customers by total purchases
```
top_customers = df.groupby('Customer ID')['Total Amount'].sum().sort_values(ascending=False).head(5)
print(top_customers)
```
![top5customers](https://github.com/NECHEBLESSING/EDA.Retail/blob/main/PJ%209.PNG)
- Top 5 best-selling products
```
top_products = df.groupby('Product Category')['Total Amount'].sum().sort_values(ascending=False).head(5)
print(top_products)
```
![topproduct](https://github.com/NECHEBLESSING/EDA.Retail/blob/main/pj%2010.PNG)
4. Data Visualization
-  Sales Distribution
```
plt.figure(figsize=(10,5))
sns.histplot(df['sales'], bins=20, kde=True)
plt.title('Sales Distribution')
plt.show()
```
![SD](https://github.com/NECHEBLESSING/EDA.Retail/blob/main/PJ%20EDA%204.PNG)

- Sales by Product Category (Bar Chart)
```
plt.figure(figsize=(12,6))
df.groupby('product_category')['sales'].sum().sort_values().plot(kind='barh', color='skyblue')
plt.title('Total Sales by Product Category')
plt.xlabel('Total Sales')
plt.ylabel('Product Category')
plt.show()
```
![PD](https://github.com/NECHEBLESSING/EDA.Retail/blob/main/PJ%20EDA%205.PNG)

- Correlation Heatmap
```
sns.heatmap(numeric_df.corr(), annot=True, cmap='coolwarm', fmt=".2f")
```
![CH](https://github.com/NECHEBLESSING/EDA.Retail/blob/main/PJ%20EDA%206.PNG)

 ## RECOMMENDATION
1.**Focus on High-Spending Customers**
- A small percentage of customers  are responsible for a large portion of revenue.
  
**These are the following customers**
  
- Customer ID

CUST015    2000

CUST412    2000

CUST970    2000

CUST547    2000

CUST281    2000

  **Action**
- Implement loyalty programs or exclusive discounts for top customers.
- Send personalized emails and early access to new products to keep them engaged.

2.**Optimize Sales on High-Traffic Days**
- There are more significantly sales on weekends
  
**Action**
- Launch flash sales or promotions on high-traffic days.
- Ensure inventory and staffing are adequate on those days to meet demand.

3 **Stock High-Performing Product Categories**
- Electronics are purchased more often
  
**Action**
- Increase inventory for top-performing categories.
- Use product bundling to promote lower-performing product like Beauty categories alongside bestsellers.

4.**Leverage Gender-Based Insights**
- Sales are unevenly distributed across gender groups.
  
**Action**
- Create gender-specific promotions or ads targeting the higher-spending group.
- Explore product feedback to better cater to the needs of underrepresented groups.

5 **Plan Inventory Based on Seasonal Sales Trends**
- Sales trends over time reveal seasonal patterns.
**Action**
- Prepare early restocking plans and marketing campaigns aligned with peak months. The peak months are April,May and October ~
- Using predictive models to forecast future sales during peak seasons,
![PMF](https://github.com/NECHEBLESSING/EDA.Retail/blob/main/EDA%20200.PNG)

- Showing forecast predictions of same months in 2025 will be the peak months.
6 **Simplify Product Mix Based on Market Basket Analysis**
- Certain products are frequently bought together Like (Clothing and Beauty)

 **Action**
- Offer combo deals or bundles to increase average transaction value.
- Redesign store layout (online or physical) to promote frequently paired products.
  
7.**Improve Data Collection**
- Insight: The current dataset lacks deeper demographics (like age, location).
  
**Action**
- Encourage customers to create detailed profiles during sign-up.
- Offer small incentives for completing surveys that enhance customer understanding.










