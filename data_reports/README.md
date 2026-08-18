# 📊 Data Reports

This folder contains analytical SQL reports created from the **Gold Layer** of the data warehouse.

The purpose of these reports is to transform cleaned and modelled warehouse data into business-ready datasets that can support reporting, analysis, and dashboard development.

The reports are built as reusable SQL views and focus on two main analytical areas:

* **Customer analysis**
* **Product analysis**

---

## 👥 Customer Report

The Customer Report provides a consolidated customer-level view of sales activity and customer behaviour.

It includes analysis such as:

* Customer demographics
* Age grouping
* Customer segmentation
* Total orders
* Total sales
* Total quantity purchased
* Unique products purchased
* Customer lifespan
* Recency
* Average order value
* Average monthly spend

The report also segments customers into:

* **VIP**
* **Regular**
* **New**

📁 [View Customer Report](customer_report/)

---

## 📦 Product Report

The Product Report provides a consolidated product-level view of sales performance and customer activity.

It includes analysis such as:

* Product name, category, and subcategory
* Total orders
* Total sales
* Total quantity sold
* Unique customers
* Product lifespan
* Last sale date
* Recency
* Average selling price
* Average order revenue
* Average monthly revenue

Products are also segmented into:

* **High-Performer**
* **Mid-Range**
* **Low-Performer**

📁 [View Product Report](product_report/)

---

## 🛠️ SQL Concepts Applied

Across both reports, a range of SQL techniques are used to transform transactional data into analytical datasets, including:

* Common Table Expressions (`CTEs`)
* `LEFT JOIN`
* `GROUP BY`
* `COUNT` and `COUNT(DISTINCT)`
* `SUM`
* `AVG`
* `MIN` and `MAX`
* `DATEDIFF`
* `GETDATE`
* `CASE` statements
* `CAST`
* `NULLIF`
* `ROUND`
* `CREATE VIEW`

These techniques are used to combine data, aggregate metrics, calculate KPIs, apply business logic, and create reusable reporting views.

---

## 📁 Folder Structure

```text
data_reports/
│
├── README.md
│
├── customer_report/
│   ├── README.md
│   └── report_customers.sql
│
└── product_report/
    ├── README.md
    └── report_products.sql
```

Each report folder contains:

* A dedicated `README.md` explaining the report objectives, KPIs, segmentation logic, and SQL techniques used.
* The complete SQL script used to create the reporting view.
