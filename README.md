# FMCG ETL Pipeline – Retail Merger Use Case
## 📌 Project Overview
In the FMCG domain, when a large retail company acquires a smaller one, consolidating their data becomes critical for unified reporting and analytics.
This project builds an ETL pipeline to integrate and transform data from both companies into a single Lakehouse architecture following the Medallion framework.
The pipeline ensures:
- Seamless ingestion of structured and semi-structured data
- Standardized transformations for consistency
- Scalable storage in Amazon S3
- Unified reporting via BI dashboards

## 🏗️ Architecture
### Medallion Layers
- **Bronze Layer:** Raw data ingestion from both companies (CSV, JSON, SQL dumps).
- **Silver Layer:** Cleaned and standardized data (schema alignment, deduplication, enrichment).
- **Gold Layer:** Business-ready aggregated datasets for analytics and dashboards.

### Tech Stack
| Component | Technology Used | 
| --- | --- |
| Programming | Python, SQL | 
| Storage | Amazon S3 + Delta Lake | 
| Processing | Databricks (Apache Spark) | 
| Architecture | Medallion (Bronze, Silver, Gold) | 
| Visualization | BI Dashboard (Power BI / Tableau) | 
| Orchestration | Databricks Jobs + Genie | 

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

## 📊 Example Use Case
- Consolidating sales transactions from both companies.
- Harmonizing product catalogs (different SKUs, naming conventions).
- Building a unified customer loyalty dashboard.

## 🚀 Getting Started
### Prerequisites
- Databricks Workspace
- AWS S3 bucket configured
- Python 3.9+ environment
- BI tool (Power BI / Tableau)

### Setup
- **Clone repository**
    - git clone https://github.com/your-org/fmcg-etl-pipeline.git
    - cd fmcg-etl-pipeline

- **Install dependencies**
    - pip install -r requirements.txt


### Run Pipeline
    - Trigger ETL job
    - python etl_pipeline.py



## 📂 Repository Structure
    - fmcg-etl-pipeline/
    │── README.md
    │── requirements.txt
    │── etl_pipeline.py
    │── configs/
    │   └── aws_config.json
    │── notebooks/
    │   └── data_cleaning.ipynb
    │── dashboards/
    │   └── sales_dashboard.pbix
    │── docs/
    │   └── architecture_diagram.png



## ✅ Deliverables
- Consolidated Lakehouse with Bronze, Silver, Gold layers
- Automated ETL pipeline on Databricks
- BI dashboards for FMCG insights
- Documentation for reproducibility


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

## 🏗️ Architecture Diagram
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
git clone https://github.com/yourusername/fmcg-etl-pipeline.git
cd fmcg-etl-pipeline




