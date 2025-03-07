# ONLINE-RETAIL-STORE-ANALYSIS

### TABLE OF CONTENT
- [Overview](#Overview)
- [Dataset description](#Dataset-Description)
- [Identified issues](#Identified-Issues)
- [Data Cleaning Process](#Data-Cleaning-Process)
- [Exploratory Data Analysis](#Exploratory-Data-Analysis)
- [Visualisations](#Visualisation)
- [Feature Engineering](#Feature-Engineering)
- [Machine Model](#Machine-Model)
- [Feature Importance](#Feature-Importance)
- [Sales Forecasting](#Sales-Forecasting)
- [Recommendations](#Recommendations)
- [Conclusion](#Conclusion)
### Overview
- This project leverages predictive analytics to drive strategic business decisions by forecasting future sales trends and identifying high-value customers. Two models were implemented: a Logistic Regression model to predict high-spending customers and an ARIMA time series model to forecast sales for the next 12 months.
### Dataset Description
#### Columns:
- InvoiceNo - Unique invoice identifier.
- StockCode - Product code.
- Description - Product name.
- Quantity - Number of products purchased.
- InvoiceDate - Date and time of transaction.
- UnitPrice - Price per unit.
- CustomerID - Unique customer identifier.
- Country - Customer's country.
### Identified Issues:
- 1,454 missing values in Description.
- 135,080 missing values in CustomerID.
- 10,624 negative values in Quantity.
- 2 negative values in UnitPrice.
- 2,515 zero values in UnitPrice.
- Special characters and blanks in Description.
- 5,268 duplicate rows.
- Some rows in Country labeled as 'Unspecified'.
### Data Cleaning Process
- Filled missing values in Description as "Unknown".
- Assigned unique negative CustomerID values for missing entries.
- Removed rows with negative Quantity and zero or negative UnitPrice.
- Dropped 5,268 duplicate rows.
- Standardized Country by removing 'Unspecified' entries.
### Exploratory Data Analysis (EDA)
#### Key Insights
###### Best-Selling Products
- Top product: Paper Craft Little Birdie (80,995 units sold).
- Second: Medium Ceramic Top Storage Jar (78,033 units).
- Third: World War 2 Gliders Asstd Designs (54,855 units).
###### Top 10 Revenue-Generating Products
- Top product: Dotcom Postage ($206,248.77 revenue).
- Second: Regency Cakestand 3 Tier ($174,131.04 revenue).
- Third: Paper Craft Little Birdie ($168,469.60 revenue).
###### Total Revenue Per Country
- United Kingdom: $9,001,855.17
- Netherlands: $285,446.34
- EIRE: $283,170.52
###### Number of Transactions Per Country
- United Kingdom: 18,019 transactions.
- Germany: 457 transactions.
- France: 392 transactions.
#### Visualizations
![Screenshot 2025-03-07 192422](https://github.com/user-attachments/assets/239eada6-a2e8-4e69-9e92-57e830504cb6)
The trend reveals a hike in sales around 2011

