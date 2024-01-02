# Myntra-Data-Analysis

This data analysis project aims to provide insights into the performance of an e-commerce company "Myntra". By analyzing various aspects of the data, we seek to identify trends, make data-driven recommendations, and gain a deeper understanding of the company's performance.

## Data Source
- Customer: Contains the key factors of customer-related data
- Orders: Contains the key factors of order-related data
- Product: Contains the key factors of product-related data

## Tools
- Excel: Data cleaning
- MySQL: Analysis
- PowerBI: Creating dashboards

## Data Analysis
EDA involved exploring the data to answer the following questions:
### 1. Order and Product Information:
- How many orders are there in the dataset?
  ```sql
  SELECT COUNT(DISTINCT `Order ID`) as Total_orders FROM orders;
  ```
- What is the total revenue for each order?
  ```sql
  SELECT SUM(`Original Price`) as Total_revenue FROM orders
  ```
- What is the average order value?
  ```sql
  SELECT ROUND(AVG(`Original Price`),2) as Avg_order_value FROM orders
  ```
- How many products are there in each category and sub-category?
```sql
  SELECT `Category`,COUNT(`Sub-category`) as List_of_products FROM product
  GROUP BY `Category`
```
- What are the top-rated products overall?
```sql
  SELECT * FROM product
  WHERE `Ratings` = 5
```
- What are the top-rated products in each category?
```sql
SELECT `Sub-category` FROM product
WHERE Ratings = 5
GROUP BY `Sub-category`
```
### 2.Combined Analysis
- Who are the top 10 spending customers?
  ```sql
  select `c`.`Customer ID`,SUM(`o`.`Original Price`) as Total_spending from customer as c
  INNER JOIN orders as o
  ON `c`.`Customer ID` = `o`.`Customer ID`
  GROUP BY `c`.`Customer ID`
  ORDER BY SUM(`o`.`Original Price`) DESC
  LIMIT 10
  ```
- Top 10 Customer with highest order placed
  ```sql
  select `c`.`Customer ID`,COUNT(`o`.`Order ID`) as Total_spending from customer as c
  INNER JOIN orders as o
  ON `c`.`Customer ID` = `o`.`Customer ID`
  GROUP BY `c`.`Customer ID`
  ORDER BY COUNT(`o`.`Order ID`) DESC
  LIMIT 10
  ```
  
