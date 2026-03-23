# restaurant-sales-sql-analysis

## Overview 

The current project is based on Maven Analytics’ SQL tutorial and uses real-world restaurant data to analyse menu performance, order behaviour, and customer preferences. By joining order and menu data, we answer key business questions and provide actionable insights for restaurant strategy.

## Dataset Description
Two tables are used in this table:
- **`menu_items`** – Contains all food items sold, along with category and price.
- **`order_details`** – Records each item sold per order, with order ID and date.

--

## Project Objectives

- Explore the restaurant's menu and pricing;
- Understand ordering patterns and volume;
- Discover high-value orders and customer preferences;
- Reveal which dishes and categories drive revenue.

--

## Key Insights

### Menu Analysis

- **Italian** dishes dominate the menu in both count and price range.
- Average dish price varies significantly by **category**, suggesting different pricing strategies.
- **Least Expensive Item:** Edamame;
- **Most Expensive Item:** Shrimp Scampi.

--

### Order Behaviour

- **Date Range:** January 1, 2023 - 31 March, 2023
- Over **1,000+ unique orders** recorded
- Some orders include **more than 12 items**, likely group dining
- **Orders with the most items (14 each):** Order IDs `4305`, `3473`, `1957`, `330`, `440`, `443`, `2675`

--

### Sales & Revenue Patterns:

- **Highest spending order**: Order ID `440`, heavily favoured Italian dishes;
- **Top 5 big spenders** often ordered from **multiple categories**, especially **Asian** and **Italian**;
- Cross-category ordering is common — customers enjoy menu variety;
- High-value orders suggest group dining or shared meals.

--

## Tools Used:

- SQL (MySQL syntax)
- MySQL Workbench 
- Dataset provided by [Maven Analytics](https://mavenanalytics.io/data-playground)

--

## SQL File Structure:

- `01_menu_items_analysis.sql`  
  Explore item count, category breakdown, and pricing insights

- `02_order_details_analysis.sql`  
  Understand order frequency, size, and unique item counts

- `03_combined_analysis.sql`  
  Join data for revenue calculation and customer behavior insights

---

## Sample Queries

```MySQL

-- What are the top 5 orders that spent the most?
SELECT order_id, SUM(price) AS total_spent
FROM order_details od
LEFT JOIN menu_items mi ON od.item_id = mi.menu_item_id
GROUP BY order_id
ORDER BY total_spent DESC
LIMIT 5;



