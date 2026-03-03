# Customer Account Analysis: End-to-End Microsoft Fabric Solution

## 📌 Project Overview
This project demonstrates a comprehensive Data Engineering and Analytics solution using Microsoft Fabric. The goal is to integrate data from diverse sources—On-Premise SQL Server and Azure Data Lake Storage (ADLS) Gen2—into a unified Fabric Lakehouse.


## 🏗️ Architecture Diagram
The pipeline follows a modern cloud data architecture:
![project_5](https://github.com/user-attachments/assets/8e5f6c0d-44c0-4ec3-945f-985b26fda98c)



1. **Source: On-Premise** Customer data extracted from SQL Server using the On-Premise Data Gateway.

2. **External Cloud Source:** Data brought in from ADLS Gen2 using Fabric Shortcuts (eliminating data duplication).

3. **Bronze Layer (Lakehouse):** Raw landing zone for SQL Server and ADLS data.
   
4. **Silver Layer (Dataflow Gen2):** Data cleaning, transformation, and schema refinement.

5. **Gold Layer (Warehouse/Lakehouse):** Implementation of SCD Type 1/Type 2 logic to maintain historical accuracy.
   
6. **Orchestration:** Fabric Pipelines for automated daily scheduling.
 
7. **Visualization:** Power BI reports connected directly to Lakehouse tables via DirectLake mode


## Repository Structure

```text
├── Code/
├── Dataflows/             # Dataflow Gen2 transformation logic
├── SQL_Scripts/           # SCD Type logic and Warehouse stored procedures
├── PowerBI/               # .PBIT or Screenshots of the final Dashboard
├── Screenshots/
│   ├── Architecture Diagram/          # Diagram for Architecture
└── README.md                          # Project documentation
```



## Pipeline Workflow
**Step 1:** Data Ingestion & Bronze Layer
- On-Premise Integration: Connected to SQL Server to ingest customer account records into the Fabric Lakehouse (Bronze).
- Fabric Shortcuts: Created a "Zero-Copy" shortcut to ADLS Gen2, allowing the Lakehouse to reference external cloud data without moving the physical bytes.

**Step 2:** Cleaning & Transformation (Silver)
- Utilized Dataflow Gen2 to handle data cleansing.
- Applied transformations: data type casting, null handling, and column renaming to ensure the data is "analytics-ready."

**Step 3:** Historical Tracking (Gold/Warehouse)
- Loaded data into the Data Warehouse.
- Implemented SCD (Slowly Changing Dimensions) logic to track changes in customer account statuses over time, ensuring accurate historical reporting.

**Step 4:** Orchestration & Migration
- Scheduling: Configured a Fabric Pipeline to trigger the entire end-to-end workflow daily.
- Workspace Migration: Demonstrated environment lifecycle management by migrating pipelines and artifacts between different Fabric Workspaces.

**Step 4:** Visualization
- Developed a Power BI report utilizing the Lakehouse's SQL endpoint.
- Key Metrics: Account growth, customer distribution, and status change trends.


📊 Business Insights
- Unified Governance: Single pane of glass for on-premise and cloud data using Fabric.
- Storage Efficiency: Reduced costs by using Shortcuts instead of traditional ETL for ADLS data.
- Data Integrity: SCD implementation ensures that historical account states are preserved for audit and trend analysis.

## 👤 Author and Contributors
Bhim Sen

