# Project_1_Customer_Account_Analysis_Pipeline


## Project Overview
This project implements an end-to-end retail sales data pipeline using **Azure Data Services**. We ingest data from REST APIs and On-Premises SQL Servers, transform it using the **Medallion Architecture** (Bronze → Silver), and load it into an Azure SQL Database for visualization in Power BI.



## Architecture
The solution follows these key architectural steps:
1. **Security:** Azure Key Vault stores all database credentials and API keys.
2. **Ingestion:** - **REST API:** Ingested via Scheduled Trigger to ADLS Gen2 (Bronze).
   - **On-Prem SQL:** 5 tables (Customer, Product, Sales, etc.) extracted via Self-Hosted Integration Runtime.
3. **Transformation (Data Flows):**
   - Handling Nulls/Zeros in Primary Keys.
   - Deduplication and column pruning.
   - Implementation of **SCD Type 1** and **SCD Type 2**.
4. **Storage:** ADLS Gen2 (Bronze/Silver) and Azure SQL Database (Gold/Target).
5. **Orchestration:** ADF Pipelines triggered by Schedule and Storage Events.

## Setup Instructions
1. **Prerequisites:**
   - Azure Subscription.
   - Power BI Desktop (installed via [Microsoft Link](https://www.microsoft.com/en-us/download/details.aspx?id=58494)).
   - Draw.io for architecture updates.

2. **Database Setup:**
   - Run the scripts located in `/Code/sql_scripts/` to create your schema and sample data.

3. **ADF Configuration:**
   - Import the JSON files from `/Code/adf_pipelines/`.
   - Ensure the Linked Services are updated to point to your **Azure Key Vault** for secret retrieval.

## Data Validations
- **Row Count Check:** Validated at each transition (Bronze to Silver, Silver to SQL).
- **Schema Validation:** JSON validation performed on all pipeline definitions.
- **Data Quality:** Primary key null-checks and zero-value filters applied in Data Flows.

## Project Deliverables
- **SQL Scripts:** DDL and DML for environment setup.
- **Pipeline JSON:** Exported ADF logic.
- **Documentation:** Detailed step-by-step implementation guide.
- **Visuals:** Power BI dashboard analyzing sales trends.

## Contributors
- Bhim Sen
