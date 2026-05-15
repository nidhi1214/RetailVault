# RetailVault
Hey there! the project that covers the absolute entire data engineering lifecycle—from the second raw data lands to the moment it powers executive dashboards. It is a blueprint of how modern data platforms are built in the real world using the Medallion Architecture, robust governance and  automated workflows.

# Comprehensive End-to-End Azure Data Engineering Platform
### A Production-Grade Implementation of the Medallion Architecture

![Platform Banner](https://img.shields.io/badge/Platform-Azure-0089D6?style=for-the-badge&logo=microsoft-azure&logoColor=white)
![Engine-PySpark](https://img.shields.io/badge/Engine-PySpark-E25A1C?style=for-the-badge&logo=apache-spark&logoColor=white)
![Storage-Delta_Lake](https://img.shields.io/badge/Storage-Delta_Lake-00A4EF?style=for-the-badge)
![Status-Production_Ready](https://img.shields.io/badge/Status-Production_Ready-46A094?style=for-the-badge)

## 📝 Project Vision & Motivation

This project represents weeks of dedicated engineering, architectural design, and end-to-end implementation built entirely from scratch. I designed this platform to simulate a real-world enterprise data infrastructure, overcoming the challenges of handling messy, unstructured source data and converting it into high-value, business-ready insights.

Every stage—from configuring cloud storage networks, writing optimized PySpark scripts, establishing robust secrets governance, to building interactive executive dashboards—was developed independently. The ultimate goal was to achieve **100% automation with zero manual intervention**, high observability, and strict data integrity.

---

## 🏗️ Core Architecture Diagram

I designed a modular cloud architecture utilizing the **Medallion Framework**. Below is the data flow blueprint that illustrates how raw data moves through ingestion, validation, dimensional modeling, and final semantic visualization.

> **Architectural Note:** *Replace the placeholder below with your actual architecture diagram image once uploaded to your GitHub repository.*

![System Architecture Diagram](https://images.unsplash.com/photo-1551288049-bebda4e38f71?q=80&w=1200&auto=format&fit=crop)  
*Figure 1: Custom Engineered Multi-Tier Data Pipeline Architecture.*

---

## 🛠️ The Medallion Lifecycle: How It Works

### 🟫 1. The Bronze Layer (Ingestion & Raw Retention)
* **Goal:** Securely capture and store raw operational data lakes without altering the source state.
* **Implementation:** I configured automated pipelines within **Azure Data Factory** to detect landing files in **Azure Data Lake Storage (ADLS) Gen2**. The data is written as immutable historical records using the Delta format, ensuring we have a reliable point of recovery for pipeline replays.

### ⬜ 2. The Silver Layer (Data Cleansing & Evolution Management)
* **Goal:** Transform chaotic raw logs into a unified, high-quality corporate record.
* **Implementation:** This is where the heavy lifting happens. I built **PySpark** routines and **Delta Live Tables (DLT)** to:
  * Enforce strict schema constraints and handle schema evolution gracefully.
  * Deduplicate records using system look-back windows.
  * Handle missing values and drop records that fail critical quality checks (e.g., missing primary keys).

### 🟨 3. The Gold Layer (Star Schema & Business Modeling)
* **Goal:** Optimize the clean data for analytical performance and business logic.
* **Implementation:** I modeled the datasets into an enterprise-grade **Star Schema** consisting of highly optimized Fact and Dimension tables. Using Spark broadcasting and partitioning strategies, I maximized query performance, reducing join costs before pushing the aggregated structures into an **Azure Synapse Dedicated SQL Pool**.

---

## 📂 Repository Blueprint

I organized the codebase logically to decouple data orchestration from core compute scripts:

```text
├── .github/workflows/   # CI/CD pipelines for automated notebook deployment
├── notebooks/           # Core Databricks Notebooks
│   ├── 01_Ingestion/    # Raw source parsing and Bronze layer writing
│   ├── 02_Cleansing/    # Silver layer deduplication & data quality validation
│   └── 03_Modeling/     # Gold layer dimensional mapping (Facts & Dimensions)
├── dlt_pipelines/       # Declarative Delta Live Tables configurations
├── synapse_scripts/     # Enterprise Warehouse DDLs, indexes, and stored procedures
├── adf_orchestration/   # JSON compilation files for Azure Data Factory triggers
└── config/              # Security baseline, mount configurations, and parameter files
