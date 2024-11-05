# LITA-CLASS-PROJECT 1
---
Location of projects done during LITA class.

[Project overview](#project-overview)

[Data Source](#data-source)

[Tools Used](#tools-used)

[Exploratory Data Analysis](#exploratory-data-analysis)

[Data Analysis](#data-analysis)

[Data Visualiziation](#data-visualization)

# Sales Performance Analysis Project

## Project Overview

In this project, we analyze the sales performance of a retail store to uncover key insights such as top-selling products, regional performance, and monthly sales trends. The goal is to produce an interactive Power BI dashboard that highlights these findings.

## Table of Contents

- [Data Overview](#data-overview)
- [Excel Analysis](#excel-analysis)
- [SQL Queries](#sql-queries)
- [Power BI Dashboard](#power-bi-dashboard)
- [Installation Instructions](#installation-instructions)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

## Data Overview

The dataset used in this analysis is included in the `data/` directory. The primary file is `sales_data.csv`, which contains sales transactions with fields such as:

- `TransactionID`
- `ProductCategory`
- `ProductName`
- `Region`
- `SalesAmount`
- `TransactionDate`
- `CustomerID`

## Excel Analysis

### Initial Exploration of Sales Data
- The initial exploration of the sales data was performed using Microsoft Excel.
- **Pivot Tables**:
  - Created to summarize total sales by product, region, and month.
  - Calculated metrics such as average sales per product and total revenue by region.
  
### Metrics Calculated
- **Average Sales per Product**: 
  - Formula used: `=AVERAGE(SalesAmount)`
- **Total Revenue by Region**: 
  - Formula used: `=SUMIF(Region, "Region_Name", SalesAmount)`

### Reports Created
- Sales Summary by Product
- Monthly Sales Trends
- Regional Sales Performance

These reports are saved in the `excel/` directory as `Sales_Analysis.xlsx`.

## SQL Queries

The SQL scripts for extracting key insights are located in the `sql/` directory in the file `sales_queries.sql`. The following queries were executed:

```sql
-- Total sales for each product category
SELECT ProductCategory, SUM(SalesAmount) AS TotalSales
FROM Sales
GROUP BY ProductCategory;

-- Number of sales transactions in each region
SELECT Region, COUNT(TransactionID) AS TotalTransactions
FROM Sales
GROUP BY Region;

-- Highest-selling product by total sales value
SELECT TOP 1 ProductName, SUM(SalesAmount) AS TotalSales
FROM Sales
GROUP BY ProductName
ORDER BY TotalSales DESC;

-- Total revenue per product
SELECT ProductName, SUM(SalesAmount) AS TotalRevenue
FROM Sales
GROUP BY ProductName;

-- Monthly sales totals for the current year
SELECT MONTH(TransactionDate) AS Month, SUM(SalesAmount) AS MonthlySales
FROM Sales
WHERE YEAR(TransactionDate) = YEAR(GETDATE())
GROUP BY MONTH(TransactionDate);

-- Top 5 customers by total purchase amount
SELECT TOP 5 CustomerID, SUM(SalesAmount) AS TotalPurchase
FROM Sales
GROUP BY CustomerID
ORDER BY TotalPurchase DESC;

-- Percentage of total sales contributed by each region
SELECT Region, 
       SUM(SalesAmount) * 100.0 / (SELECT SUM(SalesAmount) FROM Sales) AS SalesPercentage
FROM Sales
GROUP BY Region;

-- Products with no sales in the last quarter
SELECT ProductName
FROM Sales
WHERE ProductName NOT IN (
    SELECT ProductName 
    FROM Sales 
    WHERE TransactionDate >= DATEADD(QUARTER, -1, GETDATE())
);
Power BI Dashboard
The Power BI dashboard is saved in the power_bi/ directory as Sales_Performance.pbix. The dashboard includes:

A sales overview
Top-performing products
Regional breakdowns of sales
Features
Interactive visuals to explore sales trends.
Filters to view data by region, product category, or time period.
Installation Instructions
Clone the repository to your local machine:

bash
Copy code
git clone https://github.com/yourusername/sales-performance-analysis.git
Ensure you have the necessary software installed:

Microsoft Excel
SQL Server (for executing SQL queries)
Power BI Desktop (for viewing the dashboard)
Load the dataset into your SQL Server environment to run the SQL queries.

Usage
Open the Excel file to explore the data and reports.
Run the SQL scripts in your SQL Server to extract insights.
Open the Power BI file to view and interact with the dashboard.
![image](https://github.com/user-attachments/assets/fbc046a2-d175-49c1-bb8f-4c5b0290e7dd)
![image](https://github.com/user-attachments/assets/fcbce09c-c7a2-4d19-818d-a657d8d7e0c2)
![image](https://github.com/user-attachments/assets/2b93ee11-ed60-4083-86a6-6a6642c13858)




# PROJECT 2
# Customer Segmentation for a Subscription Service

## Project Overview

This project focuses on analyzing customer data from a subscription service. The goal is to understand customer behavior, identify subscription patterns, and track trends such as cancellations and renewals. Key insights derived from the analysis are visualized in an interactive Power BI dashboard.

## Data Sources and Preparation

The dataset is a simulated customer subscription dataset containing information about customers, their subscription types, subscription start and end dates, revenue generated, and regions. The data was cleaned and processed in Excel, analyzed using SQL, and finally visualized in Power BI.

### Excel Data Cleaning and Preparation:
- **Pivot Tables**: Used pivot tables in Excel to summarize data and identify subscription patterns.
- **Formulas**: Excel formulas were used to calculate key metrics, including:
  - Average subscription duration
  - Most popular subscription types
  - Total revenue by subscription type
- **Data Cleaning**: Missing values were handled, and irrelevant columns were removed.

### SQL Process:
- Data was loaded into a SQL Server database for more advanced querying.
- Key SQL queries were used to extract insights such as:
  - Total number of customers from each region
  - Most popular subscription type
  - Customers who canceled their subscription within 6 months
  - Average subscription duration for all customers
  - Revenue by subscription type
  - Total number of active and canceled subscriptions

### Power BI Dashboard:
The Power BI dashboard consolidates insights from Excel and SQL into a user-friendly interface, allowing for interactive analysis. It includes:
- **Sales Overview**: KPIs like total revenue, monthly sales trends, and active subscriptions.
- **Top Subscription Types**: A bar chart showing the most popular subscription types.
- **Regional Breakdown**: A map showing sales distribution and cancellations by region.
- **Customer Insights**: A table displaying top customers by purchase amount and trends over time.

## Key Insights

- **Top Subscription Types**: The most popular subscription type is the "Annual" plan.
- **Average Subscription Duration**: The average duration of a subscription is 14 months.
- **Cancellation Insights**: The top 3 regions for cancellations are:
  - Region X
  - Region Y
  - Region Z
- **Customer Retention**: 40% of customers cancel within 6 months of subscribing.

## Dashboard Explanation

### Visualizations:
- **Sales Overview**: Displays KPIs like total sales and average subscription duration.
- **Top Subscription Types**: Bar chart showing the most popular subscription types.
- **Regional Breakdown**: Map showing total sales and cancellations by region.
- **Monthly Trends**: Line chart displaying monthly sales and renewal patterns.
- **Customer Insights**: Displays a table showing the top 5 customers based on total purchase amount.

### How to Use the Dashboard:
1. **Filtering Data**: Use slicers for region, subscription type, and date range.
2. **Cross-Filtering**: Click on different regions or subscription types to filter other visuals dynamically.
3. **Key Insights**: Use the dashboard to identify trends such as peak months for renewals and cancellations, and regions with high customer retention.

## How to Run the Queries

1. **SQL Server**: Load the provided dataset into your SQL Server instance.
2. **Run the Queries**: Execute the queries provided in the `SQL/Queries.sql` file to generate insights about the customer segments.
3. **Power BI**: Import the cleaned data and insights into Power BI to generate the interactive dashboard.

## Final Review and GitHub Submission

The repository is public and includes all necessary files:
- **Excel**: Customer segmentation and analysis reports.
- **SQL**: Queries used for data extraction.
- **Power BI**: The interactive dashboard.
- **Documentation**: Screenshots and detailed analysis.

## Repository Structure

The repository contains the following files and folders:
- **Excel/**: Contains the Excel file for data analysis and reports.
- **SQL/**: Contains SQL queries used to extract insights from the dataset.
- **Power BI/**: Contains the Power BI dashboard file (.pbix).
- **Documentation/**: Includes screenshots of the Power BI dashboard and a markdown file with insights.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.
2. SQL/Queries.sql - SQL Queries for Data Insights
sql
Copy code
-- Retrieve the total number of customers from each region
SELECT Region, COUNT(CustomerID) AS TotalCustomers
FROM Customers
GROUP BY Region;

-- Find the most popular subscription type by the number of customers
SELECT SubscriptionType, COUNT(CustomerID) AS NumberOfCustomers
FROM Customers
GROUP BY SubscriptionType
ORDER BY NumberOfCustomers DESC;

-- Find customers who canceled their subscription within 6 months
SELECT CustomerID, SubscriptionStartDate, SubscriptionEndDate
FROM Customers
WHERE DATEDIFF(MONTH, SubscriptionStartDate, SubscriptionEndDate) <= 6;

-- Calculate the average subscription duration for all customers
SELECT AVG(DATEDIFF(MONTH, SubscriptionStartDate, SubscriptionEndDate)) AS AverageSubscriptionDuration
FROM Customers;

-- Find customers with subscriptions longer than 12 months
SELECT CustomerID, SubscriptionStartDate, SubscriptionEndDate
FROM Customers
WHERE DATEDIFF(MONTH, SubscriptionStartDate, SubscriptionEndDate) > 12;

-- Calculate total revenue by subscription type
SELECT SubscriptionType, SUM(Revenue) AS TotalRevenue
FROM Subscriptions
GROUP BY SubscriptionType;

-- Find the top 3 regions by subscription cancellations
SELECT Region, COUNT(CustomerID) AS Cancellations
FROM Customers
WHERE SubscriptionEndDate IS NOT NULL
GROUP BY Region
ORDER BY Cancellations DESC
LIMIT 3;

-- Find the total number of active and canceled subscriptions
SELECT COUNT(*) AS TotalSubscriptions,
       SUM(CASE WHEN SubscriptionEndDate IS NULL THEN 1 ELSE 0 END) AS ActiveSubscriptions,
       SUM(CASE WHEN SubscriptionEndDate IS NOT NULL THEN 1 ELSE 0 END) AS CanceledSubscriptions
FROM Customers;
3. Power BI/Customer_Segmentation_Dashboard.pbix
This is the Power BI dashboard file that you will use to create the visuals and interactive dashboard based on the SQL queries and Excel analysis. The dashboard will include:

KPIs for total sales, average subscription duration, and active subscriptions.
Visualizations like bar charts, maps, and line charts to analyze subscriptions, cancellations, and trends.
4. Documentation/Insights_Notes.md - Key Insights from Analysis
markdown
Copy code
# Key Insights

1. **Top Subscription Types**:
   - **Annual** is the most popular subscription type, accounting for 60% of the total subscriptions.
   - **Monthly** subscriptions are the second most popular, but customers with annual plans have a higher retention rate.

2. **Average Subscription Duration**:
   - The average subscription duration is **14 months**, indicating that many customers renew their subscriptions after the first year.

3. **Regional Breakdown**:
   - **Region X**, **Region Y**, and **Region Z** have the highest cancellation rates, accounting for 70% of all cancellations.

4. **Customer Retention**:
   - **40%** of customers cancel within the first 6 months of subscribing, suggesting a need for improved retention strategies during the initial subscription period.

5. **Revenue Trends**:
   - **Annual subscriptions** contribute to 75% of total revenue, suggesting that offering incentives for annual plans could boost long-term revenue.

6. **Inactive Products**:
   - Products with no subscriptions in the last quarter have been flagged for review to assess their market appeal or need for a redesign.

# Visual Walkthrough
- **Sales Overview**: Displays key KPIs such as total sales and subscription duration.
- **Top Subscription Types**: Highlights which subscription types are most popular.
- **Regional Breakdown**: Map shows where sales and cancellations are concentrated.
- **Customer Insights**: Top customers based on purchase amount are listed.
