# 🚀 Zepto Sales Analytics Dashboard

🔗 **Interactive Dashboard:** [View Live Report](https://app.powerbi.com/view?r=eyJrIjoiOWQ2MjIwMTEtN2FmYi00OGM0LThkYTYtNjZmNDY0NGJmN2RjIiwidCI6IjZiNGQwNDQ4LTc5MGMtNGQ5MS1iZjY3LTg5ZDk1NmJlNDEwYSJ9&pageName=6ac9fb54130462a9ddae)

---

## 📌 Problem Statement
This dashboard provides a comprehensive analysis of **Zepto’s 10-minute grocery delivery performance**. By evaluating sales, inventory, and discount strategies, it empowers stakeholders to:
* Identify high-growth categories like **Packaged Food** and **Chocolates**.
* Understand the correlation between **MRP and Discounted Selling Price**.
* Monitor monthly trends to optimize inventory for peak demand periods.
* Pinpoint underperforming categories (e.g., **Fruits & Vegetables**) to improve supply chain or pricing strategies.

---

## 📊 Key Metrics (KPIs)
Based on the dashboard analysis, the following high-level indicators are tracked:
* **Total Sales:** 122.27M
* **Total Orders:** 3,731
* **Total Quantity Sold:** 796K
* **Average Sales Per Order:** 32.77K
* **Total Available Quantity:** 15K

---

## 🎯 Business Requirements
* **Top & Bottom 5 Analysis:** Identify leading and lagging categories by Sales, Quantity Sold, Available Stock, and Discount Value.
* **Monthly Trend Tracking:** Visualize fluctuations in Quantity Sold and Average Discount % throughout the year 2025.
* **Category Contribution:** Analyze the % contribution of top categories to total sales.
* **Pricing Strategy:** Compare MRP vs. Discounted Selling Price to evaluate promotional impact.

---

## 🔧 Workflow & Technical Steps

### 1️⃣ Data Cleaning & Integrity (SQL Server)
I used **SSMS** to perform deep data cleaning and validation:
* **Database Setup:** Created the `zepto` database and audited the schema using `INFORMATION_SCHEMA.columns`.
* **Handling Nulls & Blanks:** Ran validation queries to identify missing values in `Category`, `Name`, and `MRP`.
* **Data Sanitization:** * Removed specific inconsistent records (e.g., *Cherry Blossom Liquid Shoe Polish* entries).
    * Investigated and resolved zero-value anomalies in `discountedSellingPrice`.
* **Value Correction:** Identified records with `0g` weight and updated them to a baseline of `5g` to maintain distribution accuracy.

### 2️⃣ Advanced ETL (Power Query Editor)
After initial SQL cleaning, the data was shaped in Power BI:
* **Schema Refinement:** Performed **Data Type Conversion** (Currency, Whole Numbers, Dates) to ensure calculation integrity.
* **Feature Engineering:** Added an **Index Column** to ensure each row has a unique identifier for granular modeling.
* **Data Enrichment (The Merge):** * Created a custom **Order Date** sheet in Excel using `RANDBETWEEN` to simulate transactional dates for 2025.
    * Performed a **Left Outer Join** between the Zepto dataset and the Date sheet using `Index` and `ID` to enable time-series analysis.

### 2️⃣ Advanced DAX Measures
Created dynamic measures to drive the interactive visuals:
* `Total Sales`, `Total Orders`, and `Avg Sales Per Order`.
* `Average Discount %` by Category and Month.
* `Top/Bottom 5` ranking logic for dynamic category analysis.
* `MRP vs. Discounted Selling Price` comparison logic.

---

## 📊 Dashboard Preview & Insights

### 📄 Page 1: Sales & Discount Overview
![Sales & Discount Overview](https://github.com/ShouryaSrivastav/Zepto-Project/blob/5ccb8a43d76a5287238f59a3e1d983164fc99f61/Page%201%20-%20Overview%20.png?raw=true)

* **Visuals:** KPI cards, Category-wise Average Discount, and MRP vs. Discounted Price.
* **Key Insight:** **Fruits & Vegetables** receive the highest average discount (15.5%), despite being a bottom-performing category by sales.

### 📄 Page 2: Top/Bottom 5 Analysis
![Top Bottom Analysis](https://github.com/ShouryaSrivastav/Zepto-Project/blob/5ccb8a43d76a5287238f59a3e1d983164fc99f61/Page%202%20-%20Top%20Bottom%20Analysis.png?raw=true)

* **Visuals:** Six bar chart analysis.
* **Key Insight:** **Cooking Essentials** and **Munchies** are top performers in both quantity sold and available stock, suggesting high demand and efficient restocking.

### 📄 Page 3: Business Insights & Monthly Trends
![Monthly Trends](https://github.com/ShouryaSrivastav/Zepto-Project/blob/5ccb8a43d76a5287238f59a3e1d983164fc99f61/Page%203%20-%20Business%20Insights%20%26%20Trends.png?raw=true)

* **Visuals:** Monthly Sales/Quantity bar charts and Category Sales Contribution donut chart.
* **Key Insight:** **Packaged Food**, **Ice Cream**, and **Chocolates** each contribute 21.9% to total sales, dominating the revenue share.

---

## 🛠️ Tools & Technologies
* **SQL Server (SSMS):** Backend data cleaning and data integrity validation.
* **Power BI Desktop:** Dashboard design, Power Query (Merging/Indexing), and DAX.
* **Microsoft Excel:** Data sourcing and date generation via formulas.

---

## ✅ Conclusion
The **Zepto Sales Analytics Dashboard** demonstrates a complete end-to-end data analytics workflow. It successfully transforms raw, messy data into actionable insights, highlighting the "high-discount vs. low-sales" paradox in certain categories and providing a clear roadmap for inventory and promotional optimization.
