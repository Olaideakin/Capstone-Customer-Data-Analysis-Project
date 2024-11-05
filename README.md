### Capstone-Customer-Data-Analysis-Project
This repository contains a comprehensive analysis of customer subscription across Regions. This project is designed to analyze a comprehensive customer dataset to gain insights into subscription patterns, revenue generation, and customer engagement across various regions. 

### Project Significance: Customer Subscription Analysis
Understanding customer subscription patterns, revenue generation, and churn is essential for businesses that rely on recurring revenue models. This project is significant for several key reasons:

- Enhanced Customer Retention: By analyzing the subscription duration, types, and cancellation trends, the project will reveal insights into factors that contribute to customer churn. This information can guide strategies to improve retention, such as targeted retention offers or adjustments to subscription plans.

- Revenue Optimization: Identifying high-performing regions and subscription types allows the business to focus on the most profitable areas. This revenue analysis will highlight segments that contribute most significantly to income, helping optimize marketing and product development investments.

- Regional and Market Segmentation: By examining regional data, the project can uncover market-specific trends, revealing which regions may benefit from customized marketing campaigns. This segmentation can also inform strategic decisions regarding regional investments and potential market expansion.

- Informed Product and Pricing Strategies: Insights into popular subscription types and durations will help shape future product offerings and pricing models. Understanding customer preferences can lead to the development of new subscription tiers, loyalty programs, or seasonal pricing strategies tailored to customer needs.

- Forecasting and Strategic Planning: Trends observed in this dataset can support forecasting efforts, enabling more accurate predictions for future subscriptions, revenue growth, and regional expansion. This project thus provides a foundation for making data-driven business decisions that align with customer demand and market conditions.

- In essence, this project is essential for building a deeper understanding of customer behavior, driving growth, and supporting the long-term success of the business through data-informed decision-making.

## Data Sources/ Data Generation
Capstone Customer Data: The primary dataset used for this analysis is the "Capstone Customer Data" file, containing detailed datapoints which include but not limited to customerid, customername, subscription type and revenue. The dataset was generated from different regions.

## Data Structure
The sales dataset employed for this analysis was structured (dataset was in a tabular form). 

## Data Description
The dataset contained the essential datapoints:

- CustomerID: A unique identifier assigned to each individual customer within the sales dataset
- CustomerName: A unique datapoints that contains the name of each customer
- Region: The geographical area or division where transaction was made
- Subscription Type: This describes the specific plan, tier, or category of service that a customer has chosen to subscribe to
- Subscription Start: The date when a customer's subscription begins. It marks the first day of access to the subscribed service or product for that customer.
- Subscription End: The date on which a customer’s subscription is set to expire or end. It marks the last day of access to the subscribed service or product for the customer unless the subscription is renewed.
- Cancelled:  This is a data point indicating whether a customer’s subscription has been terminated before its scheduled end date or has not been renewed. It appeared as true/fasle appaered in binary number where 0=false and 1=true
- Revenue: The total monetary value generated from the sale

## Tools Used
- Microsoft Excel [Download Here](https://www.microsoft.com)
  The dataset was ingested, transformed, visualized, analysed and presented
1) For Data Cleaning: The capstone sales dataset was cleaned to ensure duplicates were removed and ensured all columns were properly
2) For Data Analysis: The capstone dataset was analyzed using Microsoft Excel, statistical measures and techniques were deployed over the dataset
3) For Data Visualization: Charts and graphs were deployed to summarize the dataset such as pivot tables, bar charts etc

- SQL- Structured Query Language for Querying of Data [Download Here](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)

- GitHub for Portfolio Building [Join Here](https://github.com/)
  
- Power BI(Business Intelligence) for Data Visualization [Download Here](https://www.microsoft.com)

## Data Cleaning and Preparation
The initial phase of the data cleaning and preparations performed the following actions;
1) Data loading and inspection
2) Handling missing variables
3) Data cleaning and formatting

## Exploratory Data Analysis
EDA involves exploring the dataset
1. Use of pivot tables to find subscription patterns, average subscription duration and the most popular types of subcription
2. Use of SQL to query and 
- a) retrieve the total number of customers from each region
- b) find the most popular subscription type by number of customers
- c) find customers who canceled their subscription within 6 months.
- d) calculate the average subscription duration for all customers.
- e) find customers with subscriptions longer than 12 months.
- f) calculate total revenue by subscription type.
- g) find the top 3 regions by subscription cancellations.
- h) find the total number of active and canceled subscriptions.
3. Use of Power BI to create a dashboard that visualizes the key customer segments, cancellation, and subscription trends.

## Data Analysis
#### Functions Used in Excel
```
AVERAGEIF, SUMIF
```
  
#### Query Used in SQL
```
- **Total Number of Customers from each Region**
SELECT Region, COUNT(CustomerID) AS TotalCustomers
FROM [dbo].[Customer_Data]
GROUP BY Region;
```

```
- **Most Popular Subscription Type by the Number of Customers**
SELECT TOP 1 SubscriptionType, COUNT(DISTINCT CustomerID) AS TotalCustomers
FROM [dbo].[Customer_Data]
GROUP BY SubscriptionType
ORDER BY TotalCustomers DESC;

SELECT TOP 1 SubscriptionType, COUNT(CustomerID) AS TotalCustomers
FROM [dbo].[Customer_Data]
GROUP BY SubscriptionType
ORDER BY TotalCustomers DESC;
```

```
-**Customers who Canceled their Subscription within 6 Months**
SELECT * FROM [dbo].[Customer_Data]
WHERE Canceled = '1' 
  AND DATEDIFF(month, SubscriptionStart, SubscriptionEnd) <= 6;
```

```
-**Average Subscription Duration for all Customers**
SELECT AVG(DATEDIFF(day, SubscriptionStart, SubscriptionEnd)) AS AverageDurationDays
FROM [dbo].[Customer_Data]
WHERE SubscriptionStart IS NOT NULL 
  AND SubscriptionEnd IS NOT NULL;
```

```
-**Customers with Subscriptions Longer than 12 Months
SELECT * FROM [dbo].[Customer_Data]
WHERE DATEDIFF(month, SubscriptionStart, SubscriptionEnd) > 12
  AND SubscriptionStart IS NOT NULL 
  AND SubscriptionEnd IS NOT NULL;
```

```
-**Total Revenue by Subscription Type
SELECT SubscriptionType, SUM(Revenue) AS TotalRevenue
FROM [dbo].[Customer_Data]
WHERE Revenue IS NOT NULL
GROUP BY SubscriptionType
ORDER BY TotalRevenue DESC;

SELECT SubscriptionType, SUM(Revenue) AS TotalRevenue
FROM [dbo].[Customer_Data]
WHERE Revenue IS NOT NULL
GROUP BY SubscriptionType
ORDER BY TotalRevenue
```

```
-**Top 3 Regions by Subscription Cancellations**
SELECT TOP 3 Region, COUNT(*) AS CanceledCount
FROM [dbo].[Customer_Data]
WHERE Canceled = 1
GROUP BY Region
ORDER BY CanceledCount;
```

```
-**Total Number of Active and Canceled Subscriptions**
SELECT 
    SUM(CASE WHEN Canceled = 1 THEN 1 ELSE 0 END) AS TotalCanceled,
    SUM(CASE WHEN Canceled = 0 THEN 1 ELSE 0 END) AS TotalActive
FROM [dbo].[Customer_Data];
```


 






