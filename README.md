# 🚀 Modern Azure Data Lakehouse with Delta Live Tables (DLT)

![Azure](https://img.shields.io/badge/Azure-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)
![Databricks](https://img.shields.io/badge/Databricks-FF3621?style=for-the-badge&logo=databricks&logoColor=white)
![Delta Lake](https://img.shields.io/badge/Delta_Lake-D45500?style=for-the-badge&logo=deltalake&logoColor=white)
![Synapse](https://img.shields.io/badge/Synapse%20Analytics-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)

## 📖 Overview
This project demonstrates an enterprise-grade **Data Lakehouse architecture** built on **Azure** and **Databricks**. It leverages **Delta Live Tables (DLT)** to replace traditional orchestration with a declarative, quality-enforced pipeline.

The system ingests a comprehensive **Netflix Dataset** to simulate a real-world digital media analytics platform. It processes raw entertainment data through a **Medallion Architecture** (Bronze → Silver → Gold) to generate insights on content trends, regional availability, and user engagement.

---

## 🏗️ High-Level Design (Architecture)

![High level diagram](https://github.com/Sharmaaditya22/modern-azure-lakehouse-dlt/blob/0c59aecaca9dcd9bdaf4cff3c2cd85785df5c915/Images/Azure_Netflix_project_flow.png)

The solution follows the **Lakehouse** paradigm, combining the low-cost storage of a Data Lake with the transactional integrity (ACID) of a Data Warehouse. The data flows through the following stages:

1. **Ingestion:** Raw Netflix data (CSV/JSON) is ingested from external sources into **Azure Data Lake Storage (ADLS) Gen2**.
2. **Bronze Layer (Raw):** **Autoloader** incrementally detects new files and loads them into the raw Delta tables.
3. **Silver Layer (Transformation):** **Delta Live Tables (DLT)** perform cleaning, deduplication, and schema enforcement to create high-quality curated tables.
4. **Gold Layer (Aggregated):** Business logic is applied to create fact and dimension tables (Star Schema) optimized for reporting.
5. **Serving & Reporting:** **Azure Synapse Analytics** (Serverless) allows for SQL-based querying, while **Power BI** visualizes the insights.

---

## 📊 Dataset (Netflix Data)
This project uses a rich dataset representing a global streaming catalog. The data is located in the `data/` directory and includes:
* **Titles:** Metadata for movies and TV shows (Director, Cast, Country, Rating).
* **Credits:** Detailed cast and crew information.
* **User Metrics:** Simulated viewership and rating data.

*Note: This data is used to demonstrate complex transformations, such as handling nested JSON structures (e.g., separating multiple actors from a single column) and analyzing content distribution strategies.*

---

## 🔑 Key Components

### 1. Ingestion Layer (Bronze)
* **Tool:** Azure Data Factory (ADF) & Databricks Autoloader.
* **Process:** ADF triggers the movement of Netflix CSV/JSON files into ADLS Gen2. Autoloader incrementally detects new files and loads them into the **Bronze** layer.

### 2. Transformation Layer (Silver)
* **Tool:** **Delta Live Tables (DLT)**.
* **Logic:**
    * **Cleaning:** Removes duplicates and handles null values in critical fields like `Director` or `Cast`.
    * **Enrichment:** Unflattens complex strings (e.g., separating "Tom Hanks, Tim Allen" into distinct rows) for granular analysis.
    * **Quality Checks:** Enforces schema validation using DLT constraints.

### 3. Analytics Layer (Gold & Serving)
* **Tool:** Databricks SQL & Synapse Analytics.
* **Output:** Creates business-ready aggregates, such as "Top 10 Genres by Region" or "Content Growth over Years."

---

## 📂 Repository Structure

The project is organized into the following modules:

```bash
├── data/                    # Source Netflix datasets (CSV, JSON) used in the project
├── Databricks notebook/     # PySpark notebooks containing transformation logic and DLT pipeline code
├── databrick worflow/       # JSON configuration for Databricks Jobs/Workflows to trigger DLT
├── datafactory/             # Azure Data Factory (ADF) pipeline definitions and orchestration logic
└── README.md                # Project Documentation
```
## 🚀 Key Features

* ✅ Declarative ETL: Uses Delta Live Tables to manage dependencies and data flow automatically.
* ✅ Real-Time Data Quality: Automated constraints ensure the Netflix catalog data is accurate and consistent.
* ✅ Hybrid Orchestration: Combines Azure Data Factory for external file detection with Databricks Workflows for internal processing.
* ✅ Warehouse-Grade Analytics: Enables enterprise-scale SQL reporting via Synapse Analytics without duplicating data.
* ✅ CI/CD Integrated: Modular structure allows for easy deployment via GitHub Actions or Azure DevOps.

## 🛠️ Technology Stack

| Category | Technology Used |
| :--- | :--- |
| **Cloud Provider** | Microsoft Azure |
| **Compute & ETL** | Azure Databricks (Spark / PySpark) |
| **Orchestration** | Delta Live Tables (DLT), Azure Data Factory (ADF) |
| **Storage** | ADLS Gen2, Delta Lake |
| **Warehousing** | Azure Synapse Analytics (Serverless SQL) |
| **Visualization** | Microsoft Power BI |
