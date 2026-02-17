# 🏭 FMCG Data Engineering Project – Lakehouse ETL Pipeline

## 📌 Project Overview
This project demonstrates an **end-to-end data engineering pipeline** using **Databricks (Free Edition)** in the **FMCG domain**.  
Scenario: A **large retail company acquires a smaller one**, and we need to consolidate their data into a **single Lakehouse architecture**.

The pipeline follows the **Medallion Architecture (Bronze → Silver → Gold)** and integrates with **Amazon S3, Spark, SQL, Python, Genie, and BI dashboards**.

---

## ⚙️ Tech Stack
- **Databricks (Free Edition)**
- **Python** (ETL scripts, automation)
- **SQL** (data transformations, reconciliation)
- **Apache Spark** (distributed processing)
- **Amazon S3** (data lake storage)
- **Medallion Architecture** (Bronze, Silver, Gold layers)
- **BI Dashboard** (analytics & visualization)
- **Genie** (workflow orchestration)

---

## ⚙️ Workflow
1. **Data Ingestion**
    - Source data from legacy systems (CSV, JSON, SQL dumps).
    - Load into Databricks Bronze tables (Delta Lake on S3).
2. **Data Transformation**
    - Use PySpark notebooks for schema harmonization, deduplication, and enrichment.
    - Apply SQL transformations for business rules.
    - Store results in Silver tables.
3. **Data Aggregation**
    - Build curated datasets (sales, inventory, customer insights).
    - Store in Gold tables for analytics.
4. **Visualization**
    - Connect BI tools (Power BI, Tableau) to Gold layer.
    - Deliver dashboards for executives and analysts.
5. **Orchestration**
    - Schedule and monitor pipelines using Databricks Jobs.
    - Integrate Genie for workflow automation.

---

## 🏗️ Architecture Diagram

![Project Architectuire Image](https://github.com/Priyanka9124/fmcg_domain/blob/main/resources/project_architecture.png)


    Raw Data (Company A + Company B)
                 |
              Amazon S3
                 |
             Bronze Layer
                 |
             Silver Layer
                 |
             Gold Layer
                 |
          BI Dashboard + Genie

---

## 🚀 Getting Started

### 1. Clone Repository
    ```bash
    [git clone https://github.com/Priyanka9124/fmcg_domain.git]
    cd fmcg-domain

### 2. Setup Databricks Notebook
Upload the provided notebooks into your Databricks workspace.

## 📂 Project Structure

    - fmcg_domain/
    │── 0_data/
    │── │── 0_data/
    │   ├── bronze_ingestion.py
    │   ├── silver_transformation.sql
    │   ├── gold_aggregation.py
    │── configs/
    │   ├── s3_config.json
    │── dashboards/
    │   ├── fmcg_sales_dashboard.twb
    │── README.md

## 📝 Sample Code
### Bronze Layer – Raw Data Ingestion
    - from pyspark.sql import SparkSession
    spark = SparkSession.builder.appName("FMCG Bronze Ingestion").getOrCreate()
    // Load raw data from S3
    raw_df = spark.read.option("header", True).csv("s3://fmcg-data/raw/companyA/*.csv")
    // Write to Bronze Layer
    raw_df.write.format("delta").mode("overwrite").save("/mnt/bronze/companyA")

### Silver Layer – Data Cleaning & Transformation
-- Remove duplicates and standardize schema
    - CREATE OR REPLACE TABLE silver.sales AS
    SELECT DISTINCT
        CAST(order_id AS INT) AS order_id,
        customer_name,
        LOWER(product_name) AS product_name,
        CAST(sale_amount AS DOUBLE) AS sale_amount,
        sale_date
    FROM bronze.sales;

### Gold Layer – Aggregation for BI
    - gold_df = spark.sql("""
        SELECT product_name, SUM(sale_amount) AS total_sales
        FROM silver.sales
        GROUP BY product_name
    """)
    
    gold_df.write.format("delta").mode("overwrite").save("/mnt/gold/sales_summary")

## 📊 BI Dashboard
- Connect Tableau / Power BI to the Gold Layer Delta tables.
- Example KPI:
    - Total Sales by Product
    - Sales Trend by Month
    - Comparison between Company A & B
 
## 🔮 Genie Workflow
- Genie orchestrates:
    - Daily ingestion jobs
    - Transformation pipelines
    - Dashboard refresh schedules

