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

## Data Visualization & Inferences

### 1. **SUBSCRIPTION PLAN BY REVENUE**

#### Pivot Table
![Subscription Plan by Revenue](https://github.com/user-attachments/assets/4dc44f7b-f8b5-4309-a913-947beee0207e)

#### **Inference**
- Dominant Revenue Source: The Basic subscription plan is the highest revenue generator, contributing (currency)33,776,735, which accounts for approximately 49.9% of the total revenue of (currency)67,540,175. This indicates that the Basic plan is likely appealing to a significant portion of the customer base.

- Close Competition Between Plans: The Premium and Standard plans generate similar revenue, with the Premium plan at (currency)16,899,064 and the Standard plan at (currency)16,864,376. The proximity of these figures suggests a competitive landscape between these two subscription tiers, indicating that customers are likely evaluating both options based on value and features.

- Potential for Growth in Premium and Standard Plans: Given that the Basic plan constitutes almost half of the revenue, there may be opportunities to enhance the features or marketing of the Premium and Standard plans to increase their appeal. The close revenue figures suggest that minor adjustments could potentially lead to greater customer conversion from Basic to higher-tier plans.

- Market Preferences: The strong revenue from the Basic plan indicates a preference for more accessible pricing or entry-level offerings among customers. This could inform future product development and pricing strategies, suggesting a market need for affordable options.

- Revenue Distribution Insight: The distribution of revenue among the three plans shows that while the Basic plan dominates, the combined revenue of the Premium and Standard plans ((currency)33,763,440) is substantial. This highlights the importance of all tiers in contributing to overall revenue, emphasizing the need to maintain a balanced approach to marketing and feature enhancement across all subscription types.

#### **Conclusion**
- Analysis  suggests a strong performance for the Basic plan, while also highlighting the competitive nature of the Premium and Standard plans, indicating opportunities for growth and optimization within the subscription offerings.


### 2. **AVERAGE SUBSCRIPTION DURATION**

#### Pivot Table
![Average Subscription Duration](https://github.com/user-attachments/assets/a1cd5af6-2e3d-4119-957d-0c184318cc04)

#### **Inference**
-The average subscription durations for the different plans are quite close to each other, with the Standard plan having the highest average duration at approximately 365.40 days. The Basic plan has the lowest average duration at approximately 365.30 days.

-Overall, the Grand Total average subscription duration is 365.35 days, indicating that, on average, customers tend to subscribe for a duration of around one year across all subscription types. This suggests a relatively stable customer retention period, but the slight differences in duration might imply varying levels of satisfaction or engagement with each subscription type.

#### **Recommendations**:
- To further understand these patterns, it may be useful to analyze customer feedback, subscription features, or demographics associated with each plan.

 
### 3. **MOST POPULAR SUBSCRIPTION PLAN**

#### Pivot Table
![Most Popular Subscription Type](https://github.com/user-attachments/assets/d62c6b27-c6cd-4fcc-a9e0-1f8a671910c1)

#### **Inference**
- The Basic subscription is by far the most popular choice among customers, with a total of 16,921 subscriptions, representing a significant majority of the total 33,787 subscriptions. In contrast, both the Premium and Standard subscriptions have similar counts of 8,446 and 8,420 customers, respectively.

- This indicates that the Basic plan appeals to a larger customer base, which could suggest it meets the needs of the majority effectively, possibly due to its cost-effectiveness or the features offered. The relatively close counts for the Premium and Standard plans suggest that these options may cater to a niche market or specific customer preferences, but they are not as widely adopted as the Basic plan.

#### **Recommendations**:
-There may be need to explore factors contributing to the popularity of the Basic subscription, such as pricing, features, or customer demographics, as well as reasons why customers may choose the other subscription types despite their lower popularity.


### 4. **SUBSCRIPTION REVENUE BY REGION**

#### Pivot Table
![Subscription Revenue by Region](https://github.com/user-attachments/assets/f52bc4cd-03dc-444b-83f8-1ba59c907316)

#### **Inference**
- The total subscription revenue across all regions is (currency)67.54 million, with revenues being relatively balanced among the four regions. The East region leads slightly with (currency)16,958,763, followed closely by the North at (currency)16,817,972, the South at (currency)16,899,064, and the West at (currency)16,864,376.

- This relatively even distribution of revenue suggests that customer demand for subscriptions is consistent across different geographic areas, indicating a potentially robust and evenly spread market presence. The East region's marginally higher revenue could point to either a larger customer base, higher subscription rates, or more effective marketing strategies in that area.

#### **Recommendations**:
Further analysis could explore factors influencing these revenue figures, such as regional marketing efforts, economic conditions, or customer preferences, to better understand the dynamics driving subscription revenue in each region. Additionally, investigating the specific features or pricing of subscriptions in each region may provide insights into why certain regions outperform others.


### 5. **SUBSCRIPTION PLAN REVENUE BY MONTH**

#### Pivot Table
![Subscription Plan Revenue by Month](https://github.com/user-attachments/assets/01524a3b-f115-44f1-b95e-fb4f959b3930)

#### **Inference**
Based on the subscription plan revenue data by month for the years 2022 and 2023,
- Overall Revenue Decline: The total revenue decreased from (currency)40,538,438 in 2022 to (currency)27,001,737 in 2023, indicating a significant decline of approximately 33.5%. This suggests potential challenges in customer retention or market conditions affecting subscription uptake.

- Basic Plan Dominance: The Basic subscription plan consistently generates the highest revenue in both years, totaling (currency)33,776,735 across the entire period. Its strong performance indicates a robust customer preference for this tier, making it a critical component of overall revenue.

- Stable Performance of Premium and Standard Plans: Both the Premium and Standard plans show relatively stable revenue figures over the months, although they contribute less than the Basic plan. The Premium plan totaled (currency)16,899,064 and the Standard plan totaled (currency)16,864,376, reflecting a competitive landscape between these two tiers, but indicating they are less appealing than the Basic plan.

- Monthly Revenue Trends: The monthly data reveal fluctuations in revenue across the months, with certain months demonstrating peaks (e.g., November 2022 for Basic plan revenue at (currency)3,437,444). There appears to be no clear seasonal pattern; however, some months show stronger revenue performance for the Basic plan compared to others.

- Opportunities for Growth: The decrease in overall revenue, particularly in the Premium and Standard plans, suggests an opportunity for targeted marketing strategies to boost interest in these tiers. Improving features or offering promotions could potentially convert Basic subscribers to higher-tier plans.

- Consistent Subscription Activity: Despite the overall decline in revenue, the Basic plan's monthly revenue remains relatively consistent throughout both years, suggesting a stable base of customers. This consistency can serve as a foundation for future growth if the business can enhance the appeal of the Premium and Standard plans.

#### Recommendation:
-The data highlights the need for strategic initiatives to address the declining revenue trend while leveraging the strong performance of the Basic plan and exploring ways to enhance the Premium and Standard offerings to maximize overall subscription revenue.

  
### 6. **CANCELLATION RATE**

#### Pivot Table
![Cancelation Rate](https://github.com/user-attachments/assets/311d4f78-c5b7-4d4a-ba40-aad33ad70e70)

#### **Inference**
- Overall Cancellation Rate: The overall cancellation rate stands at 44.91%, indicating that nearly half of the customers have canceled their subscriptions. This high rate is concerning and suggests potential issues with customer satisfaction, product fit, or competitive pressure.

- Churn by Subscription Type: The Basic plan shows the highest cancellation rate among the subscription types, with 15.00% of customers canceling their subscriptions. This is significant given that the Basic plan also has the largest customer base (11,854), making it critical for the business to understand the factors contributing to these cancellations.

- Premium and Standard Plans: Both the Premium and Standard plans have similar cancellation rates of  14.99% and 14.93%, respectively. This indicates that these higher-tier plans are not immune to churn, highlighting a need for investigation into customer experiences across all plans.

- Active Customers vs. Canceled Customers: The analysis shows that a significant portion of active customers (55.09%, or 18,612) have not canceled their subscriptions. This retention rate provides an opportunity for the business to leverage positive customer experiences and feedback to encourage upselling and reduce churn in higher-tier plans.

- Implications for Customer Retention Strategies: With cancellation rates being relatively high across all subscription types, particularly in the Basic plan, there is a strong need for targeted customer retention strategies. This could include improving customer service, enhancing product offerings, or implementing loyalty programs aimed at reducing churn and increasing customer satisfaction.

- Potential for Upselling: The result also suggests that since a majority of active customers remain subscribed, there may be an opportunity to identify and upsell those in the Basic plan to the Premium or Standard plans. This could improve overall revenue while providing customers with additional features that may enhance their satisfaction.

#### Conclusion 
While there is a substantial customer base remaining active, the high cancellation rates—especially among the Basic plan subscribers—indicate an urgent need for deeper analysis into customer experiences and improved retention strategies to enhance loyalty and reduce churn across all subscription types.


### 7. **CANCELLATION RATES BY REGION**

#### Pivot Table
![Cancellation Rates by Region](https://github.com/user-attachments/assets/a66260a8-2bd2-45bd-aa9d-b70ef30cbfa8)

#### **Inference**
- Overall Cancellation Rate: The overall cancellation rate stands at 44.91%, indicating that a significant proportion of customers across all regions have canceled their subscriptions. This high churn rate signals potential issues that need addressing to improve customer retention.

- Regional Distribution of Active Customers: The East region has the highest number of active customers (8,488), representing 25.12% of the total active customers. This region also has a notable number of cancellations, suggesting that while it has a large customer base, it may also face challenges in customer satisfaction or engagement.

- Cancellation Rates by Region: The North region has the highest cancellation rate at 15.00%, closely followed by the South (14.99%) and West (14.93%) regions. This indicates that these regions may be experiencing higher dissatisfaction or competitive pressure compared to the East.

- Retention in the East: The East region has a relatively lower cancellation rate compared to the other regions, which might suggest stronger customer loyalty or satisfaction in this area. Understanding the factors contributing to this stability could provide insights for improving retention strategies in other regions.

- Opportunities for Targeted Strategies: Given that the North, South, and West regions exhibit higher cancellation rates, targeted customer retention strategies should be developed to address the specific needs and concerns of customers in these areas. This might involve focused marketing campaigns, enhanced customer service efforts, or tailored product offerings to boost satisfaction and reduce churn.

#### Conclusion
In conclusion, while there are regions with strong active customer bases, the high cancellation rates, particularly in the North, South, and West regions, indicate a pressing need for targeted retention efforts to address customer concerns and improve satisfaction across all geographical areas.

#### Recommendations
- Actionable Insights for Improvement: The result highlights the need for a deeper investigation into the customer experience within the regions with higher cancellation rates. Identifying the root causes of dissatisfaction and implementing changes based on customer feedback could help reduce churn and improve overall retention rates.


### 8. **TOTAL NUMBER OF CUSTOMERS BY REGION**

#### Pivot Table
![Total Number of Customers by Region](https://github.com/user-attachments/assets/cbbc0c6d-bf97-4723-8595-ccf57bf84b55)

#### **Inference**  
- Balanced Customer Distribution: The customer distribution across the four regions—East (8,488), North (8,433), South (8,446), and West (8,420)—is relatively balanced, with only slight variations in customer counts. This suggests that the business has successfully established a presence across all regions.

- East Region as the Largest Segment: The East region has the highest number of customers at 8,488, accounting for approximately 25.1% of the total customer base. This could indicate stronger market penetration or customer acquisition strategies in that region compared to others.

- North Region Close in Competition: The North region is very close to the East in customer numbers, with only a difference of 55 customers. This proximity indicates a competitive landscape, suggesting that strategies implemented in one region may be effective in the other.

- Opportunity for Growth: Although all regions have a similar number of customers, there is room for growth, especially in the South and West regions, which are slightly lower in customer counts (8,446 and 8,420, respectively). Targeted marketing efforts or service enhancements in these regions could help boost customer acquisition and retention.

- Strategic Resource Allocation: Given the relatively equal distribution of customers, the business can allocate resources and marketing efforts uniformly across regions. However, focusing slightly more on the East and North regions might yield better returns due to their larger customer bases.

- Implications for Regional Marketing: The balanced customer distribution allows for tailored regional marketing strategies to optimize engagement and retention. Understanding regional preferences and customer behaviors could further enhance the effectiveness of these strategies.

#### Conclusion
- The relatively balanced customer distribution across the regions highlights a strong market presence, with the East region leading slightly. This provides a solid foundation for the business to implement targeted growth strategies, particularly in the South and West regions, to enhance overall customer acquisition and retention efforts.


### POWER BI 
![Customer Data PowerBI Visuals](https://github.com/user-attachments/assets/fd950ecc-1d62-43c9-8410-fd065d19175e)







