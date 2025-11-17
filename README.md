# Olist-E-Commerce-Power-BI-Dashboard
*A complete end-to-end Business Intelligence project built using Power BI.*
---

##  **Project Overview**

This project analyzes the **Olist E-Commerce Dataset**, a real Brazilian marketplace platform connecting small sellers to customers nationwide.
The goal is to build an **interactive Power BI dashboard** that helps business managers monitor:

* Sales performance
* Seller performance
* Product category trends
* Customer satisfaction
* Payment behaviors
* Delivery efficiency

This dashboard enables **data-driven decision-making** across operations, marketing, logistics, and customer service.

---

##  **Tools Used**

* **Power BI Desktop**
* Power Query (Data Cleaning & Transformation)
* DAX (Data Analysis Expressions)
* Star Schema Data Modeling
* GitHub (Version Control)

---

##  **Dataset Description**

Dataset contains **8 CSV files:**

| Table       | Description                         |
| ----------- | ----------------------------------- |
| orders      | Order-level details (status, dates) |
| order_items | Product-level sales data            |
| customers   | Customer details (state, city)      |
| sellers     | Seller information                  |
| products    | Product category & attributes       |
| payments    | Payment method & transaction data   |
| reviews     | Customer reviews & ratings          |
| geolocation | City/state mapping                  |

---

##  **Data Cleaning Steps (Power Query)**

* Converted columns to correct **data types**
* Removed duplicates from Customers & Sellers
* Removed blank and error rows
* Created calculated fields (Delivery Days, Delay Days)
* Standardized category & payment values
* Trimmed extra spaces and fixed text formatting
* Cleaned date columns (purchase, approved, delivered)

---

##  **Data Modeling (Star Schema)**

Fact Table:

* **order_items**

Dimension Tables:

* orders
* customers
* sellers
* products
* payments
* reviews
* geolocation

Key relationships created on:

* **customer_id**
* **seller_id**
* **order_id**
* **product_id**

Cross-filter: **Single Direction**
Cardinality: **Many-to-One**

---

##  **DAX Measures Used**

Key Measures:

```dax
Total Sales = SUM(order_items_data[price])

Total Orders = DISTINCTCOUNT(orders_data[order_id])

Total Customers = DISTINCTCOUNT(olist_customers_dataset[customer_id])

Total Freight = SUM(order_items_data[freight_value])

Profit = [Total Sales] - [Total Freight]

Profit Margin % = DIVIDE([Profit], [Total Sales], 0)

Average Review Score = AVERAGE(order_reviews_data[review_score])

Late Orders % =
VAR Late =
    COUNTROWS(
        FILTER(
            orders_data,
            orders_data[order_delivered_customer_date] > orders_data[order_estimated_delivery_date]
        )
    )
RETURN
DIVIDE(Late, [Total Orders], 0)
```

---

##  **Dashboard Features**

###  KPI Indicators

* Total Sales
* Total Orders
* Total Customers
* Profit
* Profit Margin %
* Average Review Score

###  Visualizations

* **Monthly Sales Trend** (Line Chart)
* **Sales by Category** (Bar Chart)
* **Sales by Payment Method** (Donut Chart)
* **Sales by State** (Bar/Treemap)
* **Top Sellers** (Table/Bar Chart)

###  Interactive Elements

* Slicers for State, Category, Payment Type, Year
* Drill-through analysis
* Conditional formatting
* Clean, professional layout

---

##  **Key Insights**

* Sales peak during mid-year months (May–October)
* Top product categories drive majority of revenue
* Credit card is the most used payment method
* States SP, RJ, MG contribute the highest sales
* Customer satisfaction is moderate (Avg review score ~3.8)
* Late deliveries impact review scores negatively

---

##  **Business Recommendations**

* Improve delivery performance in high-volume states
* Promote high-profit categories more
* Strengthen seller onboarding to reduce delivery delays
* Offer incentives for fast payment methods
* Improve customer service for low-rating orders

---

##  **Project Files in This Repository**

* `Olist_Ecommerce_Dashboard.pbix` – Power BI file
* `datasets/` – Raw CSV files
* `README.md` – Documentation
* `Insights.pdf` (optional)

---

##  **Conclusion**

This end-to-end Power BI project demonstrates:

* Data cleaning
* Data modeling
* DAX measure creation
* Dashboard design
* Insight generation

It showcases strong skills in **business analytics**, **data visualization**, and **problem-solving**.

---
