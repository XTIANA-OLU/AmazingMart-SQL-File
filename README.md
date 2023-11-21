# Data Validation Using SQL Queries for AmazingMart Data

![](Image_Intro.jpg)

# Introduction

This project aims to analyze the sales trends of AmaingMart Superstore to improve their business growth using data-driven insights generated from the data.

Type of dataset-Sales Dataset

Problem Statement- Write SQL queries to generate insights that can be useful in  understanding the inconsistency in business growth patterns over the period of years included in the dataset.
 
Data Validation- Testing the results generated from Power BI and validating this using  SQL queries 

Data Structure- Two tables are included in the dataset named "List of Orders" and " Orders Breakdown".

- Table 1 : List Of Orders ![](List of Orders(Table).png)


# Analysing Pipelines using SQL queries 

Data source- Sharepoint

Data cleaning- Data transformation was carried out in Power BI to check for incomplete data and missing values.

Import-Dataset was imported into SSMS as an Excel workbook using the Microsoft Access database 2016 Redistributable to gain access.



# Analysis 

Data Validation: Click the link for Power BI visualization [live visualization](https://app.powerbi.com/groups/me/reports/b5d02386-ee1f-4e0d-9377-2dde1ee5a59b/ReportSectioneb36539ae679103d20f1?experience=power-bi)

SQL Software- Studio Server Management System.

A. ### Key Performance Indicators 

1. Total Orders

SELECT COUNT (OrderID) AS TotalOrder FROM dbo.OrderBreakdown$

#### Result

![](
