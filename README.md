# 🚛 Azure Fleet Telemetry Data Engineering Platform

> **An enterprise-scale Azure Data Engineering solution that ingests, validates, transforms, and orchestrates connected vehicle telemetry using Azure Databricks, Azure Data Factory, Azure Blob Storage, and Azure SQL Database.**

---

# 📖 Overview

Modern transportation and logistics organizations generate millions of telemetry events from connected fleet vehicles every day. These events include GPS coordinates, speed, fuel levels, engine status, driver information, environmental readings, and operational metrics that must be processed reliably for monitoring, analytics, compliance, and business decision-making.

This project simulates a production-grade Azure Data Engineering platform that automates the complete lifecycle of fleet telemetry data—from ingestion through validation and transformation to loading curated datasets into Azure SQL Database.

The solution demonstrates enterprise data engineering practices including **Medallion Architecture**, **modular pipeline orchestration**, **PySpark transformations**, **incremental loading**, **data quality validation**, **SQL verification**, **pipeline auditing**, and **CI/CD integration**.

---

# 🏢 Business Scenario

A multinational logistics company operates thousands of connected commercial vehicles across multiple regions. Every vehicle continuously streams telemetry data to the cloud.

The organization requires a centralized platform capable of:

* Collecting high-volume JSON telemetry data
* Validating incoming records against business rules
* Cleaning and transforming raw data
* Managing incremental data loads
* Recording pipeline execution audits
* Loading curated datasets into Azure SQL Database
* Supporting operational reporting and business analytics
* Automating deployments through CI/CD

This repository demonstrates how such a solution can be implemented using Microsoft Azure services.

---

# 🏗 Solution Architecture

The solution follows a modular orchestration pattern where Azure Data Factory coordinates validation, transformation, auditing, and SQL loading.

```text
Fleet Vehicles
       │
       ▼
Azure Blob Storage (Landing)
       │
       ▼
PL_MasterFleetTelemetry
       │
 ┌─────┴─────────────────────────────┐
 │                                   │
 ▼                                   ▼
Run_Validation                Run_LoadToSQL
(Execute Pipeline)          (Execute Pipeline)
 │                                   │
 ▼                                   ▼
PL_Databricks_Validation      Copy_Staging_SQL
 │                                   │
 ▼                                   ▼
Azure Databricks        Azure SQL Staging Tables
 │                                   │
 ├── JSON Processing                 ▼
 ├── PySpark Transformations   usp_InsertPipelineAudit
 ├── Data Validation                  │
 ├── Business Rules                   ▼
 └── Medallion Architecture    usp_VerifyFleetTelemetry
                                        │
                                        ▼
                              Curated Azure SQL Database
                                        │
                                        ▼
                               Reporting & Analytics
```

---

# ⚙ Pipeline Workflow

## 1. Data Ingestion

Fleet telemetry is received as JSON files and stored in Azure Blob Storage.

The data contains:

* Vehicle ID
* Driver ID
* Timestamp
* Speed
* Fuel Level
* Temperature
* GPS Coordinates
* Engine Status

---

## 2. Master Pipeline

`PL_MasterFleetTelemetry` serves as the orchestration layer for the entire solution.

Responsibilities include:

* Coordinating pipeline execution
* Managing dependencies
* Triggering validation
* Loading validated data into SQL
* Monitoring execution flow

---

## 3. Validation Pipeline

The **Run_Validation** activity executes **PL_Databricks_Validation**, which launches an Azure Databricks notebook.

PySpark performs:

* JSON ingestion
* Schema enforcement
* Data cleansing
* Business transformations
* Medallion Architecture processing
* Validation against business rules

Validated datasets are written back to Azure Blob Storage for downstream consumption.

---

## 4. SQL Load Pipeline

After successful validation, **Run_LoadToSQL** executes.

The pipeline performs:

### Copy Activity

Validated telemetry is copied into Azure SQL staging tables.

### Stored Procedure

**usp_InsertPipelineAudit**

Records pipeline metadata including:

