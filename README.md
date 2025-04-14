
# 📊 Grocery inventory analysis

The objective of this analysis was to gain actionable insights into stock management, supplier performance, and sales trends using real-time product data. The analysis was conducted across key dimensions such as product performance (sales and turnover), supplier effectiveness, inventory efficiency, and stock expiry.

---

## 📌 Table of Contents

- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Business/Research Questions](#businessresearch-questions)
- [Methodology](#methodology)
- [Analysis and Visualizations](#analysis-and-visualizations)
- [Findings](#findings)
- [Recommendation](#recommendation)
---

## 🧠 Project Overview

This project focuses on inventory and sales data analysis to help optimize supply chain decisions, reduce waste, and improve overall product performance. The dataset contains information about products, their suppliers, stock levels, reorder status, sales volume, inventory turnover, and expiry date.
By analyzing this dataset, we aim to identify high-performing products, underperforming inventory, supplier efficiency, and financial losses due to product expiration.

---

## 📂 Dataset

- **Source:** <a href ='https://github.com/ikechidiogo19/Grocery_inventory_analysis/blob/main/Grocery_Inventory_and_Sales_Dataset.csv'> Dataset </a>
- **Format:** CSV.
---

## ❓ Business/Research Questions
- Which products are below their reorder level and need to be restocked immediately?
- Which products have the lowest inventory turnover rates?
- Are there products that haven’t been reordered in a long time?
- Which products are the top 5 best sellers by sales volume?
- Is there a relationship between unit price and sales volume?
- Which suppliers provide the best-selling products?
- Which supplier are responsible for low turnover product?
- Which category has the most expired products?
- Which products or category bring in the most revenue?

---

## 🛠 Methodology

Outline your process:
- **Data Cleaning** (Handled missing values, checked for duplicates, standardized the data types)
- **Exploratory Data Analysis** (EDA)
- created a new column 'Expired' and compared the expiration date with the last order date
- categorized the unit price into 'low price tier' 'mid-price tier' 'High price teir' and 'premeuim price tier' in order to find the relationship the sales volume

---

## 📈 Analysis and Visualizations
``` sql
-- Which category has the most expired products?
SELECT catagory,COUNT(expired) AS expired
FROM Grocery
Group BY catagory
ORDER BY expired desc;
```
``` sql
-- Which products are the top 5 best sellers by sales volume?
SELECT product_name, SUM(sales_volume) AS sum_of_sales_volume
FROM Grocery
GROUP BY product_name
ORDER BY sum_of_sales_volume desc
LIMIT 5;
```
``` sql
-- Which products are below their reorder level and need to be restocked immediately?
SELECT product_name
FROM Grocery
WHERE stock_quantity < reorder_level;
```
``` sql
-- Which products have the lowest inventory turnover rates ?
SELECT product_name, MIN(inventory_turnover_rate) AS lowest_inventory_Turnover
FROM Grocery
GROUP BY product_name
ORDER BY lowest_inventory_Turnover ;
```
``` sql
-- What is the total value of stock currently in the warehouse?
SELECT ROUND(SUM(stock_quantity) * SUM(unit_price)) AS total_value
FROM Grocery;
```

---

## 📌 Findings

- low price tier sold the most while Premium price tier sold the least 
- Katz was the supplier that provided the best selling product
- Zoozzy, Twinte, Skyvu, Tekfly  are responsible for low turnover products
- Fruits & Vegetables  category has the most expired products
- Arabica coffee brings in the most revenue   while Fruits & Vegetables category brings in the most revenue 
---

## 🧾 Recommedation
- Restock Critical Items Immediately to avoid stockouts, especially fast-selling products like Arabica Coffee.
- Focus on Low-Price Tier Strategy since they perform best in sales volume.
- Review and Adjust Reorder Quantities for slow-moving or expired items to prevent overstocking and waste.
- Improve Expiration Management and prioritizing the sales of near-expiry products, especially in the Fruits & Vegetables category.

---

## ⚙️ Technologies Used
- SQL
- Excel / Power BI

---
