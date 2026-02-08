# Project 1 Customer Account Analysis Pipeline


## 📌 Project Overview
The Customer Account Analysis Pipeline is an end-to-end data engineering solution designed to ingest, transform, and analyze customer account data. We ingest data from REST APIs and On-Premises SQL Servers, transform it using the **Medallion Architecture** (Bronze → Silver), and load it into an Azure SQL Database for visualization in Power BI. This project demonstrates the ability to handle raw data, apply business logic for data cleaning, and generate actionable insights through a structured data pipeline.



## 🏗️ Architecture Diagram
The pipeline follows a modern cloud data architecture:

1. **Security:** Azure Key Vault stores all database credentials and API keys.
2. **Ingestion:** - **REST API:** Ingested via Scheduled Trigger to ADLS Gen2 (Bronze).
   - **On-Prem SQL:** 5 tables (Customer, Product, Sales, etc.) extracted via Self-Hosted Integration Runtime.
3. **Transformation (Data Flows):**
   - Handling Nulls/Zeros in Primary Keys.
   - Deduplication and column pruning.
   - Implementation of **SCD Type 1** and **SCD Type 2**.
4. **Storage:** ADLS Gen2 (Bronze/Silver) and Azure SQL Database (Gold/Target).
5. **Transformation**: ADF Mapping Data Flows (Deduplication, Null Handling, SCD Type 1 & Type 2).
6. **Orchestration:** ADF Pipelines triggered by Schedule and Storage Events.
7. **Target**: Azure SQL Database & Power BI for visualization.


## Repository Structure

```text
├── Code/
│   ├── adf_pipelines/      # JSON exports of API and SQL ingestion pipelines
│   ├── data_flows/         # Data Flow logic for Deduplication, Null checks, and SCD
│   └── sql_scripts/        # DDL/DML for Customer, Product, Sales, and Category tables
├── Documentation/          # Architecture diagrams and step-by-step process docs
├── Screenshots/            # Validation screenshots of successful pipeline runs
└── README.md               # Project documentation
```

## Project Architecture

1. **RestApi Architecture**
<img width="612" height="221" alt="Http_ADF_pipeline_flow drawio" src="https://github.com/user-attachments/assets/0677d617-7334-446a-8109-622edb700b5b" />

2. **On-Prem To SQL Architecture**
<img width="1544" height="721" alt="on_prem_to_sql drawio" src="https://github.com/user-attachments/assets/c0b1e9fb-707a-4e4b-8366-d8eb7b41d260" />


## Setup Instructions
1. **Prerequisites:**
   - Azure Subscription.
   - Power BI Desktop (installed via [Microsoft Link](https://www.microsoft.com/en-us/download/details.aspx?id=58494)).
   - SQL Server Management Studio
   - Draw.io for architecture updates.

2. **Database Setup:**
   - Run the scripts located in `/Code/sql_scripts/` to create your schema and sample data.

3. **ADF Configuration:**
   - Import the JSON files from `/Code/adf_pipelines/`.
   - Ensure the Linked Services are updated to point to your **Azure Key Vault** for secret retrieval.

## Data Validations
- **Row Count Check:** Validated at each transition (Bronze to Silver, Silver to SQL).
- **Data Quality:** Primary key null-checks, duplicates and zero-value filters applied in Data Flows.

## Project Deliverables
- **SQL Scripts:** DDL and DML for environment setup.
- **Pipeline JSON:** Exported ADF logic.
- **Documentation:** Detailed step-by-step implementation guide.
- **Visuals:** Power BI dashboard analyzing sales trends.

## 👤 Author and Contributors
Bhim Sen