* Pipeline Name
* Execution Time
* Status
* Row Count
* Audit Timestamp

### Stored Procedure

**usp_VerifyFleetTelemetry**

Performs SQL-based validation to verify:

* Vehicle ID format
* Driver ID format
* Missing timestamps
* Temperature range
* Speed limits
* Fuel level range
* GPS coordinates
* Engine status values

The procedure generates validation metrics that support operational monitoring and data quality reporting.

---

# 🧹 Data Quality Framework

The platform validates every incoming telemetry record before it reaches the reporting layer.

Implemented validation rules include:

* Vehicle ID format (`TRK######`)
* Driver ID format (`DRV#####`)
* Timestamp validation
* Temperature range validation
* Speed range validation
* Fuel level validation
* Latitude validation
* Longitude validation
* Engine status validation
* Null value detection

Validation metrics are generated both during PySpark processing and through SQL verification procedures.

---

# 🏛 Medallion Architecture

The project follows the Medallion Architecture pattern to progressively improve data quality.

### 🥉 Bronze

* Raw JSON ingestion
* Immutable landing data

### 🥈 Silver

* Cleansed datasets
* Standardized schema
* Business rule validation
* Data quality enforcement

### 🥇 Gold

* Curated business-ready datasets
* SQL reporting layer
* Analytics-ready data

---

# ☁ Azure Services

* Azure Data Factory
* Azure Databricks
* Azure Blob Storage
* Azure SQL Database
* Azure DevOps
* Azure Storage Explorer

---

# 💻 Technologies

### Data Engineering

* PySpark
* Spark SQL
* T-SQL
* JSON

### Azure

* Azure Data Factory
* Azure Databricks
* Azure SQL Database
* Azure Blob Storage

### Engineering Practices

* ETL / ELT Pipelines
* Incremental Loading
* Medallion Architecture
* Data Validation Framework
* Pipeline Auditing
* CI/CD Integration
* Git Version Control

---

# 🚀 Key Features

* Enterprise Azure Data Engineering architecture
* End-to-end ETL pipeline
* Modular Azure Data Factory orchestration
* Azure Databricks notebook processing
* PySpark-based transformations
* Business rule validation
* Data quality monitoring
* SQL verification procedures
* Incremental data loading
* Pipeline audit logging
* Automated SQL data loading
* CI/CD-enabled deployment
* Production-ready cloud architecture

---

# 📂 Repository Structure

```text
Azure-Fleet-Telemetry-Data-Engineering/
│
├── Azure Data Factory/
│   ├── PL_MasterFleetTelemetry
│   ├── PL_Databricks_Validation
│   └── Copy Activities
│
├── Databricks/
│   ├── Bronze
│   ├── Silver
│   ├── Gold
│   └── PySpark Notebooks
│
├── SQL/
│   ├── Tables
│   ├── Stored Procedures
│   ├── Validation Queries
│   └── Audit Scripts
│
├── Sample Data/
│   └── FleetTelemetry.json
│
├── Architecture/
│   └── Solution Diagram
│
└── README.md
```

---

# 🎯 Skills Demonstrated

* Azure Data Engineering
* Azure Data Factory
* Azure Databricks
* PySpark Development
* Spark SQL
* Azure SQL Database
* JSON Processing
* ETL Pipeline Design
* Incremental Data Loading
* Data Validation Framework
* Stored Procedure Development
* Pipeline Auditing
* Medallion Architecture
* CI/CD Integration
* Enterprise Data Architecture

---

# 🔮 Future Enhancements

* Delta Lake implementation
* Unity Catalog integration
* Real-time ingestion with Azure Event Hubs
* Power BI dashboards
* Azure Monitor integration
* Automated data quality alerts
* Data lineage and governance
* Performance optimization using partitioning

---

## 👨‍💻 Author

This project was developed as an enterprise-style Azure Data Engineering portfolio demonstrating cloud-native data ingestion, transformation, orchestration, validation, auditing, incremental loading, and deployment using the Microsoft Azure ecosystem and industry-standard data engineering practices.
