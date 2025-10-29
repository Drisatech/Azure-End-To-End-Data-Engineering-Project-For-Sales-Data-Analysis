# 🌐 Azure End-to-End Data Engineering Pipeline  

[![Azure](https://img.shields.io/badge/Platform-Microsoft%20Azure-blue)](https://azure.microsoft.com)  
[![Power BI](https://img.shields.io/badge/Visualization-Power%20BI-yellow)](https://powerbi.microsoft.com)  
[![Databricks](https://img.shields.io/badge/Compute-Azure%20Databricks-orange)](https://azure.microsoft.com/en-us/products/databricks/)  
[![Synapse](https://img.shields.io/badge/Analytics-Azure%20Synapse%20Analytics-lightblue)](https://azure.microsoft.com/en-us/products/synapse-analytics/)  

This project demonstrates an **End-to-End Azure Data Engineering Solution** — a complete modern data pipeline that performs **Data Ingestion**, **ETL Processing**, **Data Transformation**, and **Analytics** using **Microsoft Azure Services** and **Power BI**.  

---

## 🎯 Project Goal  

The goal of this project is to **migrate an on-premise database** (Microsoft SQL Server) to the **Azure Cloud**, implementing a robust **ETL pipeline** using:  

- **Azure Data Factory (ADF)** for orchestration  
- **Azure Databricks** for transformation (PySpark-based)  
- **Azure Data Lake Storage (ADLS Gen2)** for data lake staging (Bronze–Silver–Gold architecture)  
- **Azure Synapse Analytics** for data loading and modeling  
- **Power BI** for reporting and visualization  

This architecture mirrors the **real-world enterprise data workflow**, where scalable, secure, and automated pipelines feed insights to business intelligence platforms.  

---

## 🧭 Architecture Overview  

![Azure Data Engineering Pipeline Architecture](https://github.com/Drisatech/Azure-End-To-End-Data-Engineering-Project-For-Sales-Data-Analysis/blob/main/Images/Arc%20img.png)

The pipeline integrates **Data Factory**, **Databricks**, **Synapse**, and **Power BI**, forming a unified flow from **raw data ingestion** to **actionable insights**.

---

## 🧠 Key Learnings & Skills  

By completing this project, I gained hands-on experience in:  
✅ Cloud-based Data Ingestion & Integration  
✅ ETL Design using Azure Data Factory  
✅ PySpark Data Transformation in Azure Databricks  
✅ Data Lakehouse Architecture (Bronze–Silver–Gold)  
✅ Data Modeling & Analytics with Azure Synapse  
✅ Visualization & Reporting in Power BI  
✅ Data Governance & Security via Azure Key Vault and Entra ID  

---

## 🧩 Prerequisites  

| Tool / Service | Purpose |
|-----------------|----------|
| **Microsoft SQL Server Management Studio (SSMS)** | Source Database |
| **Azure Subscription** | Cloud Platform |
| **Azure Data Factory** | Orchestration & Pipeline Automation |
| **Azure Databricks** | ETL Processing with PySpark |
| **Azure Synapse Analytics** | Data Modeling & Querying |
| **Azure Data Lake Storage Gen2** | Centralized Data Storage (Bronze/Silver/Gold) |
| **Azure Key Vault** | Secrets Management |
| **Microsoft Power BI** | Visualization Layer |

**Database Used:** `AdventureWorksLT2017` (Sales Database)  
Set up credentials (`usr1`) and store them as secrets in Azure Key Vault.

---

## ⚙️ Implementation Steps  

### 🔹 Part 1: Data Ingestion  

1. **Restore** the AdventureWorksLT2017 `.bak` file in SQL Server.  
   ![image](https://github.com/zBalachandar/AdventureWorks-Sales-Data-Analytics-Azure-Data-Engineering-End-to-End-Project/blob/main/pix/SOURCE%202017LTv1.png)  

2. **Establish Integration Runtime (IR)** to connect on-premise SQL Server with Azure Data Factory.  
3. **Create a Copy Pipeline** to move data from SQL Server into **Azure Data Lake Storage (Bronze layer)** in **Parquet format**.  

   ![ADF Copy Activity](https://github.com/Shashi42/Azure-End-to-End-Sales-Data-Analytics-Pipeline/assets/26250463/d2126d21-6f67-4fd1-bfa8-0902c5182ddc)

---

### 🔹 Part 2: Data Transformation  

Data is transformed in **Azure Databricks** using **PySpark Notebooks**, following the **Bronze → Silver → Gold** data refinement pattern.  

**Steps:**
1. Mount ADLS Gen2 in Databricks.  
2. **Bronze → Silver:** Clean and cast data types.  
3. **Silver → Gold:** Apply naming conventions and business transformations.  

Final **Gold-layer data** is stored in **Delta format**, optimized for analytics.  

![Databricks Storage Mount](https://github.com/zBalachandar/Tokyo-Olympic-Data-Analytics-Azure-End-To-End-Data-Engineering-Project-12/blob/45a3dedcef5ab3a1867dfafb655a827c3052b643/Assets/Storage%20Mount%200.png)  
![Databricks Notebook](https://github.com/Shashi42/Azure-End-to-End-Sales-Data-Analytics-Pipeline/assets/26250463/782503d8-453b-4bc4-8b24-5a2417bff378)  

These Databricks notebooks are then **integrated with ADF**, enabling a **fully automated ETL workflow**.  

---

### 🔹 Part 3: Data Loading  

The **Gold data** is loaded into **Azure Synapse Analytics**, where **Stored Procedures** dynamically:  
- Create or refresh views for each transformed table  
- Prepare data models for Power BI consumption  

![Synapse Pipeline](https://github.com/Shashi42/Azure-End-to-End-Sales-Data-Analytics-Pipeline/assets/26250463/7f935213-4dd9-471a-aa24-bc4b1c68f41b)

---

### 🔹 Part 4: Data Analytics & Reporting  

Power BI connects directly to **Azure Synapse Views** using **DirectQuery** mode.  
This ensures the dashboard always reflects the latest data updates from the automated pipeline.  

Interactive visuals showcase **Sales Performance**, **Customer Segmentation**, and **Product Profitability**.  

![Power BI Dashboard](https://github.com/zBalachandar/AdventureWorks-Sales-Data-Analytics-Azure-Data-Engineering-End-to-End-Project/blob/main/PowerBI%20files/PowerBI%20Reporting%20output.png)

---

### 🔹 Part 5: Automation & Scheduling  

Using **ADF Triggers**, the pipeline runs on a **daily schedule**, automating data refresh and transformation cycles.  

**Before Trigger Execution:**  
![Before Trigger](https://github.com/Shashi42/Azure-End-to-End-Sales-Data-Analytics-Pipeline/assets/26250463/51405c5f-331a-4bbd-83cf-439f91ca2525)  

**After Trigger Execution:**  
![After Trigger](https://github.com/Shashi42/Azure-End-to-End-Sales-Data-Analytics-Pipeline/assets/26250463/578aca35-89b1-4a31-b1e0-27fb7fd923ed)

---

## 🔒 Security & Governance  

- **Azure Key Vault** stores credentials, ensuring no hardcoded secrets in pipelines.  
- **Microsoft Entra ID (Azure Active Directory)** manages access permissions and security groups for collaborators.  

---

## 📚 References  

- [Mr. K Talks Tech – E2E Azure Data Engineering Project](https://www.youtube.com/watch?v=iQ41WqhHglk&t=3624s)  
- Microsoft Azure Official Documentation  
- Databricks Academy Tutorials  

---

## 🧾 End Notes  

- This project showcases a complete enterprise-grade **ETL + Analytics pipeline** using multiple Azure services.  
- The modular architecture allows easy **scalability**, **governance**, and **automation**.  
- While the dataset is small (AdventureWorksLT2017), the same principles apply to large-scale real-world data solutions.  
- Future improvements may include integration with **Azure Event Hub** or **Real-time Streaming Analytics**.  

---

### 👨‍💻 Author  
**Aliyu Idris Adeiza**  
Data Engineer | Azure & Python Developer | Power BI Analyst  

🔗 [GitHub](https://github.com/Drisatech) • [LinkedIn](https://linkedin.com/in/aliyu-idris-adeiza)  

---

### 📁 Repository Structure

📦 azure-data-engineering-pipeline
┣ 📂 notebooks/             # Databricks PySpark transformation scripts
┣ 📂 adf_pipelines/         # JSON definitions for ADF pipelines
┣ 📂 synapse_scripts/       # SQL scripts for Synapse
┣ 📂 powerbi/               # Power BI reports and dashboard files
┣ 📂 data/                  # Sample datasets (optional)
┗ 📜 README.md              # Project documentation

---

---

⭐ **If you find this project helpful, consider giving it a star on GitHub!**
