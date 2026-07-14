# 🚀 UnitedHealth Group,UK - Azure Enterprise Insurance Data Engineering Platform

> **A production-inspired Azure Data Engineering solution implementing a Metadata-Driven Medallion Architecture with Incremental Data Loading, Generic ETL Framework, Slowly Changing Dimension (SCD Type 2), Azure Data Factory Orchestration, Databricks, Delta Lake, and Enterprise Monitoring.**

---

## 📌 Project Overview

This current project demonstrates the design and implementation of an enterprise-grade Insurance Data Platform built entirely on the Microsoft Azure ecosystem.

The solution follows the **Medallion Architecture (Bronze → Silver → Gold)** and uses a **Metadata-Driven Generic Framework** capable of processing multiple datasets without modifying business logic.

Instead of building table-specific pipelines, the framework dynamically reads configuration from metadata tables, making it scalable, reusable, and suitable for real-world enterprise environments.

---

# 🏗 Architecture

```
                  Source Files
                (CSV / JSON / XML)
                       │
                       ▼
            Azure Data Lake Storage Gen2
                  Landing Zone
                       │
                       ▼
          Azure Data Factory Orchestration
                       │
      ┌────────────────┼────────────────┐
      ▼                ▼                ▼
 Bronze Layer     Silver Layer     Gold Layer
 Raw Storage      Data Cleansing   Business Model
                       │
                       ▼
             SCD Type 2 History Layer
                       │
                       ▼
               Delta Lake Tables
                       │
                       ▼
               Power BI / Analytics
```

---

# 🎯 Project Objectives

* Build a scalable enterprise data platform
* Implement Medallion Architecture
* Develop Metadata-Driven ETL Framework
* Implement Incremental Data Loading
* Implement Watermark Processing
* Build Generic Bronze, Silver and Gold loaders
* Implement Slowly Changing Dimension Type 2
* Orchestrate complete pipeline using Azure Data Factory
* Maintain Pipeline Audit & Monitoring
* Enable Enterprise Data Governance

---

# ⚙ Technology Stack

| Category          | Technology                   |
| ----------------- | ---------------------------- |
| Cloud Platform    | Microsoft Azure              |
| Data Integration  | Azure Data Factory           |
| Data Processing   | Azure Databricks             |
| Language          | PySpark                      |
| Storage           | Azure Data Lake Storage Gen2 |
| Database          | Azure SQL Database           |
| File Format       | CSV                          |
| Data Lake         | Delta Lake                   |
| Notebook Platform | Databricks                   |
| Orchestration     | Azure Data Factory           |
| Version Control   | Git & GitHub                 |

---

# 📂 Project Structure

```
Azure-Insurance-Data-Engineering
│
├── notebooks
│   ├── 00_Configuration
│   ├── 01_Utility_Functions
│   ├── 02_Generic_Bronze_Loader
│   ├── 03_Generic_Silver_Loader
│   ├── 04_Generic_Gold_Loader
│   └── 05_Generic_SCD2_Framework
│
├── metadata
│   ├── bronze_config
│   ├── silver_config
│   ├── gold_config
│   └── pipeline_watermark
│
├── audit
│   └── pipeline_audit
│
├── adf
│   └── PL_Master_Insurance
│
└── README.md
```

---

# ⭐ Enterprise Features

## ✅ Metadata Driven Framework

The framework dynamically retrieves configuration from metadata tables including:

* Source Folder
* Source System
* Target Table
* Primary Key
* Load Strategy
* Watermark Column
* File Format

No notebook modifications are required when onboarding a new table.

---

## ✅ Generic Bronze Loader

Responsibilities:

* Read Landing files
* Apply Incremental Load Logic
* Validate Primary Keys
* Handle Null Records
* Add Metadata Columns
* Write Delta Tables
* Update Audit Table

---

## ✅ Generic Silver Loader

Responsibilities:

* Data Cleansing
* Remove Invalid Records
* Remove Duplicate Records
* Schema Standardization
* Business Rule Validation

---

## ✅ Generic Gold Loader

Responsibilities:

* Business-ready Transformation
* Dimension Table Creation
* Analytics Optimization
* Enterprise Delta Storage

---

## ✅ Generic SCD Type 2 Framework

Supports complete historical tracking.

Features:

* Detect New Records
* Detect Changed Records
* Expire Existing Version
* Insert New Current Version
* Maintain Full History
* Automatic Version Management

---

## ✅ Incremental Data Loading

Instead of loading every record every execution:

```
Landing Data
      │
      ▼
Read Watermark
      │
      ▼
Filter New Records
      │
      ▼
Process Only Changed Data
```

Benefits

* Faster Execution
* Lower Compute Cost
* Reduced Storage
* Production Ready

---

## ✅ Watermark Framework

Tracks latest processed record using

```
insurance_metadata.pipeline_watermark
```

Supports

* Incremental Processing
* Recovery after Failure
* Enterprise Scheduling

---

## ✅ Pipeline Audit Framework

Each notebook automatically records:

* Pipeline Name
* Table Name
* Load Type
* Start Time
* End Time
* Rows Read
* Rows Written
* Status
* Error Message
* Pipeline Run ID

Supports complete operational monitoring.

---

# 📊 Data Flow

```
Landing Files
      │
      ▼
Bronze
      │
      ▼
Silver
      │
      ▼
Gold
      │
      ▼
SCD Type 2
      │
      ▼
Audit Logging
      │
      ▼
Watermark Update
```

---

# 🔄 Pipeline Workflow

```
ADF Trigger

      │

      ▼

Bronze Notebook

      │

      ▼

Silver Notebook

      │

      ▼

Gold Notebook

      │

      ▼

SCD Type 2 Notebook

      │

      ▼

Audit Update

      │

      ▼

Watermark Update
```

---

# 📈 Key Capabilities

* Metadata Driven Architecture
* Generic ETL Framework
* Dynamic Table Processing
* Incremental Loading
* Watermark Framework
* SCD Type 2
* Delta Lake
* Azure Data Factory Orchestration
* Enterprise Audit Framework
* Production-ready Medallion Architecture
* Modular Notebook Design
* Scalable Enterprise Data Platform

---

# 💼 Skills Demonstrated

* Azure Data Factory
* Azure Databricks
* PySpark
* Delta Lake
* Azure SQL Database
* Azure Data Lake Storage Gen2
* Incremental ETL Design
* Metadata-Driven Frameworks
* SCD Type 2 Implementation
* Enterprise Data Modeling
* Data Warehouse Design
* Pipeline Monitoring
* Data Quality Validation
* Git Version Control

---

# 🚀 Future Enhancements

* CI/CD using Azure DevOps
* Unity Catalog Integration
* Delta Live Tables
* Event-Driven Processing
* Auto Loader
* Change Data Capture (CDC)
* Power BI Executive Dashboard
* Azure Key Vault Integration
* Email Notifications using Logic Apps
* Data Quality Framework
* Automated Unit Testing

---

# 👨‍💻 Author

**Ashok Kumar Krishna**

**Azure Data Engineer | PySpark | Azure Databricks | Azure Data Factory | SQL | Delta Lake | Data Warehousing**

---

## ⭐ Why this README stands out

This README presents the project as an enterprise engineering solution rather than a training exercise. It emphasizes architecture, scalability, metadata-driven design, incremental processing, SCD Type 2, auditing, and orchestration—exactly the kinds of capabilities recruiters and hiring managers look for in Azure Data Engineering portfolios.
Initialized by Azure Data Factory!
