# AW-Azure-Data-Engineering-Project
**📂 Azure Data Engineering Project: End-to-End Real-Time Pipeline**  

---

### **🔍 Overview**  
**Project Description**:  
This end-to-end Azure data pipeline processes real-world sales data using a **three-layer architecture** (Bronze for raw ingestion, Silver for Spark transformations, Gold for analytics-ready outputs). It automates data ingestion from APIs via Azure Data Factory, cleans and enriches datasets in Databricks (e.g., date parsing, aggregations), and loads refined data into Synapse Analytics for reporting. Built with security in mind—using RBAC roles and managed identities—it mirrors industry practices, turning raw, messy API data into structured insights while ensuring scalable cloud workflows and access controls.

---

### **🏗️ Architecture**  
1. **Bronze Layer (Raw Data)**:  
   - **Source**: AdventureWorks data pulled from GitHub APIs using **Azure Data Factory (ADF)**.  
   - **Storage**: Raw data stored in **Azure Data Lake Gen2** (CSV format).  

2. **Silver Layer (Cleaned/Transformed Data)**:  
   - **Transformation**: PySpark in **Azure Databricks** (date parsing, column splitting, aggregations).  
   - **Storage**: Processed data saved as Parquet files in Data Lake.  

3. **Gold Layer (Serving Layer)**:  
   - **Data Warehouse**: Structured tables in **Azure Synapse Analytics** for BI/reporting.  
   - **Visualization**: Power BI dashboards connected to Synapse.  

---

### **🛠️ Tools & Technologies**  
| **Category**       | **Tools Used**                                      |  
|---------------------|-----------------------------------------------------|  
| **Orchestration**   | Azure Data Factory (Dynamic Pipelines, Parameters)  |  
| **Transformation**  | Azure Databricks (PySpark, Spark SQL)               |  
| **Storage**         | Azure Data Lake Gen2 (Bronze/Silver/Gold containers)|  
| **Analytics**       | Azure Synapse Analytics (Serverless SQL Pool)        |  
| **Visualization**   | Power BI                                            |  

---

### **🚀 Key Features**  
1. **Dynamic Data Ingestion**:  
   - ADF pipelines use **parameters and loops** to process 10+ tables from APIs dynamically.
   - **Dynamic Pipelines in ADF**:
      - Parameterized Datasets & Linked Services: Avoided hardcoding by using parameters for file paths, containers, and API URLs. For example:
      - Created a config.json file stored in Azure Data Lake to define source files, destinations, and transformations.
      - Used Lookup Activity to fetch configurations and ForEach Loops to iterate over files (e.g., 10+ AdventureWorks tables).
Example JSON structure:
   - Example: Auto-fetching `Sales_2015.csv`, `Sales_2016.csv`, etc., without hardcoding paths.
     <img src="https://github.com/user-attachments/assets/f46b4890-37a6-405e-ba88-910c16752a15" width="450" height="270">


2. **PySpark Transformations**:  
   - **Data Cleaning**: Split product codes, handle nulls, parse dates.  
   - **Advanced Functions**: `withColumn`, `groupBy`, `concat_ws`, and window functions.  
   - **Data Analysis**: Aggregated sales trends and visualized results in Databricks notebooks.  

3. **Cost Optimization**:  
   - Used **locally redundant storage (LRS)** for non-critical data.  
   - Auto-terminating Databricks clusters to save costs.  

4. **Real-time Focused Scenarios**:  
   - Solved questions like *“Blob vs. Data Lake?”*, *“Explain ADF triggers”*, and *“Dynamic vs. Static Pipelines”*.

5. **Access Controls & Security**:
   - **Service Principals**: Created an Azure AD app to grant Databricks secure access to Data Lake (using Storage Blob Contributor role).
   - **Managed Identity**: Enabled Synapse Analytics’ system-managed identity to access Data Lake without exposing credentials.
   - **RBAC**: Applied role-based access controls (e.g., LRS redundancy, private endpoints for sensitive data).

---

### **📈 Steps to Build**  
1. **Set Up Azure Resources**:  
   - Created Resource Group, Data Lake, ADF, Databricks workspace, and Synapse Analytics.  

2. **Ingest Data with ADF**:  
   - Built pipelines to pull CSV files from GitHub APIs into Bronze layer.  
   - Used **linked services** and **parameterized datasets** for scalability.  

3. **Transform in Databricks**:  
   - Read Bronze data, applied transformations (e.g., `split` product IDs, `to_timestamp`).  
   - Wrote transformed data to Silver layer (Parquet).  

4. **Serve Data in Synapse**:  
   - Created SQL tables in Synapse for reporting.  
   - Joined fact/dimension tables (e.g., `Sales` ↔ `Products`).  

5. **Connect to Power BI**:  
   - Built dashboards to visualize sales trends, product performance, etc.
   <img src="https://github.com/user-attachments/assets/0ab36012-cde5-441d-8847-8370b9287a5e" width="450" height="330">


---

### **📌 Outcomes**  
- **Technical Skills Proved**:  
  - Built a **scalable, low-code pipeline** with ADF.  
  - Mastered Spark for big data transformations.  
  - Designed a cloud data warehouse in Synapse.  

- **Impact**:  
  - Discussed **real-time use cases** (e.g., handling incremental loads, cost optimization).  
  - Explained architecture tradeoffs (e.g., why Medallion over a single-layer lake?).  

---

**🔗 GitHub Repo Contents**:  
- `ADF Pipelines`: JSON templates for dynamic data ingestion.  
- `Databricks Notebooks`: PySpark code for transformations.  
- `Synapse SQL Scripts`: DDL/DML for tables and views.  
- `Power BI Reports`: Sample dashboards.  

---
