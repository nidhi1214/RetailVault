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
