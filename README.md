# LITA-CLASS-PROJECT
---
Location of projects done during LITA class.

[Project overview](#project-overview)

[Data Source](#data-source)

[Tools Used](#tools-used)

[Exploratory Data Analysis](#exploratory-data-analysis)

[Data Analysis](#data-analysis)

[Data Visualiziation](#data-visualization)

## Project overview
---
This project analyzes customer subscription data to uncover behavioral patterns, track subscription types, and identify trends in cancellations and renewals. The objective is to support business decision-making by visualizing these insights in a Power BI dashboard.

## Data Source
---
For this project, the dataset is a mock customer subscription dataset, representing a typical subscription service with details about customer subscriptions, regions, subscription types, start dates, end dates, and revenu

## Data Cleaning and Exploration
## In Excel:

1. Remove Duplicates: Ensured no duplicate sales records exist.

2. Handle Missing Values: Removed rows with critical missing information in fields like ProductID, Region, or SalesAmount.
3.Formatting Adjustments: Formatted Date columns as dates and SalesAmount as currency for accurate calculations.
Using pivot tables, we calculated:

4. Total Sales by Product: Identified the best-selling products.
5. Total Revenue by Region: Evaluated regional performance.
6. Monthly Sales Trends: Analyzed sales patterns over time.

## SQL Queries and Key Insights
Loaded the dataset into SQL Server to run the following queries:

Example Queries

Total Sales for Each Product Category:

sql
Copy code
SELECT ProductCategory, SUM(SalesAmount) AS TotalSales
FROM Sales
GROUP BY ProductCategory;

Monthly Sales Totals for Current Year:
sql

Copy code
SELECT MONTH(SaleDate) AS Month, SUM(SalesAmount) AS MonthlySales
FROM Sales
WHERE YEAR(SaleDate) = YEAR(GETDATE())
GROUP BY MONTH(SaleDate)
ORDER BY Month;
Key Insights
Top-Selling Products: Product A, B, and C are the highest-selling products.
Regional Sales Contribution: Region X, Y, and Z contribute significantly to total sales.
Seasonal Trends: Sales peak in specific months, indicating seasonal trends.
(See Insights.md for more details.)

## Power BI Dashboard
The Power BI dashboard includes the following visuals:
1 Sales Overview: KPI cards displaying Total Sales, Total Transactions, and Average Sales per Product.

2 Top Products: A bar chart showcasing top-selling products by sales value.

4 Monthly Sales Trends: A line chart tracking sales month by month.
Using the Dashboard

5 Filtering: Use slicers for Region, Month, and Product Category.

6 Cross-Filtering: Click on visuals (e.g., regions on the map) to dynamically filter related visuals.

7 Using Insights: Identify high-performing regions, seasonal peaks, and product demand.

Screenshots
See the /Documentation/Dashboard_Screenshots folder for annotated screenshots of each dashboard element.
