# sql-data-warehouse-project

# 📊 Data Warehouse & Analytics Project

Welcome to the **Data Warehouse & Analytics Project** repository! 🚀

This project demonstrates the end-to-end development of a modern SQL Server data warehouse, from importing and transforming raw data to building a structured analytical model. It showcases data engineering and business intelligence techniques used to generate meaningful insights for decision-making.

---
## 🏗️ Data Architecture

The data architecture for this project follows Medallion Architecture **Bronze**, **Silver**, and **Gold** layers:
![Data Architecture](documents/data_architecture.png)

1. **Bronze Layer**: Stores raw data as-is from the source systems. Data is ingested from CSV Files into SQL Server Database.
2. **Silver Layer**: This layer includes data cleansing, standardization, and normalization processes to prepare data for analysis.
3. **Gold Layer**: Houses business-ready data modeled into a star schema required for reporting and analytics.

---

# 🚀 Project Overview

## Building the Data Warehouse (Data Engineering)

### Objective
Design and develop a scalable SQL Server data warehouse by integrating data from multiple source systems, ensuring high data quality and creating a reliable foundation for reporting and analytics.

### Key Features
- Import data from multiple source systems (ERP & CRM).
- Clean, validate, and transform raw data.
- Design a Star Schema data model.
- Build fact and dimension tables.
- Develop ETL processes using SQL.
- Document the data model and warehouse architecture.

---

## 🔄 Data Flow

The data flow illustrates how data moves from the **CRM and ERP source systems** through the **Bronze, Silver, and Gold layers** of the data warehouse.

![Data Flow](documents/data_flow.png)

### 🥉 Bronze Layer
Raw data is extracted from the source systems and loaded into the Bronze layer without transformation.

- **CRM Sources:** Customer information, product information, and sales details.
- **ERP Sources:** Customer data, location data, and product category data.
- The original source structure is preserved for traceability and auditing.

### 🥈 Silver Layer
Data from the Bronze layer is cleansed, standardized, and transformed before being used for analytics.

- Data quality issues are identified and resolved.
- Values are standardized and normalized.
- Data from CRM and ERP systems is prepared for integration.
- Business rules and transformations are applied.

### 🥇 Gold Layer
The cleaned Silver layer data is integrated into business-ready datasets designed for reporting and analytics.

- **`fact_sales`** – Contains sales transaction and performance data.
- **`dim_customers`** – Combines customer information from CRM and ERP sources.
- **`dim_products`** – Combines product information from CRM and ERP sources.

The Gold layer forms the final **Star Schema**, providing a structured data model optimized for analytical queries and business intelligence reporting.

---

## ⭐ Data Model

The **Gold Layer** is designed using a **Star Schema** to provide a simple and efficient structure for analytical queries and reporting.

![Data Model](documents/data_model.png)

The model consists of one central fact table connected to two dimension tables:

1. **Fact Sales (`gold.fact_sales`)**: Stores transactional sales data including order numbers, order dates, shipping dates, quantities, prices, and sales amounts. It connects to the customer and product dimensions through foreign keys.

2. **Customer Dimension (`gold.dim_customers`)**: Contains descriptive customer information such as customer ID, name, country, marital status, gender, and birthdate. Each customer is uniquely identified using a surrogate `customer_key`.

3. **Product Dimension (`gold.dim_products`)**: Contains product-related information including product name, category, subcategory, product line, cost, and maintenance information. Each product is uniquely identified using a surrogate `product_key`.

### 🔗 Relationships

- `gold.fact_sales.customer_key` → `gold.dim_customers.customer_key`
- `gold.fact_sales.product_key` → `gold.dim_products.product_key`

The dimension tables have a **one-to-many relationship** with the fact table, allowing each customer and product to be associated with multiple sales transactions.

### 🧮 Sales Calculation

Sales values are calculated using:

**Sales Amount = Quantity × Price**

This star schema provides a business-ready data model optimized for **SQL analytics, reporting, and BI applications**.

---

