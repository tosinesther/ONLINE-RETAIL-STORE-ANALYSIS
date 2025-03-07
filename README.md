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
### Visualizations
![Screenshot 2025-03-07 192422](https://github.com/user-attachments/assets/239eada6-a2e8-4e69-9e92-57e830504cb6)
The trend reveals a hike in sales around 2011
![Screenshot 2025-03-07 192756](https://github.com/user-attachments/assets/c0ad8233-d376-41bd-9b22-fcb22edbb85d)
This visual uncovers the monthly sales trend around 2011. Seasonal demand contributed significantly to the sales boost.
![Screenshot 2025-03-07 192904](https://github.com/user-attachments/assets/89d4b879-9d58-48e9-bf5a-fd360f7b41b4)
UK had a serious boost in sales around 2011 - contributing significantly to the sales hike, also expansion in new international market was a big contribution.
![Screenshot 2025-03-07 193000](https://github.com/user-attachments/assets/c9e515ff-b17e-474d-a8bd-7cbbc185099e)
There was a high rate of new customers in 2011, this contributed significantly to the sales hike.
![Screenshot 2025-03-07 193054](https://github.com/user-attachments/assets/0b5942aa-ce5f-4aea-bdf3-660e29d0d260)
![Screenshot 2025-03-07 193156](https://github.com/user-attachments/assets/831678ee-bfa5-43a5-8331-7033be3ffe75)
![Screenshot 2025-03-07 193229](https://github.com/user-attachments/assets/4d8d62a1-dc7c-4419-849d-0dfee442a984)
![Screenshot 2025-03-07 193351](https://github.com/user-attachments/assets/17854be0-f788-48a4-b9bd-34c6411a7dec)
![Screenshot 2025-03-07 193300](https://github.com/user-attachments/assets/55f88aa2-088f-4e75-b80e-4d7a9709b46e)
We observed that UK dominated in sales because they have a dominant customer base as compared to other countries.
![Screenshot 2025-03-07 193436](https://github.com/user-attachments/assets/99526506-2a56-40cb-81a2-4e905e763e8b)
## Feature Engineering
### Key Features Created:
1. Transaction-Based Features

- TotalSales = Quantity * UnitPrice
- AvgSpendPerPurchase = df.groupby("CustomerID")["TotalSales"].transform("mean")
- HighSpender = (AvgSpendPerPurchase > Median(AvgSpendPerPurchase)).astype(int)
2. Customer Behavior Features
- TotalTransactions = df.groupby("CustomerID")["InvoiceNo"].transform("nunique")
- AvgItemsPerPurchase = df.groupby("CustomerID")["Quantity"].transform("mean")
- FrequentBuyer = (TotalTransactions > Median(TotalTransactions)).astype(int)
3. Time-Based Features
- Extracted Year, Month, Day, Hour, Weekday from InvoiceDate.
- Calculated Recency as the number of days since last purchase.
- Created a Seasonality flag for peak sales months (Nov-Dec).
4. Scaling Numerical Features
- Used MinMaxScaler to normalize features like Quantity, UnitPrice, TotalSales, Recency.
### Data Preprocessing
- Dropped irrelevant columns (InvoiceNo, StockCode, Description, InvoiceDate).
- Encoded categorical features (Country, ProductCategory).
- Applied SMOTE to balance class distribution.
### Machine Learning Model: Predicting High-Spending Customers
#### Model Used: Logistic Regression
- Performance Metrics:
  - Accuracy: 90.27%
  - Precision: 91.85%
  - Recall: 90.27%
  - F1 Score: 90.17%
- Overfitting Check:
  - Training Accuracy: 96.18%
  - Test Accuracy: 90.27%
  - Conclusion: Possible overfitting detected.
- Hyperparameter Tuning:
  - Best Regularization Strength (C): 100
  - Tuned Test Accuracy: 99.66%
  - Conclusion: Overfitting significantly reduced.
#### Feature Importance
####![Screenshot 2025-03-07 195522](https://github.com/user-attachments/assets/5648b48b-919f-4715-adb1-ca00499cb691)
#### Sales Forecasting using ARIMA
![Screenshot 2025-03-07 195803](https://github.com/user-attachments/assets/e58ec2de-4e29-4e43-8cea-0713867dd0e8)
- Key Observations:
  - Steady growth, fluctuating around 1,850 - 1,865 units.
  - February sees the highest sales (1,865 units).
  - No drastic spikes or drops.
![Screenshot 2025-03-07 195852](https://github.com/user-attachments/assets/10df11ad-5bb5-45d6-9810-6ef568e715e8)
### Business Recommendations
- Leverage Peak Sales Insights to Sustain Growth: Strengthen acquisition campaigns in months with historically high sales and offer volume-based incentives to encourage bulk purchases, especially among high-spending customers.

- Expand Internationally by Replicating UK’s Success: Apply the UK’s successful strategies to Eire, Netherlands, Germany, and France, and monitor customer response and adjust strategies to optimize sales in these new regions.

- Strengthen Customer Retention Through Targeted Promotions: Leverage referral programs to encourage high-value customers to bring in new buyers.

- Align Inventory Planning with Seasonal Sales Trends: Launch seasonal marketing campaigns with limited-time offers and special promotions.

- Sustain Sales Growth Using Predictive Sales Forecasting: Introduce new product lines based on emerging market trends and consumer behavior shifts.

### Conclusion
- This project provides actionable insights into customer behavior, sales forecasting, and revenue generation. The predictive models help businesses make data-driven decisions, optimize inventory, and enhance customer engagement.

  




