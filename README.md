# Data Validation Using SQL Queries for AmazingMart Data

![](Image_Intro.jpg)

# Introduction

This project aims to analyze the sales trends of AmaingMart Superstore to improve their business growth using data-driven insights generated from the data.

Type of dataset-Sales Dataset

Problem Statement- Write SQL queries to generate insights that can be useful in  understanding the inconsistency in business growth patterns over the period of years included in the dataset.
 
Data Validation- Testing the results generated from Power BI and validating this using  SQL queries 

Data Structure- Two tables are included in the dataset named "List of Orders" and " Orders Breakdown".

- Table 1: List Of Orders
  ![]()


# Analysing Pipelines using SQL queries 

Data source- Sharepoint

Data cleaning- Data transformation was carried out in Power BI to check for incomplete data and missing values.

Import-Dataset was imported into SSMS as an Excel workbook using the Microsoft Access database 2016 Redistributable to gain access.



# Analysis 

Data Validation: Click the link for Power BI visualization [live visualization](https://app.powerbi.com/groups/me/reports/b5d02386-ee1f-4e0d-9377-2dde1ee5a59b/ReportSectioneb36539ae679103d20f1?experience=power-bi)

SQL Software- Studio Server Management System.

 
 # A. Key Performance Indicators 

 ### 1. Total Orders

SELECT COUNT (OrderID) AS TotalOrder FROM dbo.OrderBreakdown$

#### Result :

![](TotalOrders.png)

### 2. Total Cost price

SELECT SUM(Sales-Profit) AS TotalCostprice FROM OrderBreakdown$

#### Result :
![](Total_CostPrice.png)

### 3. Total Sales

SELECT SUM(Sales) AS Totalsales FROM OrderBreakdown$

#### Result :

![](Totalsales.png)

### 4. Total Profit

SELECT SUM(Profit)  AS Totalprofit FROM OrderBreakdown$

#### Result :

![](TotalProfit.png)

### 5. Company Profit Margin

Select SUM(Profit)/SUM(Sales)*100 AS profit_Margin FROM OrderBreakdown$

#### Result :

![](CompanyProfitMargin.png)

# B. Yearly Performance

 ### 6. Company Yearly Sales

SELECT YEAR(Date) AS Year,SUM(Sales) AS Totalsales FROM OrderBreakdown$
JOIN dbo.ListOfOrders$ ON dbo.ListOfOrders$.OrderID=OrderBreakdown$.OrderID
GROUP BY YEAR(Date)
ORDER BY YEAR(Date)

#### Result :

![](CompanyYearlySales.png)

 ### 7. Company Yearly Profit

SELECT YEAR(Date) AS Year,SUM(Profit) AS Totalprofit FROM OrderBreakdown$
JOIN dbo.ListOfOrders$ ON dbo.ListOfOrders$.OrderID=OrderBreakdown$.OrderID
GROUP BY YEAR(Date)
ORDER BY YEAR(Date)

### Result :

 ![](CompanyYearlyProfit.png)

 # C. Product Category

 ### 8. Total Quantity Sold

SELECT SUM(Quantity) AS TotalquantitySold FROM OrderBreakdown$


#### Result :

![](Totalquantitysold.png)

### 9. Total QuantitySold by Category

SELECT Category, SUM(Quantity) AS Totalquantity FROM OrderBreakdown$
GROUP BY Category

#### Result :

![](Quantitysoldby_Category.png)

### 10. Product Category by Year, Total Sales, and Total Profit

SELECT Category, YEAR(Date) AS Year,SUM(Sales) AS Totalsales,SUM(Profit) AS Totalprofit FROM OrderBreakdown$
JOIN dbo.ListOfOrders$ ON dbo.ListOfOrders$.OrderID=OrderBreakdown$.OrderID
GROUP BY YEAR(Date),Category
ORDER BY YEAR(Date)

#### Result :

![](CategoryYearly_sales&profit.png)

# D. Country Analysis

### 11. Country Profit  Margin

Select  Country,SUM(Profit)/SUM(Sales)*100 AS profit_Margin FROM OrderBreakdown$
JOIN dbo.ListOfOrders$ ON dbo.OrderBreakdown$.OrderID=dbo.ListOfOrders$.OrderID
GROUP BY Country
ORDER BY profit_Margin desc


#### Result :

![](CountryProfitMargin.png)

### 12. Country by Quantity Sold and Profit

SELECT  Country,SUM(Quantity) AS Totalquantitysold,SUM(Profit) AS Totalproffit FROM OrderBreakdown$
JOIN dbo.ListOfOrders$ ON dbo.OrderBreakdown$.OrderID=dbo.ListOfOrders$.OrderID
GROUP BY Country
ORDER BY Totalprofit DESC

### Result :

![](CountryQuantity_Profit.png)

### 13. Top Five Countries

SELECT TOP(5) Country AS Top_5countries, SUM(Profit) AS Total profit FROM ListOfOrders$
JOIN dbo.OrderBreakdown$ ON dbo.OrderBreakdown$.OrderID= dbo.ListOfOrders$.OrderID
GROUP BY Country
ORDER BY Totalprofit desc

### Result :
![](Top5Countries.png)

### 14. Total Sales by Country

SELECT Country,SUM(Sales) AS TotalSales FROM ListOfOrders$
JOIN dbo.OrderBreakdown$ ON dbo.OrderBreakdown$.OrderID= dbo.ListOfOrders$.OrderID
GROUP BY Country
ORDER BY TotalSales desc

### Result :
![](CountrySales.png)

# E. Company Sales Analysis and Discount

### 15. Discount by Profit

SELECT Discount AS Discount,SUM(Profit) AS TotalProfit FROM OrderBreakdown$
GROUP BY Discount
ORDER BY Discount desc

### Result :
![](DiscountTable.png)

### 16.  Total Sales Without Discount

SELECT ROUND(SUM(Sales/(1-Discount)),2) AS Totalsales_Bdiscount FROM OrderBreakdown$

### Result :
![](TotalSales-WithoutDiscount.png)

### 17. Total Profit Without Discount

SELECT ROUND(SUM(Sales/(1-Discount)),2)-SUM(Sales-Profit) AS Totalprofit_Bdiscount FROM OrderBreakdown$


### Result :
![](TotalProfit-WithoutDiscount.png)

### 18. Total Profit when the discount is less than 30%

SELECT SUM(Profit) AS Total profit FROM OrderBreakdown$
WHERE Discount between 0 and 0.3


### Result :
![](ProfitLessthan30.png)


### 19.  Total Profit when the discount is greater than 30%

SELECT SUM(Profit) AS Total profit FROM OrderBreakdown$
WHERE Discount between 0.3 and 1

### Result :
![](ProfitGreaterthan30.png)

### 20. Average number of days by Ship mode

SELECT 
    ShipMode,
    AVG(DATEDIFF(day, Date, ShipDate)) AS AvgDeliveryTime 
FROM ListOfOrders$
GROUP BY ShipMode

### Result :
![](AverageNoOfdays_for_Delivery.png)



# Thank you for reading

















    








   

