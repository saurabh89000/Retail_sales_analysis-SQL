#Retail Sales Analysis SQL Project

Project Overview
Project Title: Retail Sales Analysis
Level: Beginner
Database: retailer

This project is designed to demonstrate SQL skills and techniques typically used by data analysts to explore, clean, and analyze retail sales data. The project 
involves setting up a retail sales database, performing exploratory data analysis (EDA), and answering specific business questions through SQL queries. 
This project is ideal for those who are starting their journey in data analysis and want to build a solid foundation in SQL.


#Qustions--

Q.1 Write a SQL query to retrieve all columns for sales made on '2022-11-05
Q.2 Write a SQL query to retrieve all transactions where the category is 'Clothing' and the quantity sold is more than 4.
Q.3 Write a SQL query to calculate the total sales (total_sale) for each category.
Q.4 Write a SQL query to find the average age of customers who purchased items from the 'Beauty' category.
Q.5 Write a SQL query to find all transactions where the total_sale is greater than 1000.
Q.6 Write a SQL query to find the total number of transactions (transaction_id) made by each gender in each category.
Q.7 Write a SQL query to calculate the total price per unit of each category.
Q.8 Write a SQL query to find the top 5 customers based on the highest total sales 
Q.9 Write a SQL query to find the number of unique customers who purchased items from each category.
Q.10 Write a SQL query to find the total sales of males under the age of 30 in each category.

#ANSWERS--

-- Q.1 Write a SQL query to retrieve all columns for sales made on '2022-11-05
SELECT *
FROM retail_sales
WHERE sale_date = '2022-11-05';

-- Q.2 Write a SQL query to retrieve all transactions where the category is 'Clothing' and the quantity sold is more than 4 .

SELECT 
  *
FROM retail_sales
WHERE 
    category = 'Clothing'
  
    AND
    quantity >= 4;

-- Q.3 Write a SQL query to calculate the total sales (total_sale) for each category.

SELECT 
    category,
    SUM(total_sale) as net_sale,
    COUNT(*) as total_orders
FROM retail_sales
GROUP BY 1;

-- Q.4 Write a SQL query to find the average age of customers who purchased items from the 'Beauty' category.

SELECT
    ROUND(AVG(age), 2) as avg_age
FROM retail_sales
WHERE category = 'Beauty';


-- Q.5 Write a SQL query to find all transactions where the total_sale is greater than 1000.

SELECT * FROM retail_sales
WHERE total_sale > 1000;


-- Q.6 Write a SQL query to find the total number of transactions (transaction_id) made by each gender in each category.

SELECT 
    category,
    gender,
    COUNT(*) as total_trans
FROM retail_sales
GROUP 
    BY 
    category,
    gender
ORDER BY 1;


-- Q.7 Write a SQL query to calculate the total price per unit of each category.

select 
category,
sum(price_per_unit)
from retail_sales
 group by 1 ;
    

-- Q.8 Write a SQL query to find the top 5 customers based on the highest total sales 

SELECT 
    customer_id,
    SUM(total_sale) as total_sales
FROM retail_sales
GROUP BY 1
ORDER BY 2 DESC
LIMIT 5;

-- Q.9 Write a SQL query to find the number of unique customers who purchased items from each category.


SELECT 
    category,    
    COUNT(DISTINCT customer_id) as cnt_unique_cs
FROM retail_sales
GROUP BY category;



-- Q.10 Write a SQL query to find the total sales of males under the age of 30 in each category.

SELECT 
    gender, age, total_sale, category
FROM
    retail_sales
WHERE
    gender = 'Male' AND age <= '30'
ORDER BY category , age;

#Reports
:-Sales Summary: A detailed report summarizing total sales, customer demographics, and category performance.
:-Trend Analysis: Insights into sales trends across different months and shifts.
:-Customer Insights: Reports on top customers and unique customer counts per category.

#Conclusion
This project serves as a comprehensive introduction to SQL for data analysts, covering database setup, data cleaning, exploratory data analysis, and business-driven SQL queries. 
The findings from this project can help drive business decisions by understanding sales patterns, customer behavior, and product performance.


------------------------------------------*------------------------------------------------------




