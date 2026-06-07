# ecommerce-data-engineering-project

This repository contains hands-on data engineering projects covering the complete modern data engineering lifecycle, from building a Lakehouse architecture and ETL pipelines to implementing real-time analytics, machine learning pipelines, and semantic search applications.

The project is structured into three architectural paradigms: 
  - **Modern Data Lakehouse**
  - **Streaming & Real-Time Analytics**
  - **Data Engineering for AI/ML**

The architecture is implemented using the Open-Source `Apache` Ecosystem to solve critical business problems including scalability, real-time inventory tracking, anomaly detection, and personalized user experiences.

## 🏗️ System Architecture Overview

```text
                ┌───────────────┐
                │ Source Systems│
                └───────┬───────┘
                        │
                        ▼
               ┌─────────────────┐
               │ Apache Iceberg  │
               │ Lakehouse       │
               └───────┬─────────┘
                       │
         ┌─────────────┼─────────────┐
         ▼             ▼             ▼
      Bronze         Silver         Gold
       Layer          Layer         Layer
         │             │             │
         ▼             ▼             ▼
      Spark ETL    Data Models   BI & ML
                                   │
                ┌──────────────────┼──────────────────┐
                ▼                  ▼                  ▼
            Superset         Recommendation      Semantic
            Dashboard          Engine             Search
```

## 🛠️ Tech Stack
*   **Storage & Format:** Apache Iceberg, MinIO
*   **Compute & Query Engines:** Apache Spark, Trino
*   **Streaming & Ingestion:** Apache Kafka, Debezium (CDC), Apache Flink
*   **Orchestration & Analytics:** Apache Airflow, ClickHouse, OpenSearch
*   **AI/ML & Vector:** Spark MLlib, PostgreSQL
*   **Visualization:** Apache Superset, Streamlit


## 📁 Repository Structure & Projects

### 🌟 Part 1: Modern Data Lakehouse & Batch ETL
This section covers the core data infrastructure, utilizing the **Medallion Architecture** to transform raw transactional data into business insights.

*   **Infrastructure Setup (Data Lakehouse):** Implemented an **Apache Iceberg** data lakehouse from the ground up to serve as the unified storage layer for OneShop's data assets.
*   **Batch ETL Pipelines (Spark):** Developed PySpark batch pipelines to ingest raw application logs into the **Bronze layer**, applying schema enforcement and data cleaning to populate the **Silver layer**.
*   **Ad-hoc Querying & Business Intelligence:** Defined analytical business models in the **Gold layer** using **Trino** as the distributed query engine, creating interactive executive dashboards via **Apache Superset**.
*   **Workflow Orchestration (Airflow):** Automated a customer segmentation pipeline. Airflow coordinates dependencies across Silver tables, extracts high-value segments, exports the results to MinIO storage as CSVs, and triggers automated email alerts to the marketing team.


### ⚡ Part 2: Streaming & Real-Time Analytics
Shifting from batch to sub-second latency, this section focuses on event-driven streaming architectures using the **Apache Kafka** ecosystem.

*   **Change Data Capture (CDC):** Deployed a **Debezium** connector on a transactional PostgreSQL database to capture real-time inventory level changes, streaming mutations into Kafka, and reliably updating a search index in **OpenSearch** for zero-lag storefront inventory tracking.
*   **Flash Sale Real-Time Dashboard:** Built a high-throughput streaming pipeline using Kafka, **ClickHouse** (OLAP storage), and **Streamlit** to provide live telemetry on conversion rates and traffic spikes during flash sales.
*   **Anomaly Detection:** Implemented a stateful stream processing application using **Apache Flink** to monitor user login streams and flag anomalous, potentially fraudulent access patterns in real-time.


### 🤖 Part 3: Data Engineering for AI/Machine Learning
Demonstrating how robust data pipelines serve as the foundation for modern machine learning and cognitive search systems.

*   **Recommendation Engine Feature Store:** Engineered a machine learning feature pipeline using **Spark MLlib**. The pipeline extracts user behavior signals from Silver tables, computes behavioral features, and stores them in a high-performance Gold layer feature table optimized for a product recommendation model.
*   **Semantic Similarity Search Engine:** Built an AI-powered customer review analytics engine. Leveraged the **`pgvector`** extension on PostgreSQL to store and query high-dimensional text embeddings of customer reviews, enabling semantic similarity search and sentiment clustering.


