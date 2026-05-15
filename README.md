# RetailVault
Hey there! the project that covers the absolute entire data engineering lifecycle—from the second raw data lands to the moment it powers executive dashboards. It is a blueprint of how modern data platforms are built in the real world using the Medallion Architecture, robust governance and  automated workflows.

# Enterprise Data Engineering Platform: End-to-End Incremental Retail Pipeline
### Production-Grade Ingestion, Governance, Dimensional Modeling, and Workflows on Azure Databricks

![Platform-Azure](https://img.shields.io/badge/Platform-Azure-0089D6?style=for-the-badge&logo=microsoft-azure&logoColor=white)
![Engine-PySpark](https://img.shields.io/badge/Engine-PySpark-E25A1C?style=for-the-badge&logo=apache-spark&logoColor=white)
![Storage-Delta_Lake](https://img.shields.io/badge/Storage-Delta_Lake-00A4EF?style=for-the-badge)
![Governance-Unity_Catalog](https://img.shields.io/badge/Governance-Unity_Catalog-FF6F00?style=for-the-badge)
![Status-Production_Ready](https://img.shields.io/badge/Status-Production_Ready-46A094?style=for-the-badge)

---

## 📝 Project Overview & Motivation

This repository represents an intensive, production-scale implementation of a modern retail data platform that I built entirely from the ground up. Moving far shadow of a basic tutorial or hobby script, this platform represents hours of dedicated engineering to handle advanced enterprise data engineering principles—such as infrastructure provisioning, strict cloud network administration, programmatic data quality enforcement, and fully automated, event-driven pipelines with zero manual intervention.

I designed and engineered the entire pipeline to ingest complex columnar data increments, refine them through a unified Medallion Architecture, manage historical state changes using Slowly Changing Dimensions (SCD Type 1 & Type 2), and deliver high-performance semantic views to power downstream business dashboards.

### 🌟 Key Architectural & Engineering Milestones:
* **Admin-to-Developer Execution:** I hand-provisioned the storage firewalls, Unity Catalog metastores, and external storage credentials to mirror an actual enterprise security landscape.
* **Production Ingestion Framework:** I built a 100% idempotent structured streaming flow using Auto Loader with programmatic schema evolution controls.
* **Software Engineering for Data:** I applied unified Python Object-Oriented Programming (OOP) classes tightly integrated within my PySpark processing.
* **Hybrid Modeling Strategy:** I hand-coded custom PySpark Merge operations for target tables paired alongside declarative Delta Live Tables (DLT) for streaming state maintenance.

---

## 🏗️ Architecture Blueprint

I decoupled the compute-and-storage pattern over the **Medallion Framework** across three distinct structural horizons (Bronze, Silver, and Gold):
<img width="1500" height="1778" alt="image" src="https://github.com/user-attachments/assets/18359216-5224-4576-b371-ee4b2891e1b7" />


> **Architectural Note:** *Replace the placeholder below with your actual architecture diagram image once uploaded to your GitHub repository.*

![System Architecture Diagram](https://images.unsplash.com/photo-1551288049-bebda4e38f71?q=80&w=1200&auto=format&fit=crop)  
*Figure 1: Custom Engineered Multi-Tier Data Pipeline Architecture.*

---

## 🛠️ Multi-Layer Lifecycle & Technical Highlights

### 🟫 1. The Bronze Layer (Streaming Ingestion & Auto Loader)
* **Ingestion Strategy:** I configured the pipeline to capture raw incremental files (shipped as compressed columnar Parquet files) from Azure Data Lake Storage (ADLS) Gen2 using **Spark Structured Streaming** and **Databricks Auto Loader (`cloudFiles`)**.
* **Idempotency & Guardrails:** I configured explicit trigger settings (`AvailableNow`) paired with localized checkpoint management directory tracking. This guarantees exactly-once processing constraints (Idempotency), preventing downstream operational duplication.
* **Schema Evolution:** I implemented isolated schema log locations. The engine dynamically infers file adjustments, trapping structural variations without causing streaming jobs to drop or terminate.

### ⬜ 2. The Silver Layer (Enterprise Transformation & Python OOP)
* **Object-Oriented PySpark:** I designed modular Python classes to systematically clean records. I abstracted the ingestion structures through programmatic routines, ensuring absolute structural reusability across diverse source streams.
* **Data Cleansing Guardrails:** I enforced row-level data quality thresholds. My processing logic captures and isolates corrupted variants, standardizes primitive types, handles missing values, and prunes missing entity keys.
* **Unity Catalog Reusable Functions:** I built custom, catalog-registered functions inside Unity Catalog to enforce corporate business data transforms globally across distinct organizational domains.

### 🟨 3. The Gold Layer (Star Schema, SCD Type 1 & Type 2)
The curated analytical destination is constructed using a hybrid strategy to model a comprehensive **Star Schema** comprised of distinct Dimension and Fact tables:
* **SCD Type 1 (Overwrite/Upsert):** I implemented this programmatically by constructing direct PySpark `MERGE INTO` conditional trees, recalculating rolling business metrics while tracking structural state tables natively.
* **SCD Type 2 (Historical Tracked):** I engineered this layer utilizing **Delta Live Tables (DLT)**. Leveraging the declarative DLT API (`dlt.apply_changes`), my pipeline records audit histories by automatically generating system `START_AT`, `END_AT`, and `IS_CURRENT` flag markers.

---

## 📂 Repository Structure

I organized the codebase to isolate job orchestration definitions from active data engine compute:

```text
├── config/                 # Cloud network configurations & ADLS Storage Mount definitions
├── notebooks/              # Operational Core Compute Engine Notebooks
│   ├── 01_Ingestion/       # Auto Loader configuration files parsing raw data to Bronze
│   ├── 02_Cleansing/       # Python OOP classes applying business filtering rules for Silver
│   └── 03_Modeling/        # Custom SQL MERGE statement configurations establishing Gold
├── dlt_pipelines/          # Declarative Delta Live Tables configurations for SCD Type 2 state tracking
├── workflows/              # Parameterized JSON blueprints mapping multi-task workflow lineages
└── sql_scripts/            # Data Warehouse schema configurations and Fact table def
