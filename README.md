# Sales-Performance-Analysis for a Retail Store

## Project Summary
This project analyzes the sales performance of a retail store using sales data to uncover key insights, including top-selling products, regional performance, and monthly sales trends. The final deliverable is an interactive Power BI dashboard.

## Project Objectives
- Explore sales data to summarize sales by product, region, and month.
- Produce insights using Excel pivot tables and SQL queries.
- Create a Power BI dashboard to visualize findings.

## Instructions

### Excel
1. Perform an initial exploration of the sales data.
       1. **Data Exploration:**
   - Use **Pivot Tables** to summarize total sales by product, region, and month.
   - Use the following **formulas** to calculate metrics:
     - **Average Sales per Product:**  
       `=AVERAGEIF(range_of_sales, product_cell, sales_range)`
     - **Total Revenue by Region:**  
       `=SUMIF(range_of_region, region_cell, sales_range)`
     - **Total Sales:**  
       `=SUM(sales_range)`
     - **Monthly Sales Trend:**  
       Use a combination of `=SUMIFS()` for cumulative calculations or create a line chart.

2. Create any other interesting reports based on your findings.
**Additional Reports:**
   - Create a report comparing sales trends over different months.
   - Generate a report listing the top 10 selling products with total sales amounts.

### SQL
1. Load the dataset into your SQL Server environment.
2. Write queries to extract insights:
   - Total sales for each product category.
   - Number of sales transactions in each region.
   - Highest-selling product by total sales value.
   - Total revenue per product.
   - Monthly sales totals for the current year.
   - Top 5 customers by total purchase amount.
   - Percentage of total sales contributed by each region.
   - Products with no sales in the last quarter.
   ```sql
   -- Total sales for each product category
   SELECT ProductCategory, SUM(SalesAmount) AS TotalSales
   FROM SalesData
   GROUP BY ProductCategory;

   -- Number of sales transactions in each region
   SELECT Region, COUNT(TransactionID) AS NumberOfSales
   FROM SalesData
   GROUP BY Region;

   -- Highest-selling product by total sales value
   SELECT ProductName, SUM(SalesAmount) AS TotalSales
   FROM SalesData
   GROUP BY ProductName
   ORDER BY TotalSales DESC
   LIMIT 1;

   -- Total revenue per product
   SELECT ProductName, SUM(SalesAmount) AS TotalRevenue
   FROM SalesData
   GROUP BY ProductName;

   -- Monthly sales totals for the current year
   SELECT MONTH(SaleDate) AS Month, SUM(SalesAmount) AS MonthlyTotal
   FROM SalesData
   WHERE YEAR(SaleDate) = YEAR(CURRENT_DATE)
   GROUP BY MONTH(SaleDate);

   -- Top 5 customers by total purchase amount
   SELECT CustomerID, SUM(SalesAmount) AS TotalPurchases
   FROM SalesData
   GROUP BY CustomerID
   ORDER BY TotalPurchases DESC
   LIMIT 5;

   -- Percentage of total sales contributed by each region
   SELECT Region, SUM(SalesAmount) / (SELECT SUM(SalesAmount) FROM SalesData) * 100 AS PercentageContribution
   FROM SalesData
   GROUP BY Region;

   -- Products with no sales in the last quarter
   SELECT ProductName
   FROM Products
   WHERE ProductID NOT IN (
       SELECT DISTINCT ProductID
       FROM SalesData
       WHERE SaleDate >= DATEADD(QUARTER, -1, CURRENT_DATE)

### Power BI
1. Create a dashboard visualizing the insights from Excel and SQL.
   - Include sales overview, top-performing products, and regional breakdowns.
- Dashboard Overview:
  - Create a Sales Overview section showing total sales, average sales, and revenue trends.
  - Use bar charts for Top-Performing Products based on sales.
  - Incorporate a Map Visualization to depict regional sales performance.
  - Include a line chart for Monthly Sales Trends to visualize changes over time.
  - Add filters (slicers) for product categories and regions for interactive analysis.

## Resources
- [Excel Guide](https://support.microsoft.com/excel)
- [SQL Server Documentation](https://docs.microsoft.com/sql/sql-server/)
- [Power BI Documentation](https://docs.microsoft.com/power-bi/)
