# Azure-Netflix-Project
Overview

This project demonstrates a modern Data Lakehouse architecture built on Azure + Databricks, leveraging Delta Live Tables (DLT) for real-time and incremental data processing.

The architecture ingests data from multiple sources, processes it through a medallion architecture (Bronze → Silver → Gold), and makes it available for analytics and reporting via Azure Synapse Analytics and Power BI.

🏗️ Architecture

🔑 Key Components

Data Sources:

Files, APIs, and streaming data

GitHub integration for CI/CD and pipeline orchestration

Ingestion (Bronze Layer)

Azure Data Factory (ADF) orchestrates batch and streaming data ingestion.

Data lands in Azure Data Lake Storage Gen2 as raw incremental data.

Transformation (Silver Layer)

Databricks Delta Live Tables (DLT) handle transformations (cleaning, joins, enrichment).

Data is stored in curated Silver tables for downstream use.

Star Schema (Gold Layer)

Business-ready fact and dimension tables are built in the Gold layer.

Optimized for analytics and reporting.

Warehouse & Reporting

Data flows into Azure Synapse Analytics for enterprise-scale queries.

Power BI connects to Synapse or directly to Delta tables for dashboards and reporting.

🏅 Medallion Architecture

Bronze (Incremental Data) → Raw, append-only ingestion.

Silver (Transformation) → Cleansed and conformed data.

Gold (Star Schema) → Aggregated, analytics-ready datasets.

🚀 Features

✅ Real-time and incremental data ingestion

✅ Fully automated pipelines with Delta Live Tables

✅ End-to-end orchestration with Azure Data Factory

✅ Warehouse-ready tables for Synapse Analytics

✅ Self-service BI with Power BI

✅ GitHub integration for CI/CD

HiGH LEVEL DESIGN

![screenshot](https://github.com/Sharmaaditya22/Azure-Netflix-Project/blob/10dc5a00ee7d7a5261c23916bada5791e37491eb/Azure_Netflix_project_flow.png)
