# 🚗 Azure Data Engineering Project - Car Showroom Enterprise

An end-to-end Azure Data Engineering project implementing the **Medallion Architecture (Bronze → Silver → Gold)** using Azure Data Factory, Azure Data Lake Storage Gen2, Azure Databricks, Delta Lake, and Azure Synapse Analytics.

---

# 📌 Project Overview

This project demonstrates how to build a scalable and metadata-driven data pipeline that ingests data from multiple databases, performs incremental loading, transforms data using PySpark, and prepares analytics-ready datasets.

---

# 🏗 Architecture

```
                SQL Server
                    │
                    │
                    ▼
             Azure Data Factory
                    ▲
                    │
              PostgreSQL
                    │
                    ▼
        Azure Data Lake Storage Gen2
                    │
                    ▼
            Bronze Layer (Raw)
                    │
                    ▼
        Azure Databricks (PySpark)
                    │
                    ▼
          Silver Layer (Clean)
                    │
                    ▼
       Azure Synapse Analytics
                    │
                    ▼
        Gold Layer (Analytics)
```

---

# 🎯 Project Objectives

- Build a Metadata Driven Pipeline
- Load data from SQL Server & PostgreSQL
- Perform Full Load (Initial)
- Perform Incremental Loading using Watermark
- Store Raw Data in Bronze Layer
- Clean and Transform Data in Silver Layer
- Create Business Ready Data in Gold Layer
- Automate Pipeline Execution

---

# 🛠 Technologies Used

- Azure Data Factory
- Azure Data Lake Storage Gen2
- Azure Databricks
- PySpark
- Apache Spark
- Delta Lake
- Azure Synapse Analytics
- SQL Server
- PostgreSQL
- GitHub

---

# 📂 Source Tables

## SQL Server

- Customers
- Sales
- Service Logs

## PostgreSQL

- Marketing Leads

---

# 📊 Metadata Table

The pipeline uses a metadata table called:

```
data_factory_control_log
```

Metadata stored:

- Source Database Type
- Linked Service
- Source Schema
- Source Table
- Watermark Column
- Last Load Value
- Target Directory

---

# 🔄 Incremental Loading

The pipeline performs:

## First Execution

✔ Full Load

## Next Executions

✔ Incremental Load

using Watermark Columns.

### Watermark Columns

| Table | Watermark |
|--------|-----------|
| Customers | created_date |
| Sales | purchased_date |
| Service Logs | service_date |
| Marketing Leads | created_date |

---

# ⚙ Azure Data Factory Pipeline

Pipeline Activities

```
Lookup Metadata

↓

ForEach

↓

If Condition

↓

Copy Activity

↓

Lookup MAX Watermark

↓

Stored Procedure

↓

Next Table
```

---

# 📥 Dynamic SQL Query

```sql
SELECT *
FROM dbo.sales
WHERE purchased_date > '2026-06-27'
```

---

# 🥉 Bronze Layer

Format

- Parquet

Purpose

- Raw Data Storage
- Immutable Data
- Historical Records

---

# 🥈 Silver Layer

Transformations

- Remove Duplicate Records
- Remove Null Values
- Standardize Column Names
- Trim Spaces
- Change Data Types
- Schema Evolution
- Convert to Delta Format

---

# 🥇 Gold Layer

Business Tables

- Customer Analytics
- Sales Analytics
- Marketing Analytics
- Service Analytics

Optimized for Reporting & Dashboarding.

---

# 📂 Project Structure

```
Azure-Data-Engineering-Project/

│
├── ADF
│   ├── Pipelines
│   ├── Linked Services
│   ├── Datasets
│
├── SQL
│   ├── Source Tables
│   ├── Metadata Table
│   ├── Stored Procedures
│
├── Databricks
│   ├── Bronze_to_Silver.py
│   ├── Silver_to_Gold.py
│
├── Synapse
│
├── Images
│
└── README.md
```

---

# 🚀 Features

- Metadata Driven Pipeline
- Dynamic Dataset
- Dynamic SQL Query
- Dynamic Linked Service
- Incremental Loading
- Watermark Strategy
- Multi Database Support
- Parameterized Pipeline
- Medallion Architecture
- Delta Lake
- Schema Evolution
- Automated Processing

---

# 📈 Data Flow

```
SQL Server
        \
         \
          ---> Azure Data Factory
         /
PostgreSQL

↓

Bronze (Parquet)

↓

Databricks (PySpark)

↓

Silver (Delta)

↓

Azure Synapse

↓

Gold

↓

Power BI
```

# 👨‍💻 Author

**Sachin Subhash Kaware**

Azure Data Engineer | Python | SQL | PySpark | Azure Data Factory | Azure Databricks | Azure Synapse | Delta Lake

---

# ⭐ If you like this project

Please give this repository a ⭐ Star.
