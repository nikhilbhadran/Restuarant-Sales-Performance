# Restuarant-Sales-Performance-Dashboard

I am sharing a pizza restaurant Sales Performance Analysis - performed on Power BI & SQL.

# About Project 👨‍💻

Developed ETL mappings using SQL to extract the data from unstructured data and transformed it to the staging area to conduct data cleaning on Power BI.

Developed a Power BI dashboard to perform analysis, producing quantitative visualizations to draw valuable insights based on different parameters affecting the restaurant's performance year on year and further provide business solutions.

# Technologies used ⚙️

Advanced Excel

MS SQL SERVER: 19.0
SQL SERVER MANAGEMENT

Power BI 

# Certifications 📜 🎓 ✔️

[Google Data Analytics Professional Certificate](https://www.credly.com/badges/af046fef-b65a-46a3-9627-5e32b2fe9ced)- by Coursera

[Programming for Everybody](https://www.coursera.org/account/accomplishments/certificate/UQ9WNPYF9MR2) by University of Michigan

# KPI's Requirement
We need to analyze key indicators for our pizza sales data to gain insights into our business performance. Specifically, we want to calculate the following metrics:
1. Total Revenue: **The sum of the total price of all pizza orders.
2. Average Order Value: **The average amount spent per order, calculated by dividing the total revenue by the total number of orders.
3. Total Pizzas Sold: **The sum of the quantities of all pizzas sold.
4. Total Orders: **The total number of orders placed.
5. Average Pizzas Per Order: **The average number of pizzas sold per order, calculated by dividing the total number of pizzas sold by the total number of orders.

# Charts Requirement
We would like to visualize various aspects of our pizza sales data to gain insights and understand key trends. We have identified the following requirements for creating charts:

**1.Daily Trend for Total Orders:**
Create a bar chart that displays the daily trend of total orders over a specific time period. This chart will help us identify any patterns or fluctuations in order volumes on a daily basis.

**2.Monthly Trend for Total Orders:**
Create a line chart that illustrates the hourly trend of total orders throughout the day. This chart will allow us to identify peak hours or periods of high order activity.

**3. Percentage of Sales by Pizza Category:**
Create a pie chart that shows the distribution of sales across different pizza categories. This chart will provide insights into the popularity of various pizza categories and their contribution to overall sales.

# Data Analysis Approach
<p  align="center"><a href="https://github.com/nikhilbhadran"><img width="80%" src="Data Approach.png" /></a></p>

# Setup Process

Step 1: Download file: pizza_sales.xlsx

Step 2: Import it in MySql do ETL(Extract, Transform, Load) if required

Step 3: Download Power BI to perform Data Analysis

Step 4: Connect Power BI with MySql database or Excel database

# Data Analysis Using SQL
PIZZA SALES SQL QUERIES
KPI’s

1. Total Revenue:
`SELECT SUM(total_price) AS Total_Revenue FROM pizza_sales;`

2. Average Order Value
`SELECT (SUM(total_price) / COUNT(DISTINCT order_id)) AS Avg_order_Value FROM pizza_sales`

3. Total Pizzas Sold
`SELECT SUM(quantity) AS Total_pizza_sold FROM pizza_sales`
 
4. Total Orders
`SELECT COUNT(DISTINCT order_id) AS Total_Orders FROM pizza_sales`
 
5. Average Pizzas Per Order
`SELECT CAST(CAST(SUM(quantity) AS DECIMAL(10,2)) / 
CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2)) AS DECIMAL(10,2))
AS Avg_Pizzas_per_order
FROM pizza_sales`
 
6. Daily Trend for Total Orders
`SELECT DATENAME(DW, order_date) AS order_day, COUNT(DISTINCT order_id) AS total_orders 
FROM pizza_sales
GROUP BY DATENAME(DW, order_date)`
 
7. Monthly Trend for Orders
`SELECT DATENAME(MONTH, order_date) as Month_Name, COUNT(DISTINCT order_id) as Total_Orders
from pizza_sales
GROUP BY DATENAME(MONTH, order_date)Output`

8. % of Sales by Pizza Category
`SELECT pizza_category, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_category`

9. of Sales by Pizza Size
`SELECT pizza_size, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_size
ORDER BY pizza_size`

10. Total Pizzas Sold by Pizza Category
`SELECT pizza_category, SUM(quantity) as Total_Quantity_Sold
FROM pizza_sales
WHERE MONTH(order_date) = 2
GROUP BY pizza_category
ORDER BY Total_Quantity_Sold DESC`

11. Top 5 Pizzas by Revenue
`SELECT Top 5 pizza_name, SUM(total_price) AS Total_Revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Revenue DESC`
 
12. Bottom 5 Pizzas by Revenue
`SELECT Top 5 pizza_name, SUM(total_price) AS Total_Revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Revenue ASC`
 
13. Top 5 Pizzas by Quantity
`SELECT Top 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizza_Sold DESC`
 
14. Bottom 5 Pizzas by Quantity
`SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizza_Sold ASC`

15. Top 5 Pizzas by Total Orders
`SELECT Top 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Orders DESC`
 
16. Borrom 5 Pizzas by Total Orders
`SELECT Top 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Orders ASC`

17. To apply the pizza_category or pizza_size filters to the above queries we can use WHERE clause. Examples :-
`SELECT Top 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
WHERE pizza_category = 'Classic'
GROUP BY pizza_name
ORDER BY Total_Orders ASC`

# Power BI Dashboard
<p  align="center"><a href="https://github.com/nikhilbhadran"><img width="80%" src="Pizza dash.png" /></a></p>

# Best/Worst Dashboard
<p  align="center"><a href="https://github.com/nikhilbhadran"><img width="80%" src="https://github.com/nikhilbhadran/Restuarant-Sales-Performance-Dashboard/blob/main/Best%3Aworst.png" /></a></p>

