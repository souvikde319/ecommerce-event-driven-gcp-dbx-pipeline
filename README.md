# 🚀 Event-Driven Data Pipeline | GCP → Databricks Lakehouse

<p align="left">
  <img src="https://img.shields.io/badge/Cloud-GCP-blue?logo=googlecloud&logoColor=white" />
  <img src="https://img.shields.io/badge/Compute-Databricks-red?logo=databricks&logoColor=white" />
  <img src="https://img.shields.io/badge/Storage-Delta%20Lake-green?logo=delta&logoColor=white" />
  <img src="https://img.shields.io/badge/Language-PySpark-orange?logo=apache-spark&logoColor=white" />
  <img src="https://img.shields.io/badge/Governance-Unity%20Catalog-purple" />
</p> 

---

## 📌 Project Overview
This project implements an **end-to-end, event-driven data ingestion and analytics pipeline** using **Google Cloud Storage (GCS)** and **Databricks Lakehouse architecture**.  
The pipeline automatically triggers when files are dropped into GCS buckets and processes data through **staging, validation, enrichment, and analytics layers**, producing analytics-ready Delta tables.

---

## 🏗️ Architecture & Data Flow

### 🔄 High-Level Flow
- Source data lands in GCS buckets
- Databricks pipeline is triggered automatically
- Data flows through Bronze → Silver → Gold layers
- Final analytics tables are stored in Delta Lake

---

## 📊 Pipeline Diagram

> 📁 Diagram file included: `gcp_databricks_pipeline.drawio`  
(Open with https://app.diagrams.net)

```mermaid
flowchart LR
    A[GCS Customers] --> S[Stage Load]
    B[GCS Inventory] --> S
    C[GCS Orders] --> S
    D[GCS Products] --> S
    E[GCS Shipping] --> S

    S --> V[Data Validation]
    V --> E1[Data Enrichment]
    E1 --> G[Final Merge - Gold]

    G --> D1[Delta Lake + Unity Catalog]
