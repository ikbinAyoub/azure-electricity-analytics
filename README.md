# azure-electricity-analytics
Automated electricity price analytics pipeline using Azure and Power BI
> *This project demonstrates my hands-on learning and application of Azure cloud technologies, including Functions, Blob Storage, Synapse Analytics, SQL Database, Power BI and Cost Management.*
# ⚡ Automated Electricity Price Analytics Pipeline on Azure

## 📖 Project Overview

This project is an end-to-end cloud engineering solution designed to analyze electricity market volatility. It automates the extraction of daily electricity price data (from 2019 to present), processes it using a scalable ETL pipeline, and visualizes trends to identify market patterns.

The system is built entirely on **Microsoft Azure**, utilizing serverless computing, enterprise-grade warehousing, and modern BI tools to deliver actionable insights.

---

## 🏗️ Architecture & Data Flow

The pipeline follows a modern ELT (**Extract, Load, Transform**) pattern, ensuring data integrity and scalability.

**Workflow Steps:**

<img width="1654" height="599" alt="foto1 (2)" src="https://github.com/user-attachments/assets/289d8154-3c84-4ce5-81e8-80185afd3fcb" />

1. **Ingestion (Azure Functions):**
    - A Python-based Azure Function is triggered daily via a Timer Trigger.
    - It queries an open-source electricity market API (`api.awattar.de`) to fetch the latest pricing data.
    - *Function code screenshot:*
  
<img width="1890" height="792" alt="foto2" src="https://github.com/user-attachments/assets/344b2adb-e6a4-49bb-ae16-f4319b4a341c" />

2. **Raw Storage (Azure Blob Storage Gen2):**
    - Data is ingested as raw JSON files into a secured Blob Storage container.
    - This acts as the Data Lake, holding both historical data (2019–2024) and new daily increments.
    - *Screenshot: Azure Blob Storage container with daily price JSON files:*

<img width="1627" height="726" alt="foto3" src="https://github.com/user-attachments/assets/731f4786-0200-4543-82df-815eafb38526" />

3. **Processing (Azure Synapse Analytics):**
    - Synapse pipelines orchestrate the transformation.
    - Tasks include normalizing JSON structures, converting Unix timestamps to datetime objects, and cleaning null values.
    - *Synapse Pipeline screenshot:*
<img width="1555" height="769" alt="foto5" src="https://github.com/user-attachments/assets/1e96c4cd-58f9-481c-89bd-b083d93580ee" />

4. **Warehousing (Azure SQL Database):**
    - Cleaned, structured data is loaded into an Azure SQL Database.
    - This serves as the "Gold" layer, optimized for high-performance querying and reporting.
    - *Screenshot: Azure SQL Database with price data:*
    
<img width="1456" height="847" alt="foto4" src="https://github.com/user-attachments/assets/18b171d5-c7d2-4034-b2f0-d2f9b482cf0a" />

5. **Visualization (Power BI):**
    - Power BI connects directly to the SQL Database via DirectQuery/Import.
    - Dashboards provide insights into daily volatility, day vs. night pricing, and long-term trends.
    - *Screenshot: Power BI dashboard example:*

<img width="1802" height="919" alt="foto6" src="https://github.com/user-attachments/assets/db284213-2a32-49a6-a9c6-bce31a7c909b" />


## 📊 Dashboard Insights

The Power BI report is designed to answer key business questions regarding energy costs:

- **Daily Price Range:** Visualizes the spread between the lowest and highest prices of the day.
- **Volatility Analysis:** A dedicated KPI showing price fluctuation percentages.
- **Day vs. Night:** Compares average pricing windows to determine optimal energy usage times.
- **Weekly Trends:** Analysis of price drops on weekends vs. weekdays.

---

## 💰 Azure Cost Management

Controlling and forecasting cloud costs is essential in any real-world solution. Here is a snapshot of the Azure Cost Analysis for this project deployment, showing actual and forecasted expenditure per resource:

<img width="1896" height="824" alt="foto7" src="https://github.com/user-attachments/assets/24ad1bc1-5712-4952-914b-94b88d947ff2" />
---

## 📦 Possible Use Cases & Extension Ideas

- **Dynamic Price Notifications:**  
  Automated email or push notifications when electricity prices are exceptionally high or low.

- **Forecasting & Machine Learning:**  
  Develop predictive models for future electricity prices using machine learning algorithms and historical market data.
  
  **Reproducible Infrastructure with Terraform & Flexible Data Sources:**  
  Use Terraform (Infrastructure as Code) to automate and version-control the deployment of all Azure resources (Function App, Storage, Synapse, SQL, etc.).  
  Extend the solution to fetch data from various APIs beyond electricity market data, enabling scalable data ingestion, unified storage, and integrated analytics for diverse datasets.

---

**Contact:** [linkedin Profile](https://www.linkedin.com/in/ayoub-b-b42aa72a6/)
