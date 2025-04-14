
# 📊 Inventory and Sales  analysis

This project involves analyzing inventory and sales data from a retail supply chain system, with the aim of identifying operational inefficiencies, sales performance trends, supplier reliability, and potential revenue opportunities. The dataset contains critical information on product categories, stock levels, supplier details, expiration dates, and sales performance metrics

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

- Multiple high-demand products such as Sushi Rice, Arabica Coffee, and Egg (Goose) are below their reorder levels, indicating an urgent need for restocking to avoid lost sales.
- Products like Whole Wheat Flour, Swiss Cheese, and Orange have low inventory turnover rates, suggesting either overstocking or low demand. These products are tying up warehouse space and capital.
- Items such as Grapes, Anchovies, and Cauliflower have not been reordered in a long time, possibly pointing to lapses in restocking or declining demand.
-  Bread Flour, Pomegranate, and Cauliflower are among the best-selling products. Notably, Arabica Coffee stands out both in sales volume and revenue generation.
-  There is a strong correlation between pricing tier and sales volume—low-priced products significantly outperform premium-tier items in volume sold, showing price sensitivity among customers.
-  The Fruits & Vegetables category has the highest number of expired products (332 items).
-  Arabica Coffee is the top revenue-generating product.
-  The Fruits & Vegetables category generates the highest revenue overall.
-  Suppliers such as Zoozzy, Twinte, Skyvu, and Tekfly are associated with low turnover items and may require performance evaluation.
---

## 🧾 Recommedation
- Reduce order quantities or consider discontinuing low-turnover products to free up resources.
- Set up automated triggers to reorder products once they approach the reorder level to avoid stockouts of high-demand products.
- Consider promotions or discounts for premium-tier products that are underperforming to increase demand.
- Re-evaluate supplier contracts and performance metrics for those consistently linked with underperforming or expiring stock.

---

## ⚙️ Technologies Used
- SQL
- Excel / Power BI

---
