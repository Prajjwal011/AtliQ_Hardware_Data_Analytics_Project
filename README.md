# AtliQ_Hardware_Data_Analytics_Project 📈
![Power Bi](https://img.shields.io/badge/power_bi-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)

# Introduction
This project aims to address the data management challenges faced by AtliQ Hardware through the implementation of a comprehensive data analytics solution

# Problem Statement
The AtliQ Hardware Sales Insights Project endeavors to transform the way the company navigates its sales landscape. 

Faced with challenges in tracking sales amid dynamic market growth and verbal updates from regional managers lacking concrete evidence, the Sales Director seeks a data-driven solution. 

Our project objective is to provide AtliQ Hardware with a Power BI dashboard, offering real-time insights and addressing the decline in overall sales. Key features include dynamic market tracking, regional performance metrics, and daily accessible data. The benefits encompass data-driven decision-making, increased sales through strategic planning, and more efficient communication.

The project invites contributions for dashboard development, insights sharing, and collaborative feedback, aiming to empower the Sales Director and the organization with actionable insights for sustainable growth. Your valuable contributions are crucial to the success of this initiative! 🚀

# Steps of Data Analysis 

1) Requirement Gathering

2) Data Collection

3) Data Preparation

4) Data Modeling

5) Dashboard Building

6) Deployment

# Project Planning with AIMS Grid
## AIMS Grid (Project Management Tool)
Four components of AIMS grid:
Purpose (Identifying pain points and defining project objectives)
Stakeholders (Involvement of marketing, sales, IT, and data analytics teams)
End Result (Creating a dynamic Power BI dashboard for real-time sales insights) 
Success Criteria (Cost reduction by 10%, streamlined Excel-based operations, and a 5% increase in sales personnel)

# Sales Insight Using SQL 

![MySQL Workbench 06-03-2024 21_09_45](https://github.com/Prajjwal011/AtliQ_Hardware_Data_Analytics_Project/assets/140709421/423a9e7c-8389-4430-bc50-6e268b604a2d)
![MySQL Workbench 07-03-2024 13_29_45](https://github.com/Prajjwal011/AtliQ_Hardware_Data_Analytics_Project/assets/140709421/7ffbeaab-00e2-4a2b-a6bb-c944481f7611)
![MySQL Workbench 07-03-2024 13_30_47](https://github.com/Prajjwal011/AtliQ_Hardware_Data_Analytics_Project/assets/140709421/8f2810b9-56e8-49fa-a4d7-858ed292c6ed)
![MySQL Workbench 07-03-2024 13_34_52](https://github.com/Prajjwal011/AtliQ_Hardware_Data_Analytics_Project/assets/140709421/7c94f155-d16f-44db-b3f0-1a4fe8578288)

## SQL Queries Used for Sales Insights

1.To find transactions in 2020 

SELECT sales.transactions.*, sales.date.* FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020;

2.To find transactions in 2019 

SELECT sales.transactions.*, sales.date.* FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2019;

3.To find total revenue in year 2020

SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r";

4.To find total revenue in year 2019

SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2019 and sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r";

5.To find total revenue in Jan 2020  

SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.date.month_name="January" and (sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r");

6.To find total revenue in Feb 2020 

SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.date.month_name="February" and (sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r");

7.To find total revenue in Jan 2019

SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.date.month_name="January" and (sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r");

8.To find total revenue in year 2020 in Chennai

SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.transactions.market_code="Mark001";

9.To find total revenue in year 2020 in Mumbai

SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.transactions.market_code="Mark002";

# Data Cleaning and Transformation Using Power BI

## Step 1: Connect MY SQL database with Power BI and load the data into Power BI

## Step 2: The focus now is on data cleaning and transformation, commonly known as ETL (Extract, Transform, Load)

### Navigate to the Power Query Editor by clicking on "Transform Data."

a) Filtering Unnecessary Data: Identify tables that may contain irrelevant data. For instance, filter out irrelevant zones like New York and Paris.

b) Handling Negative or Zero Sales Amounts : Identify and filter out rows with negative or zero sales amounts in the Sales Transaction table

c) Currency Conversion : Add a new column called "Normalized Sales Amount" to convert all sales amounts into Indian Rupees (INR).

# Data Modeling

Now, Establishing relationships between tables using Power BI's Data Model. This ensures a structured and interconnected dataset.
Understand the concept of a "star schema" in data modeling, where fact tables (transactions) are linked to dimension tables (e.g., customers, products).

![data analysis 07-03-2024 15_24_45](https://github.com/Prajjwal011/AtliQ_Hardware_Data_Analytics_Project/assets/140709421/0967c379-407b-4a92-9914-04d3120ef1aa)

# Data Analysis and Visualization

Key Measures used are:

      Profit Margin % = DIVIDE([Total Profit Margin],[Revenue],0)
      
      Profit Margin Contribution % = DIVIDE([Total Profit Margin],CALCULATE([Total Profit Margin],ALL('sales products'),ALL('sales 
      customers'),ALL('sales markets')))
      
      Revenue = SUM('sales transactions'[sales_amount])
      
      Revenue Contribution % = DIVIDE([Revenue],CALCULATE([Revenue],ALL('sales products'),ALL('sales customers'),ALL('sales markets')))
      
      Revenue LY = CALCULATE([Revenue],SAMEPERIODLASTYEAR('sales date'[date]))
      
      sales quntity = SUM('sales transactions'[sales_qty])
      
      Total Profit Margin = SUM('Sales transactions'[Profit_Margin])

Profit Target:

    Profit Target1 = GENERATESERIES(-0.05, 0.15, 0.01)
    
    Profit Target Value = SELECTEDVALUE('Profit Target1'[Profit Target])
    
    Target Diff = [Profit Margin %]-'Profit Target1'[Profit Target Value]
    Build Dashboard Or a Report:

## Dashboard Containing all the Visualizations

![data analysis 05-03-2024 13_32_22](https://github.com/Prajjwal011/AtliQ_Hardware_Data_Analytics_Project/assets/140709421/170e5ebf-9e9c-4c5f-bb4f-ec1954ac4969)
![data analysis 05-03-2024 13_32_31](https://github.com/Prajjwal011/AtliQ_Hardware_Data_Analytics_Project/assets/140709421/5a91554d-206c-4bfc-96d0-23b31829052a)
![data analysis 05-03-2024 13_32_40](https://github.com/Prajjwal011/AtliQ_Hardware_Data_Analytics_Project/assets/140709421/a256aa1b-afe8-4274-8625-bf1365a81873)

# Tools and Software Used: 
MySQL

Power Bi

Power Query Editor

DAX language