## 📈 Analytics & Reporting (Business Intelligence)

### Objective
Create SQL-based analytical queries and reports to provide actionable business insights and support data-driven decision making.

### Business Insights
- Customer Analysis
- Product Performance
- Sales Trends
- Revenue Analysis
- KPI Reporting

These reports enable stakeholders to monitor business performance, identify trends, and make informed strategic decisions.

---

## 📊 Data Visualisation

To complete the end-to-end workflow, the Gold Layer reporting views were connected directly to **Tableau Desktop using a live SQL Server connection**.

A simple Sales Performance dashboard was created to present key customer and product insights from:

- `gold.report_customers`
- `gold.report_products`

### Dashboard Highlights

The dashboard includes:

- **Total Sales**
- **Total Customers**
- **Total Orders**
- **Total Products**
- **Average Order Value**
- Sales by Customer Segment
- Average Order Value by Customer Segment
- Sales by Product Category
- Product Performance analysis using Sales, Selling Price, Quantity and Product Segment

The product performance scatter plot is used to identify the relationship between **product revenue, selling price and sales volume**, while also highlighting High-, Mid- and Low-Performing products.

### Dashboard Preview

![Sales Performance Dashboard](documents/sales_performance_dashboard.png)

> Tableau Desktop is connected directly to the SQL Server Gold Layer using a live connection, allowing the dashboard to query the reporting views directly.

## 🛠️ Technologies Used

- SQL Server
- T-SQL
- SQL Server Management Studio (SSMS)
- Data Warehousing
- ETL
- Star Schema
- Business Intelligence
- Tableau Desktop

## 📁 Repository Structure

The repository is organised to separate source datasets, data warehouse development, testing, documentation, and analytical reporting.

```text
sql-data-warehouse-project/
│
├── data_reports/                       # Business-focused analytical reports
│   ├── README.md                       # Overview of reporting layer
│   │
│   ├── customer_report/
│   │   ├── README.md                   # Customer report documentation
│   │   └── report_customer.sql         # Customer analysis SQL view
│   │
│   └── product_report/
│       ├── README.md                   # Product report documentation
│       └── report_products.sql         # Product analysis SQL view
│
├── datasets/                           # Source data from CRM and ERP systems
│   │
│   ├── CRM/
│   │   ├── cust_info.csv
│   │   ├── prd_info.csv
│   │   └── sales_details.csv
│   │
│   └── ERP/
│       ├── CUST_AZ12.csv
│       ├── LOC_A101.csv
│       └── PX_CAT_G1V2.csv
│
├── documents/                          # Project architecture and documentation
│   ├── data_architecture.png
│   ├── data_catalog.md
│   ├── data_flow.png
│   ├── data_model.png
│   └── naming_conventions.md
│
├── scripts/                            # Data warehouse SQL development
│   │
│   ├── Bronze/
│   │   ├── ddl_bronze.sql             # Bronze layer table definitions
│   │   └── proc_load_bronze.sql       # Raw data loading procedure
│   │
│   ├── Silver/
│   │   ├── ddl_silver.sql             # Silver layer table definitions
│   │   └── proc_load_silver            # Cleansing and transformation procedure
│   │
│   ├── Gold/
│   │   └── ddl_gold.sql               # Star schema / analytical model
│   │
│   └── init_database.sql              # Database and schema initialisation
│
├── tests/                              # Data quality validation
│   ├── quality_checks_gold.sql
│   └── quality_checks_silver.sql
│
├── LICENSE
└── README.md                           # Main project documentation
```

### 🔎 Key Areas

* **`scripts/`** – Contains the complete Bronze, Silver, and Gold data warehouse implementation.
* **`datasets/`** – Contains the CRM and ERP source datasets used by the ETL pipeline.
* **`documents/`** – Contains the architecture, data flow, data model, catalogue, and naming standards.
* **`tests/`** – Contains SQL data-quality checks for the transformed warehouse layers.
* **`data_reports/`** – Contains business-ready Customer and Product analytical reports created from the Gold Layer.


