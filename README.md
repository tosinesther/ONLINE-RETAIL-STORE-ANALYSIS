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
