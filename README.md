# 🛒 E-Commerce Database Analysis | SQL & Business Intelligence

### From raw data to business insights

[![SQL](https://img.shields.io/badge/SQL-SQLite-07405E?style=for-the-badge\&logo=sqlite\&logoColor=white)](https://www.sqlite.org/)
[![Python](https://img.shields.io/badge/Python-Data_Analysis-3776AB?style=for-the-badge\&logo=python\&logoColor=white)](https://www.python.org/)
[![Google Colab](https://img.shields.io/badge/Google_Colab-Notebook-F9AB00?style=for-the-badge\&logo=googlecolab\&logoColor=white)](https://colab.research.google.com/)

**Análisis de datos de comercio electrónico mediante SQL para identificar oportunidades de crecimiento, evaluar el comportamiento de los clientes y optimizar la gestión comercial y de inventario.**

📓 **[Open in Google Colab](https://colab.research.google.com/github/sergioingmeca-cyber/E-Commerce-Database-Project/blob/main/E_Commerce_Database_Project.ipynb)** | 💻 **[View repository](https://github.com/sergioingmeca-cyber/E-Commerce-Database-Project)**

---

## 🎯 1. Business Problem

An e-commerce company needs to understand what drives its revenue, which products and categories contribute the most to sales, which customers generate the highest value, and where inventory management can be improved.

The challenge is to transform transactional data stored in a relational database into actionable insights that support commercial decision-making.

**Project objective:** use SQL to explore the database, calculate business KPIs, rank products and customers, evaluate repeat purchasing behavior, and identify opportunities to improve business performance.

## 🗂️ 2. Dataset Overview

The project uses a SQLite database named `store.db`, structured into five main business tables.

| Table         | Description                                            |
| ------------- | ------------------------------------------------------ |
| `customers`   | Customer information, location and signup date         |
| `orders`      | Order identifiers, customers, dates and order status   |
| `order_items` | Products purchased, quantities and unit prices         |
| `products`    | Product names, categories, prices and stock quantities |
| `categories`  | Product category names and identifiers                 |

### Database scale

| Metric                   | Records |
| ------------------------ | ------: |
| Customers                |     200 |
| Orders                   |     800 |
| Order items              |   2,456 |
| Products                 |      70 |
| Product categories       |       7 |
| Customers with purchases |     197 |

The analysis connects the tables through primary and foreign key relationships to consolidate transactional information and calculate business metrics.

## 🔍 3. Business Questions

The analysis focuses on answering the following questions:

* How does monthly revenue evolve over time?
* Which product categories generate the highest revenue?
* Which products contribute the most and least to sales?
* Who are the highest-value customers?
* What is the customer repeat purchase rate?
* Which products have the lowest inventory levels?
* Which products rank highest within each category?
* How concentrated is revenue among individual customers?

## 🧠 4. SQL Techniques Applied

This project demonstrates practical SQL skills used in business and data analytics.

### Data exploration

* Listing tables through `sqlite_master`.
* Exploring table structures and records.
* Identifying the relationships between customers, orders, products and categories.

### Data aggregation

* `SUM()` to calculate revenue and quantities sold.
* `COUNT()` and `COUNT(DISTINCT ...)` to measure orders, customers and products.
* `GROUP BY` to aggregate results by month, category, product and customer.
* `ORDER BY` and `LIMIT` to identify top- and bottom-performing products.

### Joining relational tables

The analysis uses multiple `JOIN` operations to combine transactional and descriptive data.

For example, `order_items` is connected to `products` to identify the products sold, and then to `categories` to calculate revenue by category.

### Common Table Expressions (CTEs)

`WITH` clauses organize complex queries into readable steps. They are used to calculate customer-level revenue and rank products before applying filters.

### Window functions

`RANK()` and `SUM() OVER()` support more advanced analysis, including:

* Ranking products within each category.
* Calculating customer revenue participation.
* Identifying the top three products in each category.

### Date functions and null handling

* `STRFTIME()` to aggregate revenue by year and month.
* `COALESCE()` to handle null values in quantity and unit-price calculations.

### Python integration

Python and `sqlite3` connect to the database, while `pandas` executes SQL queries and displays the resulting datasets in Google Colab.

## 📊 5. Key Business Findings

### Revenue performance

* **Total revenue:** $875,798.71.
* **Average monthly revenue:** $35,031.95.
* **Highest-revenue month:** June 2025, with $64,571.88.
* **Lowest-revenue month:** July 2024, with $10,835.49.

Revenue fluctuates considerably throughout the period. June 2025 represents the strongest month, while July 2024 records the lowest revenue. Investigating seasonality, demand patterns and order activity could help explain these variations.

### Revenue by product category

| Category               |     Revenue |
| ---------------------- | ----------: |
| Home & Kitchen         | $137,363.66 |
| Sports & Outdoors      | $135,881.01 |
| Toys & Games           | $132,302.32 |
| Clothing               | $126,662.31 |
| Beauty & Personal Care | $118,815.98 |
| Electronics            | $117,818.16 |
| Books                  | $106,955.27 |

**Home & Kitchen** is the leading category by revenue, while **Books** records the lowest revenue among the seven categories.

These figures measure sales revenue rather than net profitability. Cost and margin data would be required to determine which category is the most profitable.

### Top-performing products

| Rank | Product         |    Revenue |
| ---: | --------------- | ---------: |
|    1 | Yoga Mat        | $35,373.00 |
|    2 | Building Blocks | $29,079.63 |
|    3 | Monitor         | $28,971.80 |
|    4 | Keyboard        | $27,712.45 |
|    5 | Lamp            | $26,686.22 |

Yoga Mat leads product revenue and also records the highest number of units sold, with 130 units.

### Lowest-revenue products

| Product   |   Revenue |
| --------- | --------: |
| Charger   |   $506.60 |
| RC Car    |   $776.05 |
| Guidebook | $1,051.39 |
| Comic     | $1,624.52 |
| Art Set   | $1,828.60 |

Charger has the lowest revenue among the products analyzed. This finding provides an opportunity to investigate pricing, customer demand, product availability and sales performance before making commercial decisions.

### Highest-value customers

| Customer      | Total purchases | Revenue share |
| ------------- | --------------: | ------------: |
| Beth Daniels  |      $13,802.34 |         1.58% |
| Mark Brown    |      $13,711.83 |         1.57% |
| Barbara Parks |      $12,076.32 |         1.38% |
| Donald Shah   |       $9,985.81 |         1.14% |
| Anita Baxter  |       $9,784.54 |         1.12% |

Beth Daniels is the highest-value customer by cumulative purchase amount, followed closely by Mark Brown.

Together, the results demonstrate how customer-level aggregation and window functions can identify valuable customers and quantify their contribution to total revenue.

### Customer repeat purchase rate

| KPI                         |    Result |
| --------------------------- | --------: |
| Customers who purchased     |       197 |
| Repeat customers            |       184 |
| Customers with one purchase |        13 |
| **Repeat purchase rate**    | **93.4%** |

The repeat purchase rate is calculated as the proportion of purchasing customers who placed at least two distinct orders.

This indicates a high level of repeat purchasing within the observed dataset. Further analysis of purchase frequency, time between orders and customer recency would help evaluate customer retention more comprehensively.

### Inventory analysis

| Product           | Stock available |
| ----------------- | --------------: |
| Poetry Collection |               3 |
| Coffee Maker      |               9 |
| Comic             |              10 |
| Jacket            |             500 |

Poetry Collection, Coffee Maker and Comic have the lowest stock levels, while Jacket has the highest inventory among the products examined.

Low stock does not necessarily imply a shortage. The next step is to compare available inventory against sales velocity, supplier lead times and expected demand.

## 💡 6. Business Recommendations

### 1. Improve revenue planning

Investigate the months with unusually high and low revenue, identify seasonal patterns, and use historical results to plan campaigns and inventory availability.

### 2. Optimize category performance

Build on the strong revenue contribution of Home & Kitchen while investigating the sales drivers behind Books. Incorporate product costs and margins before making profitability-related decisions.

### 3. Strengthen product strategy

Maintain visibility into high-performing products such as Yoga Mat. Investigate low-revenue products such as Charger to determine whether pricing adjustments, promotions or assortment changes are justified.

### 4. Develop customer retention strategies

Use the customer revenue ranking to identify high-value buyers and design targeted loyalty initiatives. Complement revenue with frequency and recency metrics to develop a more complete customer segmentation.

### 5. Improve inventory management

Review Poetry Collection, Coffee Maker and Comic against recent demand and replenishment lead times. Establish reorder points and monitor products with potentially excessive stock, including Jacket.

## 🧱 7. Analytical Workflow

```text
SQLite Database
       ↓
Database Exploration
       ↓
Relational Joins
       ↓
Revenue & KPI Calculations
       ↓
Aggregations by Month, Category,
Product and Customer
       ↓
CTEs & Window Functions
       ↓
Business Findings
       ↓
Recommendations
```

## 🛠️ 8. Tools & Skills

**Tools**

* SQL
* SQLite
* Python
* pandas
* sqlite3
* Google Colab

**Technical skills**

* Relational database querying
* Multi-table joins
* Aggregations and grouping
* Common Table Expressions (CTEs)
* Window functions and ranking
* Date-based analysis
* Null handling
* KPI calculation
* Customer and product performance analysis

**Business skills**

* Business problem definition
* Revenue analysis
* Customer segmentation foundations
* Inventory analysis
* Insight communication
* Data-driven recommendations

## 🏁 9. Conclusion

This project demonstrates how SQL can transform relational e-commerce data into actionable business insights.

By combining multiple tables, calculating revenue metrics and applying window functions, the analysis identifies high-performing categories, leading products, valuable customers, repeat purchase behavior and potential inventory risks.

The project highlights an essential data analytics skill: connecting technical querying with business questions and translating the results into practical recommendations.

---

## 👨‍💻 About Me

**Sergio Iván Ramírez Moreno**
Aspiring Data Analyst | Mechanical Engineer | Project Management Specialist

I am developing my data analytics portfolio through practical projects focused on SQL, Python, business intelligence and data-driven decision-making.

* **GitHub:** [sergioingmeca-cyber](https://github.com/sergioingmeca-cyber)
* **LinkedIn:** [Sergio Ramírez](https://www.linkedin.com/in/sergio-ramirez-b72744343/)
* **Portfolio:** [Data Analyst Portfolio](https://sergioingmeca-cyber.github.io/portafolio/)

**Thanks for visiting this project!**
