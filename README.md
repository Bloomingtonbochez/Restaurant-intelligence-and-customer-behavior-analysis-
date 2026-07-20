# Restaurant intelligence and customer behavior analysis

This project analyzes restaurant sales data using SQL to uncover insights into customer behavior, menu performance, revenue trends, and peak business hours. The findings were used to build a Power BI dashboard that helps support smarter, data-driven business decisions.

# Executive Summary
Business Problem

A restaurant chain has accumulated thousands of customer orders but lacks visibility into:

Which menu items generate the most revenue

Customer purchasing behavior

Peak business hours

Menu performance

Product bundling opportunities

Revenue opportunities

Category performance

Management wants to transform raw transactional data into actionable business insights that improve sales, staffing, and menu strategy.

# Project Objectives
## Objective 1

Explore the Restaurant Menu

Answer questions such as:

How many menu items are available?

Which items are the most and least expensive?

Which cuisines dominate the menu?

Which categories have the highest average prices?

## Objective 2

Analyze Restaurant Orders

Understand operational performance by answering:

Total orders

Total items sold

Date range

Large customer orders

Distribution of order sizes

## Objective 3

Analyze Customer Purchasing Behavior

Discover:

Most popular menu items

Least popular menu items

Highest spending orders

Customer ordering patterns

Revenue generated per order

## Objective 4

Revenue Intelligence

Identify

Highest revenue menu items

Revenue by category

Average revenue per order

Revenue concentration

## Objective 5

Time-Based Analysis

Discover

Peak ordering hours

Revenue by hour

Customer traffic by hour

Lunch vs Dinner performance

## Objective 6

Market Basket Analysis

Discover

Which products are purchased together?

Best combo meal opportunities

Cross-selling recommendations


 OBJECTIVE 1:EXPLORE THE ITEM TABLE
 
/* 1.View the menu_table and write a query to find the number of items on the menu 
	2. What are the least and most expensive items on the menu
	3.how many italian dishes are on the menu? what are the least and most expem=nsive italian dishes on the menu
	4.how many dishes are in each category what is the average dish price within each category? */
	SELECT *
	FROM menu_items
	--View the menu_table and write a query to find the number of items on the menu 
  ```

	SELECT COUNT(*) AS Number_of_items
	FROM menu_items

```

What are the least and most expensive items on the menu
  
```
  
	SELECT *
	FROM menu_items
	ORDER BY price DESC

```
how many italian dishes are on the menu? what are the least and most expem=nsive italian dishes on the menu
  
```
	SELECT COUNT(*) number_of_items_on_italian_menu
	FROM menu_items
	WHERE category = 'italian'
```
```
	SELECT *
	FROM menu_items
	WHERE category = 'italian'
	ORDER BY price DESC
  
```
how many dishes are in each category what is the average dish price within each category?

```
	SELECT category,
	COUNT(*) number_of_dishes,
	AVG(price) Average_dish_price
	FROM menu_items
	GROUP BY category

```

OBJECTIVE 2 EXPLORE THE ORDERS TABLE 
/* 1. View the order_details table.what is the date range of the table ?
   2. How many orders were made within this date range? How many items were ordered within this date range 
   3. which orders had the most numbers of items 
   4.how many orders had more than 12 items?*/

```
1. View the order_details table.what is the date range of the table ?

```
SELECT*
	FROM order_details

SELECT MIN(order_date) start_date,
	 MAX(order_date) end_date
	FROM order_details
  
  ```

2. How many orders were made within this date range? How many items were ordered within this date range
	 
```
	 SELECT COUNT(DISTINCT order_id) Number_of_orders
	 FROM order_details

	 SELECT COUNT(*) number_of_item
	 FROM order_details

```

3. which orders had the most numbers of items

  ```
	SELECT
	order_id,
	COUNT(item_id) number_of_item
	FROM order_details
	GROUP BY order_id
	ORDER BY number_of_item DESC

```
	
4.how many orders had more than 12 items?

```
SELECT
order_id,
COUNT(item_id) number_of_item
FROM order_details
GROUP BY order_id
HAVING COUNT(item_id) > 12

```

