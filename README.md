# lita_sales
## project Title: Sales data Analysis

[project overview](#project-overview)

[data sources](#data-sources)

[Tools Used](#Tool-Used)

[Data Cleaning and preparation](#Data-Cleaning-and-preparation)

[Exploratory Data Analysis](Exploratory-Data-Analysis)

[data analysis](data-analysis)

[Data Summary](Data-Summary)


### project overview
The objective of this project is to analyze sales data to:
gain insights into customer purchasing behavior
identify trends over time
evaluate the performance of various products, regions, and customer segments. 
Through detailed analysis, we aim to uncover actionable insights that can inform strategic decisions for revenue growth, inventory management, and targeted marketing.

### data sources
The primary source of this data is Salesdata.xslx. the data can also be downloaded from open sources online and online data repositories such as kaggle.

### Tools Used
1. Microsoft Excel for :
- data cleaning
- data analysis
2. SQL - Structured Query Language for data query

3. PowerBi for data visualization

4. Github for Portfolio

### Data Cleaning and preparation
- data handling and inspection
- addressing any missing, inconsistent, or erroneous values.
- dealing with duplicate values
- deleting empty rows and mising values
- Data cleaning and formatting

  ### Exploratory Data Analysis
  This involves exploring the Data to answer some questions about it such as
  - What is the total sales  for each region?
  - What is the total sales per product?
  - What is the average unit price across products? Is there a significant variance in unit prices?
  - What is the trend in  total sales  monthly
  - How does the  quantity  vary by region?
  - What is the average quantity sold per product?
 
### data analysis
In Excel for initial data cleaning and pivot tables

![image](https://github.com/user-attachments/assets/ab3c8afa-5a2f-4fc4-b60d-f991fe592fbf)

![image](https://github.com/user-attachments/assets/2a7c276d-820a-43e1-98a7-977de343a0ee)
 
![image](https://github.com/user-attachments/assets/f60fe867-ede1-426b-aaa3-cd7c6543cfd6)

![image](https://github.com/user-attachments/assets/68cc6645-4082-4018-9fbf-cc734033afcd)

SQL for data summarization and to aggregate and analyze data.
``` SQL
Select * from [dbo].[lita project]

alter table [dbo].[lita project]
add Total_sales int 
update [dbo].[lita project]
set Total_sales = quantity*UnitPrice

SELECT DISTINCT *
INTO salesData
FROM [dbo].[lita project]
WHERE orderID IS NOT NULL 
  AND customer_id IS NOT NULL 
  AND product IS NOT NULL
  and region is not null
  and orderdate is not null
  and quantity is not null
  and unitprice is not null
  and total_sales is not null;


CREATE VIEW VW_TOP5CUSTOMERS AS
SELECT TOP 5 CUSTOMER_ID, TOTAL_SALES FROM [dbo].[salesData]
ORDER BY Total_sales DESC;

CREATE VIEW VW_RegionalPercentage as 
select region,total_sales, (total_sales*100 /sum(total_sales) over()) as percentage
from [dbo].[salesData]

CREATE VIEW vw_TotalRevenuePerProduct AS
SELECT 
   Product, 
   SUM(Quantity * UnitPrice) AS TotalRevenue from [dbo].[salesData]
   group by Product
CREATE VIEW vw_MonthlySalesCurrentYear AS
SELECT 
    YEAR(orderDate) AS Year, 
    MONTH(orderDate) AS Month, 
    SUM(Quantity * UnitPrice) AS MonthlySales
FROM [dbo].[salesData]
WHERE 
    YEAR(OrderDate) = YEAR(GETDATE())  
GROUP BY 
    YEAR(OrderDate), 
    MONTH(OrderDate)


```

 Power BI dashboard to visualize key insights.

 ![Sales Dashboard](https://github.com/user-attachments/assets/cb116a68-4550-424c-ae6f-5a37a70a3853)

### Data Summary
 
